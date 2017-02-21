# 端点

对于 `Spring Boot Actuator` 应用程序，还有一些其他的管理端点：

+ 发送 `POST` 请求到 `/env` 端点来更新环境，重新绑定 `@ConfigurationProperties` 和日志级别
+ `/refresh` 端点用来重新加载启动上下文并刷新 `@RefreshScope bean`
+ `/restart` 端点用来关闭 `ApplicationContext` 并重新启动它（默认情况下禁用）
+ `/pause` 和 `/resume` 端点用来调用 `ApplicationContext` 上的生命周期方法（ `stop（）` 和 `start（）` ）

---

# Endpoints

+ For a Spring Boot Actuator application there are some additional management endpoints:
+ POST to /env to update the Environment and rebind @ConfigurationProperties and log levels
+ /refresh for re-loading the boot strap context and refreshing the @RefreshScope beans
+ /restart for closing the ApplicationContext and restarting it (disabled by default)
+ /pause and /resume for calling the Lifecycle methods (stop() and start() on the ApplicationContext)