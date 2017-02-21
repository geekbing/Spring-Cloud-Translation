# 忽略网络接口

# TODO

---

# Ignore Network Interfaces

Sometimes it is useful to ignore certain named network interfaces so they can be excluded from Service Discovery registration (eg. running in a Docker container). A list of regular expressions can be set that will cause the desired network interfaces to be ignored. The following configuration will ignore the "docker0" interface and all interfaces that start with "veth".

application.yml
spring:
  cloud:
    inetutils:
      ignoredInterfaces:
        - docker0
        - veth.*
You can also force to use only specified network addresses using list of regular expressions:

application.yml
spring:
  cloud:
    inetutils:
      preferredNetworks:
        - 192.168
        - 10.0
You can also force to use only site local addresses. See Inet4Address.html.isSiteLocalAddress() for more details what is site local address.

application.yml
spring:
  cloud:
    inetutils:
      useOnlySiteLocalInterfaces: true
