# 多个RestTemplate对象

# TODO

---

# Multiple RestTemplate objects

If you want a RestTemplate that is not load balanced, create a RestTemplate bean and inject it as normal. To access the load balanced RestTemplate use the `@LoadBalanced qualifier when you create your @Bean.

IMPORTANT
Notice the @Primary annotation on the plain RestTemplate declaration in the example below, to disambiguate the unqualified @Autowired injection.
@Configuration
public class MyConfiguration {

    @LoadBalanced
    @Bean
    RestTemplate loadBalanced() {
        return new RestTemplate();
    }

    @Primary
    @Bean
    RestTemplate restTemplate() {
        return new RestTemplate();
    }
}

public class MyClass {
    @Autowired
    private RestTemplate restTemplate;

    @Autowired
    @LoadBalanced
    private RestTemplate loadBalanced;

    public String doOtherStuff() {
        return loadBalanced.getForObject("http://stores/stores", String.class);
    }

    public String doStuff() {
        return restTemplate.getForObject("http://example.com", String.class);
    }
}
TIP
If you see errors like java.lang.IllegalArgumentException: Can not set org.springframework.web.client.RestTemplate field com.my.app.Foo.restTemplate to com.sun.proxy.$Proxy89 try injecting RestOperations instead or setting spring.aop.proxyTargetClass=true.