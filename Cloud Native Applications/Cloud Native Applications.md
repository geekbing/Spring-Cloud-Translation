# 原生云应用

原生云是一种应用程序的开发风格，它鼓励在持续交付和价值驱动开发的领域简单的采用最佳实践。在开发实践和交付运营目标一致的情况下，开发过程中应该考虑的相关约束就是12个因素，例如通过采用声明式编程和管理与监控等等。Spring Cloud以许多特定的方式来促进这些开发风格，Spring Cloud的出发点就是提供了一系列的功能，Spring Cloud分布式系统中的所有组件可以在需要时轻松的访问。

Spring Cloud依赖于Spring Boot来构建，它的许多功能都被Spring Boot所覆盖。 Spring Cloud提供了额外的两个库：Spring Cloud Context和Spring Cloud Commons。Spring Cloud Context为Spring Cloud应用程序的ApplicationContext（引导上下文，加密，刷新作用域和环境端点）提供了实用的工具和特殊服务。Spring Cloud Commons是在不同的Spring Cloud实现（例如，Spring Cloud Netflix与Spring Cloud Consul）中使用的一组抽象和公共类。

如果由于"Illegal key size"这个原因而出现了异常，并且你正在使用Sun的JDK的话，那么你则需要安装Java密码扩展（JCE）策略文件。 有关详细信息，请参考以下链接：

+ Java 6 JCE
+ Java 7 JCE
+ Java 8 JCE

将文件解压缩到JDK/jre/lib/security文件夹（无论你使用的是JRE/JDK或者x64/x86的版本）。

注意: Spring Cloud是根据非限制性Apache 2.0许可证发布的。 如果你想贡献这一部分的文档，或者如果你发现了错误，请在github的项目中找到源代码和问题跟踪。

---

# Cloud Native Applications

Cloud Native is a style of application development that encourages easy adoption of best practices in the areas of continuous delivery and value-driven development. A related discipline is that of building 12-factor Apps in which development practices are aligned with delivery and operations goals, for instance by using declarative programming and management and monitoring. Spring Cloud facilitates these styles of development in a number of specific ways and the starting point is a set of features that all components in a distributed system either need or need easy access to when required.

Many of those features are covered by Spring Boot, which we build on in Spring Cloud. Some more are delivered by Spring Cloud as two libraries: Spring Cloud Context and Spring Cloud Commons. Spring Cloud Context provides utilities and special services for the ApplicationContext of a Spring Cloud application (bootstrap context, encryption, refresh scope and environment endpoints). Spring Cloud Commons is a set of abstractions and common classes used in different Spring Cloud implementations (eg. Spring Cloud Netflix vs. Spring Cloud Consul).

If you are getting an exception due to "Illegal key size" and you are using Sun’s JDK, you need to install the Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files. See the following links for more information:

+ Java 6 JCE
+ Java 7 JCE
+ Java 8 JCE

Extract files into JDK/jre/lib/security folder (whichever version of JRE/JDK x64/x86 you are using).

NOTE
Spring Cloud is released under the non-restrictive Apache 2.0 license. If you would like to contribute to this section of the documentation or if you find an error, please find the source code and issue trackers in the project at github.
