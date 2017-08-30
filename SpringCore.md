# Spring 
Spring handles the infrastructure so you can focus on your application.

Spring IoC container = org.springframework.context.ApplicationContext

Application context consumes metadata which is in the form of xml/annotation/java code. Several implementations of the ApplicationContext
1. ClassPathXmlApplicationContext
2. FileSystemXmlApplicationContext

AutoWiring Types
1. byName
2. byType - setter/field
3. constructor

**XML Based Configuration:**
```xml 
<!--Configuration-->
<!--Defining a Bean-->
<bean id="" class="">
```

## Loading ApplicationContext

**Annotation-based configuration:** Spring 2.5 introduced support for annotation-based configuration metadata.

```xml
<context:annotation-config/>
<context:component-scan base-package="com.pluralsight"/>
```

```java
//converting a pojo to a spring bean using annotation
@Component
@Service
@Repository
```


**Java-based configuration:** Starting with Spring 3.0, many features provided by the Spring JavaConfig project became part of the core Spring Framework. Thus you can define beans external to your application classes by using Java rather than XML files. To use these new features, see the @Configuration, @Bean, @Import and @DependsOn annotations.

**No ApplicationContext.xml**
applicationContext replaced by @Configuration
@Configuration at class level
Spring Beans defined by @Bean
@Bean at method level


```java
@Configuration
public class AppConfig {
    @Bean(name="customerService")
    public CustomerService getCustomerService() {
        CustomerServiceImpl customerService = new CustomerServiceImpl();
        customerService.setCustomerRepository(getCustomerRepository());
        return customerService;
    }
    @Bean(name = "customerRepository")
    public CustomerRepository getCustomerRepository() { //Singleton
        return new HibernateCustomerRepositoryImpl();
    }
}
```
## Loading ApplicationContext

```java
ApplicationContext cntx = new AnnotationConfigAppicationContext(Appconfig.class);
cntx.getBean("beanName", BeanName.class);
```
#Bean Scopes

Singleton
```java 
@scope(ConfigurableBeanFactory.SCOPE_SINGLETON)
```
Prototype
##Web-Aware scopes
Request
session
global

# Loading Property file

1. xml

```xml
<context:property-placeholder location="app.properties" />
<bean id="id" class="customer">
<property name="dbUName" value="${dbuname} />
</bean>
```

2. Annotaion

```java
@value("${dbuname}")
private String dbuname;
```

3. Java Config

```java
@PropertySource("app.properties")

@Bean
public static PropertySourcesPlaceHolderConfigurer getpropertySourcesPlaceHolderConfigurer(){
    retutn new PropertySourcesPlaceHolderConfigurer();
}

@value("${dbuname}")
private String dbuname;

```

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>4.3.10.RELEASE</version>
        <scope>runtime</scope>
    </dependency>
</dependencies>
<repositories>
    <repository>
        <id>io.spring.repo.maven.release</id>
        <url>http://repo.spring.io/release/</url>
        <snapshots><enabled>false</enabled></snapshots>
    </repository>
</repositories>
```


