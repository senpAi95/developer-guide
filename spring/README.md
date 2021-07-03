## Why Spring?
* Spring makes programming Java quicker, easier and safer for everybody.
* Spring's focus on speed, simplicity and productivity has made it the most popular Java framework.
* Spring can facilitate
    * [Microservices](https://spring.io/microservices) (Independent evolvable microservices).
    * [Reactive](https://spring.io/reactive) (Its asynchronous, nonblocking architecture)
    * [Cloud](https://spring.io/cloud) (Can be deployed to any cloud.)
    * [Web apps](https://spring.io/web-applications) (Frameworks for fast, secure and responsive web applications connected to any datastore.)
    * [Serverless](https://spring.io/serverless) (Scale up to demand and scale to 0 when there's no demand)
    * [Event Driven](https://spring.io/event-driven). (Acting on streaming data in real time)
    * [Batch](https://spring.io/guides/gs/batch-processing/) (Automated tasks. Offline processing of data at a time that suits application)
    
### General Stuff

#### SpringFramework
* Spring is a powerful open source, application framework created to reduce the complexity of enterprise application development.
* It is light-weighted and loosely coupled.
* It has layered architecture, which allows you to select the components to use, while also providing a cohesive framework
for J2EE application development.
* Spring framework is also called as framework of frameworks as it provides support to various other frameworks such as
Struts, Hibernate, Tapestry, EJB, JSF etc.

![Architecture](spring/images/spring-architecture.png "Architecture")

* Spring framework provides about 20 modules which can be used based on application requirement.

    * #### Core Container
        * Consists of Core, Beans, Context, Expression Language modules.
        * The <b>Core</b> module provides the fundamental parts of the framework including the IoC and Dependency Injection features.
        * The <b>Bean</b> module provides the BeanFactory, which is sophisticated implementation of the factory pattern.
        * The <b>Context</b> module builds on the solid base provided by the Core and Bean modules, and it is a medium to access any Objects. ApplicationContext is the focal point of the context module.
        * SpEL module provides a powerful expression language for querying and manipulating an object graph at runtime.
    * #### Data Access/Integration
        * This layer provides the abstraction layer that removes tedious code for JDBC, ORM, OXM, JMS (Java messaging Service), Transaction modules.
    * #### Web
        * The <b>Web</b> module provides basic web-oriented integration features such as multipart file-upload functionality and the initializaiton of IoC container using servlet listeners and a Web-Oriented Application Context.
        * The <b>Web-MVC</b> module contains Springs's Model-View-Controller implementation for web applications.
        * The <b>Web-Socket</b> module provides support for WebSocket-based, two-way communication between the client and the server in web-applications.
        * The <b>Web-Portlet</b> module provides the MVC implementation to be used in a portlet environment and mirrors the functionality of Web-Servlet module.
#### Advantages of spring framework
* Layered architecture in Spring can help us in using what we need and leaving what we don't.



#### IOC Containers
* Spring container is at the core of the Spring Framework. The container will create the objects, wire them together, configure them and manage their complete life cycle.
* Spring container uses DI to manage the components that make up the application with objects called Spring Beans.
* The container gets its instructions on what objects to instantiate, configure and assemble by reading the configuration metadata provided (XML/ Java annotations/ Java code).
* Spring provides following 2 different types of containers.
    * <b>BeanFactory</b>:
      This is the simplest container providing the basic support for DI and is defined by the org.springframework.beans.factory.BeanFactory interface. The BeanFactory and related interfaces, such as BeanFactoryAware, InitializingBean, DisposableBean, are still present in Spring for the purpose of backward compatibility with a large number of third-party frameworks that integrate with Spring.
    * <b>ApplicationContext</b>:
      This container adds more enterprise-specific functionality such as the ability to resolve textual messages from a properties file and the ability to publish application events to interested event listeners. This container is defined by the org.springframework.context.ApplicationContext interface.
      
    > The ApplicationContext container includes all functionality of the BeanFactorycontainer, so it is generally recommended over BeanFactory. BeanFactory can still be used for lightweight applications like mobile devices or applet-based applications where data volume and speed is significant.

#### Beans
* A bean is an object that is instantiated, assembled, and otherwise managed by a Spring IoC container.
* Beans are created with the configuration metadata that you supply to the container.
* Bean definition contains the information called configuration metadata, which is needed for the container to know the following −
    * How to create a bean
    * Bean's lifecycle details
    * Bean's dependencies
    
* Bean scopes:
    * singleton - Default - Single instance per Spring IOC container.
    * prototype - This scopes a single bean definition to have any number of object instances.
    * request - Scopes a bean definition to an HTTP request. Only valid in the context of a web-aware SpringApplicationContext.
    * session - This scopes a bean definition to an HTTP session. Only valid in the context of a web-aware Spring Application Context/
    * global-session - This scopes a bean definition to a global HTTP session. Only valid in the context of a web-aware Spring ApplicationContext.
    > As a rule, use the prototype scope for all state-full beans and the singleton scope for stateless beans.

#### Dependency Injection
* When writing complex Java Application, application classes should be as independent as possible of other Java classes to increase the possiblity to reuse these classes and to test them independently of other classes while unit testing.
* Dependency injection helps in gluing classes and at the same time keeping them independent.

Consider you have an application which has a text editor component and you want to provide a spell check. Your standard code would look something like this −
```Java
public class TextEditor {
    private SpellChecker spellChecker;

    public TextEditor() {
        spellChecker = new SpellChecker();
    }
}
```
What we've done here is, create a dependency between the TextEditor and the SpellChecker. In an inversion of control scenario, we would instead do something like this −

```Java
public class TextEditor {
    private SpellChecker spellChecker;

    public TextEditor(SpellChecker spellChecker) {
        this.spellChecker = spellChecker;
    }
} 
```
Here, the TextEditor should not worry about SpellChecker implementation. The SpellChecker will be implemented independently and will be provided to the TextEditor at the time of TextEditor instantiation. This entire procedure is controlled by the Spring Framework.

#### Annotation Based Configuration
* Since Spring 2.5 we can configure the DI using annotations. So instead of using XML to describe a bean wiring, we can move the configuration to annotation class itself.
* Annotation injection is performed before XML injection, so, latter can override former.
```xml
<?xml version = "1.0" encoding = "UTF-8"?>

<beans xmlns = "http://www.springframework.org/schema/beans"
   xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
   xmlns:context = "http://www.springframework.org/schema/context"
   xsi:schemaLocation = "http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
   http://www.springframework.org/schema/context
   http://www.springframework.org/schema/context/spring-context-3.0.xsd">

   <context:annotation-config/>
   <!-- bean definitions go here -->

</beans>
```
* Once <context:annotation-config/> is configured, you can start annotating your code to indicate that Spring should automatically wire values into properties, methods, and constructors.

Few Annotations
    * @Required: applies to bean property setter methods.
    * @Autowired: Setter methods, non-setter methods, constructor and properties.
    * @Qualifier: can be used along with @Autowired can be used to remove the confusion by specifying which exact bean will be wired.
    * JSR250 annotations:
        * @PostConstruct
        * @PreDestroy
        * @Resource

#### Event Handling in Spring
* You have seen in all the chapters that the core of Spring is the ApplicationContext, which manages the complete life cycle of the beans. The ApplicationContext publishes certain types of events when loading the beans. For example, a ContextStartedEvent is published when the context is started and ContextStoppedEvent is published when the context is stopped.
* Event handling in the ApplicationContext is provided through the ApplicationEvent class and ApplicationListener interface. Hence, if a bean implements the ApplicationListener, then every time an ApplicationEvent gets published to the ApplicationContext, that bean is notified.
    * ContextRefreshedEvent - This event is published when the ApplicationContext is either initialized or refreshed. This can also be raised using the refresh() method on the ConfigurableApplicationContext interface.
    * ContextStartedEvent - This event is published when the ApplicationContext is started using the start() method on the ConfigurableApplicationContext interface. You can poll your database or you can restart any stopped application after receiving this event.
    * ContextStoppedEvent - This event is published when the ApplicationContext is stopped using the stop() method on the ConfigurableApplicationContext interface. You can do required housekeep work after receiving this event.
    * ContextClosedEvent - This event is published when the ApplicationContext is closed using the close() method on the ConfigurableApplicationContext interface. A closed context reaches its end of life; it cannot be refreshed or restarted.
    * RequestHandledEvent - This is a web-specific event telling all beans that an HTTP request has been serviced.
    
#### JDBC Framework overview
* Spring JDBC provides several approaches and correspondingly different classes to interface with the database. I'm going to take classic and the most popular approach which makes use of JdbcTemplate class of the framework. This is the central framework class that manages all the database communication and exception handling.
* The JDBC Template class executes SQL queries, updates statements, stores procedure calls, performs iteration over ResultSets, and extracts returned parameter values. It also catches JDBC exceptions and translates them to the generic, more informative, exception hierarchy defined in the org.springframework.dao package.
* Instances of the JdbcTemplate class are threadsafe once configured. So you can configure a single instance of a JdbcTemplate and then safely inject this shared reference into multiple DAOs.
* A common practice when using the JDBC Template class is to configure a DataSource in your Spring configuration file, and then dependency-inject that shared DataSource bean into your DAO classes, and the JdbcTemplate is created in the setter for the DataSource.
```xml
  <bean id = "dataSource"
  class = "org.springframework.jdbc.datasource.DriverManagerDataSource">
  <property name = "driverClassName" value = "com.mysql.jdbc.Driver"/>
  <property name = "url" value = "jdbc:mysql://localhost:3306/TEST"/>
  <property name = "username" value = "root"/>
  <property name = "password" value = "password"/>
  </bean>
  ```

#### Transaction Management
* A database transaction is a sequence of actions that are treated as a single unit of work.
* The concept of transactions can be described with the following four key properties described as ACID −
    * Atomicity − A transaction should be treated as a single unit of operation, which means either the entire sequence of operations is successful or unsuccessful.
    * Consistency − This represents the consistency of the referential integrity of the database, unique primary keys in tables, etc.
    * Isolation − There may be many transaction processing with the same data set at the same time. Each transaction should be isolated from others to prevent data corruption.
    * Durability − Once a transaction has completed, the results of this transaction have to be made permanent and cannot be erased from the database due to system failure.