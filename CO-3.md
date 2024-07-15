# CO-3 : JSF & EJB

## JSF - Java Server Faces

- [CO-3 : JSF \& EJB](#co-3--jsf--ejb)
  - [JSF - Java Server Faces](#jsf---java-server-faces)
    - [Introduction](#introduction)
    - [Why JSF](#why-jsf)
    - [Advantages of JSF](#advantages-of-jsf)
    - [Features of JSF](#features-of-jsf)
    - [JSF Life Cycle](#jsf-life-cycle)
    - [JSF UI Elements or Components](#jsf-ui-elements-or-components)
    - [Bean Class](#bean-class)
    - [JSF Validation](#jsf-validation)
    - [JSF Converters](#jsf-converters)
  - [EJB - Enterprise Java Bean](#ejb---enterprise-java-bean)
    - [Introduction](#introduction-1)
    - [Why EJB](#why-ejb)
    - [Advantages of EJB](#advantages-of-ejb)
    - [When to use EJB](#when-to-use-ejb)
    - [EJB Architecture](#ejb-architecture)
    - [EJB Types/ Flavors](#ejb-types-flavors)
    - [EJB Database Access](#ejb-database-access)

### Introduction

- JSF stands for Java Server Faces
- JSF is a server side UI framework to develop dynamic web applications
- It consists of many APIs and tag libraries
- It provides several UI components or elements and it also provides validation, convertors, Page Navigation etc...
- Latest version of JSF `3.0.2`

### Why JSF

- It provides good security over JSP

### Advantages of JSF

- It provides clean and clear seperation between the presentation and behaviour of the webapplicaiton
- JSF provides `Component` class name to create our own custom components
- JSF includes facelet technology which is a massive advantage of JSF framework.

### Features of JSF

- Easy to develop
- Rapid Development
- Supports HTML file
- Security
- Default

### JSF Life Cycle

- Begins whenever a user make a `http or https` request and ends when server responds to the same request.
- JSF Life cycle will have two phases:
  1. Execute phase
  2. Render phase

### JSF UI Elements or Components

- JSF UI elements are basic building blocks used to create UI in webapps.
- The different JSF UI components/ elements are:

  1. Core components
     - The core components of JSF components are:
       1. `<h:outputText>`
          - This element or component is used to desiplay content on a webpage
          - Syntax: `<h:outputTest id="<some_name>" value="<some_value>">`
          - Syntax2: `<h:outputText name="<some_name>" value="<#{bcob.property}>" />`(bcob: bean Class Object)
          - Example:`<h:outputText id = "id" value="Welcome to JSF" />`
          - Example2: `<h:outputTest name="text" value="#{e.eid}" />`
          - Note:
            - Attributes:
              - `style`, `class` and so on.
       2. `<h:inputText>`
          - This element or component is used to create an input field for user
          - Syntax: `<h:inputText id="name" value = "#{bcob.property}" />`
          - Example: `<h:inputText id = "name" value="#{e.ename}" />`
       3. `<h:inputTextarea>`
          - This element or component is used to create an input field which accepts larger text
       4. `<h:inputSecret>`
          - THis element or component is used to create an input field where text entered will be masked
       5. `<h:inputFile>`
          - Used to provide an input field where file is given as input
       6. `h:graphicImage`
          - Used to display image on a browser
          - Syntax: `<h:graphicImage id="" value="#{Resource['path']} />"`
  2. Form components

     - The different form components of JSF components are:
       1. `<h:form>`
          - THis element is used to create a form.
          - Syntax: `<h:form action="" method=""> {elements} </h:form>`
          - Attributes: `onclick`, `onsubmit` and so on.
       2. `<h:inputHidden>`
          - uSed to create an input field for the purpose of pwd same as `inputSecret`
          - But the difference betweeen input secret and input hidden is text will be represented as `...` in case of inputSecret whereas text will be represented as `empty character` in inputHidden
          - Syntax: `<h:inputHidden id = "" name="#{bcob.property}  />"`
       3. `<h:commandButton>`
          - THis element is used to create a button in a form.
          - Syntax: `<h:commandButton value="Click me" action="url.filename"/>`
       4. `<h:commandLink>`
          - Used to create hyperlinks on webapps
          - Syntax: `<h:commandLink value="Try me" action="url/filename"/>`
          - Attributes:

  3. DataTable components
     - THe databtable components of JSF components are
       1. `h:dataTable`
          - Used to display data with table
          - Syntax: `<h:dataTable id="someID" value="#{bcob.ListOb}" var="someVar" />`
          - Attributes:
       2. `h:column`
          - This element or component is used to define a column in `<dataTable>`
          - Syntax: `<dataTable> <h:column> <!column data>  </h:column>  </dataTable>`
          - Example:
          ```xhtml
          <h:dataTable>
            <h:column>
              <f:facet name="id">ID</f:facet>
              #{e.eid}
            </h:column>
          </h:dataTable>
          ```
  4. Select components

     - The different types of select components in JSF components are

       1. `<h:selectOneMenu>`

          - this element or component is used to select one option among available options (DropDown menu)
          - Syntax:

          ```xhtml
          <h:selectOneMenu
            name="dropDownRaZuka :)"
            value="#{bcob.selectedOption}"
          >
          </h:selectOneMenu>
          ```

          - Attributes:
          - Example:

          ```xhtml
          <h:selectOneMenu name="dropDownRaZuka :)" value="valueOne">
            <f:selectItem itemValue="ValueOkati" itemName="valueeeee" />
            <f:selectItem itemValue="ValueOkat" itemName="valueeee" />
            <f:selectItem itemValue="ValueOki" itemName="valueee" />
            <f:selectItem itemValue="ValueOk" itemName="valuee" />
          </h:selectOneMenu>
          ```

       2. `<h:selectOneRadio>`
          - This element is used to choose one among the two options available
          - Syntax and Example
          ```xhtml
          <h:selectOneRadio value="#{bean.gender}">
            <f:selectItem itemLabel="Male" itemValue="Male" />
            <f:selectItem itemLabel="Female" itemValue="Female" />
          </h:selectOneRadio>
          ```
          - Attributes:

- Note:
  - Attribute defines the property of a tag
  - Every attribute consists of name and value.
  - Syntax: `<tagname attributeName="attributeValue" />`

### Bean Class

- A class MUST satisfy the following 2 conditions in order to act as a Bean class

1. All the data memebers in the class must be `private`
2. All the methods in the Bean class must only be getters and setter for all data members available

- Bean class is also called as POJO class or entity class
- Bean class in JSF will be implemented using an annotation `@ManagedBean(name=,eager=)`
- Ex:

```java
@ManagedBean(name=,eager=)
class Employee{
   private int id;
   private String name;
   private double salary;
   /*getters and setters*/
}
```

### JSF Validation

- Validation refers to validating the data provided by the user
- It is used to check whether the value entered in a field is valid or not.
- JSF provides a set of classes and tags which helps in validating the data.
- JSF validations are of 2 types:

  1. Built-in validation or Standard validation

     1. **Length validation:**
        - It is used to validate the input element with a certain limit using the attributes `maximum` and `minimum`
        - tagname: `<f:validateLength>`
        - Syntax:
        ```xhtml
        <h:outputLabel for="password" value="Password:" />
        <h:inputSecret id="password" value="#{bean.password}">
          <f:validateLength attribute="value" />
        </h:inputSecret>
        <h:message for="password" /><br />
        ```
        - Example:
        ```xhtml
        <h:outputLabel for="password" value="Password:" />
        <h:inputSecret id="password" value="#{bean.password}">
          <f:validateLength minimum="6" maximum="12" />
        </h:inputSecret>
        <h:message for="password" /><br />
        ```
     2. **Required validation:**

        - It is used to make a particular field as mandatory to fill
        - tag: `<f:validateRequired>`
        - Syntax:

        ```xhtml
        <h:outputLabel for="password" value="Password:" />
        <h:inputSecret id="password" value="#{bean.password}">
          <f:validateRequired />
        </h:inputSecret>
        <h:message for="password" /><br />
        ```

        - Example:

        ```xhtml
        <h:outputLabel for="password" value="Password:" />
        <h:inputSecret id="password" value="#{bean.password}">
          <f:validateRequired />
        </h:inputSecret>
        <h:message for="password" /><br />
        ```

     3. **Required validation:**
        - It is used to validate a field using Regular expression(used for password field).
        - tag: `<f:validateRegex />`
        - Syntax:
        ```xhtml
        <h:outputLabel for="password" value="Password:" />
        <h:inputSecret id="password" value="#{bean.password}">
          <f:validateRegex pattern="regularExp" />
        </h:inputSecret>
        <h:message for="password" /><br />
        ```
        - Example:
        ```xhtml
        <h:outputLabel for="password" value="Password:" />
        <h:inputSecret id="password" value="#{bean.password}">
          <f:validateRegex pattern="[a-zA-Z][a-zA-Z0-9]*" />
        </h:inputSecret>
        <h:message for="password" /><br />
        ```
     4. **Double Range validation:**

        - It is used to check whether the local value of a component is within a certain range or not. The value must be floating-point or convertible to floating-point.
        - Syntax:

        ```xhtml
        <h:inputText id="input" value="#{bean.value}">
          <f:validateDoubleRange minimum="minValue" maximum="maxValue" />
        </h:inputText>
        <h:message for="input" />
        ```

        - Example:

        ```xhtml
        <h:inputText id="age" value="#{user.age}">
          <f:validateDoubleRange minimum="18" maximum="100" />
        </h:inputText>
        <h:message for="age" />
        ```

     5. **Long Range validation:**
        - It is used to check whether the local value of a component is within a certain range or not. The value must be any numeric type or String that can be converted to a long.
        - Syntax:
        ```xhtml
        <h:inputText id="input" value="#{bean.value}">
          <f:validateLongRange minimum="minValue" maximum="maxValue" />
        </h:inputText>
        <h:message for="input" />
        ```
        - Example:
        ```xhtml
        <h:inputText id="quantity" value="#{product.quantity}">
          <f:validateLongRange minimum="1" maximum="100" />
        </h:inputText>
        <h:message for="quantity" />
        ```

  2. Bean class validation (Bean Validation - `Redhat`)

     - JSF provides validation for a Bean class in the form of annotation
     - Annotation can be placed for the data-member/ methods/ class itself
     - Example:

     ```java
         @ManagedBean(name="",eager="")
         class Employee{
            private int eid;
            private String ename;
            private double esal;
            // All the getters and setters
         }
     ```

     - The different types of Bean validations are:

       1. `@NotNull`
          - This is used to set a not null to a field or property
          - Example:
          ```java
            @NotNull
            private int id;
          ```
       2. `@Null`
          - This is used to set a null value to a field or property
          - Example:
          ```java
            @Null
            private int id;
          ```
       3. `@Size`

          - This is used to set the value of a field or property with a specific size
          - Example:

          ```java
            @Size(min=x,max=y)
            private String msg;
          ```

       4. `@Digits`

          - This is used to set the value of a field or property which must be a number of a specific length where the number consists of integer and fraction part.
          - Example:

          ```java
            @Digits(Integer=x,Fraction=y) //Integer - LHS of '.', Fraction - RHS of '.'
            private long phone;
          ```

       5. `@Min`

          - This is used to set a value of a field or property that must be a number which is greater than or equals to the given value
          - Example:

          ```java
            @Min("2200000000")
            private long studId;
          ```

       6. `@Max`

          - This is used to a value of a field or property that must be a number which is less than or equals to the given value
          - Example:

          ```java
            @Max("2200099999")
            private long studId;

          ```

       7. `@Pattern`

          - This is used to set the value of a field or a property that must be a regular expression.
          - Example:

          ```java
            @Pattern(regex="")
            private String email;
          ```

       8. `@DecimalMin`

          - This is used to a field or property that must be a decimal value greater than or equals to given number
          - Example:

          ```java
            @DecumalMin("30.00")
            private double discount;
          ```

       9. `@DecimalMax`

          - This is used to set a field or property that must be a decimal value less than or equal to the given number
          - Example:

          ```java
               @DecimalMax("40.00")
               private double discount;
          ```

       10. `@Past`

       - This is used to set a value to a field or property that must be past date.
       - Example:

       ```java
         @Past
         private Date pastDate;

       ```

       11. `@Future`

       - This is used to set a value to a field or property that must be a future date
       - Example:

       ```java
         @Future
         private Date futureDate;
       ```

       12. `@AssertTrue`

       - This is used to set a value to a field or property that must be of boolean type which states `true`
       - Example:

       ```java
         @AssertTrue
         private boolean state;
       ```

       13. `@AssertFalse`

       - This is used to set a value to a field or property that must be of boolean type which states `false`
       - Example:

       ```java
         @AssertFalse
         private boolean state;
       ```

### JSF Converters

- JSF converters are used to convert data of one form to another form
- THe data type will be string by default in String type that we need to convert to another type based on required
- Data converters are available in a package
- JSF converters will convert the String data type(Default) to its respective converter
- JSF converters are available in a package named as `javax.faces.convert`
- Converter tag or element will be represented as `<f:converter converterID="" >`
- **Note:** This tag or element must have an attribute converterID
- The different converter IDs are:

  1. `javax.faces.Integer`

     - This is used to convert the data type from String to Integer
     - Syntax:

     ```xhtml
     <h:inputType id="someID" value="#{bacob.property}">
       <f:converter attribute="value" />
     </h:inputType>
     ```

     - Example:

     ```xhtml
     <h:inputType id="eid" value="#{e.eid}">
       <f:converter converterID="javax.faces.Integer" />
     </h:inputType>
     ```

  2. `javax.faces.Number`
  3. `javax.faces.Float`

     - This is used to convert the data type from String to Float
     - Syntax:

     ```xhtml
     <h:inputType id="someID" value="#{bacob.property}">
       <f:converter attribute="value" />
     </h:inputType>
     ```

     - Example:

     ```xhtml
     <h:inputType id="cgpa" value="#{s.cgpa}">
       <f:converter converterID="javax.faces.Float" />
     </h:inputType>
     ```

  4. `javax.faces.Double`
  5. `javax.faces.Byte`
  6. `javax.faces.Boolean`
  7. `javax.faces.Character`
  8. `javax.faces.BigInteger`
  9. `javax.faces.BigDecimal`

- Note:

  - `DateTime`: It is used to convert that data from a String type to a form called DateTime.
  - Tag name: `<f:convertDateTime />`
  - Syntax:

  ```xhtml
  <h:inputType id="someID" value="#{bacob.property}">
    <f:convertDateTime attribute="value" />
  </h:inputType>
  ```

  - Example:

  ```xhtml
  <h:inputType id="dob" value="#{e.dob}">
    <f:convertDateTime pattern="dd-MM-YYYY" />
  </h:inputType>
  ```

## EJB - Enterprise Java Bean

### Introduction

- EJB Stands for Enterprise java bean
- It is a server side component that summarizes the business logic of an application. (or) server side component used to built java application
- To run EJB we need to have sesrver like jboss, tomcat, glassfish, etc

### Why EJB

- EJB simplifies the development of small and large scale enterprise applications

### Advantages of EJB

- Built in security
- Scalability
- Remote Access
- Many complex features are available

### When to use EJB

- When applciation needs remote access
- When application needs to be scalable (load balancing)
- When your application needs encapsulated business logic (Abstraction) (Simplification)

### EJB Architecture

- It consists of 2 layers. They are :
  - **Application layer :** The layer where servers are available to run application
  - **EJB Container :** All EJB components will be available here

### EJB Types/ Flavors

- EJB is differentiated into 3 types
  1. **Session bean:**
     - It is used to build the logic of an application
     - It is classified into 2 types:
       1. **Stateless bean:** If the session bean is stateless, there wil be no `STATE`; maintained for all the methos in class
       2. **Stateful bean:** If the session bean is stateful there will be `STATE` maintained for all the methods in a class
  2. Message driven bean
  3. Entity bean (JPA)

### EJB Database Access
