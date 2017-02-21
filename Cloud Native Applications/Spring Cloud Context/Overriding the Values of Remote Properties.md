# 覆盖远程属性的值

通过引导上下文添加到你的应用程序的属性源通常是“远程”的（例如从配置服务器），并且默认情况下它们不能在本地覆盖，除了在命令行中。 如果你想要允许应用程序使用自己的系统属性或配置文件来覆盖远程属性，则远程属性源必须通过设置 `spring.cloud.config.allowOverride = true`（在本地设置该属性不起作用）来授予它权限。 一旦该标志被设置，有一些更细粒度的设置来控制远程属性相对于系统属性和应用程序的本地配置的位置：通过设置 `spring.cloud.config.overrideNone = true` 来覆盖任何本地属性源；如果只有系统属性和环境变量而不是本地配置文件应该覆盖远程设置，那么应该设置 `spring.cloud.config.overrideSystemProperties = false` 。

---

# Overriding the Values of Remote Properties

The property sources that are added to you application by the bootstrap context are often "remote" (e.g. from a Config Server), and by default they cannot be overridden locally, except on the command line. If you want to allow your applications to override the remote properties with their own System properties or config files, the remote property source has to grant it permission by setting spring.cloud.config.allowOverride=true (it doesn’t work to set this locally). Once that flag is set there are some finer grained settings to control the location of the remote properties in relation to System properties and the application’s local configuration: spring.cloud.config.overrideNone=true to override with any local property source, and spring.cloud.config.overrideSystemProperties=false if only System properties and env vars should override the remote settings, but not the local config files.

