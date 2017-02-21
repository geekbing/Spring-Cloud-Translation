# Spring RestTemplate作为负载均衡客户端

# TODO

---

# Spring RestTemplate as a Load Balancer Client

RestTemplate can be automatically configured to use ribbon. To create a load balanced RestTemplate create a RestTemplate @Bean and use the @LoadBalanced qualifier.

WARNING
A RestTemplate bean is no longer created via auto configuration. It must be created by individual applications.
@Configuration
public class MyConfiguration {

    @LoadBalanced
    @Bean
    RestTemplate restTemplate() {
        return new RestTemplate();
    }
}

public class MyClass {
    @Autowired
    private RestTemplate restTemplate;

    public String doOtherStuff() {
        String results = restTemplate.getForObject("http://stores/stores", String.class);
        return results;
    }
}
The URI needs to use a virtual host name (ie. service name, not a host name). The Ribbon client is used to create a full physical address. See RibbonAutoConfiguration for details of how the RestTemplate is set up.