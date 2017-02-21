# 更改引导属性的位置

可以使用 `spring.cloud.bootstrap.name`（默认值为“bootstrap”）或 `spring.cloud.bootstrap.location`（默认值为空）来指定 `bootstrap.yml`（或.properties）的位置，例如在系统属性中来指定。 这些属性的行为类似于具有相同名称的 `spring.config.*` 的变体，实际上它们用于通过在其环境中设置这些属性来设置引导 `ApplicationContext`。 如果有一个激活的配置文件（通过 `spring.profiles.active` 来指定或者通过你正在构建的上下文的环境API来设置），那么该配置文件中的属性也将会被加载，就像在普通的Spring Boot应用程序中一样，例如：使用 `bootstrap-development.properties` 配置文件来作为开发环境的配置文件。

---

# Changing the Location of Bootstrap Properties

The bootstrap.yml (or .properties) location can be specified using spring.cloud.bootstrap.name (default "bootstrap") or spring.cloud.bootstrap.location (default empty), e.g. in System properties. Those properties behave like the spring.config.* variants with the same name, in fact they are used to set up the bootstrap ApplicationContext by setting those properties in its Environment. If there is an active profile (from spring.profiles.active or through the Environment API in the context you are building) then properties in that profile will be loaded as well, just like in a regular Spring Boot app, e.g. from bootstrap-development.properties for a "development" profile.