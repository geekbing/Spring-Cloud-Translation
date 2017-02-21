# 环境更改

# TODO

---

# Environment Changes

The application will listen for an EnvironmentChangedEvent and react to the change in a couple of standard ways (additional ApplicationListeners can be added as @Beans by the user in the normal way). When an EnvironmentChangedEvent is observed it will have a list of key values that have changed, and the application will use those to:

Re-bind any @ConfigurationProperties beans in the context

Set the logger levels for any properties in logging.level.*

Note that the Config Client does not by default poll for changes in the Environment, and generally we would not recommend that approach for detecting changes (although you could set it up with a @Scheduled annotation). If you have a scaled-out client application then it is better to broadcast the EnvironmentChangedEvent to all the instances instead of having them polling for changes (e.g. using the Spring Cloud Bus).

The EnvironmentChangedEvent covers a large class of refresh use cases, as long as you can actually make a change to the Environment and publish the event (those APIs are public and part of core Spring). You can verify the changes are bound to @ConfigurationProperties beans by visiting the /configprops endpoint (normal Spring Boot Actuator feature). For instance a DataSource can have its maxPoolSize changed at runtime (the default DataSource created by Spring Boot is an @ConfigurationProperties bean) and grow capacity dynamically. Re-binding @ConfigurationProperties does not cover another large class of use cases, where you need more control over the refresh, and where you need a change to be atomic over the whole ApplicationContext. To address those concerns we have @RefreshScope.

