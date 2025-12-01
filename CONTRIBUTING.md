# Contributing Guideline

We follow this [GitHub contributing guideline](https://docs.github.com/en/contributing)

## Note/FYI

### Test Fake DNS

We should use a test container.

Vertx used at some
point: [FakeDNSServer.java](https://github.com/eclipse-vertx/vert.x/blob/970dc228ac4936d24d3531cec22574b8b1c8900f/vertx-core/src/test/java/io/vertx/test/fakedns/FakeDNSServer.java)

### Vertx Interop

DNS Java is reactive/future ready and can
use [CompletionInterop](https://github.com/eclipse-vertx/vert.x/blob/4f4fa14f4cad4c536ec57fdd39038011648ceee8/vertx-core/src/main/java/examples/CompletionStageInteropExamples.java#L6)

[Vertx example for info](https://github.com/eclipse-vertx/vert.x/blob/4f4fa14f4cad4c536ec57fdd39038011648ceee8/vertx-core/src/main/asciidoc/dns.adoc#L4)

Example code from:

* [DNSExamples.java](https://github.com/eclipse-vertx/vert.x/blob/4f4fa14f4cad4c536ec57fdd39038011648ceee8/vertx-core/src/main/java/examples/DNSExamples.java#L4)
* [CoreExamples.java](https://github.com/eclipse-vertx/vert.x/blob/4f4fa14f4cad4c536ec57fdd39038011648ceee8/vertx-core/src/main/java/examples/CoreExamples.java#L4)

```java
DnsClient client = vertx.createDnsClient(new DnsClientOptions()
        .setPort(53)
        .setHost("10.0.0.1")
        .setQueryTimeout(10000)
);
```

```java
Vertx vertx = Vertx.vertx(
        new VertxOptions().
                setAddressResolverOptions(
                        new AddressResolverOptions()
                                .addServer("192.168.0.1")
                                .addServer("192.168.0.2:40000")
                                .setHostsPath("/path/to/hosts")
                                .addSearchDomain("foo.com").addSearchDomain("bar.com")
                )
);
```
