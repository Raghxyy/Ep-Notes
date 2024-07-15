# CO-4 : JPA, JMS, REST-API (jax-rs)

## JPA

- [CO-4 : JPA, JMS, REST-API (jax-rs)](#co-4--jpa-jms-rest-api-jax-rs)
  - [JPA](#jpa)
    - [Introduction](#introduction)
    - [JPA versions](#jpa-versions)
    - [Why JPA](#why-jpa)
    - [JPA ORM](#jpa-orm)
    - [JPA Entity](#jpa-entity)
    - [JPQL - Java Persistance Query Language](#jpql---java-persistance-query-language)
    - [JPA config (MySQL / Oracle)](#jpa-config-mysql--oracle)
  - [REST API/ RESTful services:](#rest-api-restful-services)
    - [Example: Simple Calculator (REST)](#example-simple-calculator-rest)
  - [JMS - Java Messaging Service - Message Driven bean](#jms---java-messaging-service---message-driven-bean)

### Introduction

- JPA stands for `Java Persistance API`
- JPA is a popular technology used for managing realtional data in java applications
- It is used to persist (store) data between java objects and relational database
- JPA acts as a bridege between object oriented paradigm and relational database systems.
- **JPA does not perform any operation by itself, it requires ORM framework/tool for data persistance.**
- Some of the popular ORM frameworks or tools:
  1. Hibernate
  2. iBatis
  3. ORMLite
  4. TopLink and so on.

### JPA versions

- The first version of JPA is `JPA 1.0` which was released in the year 2006.
- JPA versions are:
  1. `JPA 2.0`
  2. `JPA 2.1`
  3. `JPA 2.2`
  4. `JPA 2.3` - current

### Why JPA

- It is popular because of the features:
  - Simplicity
  - Follows ORM
  - Code reusability
  - Simplifies the process of database access
  - Database portability

### JPA ORM

- ORM stands for `Object Relational Mapping`
- This privides a functionality which is used to maintain and develop a realtionship between **java object** and **relational database** by mapping an object to the column of a table.
- [Refer to Diagram](link_here)
- [Some popular ORM tools](#introduction)

- ### Mapping Directions

  - Are divinded in to two types:
    1. Uni-Directional
       - In this relationsip, Only one entity can refer to the properties of another entity
    2. Bi-Directional
       - In this relationship, Every entity can refer to the properties of another entity

- ### Types of Mappings:
  - Mappings are divided into 4 types:
    1. **`OneToOne`**
       - This association is represented by using the annotation `@OneToOne`
       - In this relationship, an instance of an entity-class is related to single instance of another entity-class
    2. **`OneToMany`**
       - This association is represented by using the annotation `@OneToMany`
       - In this relationship, single instance of an entity-class is related to many instances of another entity-class
    3. **`ManyToOne`**
       - This association is represented by using the annotation `@ManyToOne`
       - In this relationship, multiple instances of one entity-class is related to one instance of another entity-class
    4. **`ManyToMany`**
       - This association is represented by using the annotation `@ManyToMany`
       - In this relationship, many instances of one entitiy are related to many instances of another entity-class.

### JPA Entity

- Entity is a group of states associated together as a single unit
- An entity behaves as an object and becomes the major role of oject oriented paradigm
- The 2 important properties of an Entity are:
  1. Persistant
     - An object is called `Persistant` if the data is stored in a database and can be accessed anytime.
  2. Transaction
     - Entity can perform various operations like: `CREATE`/ `INSERT`, `RETRIEVE`, `UPDATE`, `DELETE`
     - Each operation makes some changes in a Database.
     - It ensures that whatever the changes made in the database can be done automatically.(We can `COMMIT`(save) or `ROLLBACK`(undo) when needed)
- An entity can be implemented in two ways:
  1. Using annotaitons
  2. By making the file as `.xml`
- ### Creating an entity:
  - A java class can be transoformed into an entity class by using the following requirements:
    1. No args constructor
    2. Annotation
- Example:

```java
@Entity
class DemoClass{
    private int id;
    private String name;
    private double salary;

    public DemoClass(){}// No args constructor
   /*
    * Getters and Setters for all data-members
    */
}
```

### JPQL - Java Persistance Query Language

- The JPQL is an Object oriented query language which is used to perform database operations on a persistant entity
- JPQL uses entity object model to operate SQL queries instead of database table.
- **_Note_**: _The role of JPA is to transform JPQL queries into SQL queries._
- ### JPQL Features:
  1. Platform-independet query language
  2. It is simple and robust
  3. It can be used with anytype of databases MySQL, Oracle and so on.
- ### Creating queries in JPQL
  - JPQL provides 2 methods that can be used to access database records. These methods are:
    1. **`Query createQuery(String query)`**
       - This is a method of `EntityManager` interface which is used to create an instance of `Query` interface for executing JPQL queries
       - Syntax:
       ```java
       class someEntityClass{
            EntityManager em;
            // Some implementation of method
            Query q = em.createQuery("<JPQL_Query>");
       }
       ```
       - Example:
       ```java
       class someEntityClass{
            EntityManager em;
            // Some implementation of method
            Query q = em.createQuery("select ename from Employee");
       }
       ```
    2. **`Query createNamedQuery(String query)`**
       - This is a method of `EntityManager` interface which is used to create an instance of `Query` interface for executing JPQL queries
       - Syntax:
       ```java
       class someEntityClass{
            EntityManager em;
            // Some implementation of method
            Query q = em.createNamedQuery("<JPQL_Query>");
       }
       ```
       - Example:
       ```java
       class someEntityClass{
            EntityManager em;
            // Some implementation of method
            Query q = em.createNamedQuery("select ename from Employee");
       }
       ```

### JPA config (MySQL / Oracle)

- Steps to be followed to configue for MySQL:
  1. Set `JBOSS_HOME` environment variable with Jboss-server's path
  2. Navigate to `$JBOSS_HOME/bin` location and run `jboss-cli.bat` file on your system
  3. Then run this following command `module add --name=com.mysql --resources=<db-driver-path> --dependencies=javax.api,javax.transaction.api`
  4. Then go to `$JBOSS_HOME/standalone/configuration` and open `standalone.xml`
  5. Now copy this piece of code withing `<drivers>` xml tag:
  ```xml
    <driver name="mysql" resource="com.mysql">
      <driver-class>com.mysql.cj.jdbc.Driver</driver-class>
    </driver>
  ```
  7. Now go to CodeReadyStudio and start the server
  8. Go to your browser and open server's admin console at `localhost:9990`
  9. If prompted for username and password, Enter `admin` for both username and password. If didnt, go back to `$JBOSS_HOME/bin` and run `add-user.bat` and select `ManagementUser, add username and password`, Choose the roles as "Administrator, Deployer, Monitor"
  10. Navigate to `Configuration` tab
  11. And go to `SubSystems/Datasources and Drivers`
  12. Exapand Datasources tab and find the `+` symbol and follow the dialog to setup the datasource.

## REST API/ RESTful services:

- `REST` stands for Representation State Transfer
- **Web Service**: It is a collection of protocols which are used for exchanging the data or information between applications
- Web services based on REST architecture are called as RESTful services.
- Web services will contain many `HTTP` methods to implement REST concept.
- Some of the popular `http` methods are:
  - **`GET`**
    - It provides a READ only access to a resource.
  - **`POST`**
    - It is used to create a resource
  - **`DELETE`**
    - It is used to delete or remove a resource
  - **`PUT`**
    - It is used to update or create a resource when needed.
- **Note:**
  - _REST is an API (packages -> classes and interfaces)_
  - _A `java` class will be converted into REST class using two annotations:_
    1. _`@Path`_
    2. _`@ApplicationPath`_
  - _REST methods return only `JSON` objects in `String` format._

### Example: Simple Calculator (REST)

## JMS - Java Messaging Service - Message Driven bean

- JMS is an API which provides set of interfaces and classes for java applications to create, send, receive and read messages.
- It also exchanges the between different applications
- JMS is a messaging service which provides asynchornous communication between java applications
- JMS provides 2 types of messaging domains:
  1. **`PointToPoint`** messaging domain
     - In this type of messaging domain, it includes a sender, receiver and a queue in which one message will be sent to only one receiver.
  2. **`Publish/Subscribe`** messaging domain
     - In this type of messaging domain, it includes sender, receiver and a queue in which one message will be sent to multiple receivers.
     - In this approach, publisher acts as a sender and subscriber acts as a receiver
- Every message which is transferring from a sender to receiver, consists of 3 components:
  1. **`MessageHeader`**
  2. **`MessageProperties`**
  3. **`MessageBody`**
- **Note**: _All the messages sent by a sender will stay in queue until the receiver is free to receive the message._
