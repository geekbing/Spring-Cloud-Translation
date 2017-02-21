# 应用上下文层次结构

如果你从SpringApplication或SpringApplicationBuilder来构建应用程序上下文，则Spring Cloud会将引导上下文添加为它的父上下文。Spring的一个特点就是，子上下文会从它们的父上下文继承属性源和配置文件，所以与不使用Spring Cloud Config构建相同的上下文相比，主应用程序上下文将包含额外的属性源。其他属性源包括：

+ “bootstrap”：如果在引导上下文中找到任何PropertySourceLocators，并且它们具有非空属性，则可选的CompositePropertySource将显示为高优先级。 一个例子就是来自Spring Cloud配置服务器的属性。 有关如何自定义此属性源的内容的说明，请参阅下文。

+ “applicationConfig：[classpath：bootstrap.yml]”（如果Spring配置文件是激活的）。 如果你有一个bootstrap.yml（或properties）配置文件，那么这些属性将用于配置引导上下文。当子上下文的父上下文设置的时候，它们将被添加到子上下文中。 它们的优先级低于application.yml（或properties）以及创建Spring Boot应用程序过程中正常添加到子上下文的其他任何属性源。 有关如何自定义这些属性源的内容的说明，请参阅下文。

由于属性源的排序规则，“引导”条目优先，但是请注意，这些不包含来自bootstrap.yml的任何数据，该数据具有非常低的优先级，但可以用于设置默认值。

你可以通过简单地设置你创建的任何ApplicationContext的父上下文来扩展上下文层次结构。例如：使用它自己的接口，或者用SpringApplicationBuilder的便捷方法（parent（），child（）和sibling（））。引导上下文将是你自己创建的最高级上下文的父级。层次结构中的每个上下文都有自己的“引导”属性源（可能为空），以避免将值从父级无意间向下推送到其后代。层次结构中的每个上下文（原则上）也可以具有不同的  `spring.application.name`，如果有一个配置服务器的话，也可能具有不同的远程属性源。通常的Spring应用程序上下文行为规则适用于属性解析：来自子代上下文的属性根据名称以及属性源名称覆盖父级中的属性（如果子级具有与父级相同名称的属性源，则父项不包括在子项中）。

请注意，SpringApplicationBuilder允许你在整个上下文层次结构之间共享环境配置，但这不是默认的。因此，兄弟上下文特别不需要具有相同的配置文件或属性源，即使它们将与它们的父代共享共同的东西。

---
     
# Application Context Hierarchies

If you build an application context from SpringApplication or SpringApplicationBuilder, then the Bootstrap context is added as a parent to that context. It is a feature of Spring that child contexts inherit property sources and profiles from their parent, so the "main" application context will contain additional property sources, compared to building the same context without Spring Cloud Config. The additional property sources are:

+ "bootstrap": an optional CompositePropertySource appears with high priority if any PropertySourceLocators are found in the Bootstrap context, and they have non-empty properties. An example would be properties from the Spring Cloud Config Server. See below for instructions on how to customize the contents of this property source.

+ "applicationConfig: [classpath:bootstrap.yml]" (and friends if Spring profiles are active). If you have a bootstrap.yml (or properties) then those properties are used to configure the Bootstrap context, and then they get added to the child context when its parent is set. They have lower precedence than the application.yml (or properties) and any other property sources that are added to the child as a normal part of the process of creating a Spring Boot application. See below for instructions on how to customize the contents of these property sources.

Because of the ordering rules of property sources the "bootstrap" entries take precedence, but note that these do not contain any data from bootstrap.yml, which has very low precedence, but can be used to set defaults.

You can extend the context hierarchy by simply setting the parent context of any ApplicationContext you create, e.g. using its own interface, or with the SpringApplicationBuilder convenience methods (parent(), child() and sibling()). The bootstrap context will be the parent of the most senior ancestor that you create yourself. Every context in the hierarchy will have its own "bootstrap" property source (possibly empty) to avoid promoting values inadvertently from parents down to their descendants. Every context in the hierarchy can also (in principle) have a different spring.application.name and hence a different remote property source if there is a Config Server. Normal Spring application context behaviour rules apply to property resolution: properties from a child context override those in the parent, by name and also by property source name (if the child has a property source with the same name as the parent, the one from the parent is not included in the child).

Note that the SpringApplicationBuilder allows you to share an Environment amongst the whole hierarchy, but that is not the default. Thus, sibling contexts in particular do not need to have the same profiles or property sources, even though they will share common things with their parent.