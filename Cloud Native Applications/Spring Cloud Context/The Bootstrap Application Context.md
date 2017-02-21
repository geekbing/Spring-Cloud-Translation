# 应用程序引导上下文

Spring Cloud应用程序通过创建"引导"上下文来运行，该引导上下文是主应用程序的父上下文。它具有开箱即用的特点，并负责从外部源加载配置属性，以及解码本地外部配置文件中的属性。 这两个上下文共享一个配置环境，该配置环境是任何Spring应用程序的外部属性的源。引导属性具有高的优先级，因此默认情况下它们不能被本地配置覆盖。

与主应用程序上下文使用application.yml（或.properties）来定位外部配置不同，引导上下文使用不同的约定，它使用bootstrap.yml来代替，以此来保持引导上下文和主应用程序上下文的外部配置完全分离。 例如：

```
bootstrap.yml
spring:
  application:
    name: foo
  cloud:
    config:
      uri: ${SPRING_CONFIG_URI:http://localhost:8888}
```

如果您的应用程序需要从服务器进行任何特定于应用程序相关的配置，则最好设置 `spring.application.name`（在bootstrap.yml或application.yml中）。

您可以通过设置 `spring.cloud.bootstrap.enabled = false`（例如在系统属性中）完全禁用引导过程。

---

# The Bootstrap Application Context

A Spring Cloud application operates by creating a "bootstrap" context, which is a parent context for the main application. Out of the box it is responsible for loading configuration properties from the external sources, and also decrypting properties in the local external configuration files. The two contexts share an Environment which is the source of external properties for any Spring application. Bootstrap properties are added with high precedence, so they cannot be overridden by local configuration, by default.

The bootstrap context uses a different convention for locating external configuration than the main application context, so instead of application.yml (or .properties) you use bootstrap.yml, keeping the external configuration for bootstrap and main context nicely separate. Example:

```
bootstrap.yml
spring:
  application:
    name: foo
  cloud:
    config:
      uri: ${SPRING_CONFIG_URI:http://localhost:8888}
```

It is a good idea to set the spring.application.name (in bootstrap.yml or application.yml) if your application needs any application-specific configuration from the server.

You can disable the bootstrap process completely by setting spring.cloud.bootstrap.enabled=false (e.g. in System properties).