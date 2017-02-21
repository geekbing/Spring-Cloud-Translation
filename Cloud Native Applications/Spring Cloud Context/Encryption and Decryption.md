# 加密和解密

# TODO

---

# Encryption and Decryption

Spring Cloud has an Environment pre-processor for decrypting property values locally. It follows the same rules as the Config Server, and has the same external configuration via encrypt.*. Thus you can use encrypted values in the form {cipher}* and as long as there is a valid key then they will be decrypted before the main application context gets the Environment. To use the encryption features in an application you need to include Spring Security RSA in your classpath (Maven co-ordinates "org.springframework.security:spring-security-rsa") and you also need the full strength JCE extensions in your JVM.

If you are getting an exception due to "Illegal key size" and you are using Sun’s JDK, you need to install the Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files. See the following links for more information:

Java 6 JCE

Java 7 JCE

Java 8 JCE

Extract files into JDK/jre/lib/security folder (whichever version of JRE/JDK x64/x86 you are using).

