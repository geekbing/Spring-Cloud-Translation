# 自定义引导属性源

---

# Customizing the Bootstrap Property Sources

The default property source for external configuration added by the bootstrap process is the Config Server, but you can add additional sources by adding beans of type PropertySourceLocator to the bootstrap context (via spring.factories). You could use this to insert additional properties from a different server, or from a database, for instance.

As an example, consider the following trivial custom locator:

@Configuration
public class CustomPropertySourceLocator implements PropertySourceLocator {

    @Override
    public PropertySource<?> locate(Environment environment) {
        return new MapPropertySource("customProperty",
                Collections.<String, Object>singletonMap("property.from.sample.custom.source", "worked as intended"));
    }

}
The Environment that is passed in is the one for the ApplicationContext about to be created, i.e. the one that we are supplying additional property sources for. It will already have its normal Spring Boot-provided property sources, so you can use those to locate a property source specific to this Environment (e.g. by keying it on the spring.application.name, as is done in the default Config Server property source locator).

If you create a jar with this class in it and then add a META-INF/spring.factories containing:

org.springframework.cloud.bootstrap.BootstrapConfiguration=sample.custom.CustomPropertySourceLocator
then the "customProperty" PropertySource will show up in any application that includes that jar on its classpath.

