# Develop Microservices with Spring Boot

### What is MVC?
MVC, or Model-View-Controller, , is an architecture pattern that helps you to organize your code into three logical components: View, Model, and Controller.
###### Example: 
When the employee hits the URL from a browser or any other client, the call goes to the Controller, which fetches the data (or Model) and updates the View that the employee is viewing.


### Microservices Architecture
In this, a complex task is broken down into multiple task or services and each task is managed and developed independently.

#### Advantages
- Removing dependencies when multiple people are working on separate repository and code bases.
- Ease of development and maintenance
- Easy deployment and scalability
- Significantly shorter time for production release
- Avoiding single points of failure

### Springboot
- open source java based framework for creating microservice and production ready standalone Spring MVC application.
- build on top of Spring Framework.

#### Advantages
- plugins or dependencies can auto-configured via application.properties.
- java beans and database configs can be easily done via Annotations.


# Spring Annotations

#### @Bean
- bean is an instance of java obj managed by spring ioc container
- ioc is the process of creating objects along with their dependencies without creating them.
- annotation is way of passing metadata during compile time.

#### @Scope
- scope within which object is accessible.
- `singleton`, `prototype`, `request`, `session` and `global session`

```
// usage of `singleton` scope 
@Scope("singleton")
@Bean
public RestTemplate getRestTemplate() {
    return new RestTemplate();
}

// usage of `prototype` scope 
@Scope("prototype")
@Bean
public RestTemplate getRestTemplate() {
    return new RestTemplate();
}

// usage of `request` scope 
@Scope("request")
@Bean
public RestTemplate getRestTemplate() {
    return new RestTemplate();
}
```

#### @SpringBootApplication
entry point of application. this can take following annotations / actually it is combination of - 
- @EnableAutoConfiguration
- @SpringBootConfiguration
- @ComponentScan

#### @Bean
- method level configuration annotation

#### @Autowired
- Autowiring by Constructor: The Recommended Approach


#### @Qualifier
- A bean can be referenced using class or by name. We can have multiple beans of the same type, and during dependency injection using @Autowired, Spring IoC will not be able to distinguish between the beans.
- @Qualifier applies to all types of beans – @Bean, @Component, @Service, etc.

#### @Component
- @Component annotated class is registered as Spring bean. This is a generic annotation, and there are few specialized annotations for different purposes, like the following:
- @Service
- @Controller
- @RestController
- @Configuration

#### Other
- @EnableCaching
- @Lazy
