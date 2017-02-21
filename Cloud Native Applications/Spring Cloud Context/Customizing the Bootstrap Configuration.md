# 自定义引导配置

# TODO

可以通过在关键 `org.springframework.cloud.bootstrap.BootstrapConfiguration` 下向 `/META-INF/spring.factories` 中添加条目来训练引导上下文以执行任何操作。这是一个以逗号分隔的Spring @Configuration类的列表，将用于创建上下文。您可以在此处创建您希望可用于主应用程序上下文以进行自动装配的任何bean，并且还有一个类型为ApplicationContextInitializer的@Beans的特殊合同。如果要控制启动顺序（默认顺序为“last”），可以使用@Order标记类。

警告
在添加自定义BootstrapConfiguration时，请注意，您添加的类不是@ComponentScanned错误地插入到您的“主”应用程序上下文中，可能不需要它们。对于尚未由@ComponentScan或@SpringBootApplication注释配置类涵盖的引导配置类使用单独的包名称。
引导进程通过将初始化程序注入到主SpringApplication实例（即正常的Spring Boot启动序列，无论它作为独立应用程序运行还是部署在应用程序服务器中）结束。首先，从spring.factories中找到的类创建一个引导上下文，然后在启动之前将所有ApplicationContextInitializer类型的@Bean添加到主SpringApplication。

---

# Customizing the Bootstrap Configuration

The bootstrap context can be trained to do anything you like by adding entries to /META-INF/spring.factories under the key org.springframework.cloud.bootstrap.BootstrapConfiguration. This is a comma-separated list of Spring @Configuration classes which will be used to create the context. Any beans that you want to be available to the main application context for autowiring can be created here, and also there is a special contract for @Beans of type ApplicationContextInitializer. Classes can be marked with an @Order if you want to control the startup sequence (the default order is "last").

WARNING
Be careful when adding custom BootstrapConfiguration that the classes you add are not @ComponentScanned by mistake into your "main" application context, where they might not be needed. Use a separate package name for boot configuration classes that is not already covered by your @ComponentScan or @SpringBootApplication annotated configuration classes.
The bootstrap process ends by injecting initializers into the main SpringApplication instance (i.e. the normal Spring Boot startup sequence, whether it is running as a standalone app or deployed in an application server). First a bootstrap context is created from the classes found in spring.factories and then all @Beans of type ApplicationContextInitializer are added to the main SpringApplication before it is started.