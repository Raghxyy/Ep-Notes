# CO-2 : Servlet and JSP

`Outcome: To build or create web applications`

## Servlet

- Introduction
- Why Servlet
- Advantages of servlets
- Servlet API
- Servlet LifeCycle
- Servlet Examples (3 ways)
- Init param and Context param
- Servlet database connectivity
- Create an HTML file in servlet
- Servlet chaining / Collaboration

### Introduction

- Web Application:

  - Any application that runs on a web server and can be accessed through a browser refers to web application.
  - Every webapp that we build or design must be associated with a URL (Uniform Resource Locator)
  - Components of web application are:
    1. **Frontend - Client side**
       - User directly interacts with webapp
       - Technologies: HTML, CSS, JS, Bootstrap, TailwindCSS and so on.
    2. **Backend - Server side**
       - Handles application logic and database connectivity
       - Languages: Python, Java, Node.JS, Ruby, PHP and so on.
       - Frameworks: Django, SprinBoot, ExpressJS, RubyOnRails and so on
    3. **Connectivity - Databases**
       1. SQL
          - Databases: MySQL, PostgreSQL, Oracle, dbSQLite3 and so on
       2. NoSQL
          - Databases: MongoDB, DynamoDB, Neo4j, Cassandra, Riak and so on
  - Benefits of web applications:
    1. Ease of access
    2. Cost effective etc
  - Challenges of webapp:
    1. Performance
    2. Security
    3. Browser compatibility etc

- Servlet:
  - It is techonology which is used to create a webapp.
  - It is also defined in many ways:
    1. An API with many classes and interfaces
    2. A web component that is deployed in a server machine inorder to create a webapp.
    3. Servlet is an interface that must be implemented to create a webapp

### Why Servlet

```
          request(url)
         ------------->
        /              \
    User                Web application (Server)
 Homepage <-------------/
             response

```

- **CGI**
  - Common Gateway interface
  - User requests will be implemented by process
- **Servlet**
  - User requests will be implemented by threads

```
Note:
  - Threads execute much faster than process, so requests handled by thread will execute faster than requests handled by process.
```

### Advantages of servlets

- Better performance
- Secured
- Portable

### Servlet API

- This API consists of many classes and interfaces
- All these classes and interfaces of servlet API are available in packages: `javax.servlet.*`,`javax.servlet.http.*`
- Different interfaces and classes in packages:

  1. `javax.servlet`:

     - **Interfaces**:

       1. `Servlet`
       2. `ServletRequest`
       3. `ServletResponse`
       4. `RequestDispatcher`

     - **Classes**:
       1. `GenericServlet`
       2. `ServletInputStream`
       3. `ServletOutputStream`

  2. `javax.servlet.http.*`:
     - **Interfaces**:
       1. `HttpServletRequest`
       2. `HttpServletResponse`
       3. `HttpSession`
     - **Classes**:
       1. `HttpServlet`
       2. `Cookie`
       3. `HttpSessionEvent`

- Different ways to create a servlet:
  1. **`Servlet`**:
     - It is an interface available in the package `javax.servlet`.
     - It defines some standard methods to be implemented.
     - Some of those are:
       1. init() - `To initialize servlet`
       2. service() - `To process user requests`
       3. destroy() - `To destroy the servlet`
       4. getServletConfig() - `To get the servlet configuration`
       5. getServletInfo() - `To get the servlet info.`
  2. **`GenericServlet`**:
     - Its a class available in the package `javax.servlet`
     - It implements `Servlet` interface
     - It provides all the methods of `Servlet` interface except `service()`.
     - Some methods within this class excluding the ones in `Servlet` interface:
       1. `getServletName()`
       2. `getServletContext()`
       3. `getServletParameter`
  3. **`HttpServlet`**:
     - Its a class available in `javax.servlet.http` package.
     - It is a class which extends `GenericServlet` class and provides only `HTTP` specific methods only.
     - Methods:
       1. `service()`
       2. `doPost()`
       3. `doGet()`
       4. `doDelete()`
       5. `doTrace()`
       6. `doOptions()`

### Servlet Life Cycle

- There are 5 phases in servlet life cycle
  1. Servlet class in loaded
  2. Servlet instance is created
  3. `init()` method is invoked
  4. `service()` method is invoked
  5. `destroy()` method is invoked

### init param and context param

- init param and context param are used to store data in database using servlet
- there param must be defined withing `web.xml`
- init-param
  - Must be defined withing specific servlet
  - Scope of the init param within a servlet
  - Syntax:

```xml
<!--web.xml-->
<web-app>
  <display-name>...</display-name>
  <servlet>
    <servlet-name>...</servlet-name>
    <servlet-class>...</servlet-class>

    <init-param>
      <param-name>...</param-name>
      <param-value>...</param-value>
    </init-param>
  </servlet>

  <servlet-mapping>
    <servlet-name>...</servlet-name>
    <url-pattern>...</url-pattern>
  </servlet-mapping>
</web-app>
```

- context-param
  - Must be defined to a application or project
  - Score of context param is within an app/project
  - Syntax:

```xml
<!--web.xml-->
<web-app>
  <display-name>...</display-name>
  <servlet>
    <servlet-name>...</servlet-name>
    <servlet-class>...</servlet-class>
  </servlet>

  <servlet>
    <servlet-name>...</servlet-name>
    <servlet-class>...</servlet-class>
  </servlet>

  <servlet>
    <servlet-name>...</servlet-name>
    <servlet-class>...</servlet-class>
  </servlet>

  <servlet-mapping>
    <servlet-name>...</servlet-name>
    <url-pattern>...</url-pattern>
  </servlet-mapping>

  <servlet-mapping>
    <servlet-name>...</servlet-name>
    <url-pattern>...</url-pattern>
  </servlet-mapping>

  <servlet-mapping>
    <servlet-name>...</servlet-name>
    <url-pattern>...</url-pattern>
  </servlet-mapping>

  <context-param>
      <param-name>...</param-name>
      <param-value>...</param-value>
  </context-param>
</web-app>
```

### Servlet datbase connectivity

### Create an HTML file in servlet

### Sevlet chaining or collaoration

### Servlet examples

1. Servlet Interface

   - Steps to be followed:
     1. Create a maven project with archetype `maven-archetype-webapp` with version 1.4
     2. Then delete `index.jsp` file
     3. Then change the maven compiler version to `1.8` from `1.7`
     4. Update the maven project with `Alt + F5`
     5. Then create java source folder and create a eclass within a package inside the java source folder
     6. Then edit `web.xml` , `pom.xml` as required
     7. Run the servlet on Server.

```xml
<!--web.xml-->
<servlet>
  <servlet-name>Demo</servlet-name>
  <servlet-class>com.trial.Demo</servlet-class>
</servlet>

<servlet-mapping>
  <servlet-name>Demo</servlet-name>
  <url-pattern>/hello</url-pattern>
</servlet-mapping>
```

```xml
<!--pom.xml-->
<dependency>
  <groupId>javax.servlet</groupId>
  <artifactId>javax.servlet-api</artifactId>
  <version>4.0.0</version>
  <scope>provided</scope>
</dependency>
```

```java
package com.trial;
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.Servlet;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
public class Demo implements Servlet{
	@Override
	public void destroy() {
		// TODO Auto-generated method stub

	}
	@Override
	public ServletConfig getServletConfig() {
		// TODO Auto-generated method stub
		return null;
	}
	@Override
	public String getServletInfo() {
		// TODO Auto-generated method stub
		return null;
	}
	@Override
	public void init(ServletConfig arg0) throws ServletException {
		// TODO Auto-generated method stub

	}
	@Override
	public void service(ServletRequest rq, ServletResponse rs) throws ServletException, IOException {

		rs.setContentType("text/html");

		PrintWriter pw = rs.getWriter();
		pw.println("<h1>Hello Java</h1>");

	}

}
```

2. GenericServlet
3. HttpServlet

## JSP - Java Server Pages

### Introduction

- JSP stands for `Java Server Pages`
- It is a technology which is used to create web applications like servlet (Dynamic web applications)
- It is used to build web application by inserting java code in a `HTML` document just like `Django Template language` (JSP Tags)
- Syntax:

```html
<!--index.jsp-->
<% java code %> --> JSP Tags
```

### Why JSP

- In JSP, the execution of an applicaiton is much faster than in servlet.
- It is must better than CGI too.

### Advantages of JSP over Servlet

- Easy to maintain or build applications
- Less code
- Rapid development

### JSP API

- Inorder to create a web application using JSP, I need to use JSP classes and interfaces which are available in a package named as `javax.servlet.jsp.*`
- Some of the popular interfaces and classes of JSP are:
  - Interfaces
    1. `JspPage`
       - It is an interface which extends `Servlet` interface.
       - Methods included are:
         1. `jspInit()`
         2. `jspDestroy()`
    2. `HttpJspPage`
       - It is an interface which extends `JspPage` interface.
       - Methods included are:
         1. `jspInit()`
         2. `jspDestroy()`
         3. `jspService()`
  - Classes
    1. `JspWriter`
    2. `JspException`
    3. `JspError`
    4. `JspContent`
    5. `JspFactory`

### JSP Lifecycle

- The life cycle of JSP goes through 7 phases:

1. Translation
   - JSP code will be converted to Servlet
2. Compilation
   - Java code will be compiled into `.class` files.
3. Loading Class
   - `.class` class will be loaded
4. Create instance
   - Objects will be created for the loaded class.
5. Initialization
   - `jspInit()`
6. User Request
   - `jspService()`
7. Destroy
   - `jspDestroy()`

### JSP Elements

- It will provide us ability to insert `java` code into `JSP` (JSP Tags)
- `JSP Elements` are used to form `JSP Tags`.

1. `scriplet` tag:

- It is defined as the standard tag of JSP
- Syntax: `<% java code %>`
- Example:

  ```html
  <html>
    <body>
      <% out.println("Good Evening!"); %>
    </body>
  </html>
  ```

- Example 2:

  ```html
  <form action="display.jsp" method="post">
    <input
      type="text"
      id="name"
      name="name"
      placeholder="Enter your name"
      required
    />
    <br /><br />
    <button type="submit">Submit</button>
  </form>
  ```

  ```html
  <html>
    <body>
      <% out.println("Hello, "+request.getParameter("name")); %>
    </body>
  </html>
  ```

2. `expression` tag

   - This tag is used to print the values which are either stored in a variable or method.
   - Syntax: `<%= code %>`

3. `declaration` tag
   - This tag is used to declare fields or methods
   - Syntax: `<%! field or method %>`
4. `template` tag
   - Any tag other than `scriplet`, `expression`, `declaration` are referred to be `template` tags

- Note:

  - All `HTML` tags and `XML` tags falls under a category knows as tempalte tag.

- **TODO**: JSP CRUD Operations (Additional topic)

### JSP Action tag

- JSP Action tags are used to execute a java code which is defined in `HTML` tags and it controls the flow of `.jsp` files.
- The different JSP Action tags are:

  1. `jsp forward`
     - This action tag is used to forward the request from one resource to the other resource where the other resources might be either `.jsp` or `.html` file(s).
     - Syntax:(`.jsp` file)
     - `<jsp:forward page="relative-url" />`
     - The relative url can be of `.html` or `.jsp` or any files.
     - Example:
  2. `jsp include`
     - This action tag is used to include the contents of another resource into an existing resource where the other resources might be `html` or `jsp` or any other file.
     - Syntax: (`.jsp file`)
     - `<jsp:include page="relative-url" />`
  3. `jsp param`

     - It is a tag used within `jsp:forward` tag or `jsp:include` tag to pass the parameters from one jsp file to other jsp file.
     - Syntax:

     ```jsp
     <!--for jsp:forward: -->
     <jsp:forward>
        <jsp:param name="" value="">
        <jsp:param name="" value="">
        <jsp:param name="" value="">
        .
        .
      </jsp:forward>
      <!--for jsp:include: -->
     <jsp:include>
        <jsp:param name="" value="">
        <jsp:param name="" value="">
        <jsp:param name="" value="">
        .
        .
      </jsp:include>
     ```

     - `jsp:param` tag along with `jsp:forward` tag is known as foward tag with parameter.
     - only `jsp:forward` tag without `jsp:param` tag known as forward tag without parameter.
     - `jsp:param` tag along with `jsp:include` tag is known as include tag with parameter
     - `jsp:param` tag along without `jsp:include` tag is known as include tag without parameter

  - Note:
    - Example 1 : Note-2
    - Example 2 : Note-4
    - Example 3 : Note-1

  4.  `jsp setProperty`

      - This tag is used to set properties of a `java bean` in a jsp page
      - Syntax:

      ```html
      <jsp:setProperty name="" propertyname="" propertyvalue="" />
      ```

      - Example: Will be discussed during MVC concept.

  5.  `jsp getProperty`

      - This tag is used to get properties of `java bean` in a jsp page.
      - Syntax:

      ```html
      <jsp:getProperty property="" name="" />
      ```

      - Example: Will be discussed during MVC concept.

### JSP Implicit objects

- These objects are pre defined in web container which can be used in any jsp file
- The different implicit objects are:

  1. `out`
     - It is used to display content on a web browser
     - Example:
     ```jsp
     <body>
        <% out.println("Hello World") %>
     </body>
     ```
  2. `request`

     - It is an object which is used to handle all the requests made by the user.
     - Example:

     ```html
     <body>
       <form action="display.jsp" method="post">
         <input type="text" name="name" />
         <input type="submit" value="Display" />
       </form>
     </body>
     ```

     ```html
     <!--display.jsp-->
     <body>
       <% out.println(request.getParameter("name")); %>
     </body>
     ```

  3. `response`

     - It is used to send a response based on user request.
     - Example:

     ```html
     <body>
       <form action="display.jsp" method="post">
         <input type="text" name="name" />
         <input type="submit" value="Display" />
       </form>
     </body>
     ```

     ```html
     <!--display.jsp-->
     <body>
       <% response.sendRedirect("<some-url>"); %>
     </body>
     ```

  4. `config`
  5. `application`
  6. `session`
  7. `page`
  8. `pagecontext`
  9. `exception`

### JSP directives

- JSP Directives are the messages that tells the web container how to translate a JSP file into servlet
- Syntax: `<%@ directive attribute="" %>`
- There are 3 types of directives:

  1. `page`

     - Syntax: `<%@ page attribute="value" %>`
     - Attributes:

       1. `import`

          - This is used to import packages and interfaces
          - Syntax: `<%@ page import="java.sql.*" %> `
          - Example:

          ```jsp
          <%@ page import="java.time.*" %>
          <body>
           <%= LocalTime.now() %>
          </body>
          ```

       2. `contentType`
          - This is used to set display either text or html on a web browser
          - Syntax: `<%@ page contentType="text/html" %>`
          - Example:
          ```jsp
          <%@ page language="java" contentType="text/html; charset=UTF-8"
          ```
       3. `errorPage`
          - Specifies the URL of another JSP page to handle exceptions thrown during the processing of the current page.
          - Syntax: `<%@ page errorPage="errorPage.jsp" %>`
          - Example
          ```jsp
          <%@ page errorPage="errorPage.jsp" %>
          ```
       4. `isErrorPage`

          - Indicates whether the current JSP page is an error page that handles exceptions.
          - Syntax: `<%@ page isErrorPage="true" %>`
          - Example

          ```jsp
          <%@ page isErrorPage="true" %>
          ```

       5. `info`

          - Provides a description of the JSP page, which can be retrieved using the `getServletInfo()` method.
          - Syntax: `<%@ page info="Description of the page" %>`
          - Example

          ```jsp
          <%@ page info="This is a sample JSP page" %>
          ```

       6. `buffer`
          - Defines the buffer size in kilobytes for the output of the JSP page.
          - Syntax: `<%@ page buffer="sizekb" %>`
          - Example
          ```jsp
          <%@ page buffer="16kb" %>
          ```

  2. `include`
     - Syntax: `<% include attribute="value" %>`
     - Different attributes:
       1. `file`
          - Syntax: `<%@ include file="relativeURL" %>`
          - Example:
          ```html
          <!-- header.jsp -->
          <!DOCTYPE html>
          <html>
            <head>
              <title>My Website</title>
            </head>
            <body>
              <header>
                <h1>Welcome to My Website</h1>
              </header>
              <!-- main.jsp -->
              <%@ include file="header.jsp" %>
              <main>
                <p>This is the example of include.</p>
              </main>
            </body>
          </html>
          ```
  3. `taglib`

### MVC (Model View Controller) architechture

- MVC stands for Model-View-Controller
- It is a design pattern or a standard architecture which consists of business logic (Model), presentation logic (View), interface (Controller)
- **Model:**
  - It represents the state of an application using business logic
- **View:**
  - It represents the presentation logic (UI)
- **Controller:**
  - It acts as an interface between business logic and presentation logic (Model and View)
- Advantages of MVC
  1. Easy to maintain larger applications
  2. Navigation control is easy
- Example: JDBC CRUD Operations following MVC architecture
