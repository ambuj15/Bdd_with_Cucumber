# API Tutorial

**What is an API?**

* Api stands for Application Programming Interface.
* **When two independent systems (Client and Server) interacts with each other then the platform which is used is called API.**
* Generally, it just means an agreement about how some library or service will work.
* **It need not even be language specific means we can create API's using Java, Python, Ruby, C#.**
* API interacts between different systems in two languages Json and XML.
* An API exactly defines the methods for one software program to interact with the other. The system can use Rest or SOAP to interact using the languages like JSON or XML for communication.

> API's can be written in any language because ultimately the communication between client and server will happen in either JSON or XML format.

> Now API is a platform but there must be some set of rules , architectures or protocols that must be followed in order to enable the communication between Client and server these architectures and protocols are defined under RestFul Web Services and SOAP.

**What is web service API**

When the exchange of information between client(Who seek's information) and server(Who provides information) happens over the web using **http protocol as a medium and Json or XML as a language then that API is called Web service API.**

**Note: Sometime people confuses API as JAR's but they are all together different.**

>API is an Application Programming Interface, a collection of routines to do some specific work. A jar is a file object to encapsulate an API or more.
### Web API's can be of following types:
 * **Open API's :** Open APIs, also known as external or public APIs, are available to developers and other users with minimal restrictions. They may require registration, and use of an API key, or may be completely open. They are intended for external users (developers at other companies, for example) to access data or services.
 * **Internal API's :** In contrast to open APIs, internal APIs are designed to be hidden from external users. They are used within a company to share resources. They allow different teams or sections of a business to consume each other’s tools, data and programs.
 * **Partner API's :** Partner APIs are technically similar to open APIs, but they feature restricted access, often controlled through a third-party API gateway. They are usually intended for a specific purpose, such as providing access to a paid-for service. This is a very common pattern in software as a service ecosystem. Eg: AIRLINES exposing their API's to MMT and other booking apps.
 * **Composite API's :** Composite APIs allow developers to access several endpoints in one call. These could be different endpoints of a single API, or they could be multiple services or data sources. Composite APIs are especially useful in microservice architectures, where a user may need information from several services to perform a single task.

###Types of Web Services

![Types Of Web Services](https://github.com/ambuj15/MyNotesHub/blob/main/Resources/Images/TypesOfWebServices.png "Types of Web Services")

> **V.Imp.Note :** REST and SOAP are not type of API's they are Architectures or Protocols which API uses or follows to enable communication between client and server.
### RESTful Webservice or Rest API

* REST stands for **REpresentational State Transfer.**
* REST is a set of architectural constraints, not a protocol or a standard as in SOAP. API developers can implement REST in a variety of ways.
* REST is not restricted to XML and its the choice of implementer which Media-Type to use like XML, JSON, Plain-text,HTML, XLT, Python, PHP. Moreover, REST can use SOAP protocol but SOAP cannot use REST.
* Something else to keep in mind: **Headers and parameters are also important in the HTTP methods of a RESTful API HTTP request,** as they contain important identifier information like metadata, authorization, uniform resource identifier (URI), caching, cookies, and more.
* Rest follows six important standards:
   * **Client-server architecture :** A client-server architecture made up of clients, servers, and resources, with requests managed through HTTP.
   * **Stateless client-server communication :** Meaning no client information is stored between get requests and each request is separate and unconnected.
   * **Cacheable data :** That streamlines client-server interactions.
   * **A uniform interface** between components so that information is transferred in a standard form.
   * **A layered system** that organizes each type of server (those responsible for security, load-balancing, etc.) involved the retrieval of requested information into hierarchies, invisible to the client.
   * **Code-on-demand (optional):** the ability to send executable code from the server to the client when requested, extending client functionality.>
  
> Question : Though rest API has 6 criterias still it is considered easier. Why?
>
> Answer : Though the REST API has these criteria to conform to, it is still considered easier to use than a prescribed protocol like SOAP (Simple Object Access Protocol), which has specific requirements like XML messaging, and built-in security and transaction compliance that make it slower and heavier.


In contrast, **REST is a set of guidelines that can be implemented as needed, making REST APIs faster and more lightweight, with increased scalablity—perfect for Internet of Things (IoT) and mobile app development.**

### SOAP

* SOAP stands for Simple Object Access Protocol
* Since SOAP is a protocol, it follows a strict standard to allow communication between the client and the server.
* Because it is a protocol, it imposes built-in rules that increase its complexity and overhead, which can lead to longer page load times. Hence it is slower than REST
* SOAP was designed so that applications built with different languages and on different platforms could communicate.
* SOAP uses only XML for exchanging information in its message format.
* On the basis of Security, SOAP has SSL( Secure Socket Layer) and WS-security whereas REST has SSL and HTTPS.
* In the case of Bank Account Password, Card Number, etc. SOAP is preferred over REST.

### Difference between SOAP and REST
* SOAP stands for Simple Object Access Protocol and REST stands for REpresentational State Transfer.
* Since SOAP is a protocol, it follows a strict standard to allow communication between the client and the server whereas REST is an architectural style that doesn’t follow any strict standard but follows six constraints defined by Roy Fielding in 2000. Those constraints are – Uniform Interface, Client-Server, Stateless, Cacheable, Layered System, Code on Demand.
* SOAP uses only XML for exchanging information in its message format whereas REST is not restricted to XML and its the choice of implementer which Media-Type to use like XML, JSON, Plain-text. Moreover, REST can use SOAP protocol but SOAP cannot use REST.
* On behalf of services interfaces to business logic, SOAP uses @WebService whereas REST instead of using interfaces uses URI like @Path.
* SOAP is difficult to implement and it requires more bandwidth whereas REST is easy to implement and requires less bandwidth such as smartphones.
* Benefits of SOAP over REST as SOAP has ACID compliance transaction. Some of the applications require transaction ability which is accepted by SOAP whereas REST lacks in it.
* On the basis of Security, SOAP has SSL( Secure Socket Layer) and WS-security whereas REST has SSL and HTTPS .In the case of Bank Account Password, Card Number, etc. SOAP is preferred over REST. The security issue is all about your application requirement, you have to build security on your own. It’s about what type of protocol you use.

### Difference Between API and Web Service
Refer : https://medium.com/@programmerasi/difference-between-api-and-web-service-73c873573c9d#:~:text=An%20API%20generally%20involves%20calling,don't%20involve%20Web%20service.

### Understanding API, Client Server and HTTP protocol through a live example.

To understand the client server analogy we have to come up with few things:

1. **A medium for communication**, specifically a protocol for two systems to interact. **Also called HTTP communication protocol**
2. A protocol to ask for the required details from the server. This could be in any form of formatted data. Most commonly used formats are XML and Json.
3. Server responds by sending a Response in any form of formatted data, here also it could be XML or JSON.

**To Summarize:** A Client and a Server establishes a connection using HTTP protocol. Once the connection is established, Client sends across the request to the Server in the form of XML or JSON which both entities (Client and Server) understand. After understanding the request Server responds with appropriate data by sending back a Response.

Suppose we need an info about today's weather conditions in our city then the information flow using Web Service Api will occur in the following way:

* Client established the connection with server using HTTP protocol.
* Client creates a request by entering required parameters like City name, State , Country etc. and sends it to the server using HTTP protocol in any language be it Json or XML.
* Server receives the information and processes it and then responds and share the response in the form of Json/XMl.

## HTTP Request

Http request basically is a file formatted in the for, of Json and XML which sends client's(Source computer) binary data to Server (Receiving computer)

**_Different types of HTTP request methods_** : All these methods are used to perform CRUD (Create, read, update, Delete) operations and all of them are case sensitive i.e all of them should be written in uppercase.

* **_GET :_** This request is used to retrieve the data from the server. Everytime you hit any website get request is triggered which makes it the most commomnly used request. 
Some important points about get request are:
**a)** It does not have any body.
**b)** It only supports String data type.
**c)** We can easily bookmark the data using the GET method.
**d)** The limit of the length of values is generally 255 characters for the GET method.

* **_HEAD :_** The Head method is similar to the Get method, but it retrieves only the header data and not the entire response body. Moreover, we use it when you need to check the document’s file size without downloading the document.

* **_POST :_** It is used to send data to the server. It is mostly used when we want to add or update any data to the server. The form fill up is an example of POST request. Some of the key features of POST request are:

  **a)** Data passed through the POST method is not visible in the browser URL.
  **b)** Additionally, values passed through POST are not stored in browser history.
  **c)** Moreover, there is no restriction on the length of data sent through the POST method.
  **d)** Also, POST method request supports different data types like String, binary, integers, etc.
  **e)** **POST is NOT idempotent** i.e. You will not get the same response again and again if you hit the same POST request.

* **_PUT :_** The Put method is similar to the Post method since it updates the data. The only difference is that we use it when we have to replace an existing entity completely. Also, **PUT methods are idempotent, i.e., they return the same result on executing repeatedly.**

* **_PATCH :_** This method is again similar to Post and Put methods, but we use it when we have to update some data partially. Moreover, unlike the Post and Put methods, you may send only the entity that needs updation in the request body with the Patch method.

* **_DELETE :_** Like its name, the Delete method deletes the server’s representations of resources through the specific URL. Additionally, just like the Get method, they do not have a request body.

* **_OPTIONS :_** This is not a widely used method when compared to other ones. It returns data specifying the different methods and the operations supported by the server at the given URL. Moreover, it responds with an Allow header giving a list of the HTTP methods allowed for the resource.

**What is the structure of an HTTP Request?
The next step is to understand how an HTTP request looks like and how it is structured. An HTTP request consists of-

* Request Line ( Http method used + Request URI + HTTP protocol Version)
* Zero or more headers (Authorization, Content-type, cookie, HOST)
* An optional request body (Usually XML or JSON payload)

>URI: It's basically a combination of path parameter(End Point) and URL.

**What is Query parameter?**
Query parameters are the most common type of parameters. They appear at the end of the request URL after a question mark (?), with different name=value pairs separated by ampersands (&). Query parameters can be required and optional.

API Query parameters can be defined as the optional key-value pairs that appear after the question mark in the URL

Eg: 
**1. https://example.com/articles?sort=ASC&page=2**

In this URL, there are two query parameters, sort, and page, with ASC and 2 being their values, respectively.

**2. http//www.techopedia.com/search.aspx?q=database&ion-all**

In the URL above, the bolded values after the ‘?’ are the query parameters, q=database&ion-all (query string).

**What is Path Parameter**

Path parameters are variable parts of a URL path. **They are typically used to point to a specific resource within a collection, such as a user identified by ID.** A URL can have several path parameters, each denoted with curly braces **{ }.**

Eg:

1. GET /users/{id}
2. GET /cars/{carId}/drivers/{driverId}
3. GET /report.{format}

Above you can see that path parameters can be placed anywhere in the URI and they usually generated collection of data.

**Some important differences between GET and POST**
1. In GET Data goes through the header while in POST Data flows through the request body
2. In GET the size of data is limited to 255 character while in POST no limit on the size of data.
3. In GET since the data passes through the URL, it becomes insecure while in POST data is secure since it is not exposed
4. GET requests wait for the response of the previous request before sending the next request while the POST request does not wait for a successful response from the previous request before hitting the next one.
5. GET can be cached and bookmarked while the POST can't be cached and bookmarked.
6. In GET only String data type is allowed but no such restrictions in POST.

## HTTP Response
It is basically the response given by the server to the HTTP request sent by the client through HTTP protocol. It is basically an acknowledgement that the operation client performed is completed but whether the response is success or failure that is a different picture.

**What is the structure of an HTTP Response?

* Status Line (Http protocol version + Status code + Reason phrase)
* Zero or more headers (Content-type)
* An optional message body

**Status Code**

Every HTTP response comes with a status code. Moreover, this status code is a 3-digit integer value. **The first digit represents the class of the response. Moreover, the last 2 digits do not have any categorical value.** There are five distinct values that the first digit of the status code can take. In our example, the status code is 200. But that is not the only status code your response may come with. Additionally, the below table summarizes the different status codes you might come across.

* **1xx: Informational:** It means the request was received and the process is continuing.
* **22xx: Success:** It means the action received was successful, understandable, and acceptable.
* **33xx: Redirection:** This means further action must be taken to complete the request.
* **44xx: Client Error:** It means the request contains incorrect syntax or cannot fulfill.
* **55xx: Server Error:** It means the server failed to fulfill/ complete an apparently valid request.

**What are different HTTP Response Status Codes?**
As seen above, Status codes separate into 5 different categories. Consequently, let’s see those in details:


**1xx**	Information, i.e., it denotes that the request has been received and under process.
**100**	Continue: The client can continue with the request as long as it doesn’t get rejected.
**101**	Switching Protocols: The server is switching protocols.
**2xx**	Success, i.e., it denotes a successful receipt, processing, and acceptance of the request message.
**200**	OK: The request is OK.
**201**	Created: A successfully created new resource
**202**	Accepted: Request accepted for processing, but in progress
**203**	Non-Authoritative Information: The information in the entity header is not from an original source but a third-party
**204**	No Content: Response with status code and header but no response body
**205**	Reset Content: The form for the transaction should clear for additional input
**206**	Partial Content: Response with partial data as specified in Range header
**3xx**	Redirection, i.e., further action has to be taken for the request to complete
**300**	Multiple Choices: Response with a list for the user to select and go to a location
**301**	Moved Permanently: Requested page moved to a new url
**302**	Found: Requested page moved to a temporary new URL
**303**	See Other: One can find the Requested page under a different URL
**305**	Use Proxy: Requested URL need to access through the proxy mentioned in the Location header
**307**	Temporary Redirect: Requested page moved to a temporary new URL
**4xx**	Client Error, i.e., incorrect syntax or error in fulfillment of the request
**400**	Bad Request: Server unable to understand the request
**401**	Unauthorized: Requested content needs authentication credentials
**403**	Forbidden: Access is forbidden
**404**	Not Found: Server is unable to find the requested page
**405**	Method Not Allowed: Method in the request is not allowed
**407**	Proxy Authentication Required: Need to authenticate with a proxy server
**408**	Request Timeout: The request took a long time as expected by the server
**409**	Conflict: Error in completing request due to a conflict
**411**	Length Required: We require the “Content-Length” for the request to process
**415**	Unsupported Media Type: Unsupported media-type
**5xx**	Server Error, i.e., error invalid request fulfillment at server side
**500**	Internal Server Error: Request not completed due to server error
**501**	Not Implemented: Server doesn’t support the functionality
**502**	Bad Gateway: Invalid response from an upstream server to the server. Hence, the request not complete
**503**	Service Unavailable: The server is temporarily down
**504**	Gateway Timeout: The gateway has timed out
**505**	HTTP Version Not Supported: Unsupported HTTP protocol version

## Idempotency in Rest API's

In the context of REST APIs, when making multiple identical requests has the same effect as making a single request – then that REST API is called **idempotent.**

Idempotence essentially means that the result of a successfully performed request is independent of the number of times it is executed. For example, in arithmetic, adding zero to a number is an idempotent operation.

> **The need and benefits of Idempotency:**  Suppose while developing any API developer made a mistake and now duplicate requests are coming to the API, these duplicacy can also be intentional and some time unintentional (e.g. due to timeout or network issues). You have to design fault-tolerant APIs in such a way that duplicate requests do not leave the system unstable.

**Idempotency in different HTTP methods**

If you follow REST principles in designing API, you will have automatically idempotent REST APIs for GET, PUT, DELETE, HEAD, OPTIONS and TRACE HTTP methods. Only POST APIs will not be idempotent.

1. POST is NOT idempotent.
2. GET, PUT, DELETE, HEAD, OPTIONS and TRACE are idempotent.

Let’s analyze how the above HTTP methods end up being idempotent – and why POST is not.

**HTTP POST**
Generally – not necessarily – POST APIs are used to create a new resource on server. So when you invoke the same POST request N times, you will have N new resources on the server. So, POST is not idempotent.

**HTTP GET, HEAD, OPTIONS and TRACE**
GET, HEAD, OPTIONS and TRACE methods NEVER change the resource state on server. They are purely for retrieving the resource representation or meta data at that point of time. So invoking multiple requests will not have any write operation on server, so GET, HEAD, OPTIONS and TRACE are idempotent.

**HTTP PUT**
Generally – not necessarily – PUT APIs are used to update the resource state. If you invoke a PUT API N times, the very first request will update the resource; then rest N-1 requests will just overwrite the same resource state again and again – effectively not changing anything. Hence, PUT is idempotent.

**HTTP DELETE**
When you invoke N similar DELETE requests, first request will delete the resource and response will be 200 (OK) or 204 (No Content). Other N-1 requests will return 404 (Not Found). Clearly, the response is different from first request, but there is no change of state for any resource on server side because original resource is already deleted. So, DELETE is idempotent.

Please keep in mind if some systems may have DELETE APIs like this:
```sh
DELETE /item/last
```
In the above case, calling operation N times will delete N resources – hence DELETE is not idempotent in this case. In this case, a good suggestion might be to change the above API to POST – because POST is not idempotent.
```sh
POST /item/last
```
Now, this is closer to HTTP spec – hence more REST compliant.

>REST stands for Representation State Transfer.
>SOAP stands for Simple Object Access Protocol

## POJO Class

* POJO in Java stands for Plain Old Java Object.
* Generally, a POJO class contains variables and their Getters and Setters.

**Example:**
POJO class is used to define the object entities. For example, we can create an Employee POJO class to define its objects.

Below is an example of Java POJO class:

```

// POJO class Exmaple  
package Jtp.PojoDemo;  
public class Employee {  
private String name;  
private String id;  
private double sal;  
public String getName() {  
    return name;  
}  
public void setName(String name) {  
    this.name = name;  
}  
public String getId() {  
    return id;  
}  
public void setId(String id) {  
    this.id = id;  
}  
public double getSal() {  
    return sal;  
}  
public void setSal(double sal) {  
    this.sal = sal;  
}  
}  
```

### Properties of POJO class
Below are some properties of the POJO class:

* The POJO class must be public.
* It must have a public default constructor.
* It may have the arguments constructor.
* All objects must have some public Getters and Setters to access the object values by other Java Programs.
* The object in the POJO Class can have any access modifies such as private, public, protected. But, all instance variables should be private for improved security of the project.
* A POJO class should not extend predefined classes.
* It should not implement prespecified interfaces.
* It should not have any prespecified annotation.

### What is Serialization?
* **Serialization** is the process of converting objects (created using POJO) into a stream of data(Json).
* The serialization and deserialization process is platform-independent, it means you can serialize an object in a platform and deserialize in different platform.

###  What is Deserialization?
* **Deserialization** is the process of converting a stream of data(JSON) into objects(POJO).
* The main purpose of serialization and deserialization is to persist the data and recreate whenever needed.

### How serialization and deserialization can be performed?
Rest Assured can use the Jackson 2 library, GSON library or Jackson library for serialization and deserialization.

>**What is JSON?**
>JSON is a format that encodes objects in a string. 

### Example of Serial and Deserialization

Let's serialize a Java object to a Json file and then read that Json file to get the object back i.e Deserialize it. In this example, we've created a Student class. We'll create a student.json file which will have a json representation of Student object.

```
import java.io.BufferedReader; 
import java.io.FileNotFoundException; 
import java.io.FileReader; 
import java.io.FileWriter; 
import java.io.IOException;  

import com.google.gson.Gson; 
import com.google.gson.GsonBuilder;  

public class GsonTester { 
   public static void main(String args[]) { 
   
      GsonTester tester = new GsonTester(); 
      try { 
         Student student = new Student(); 
         student.setAge(10); 
         student.setName("Mahesh"); 
         tester.writeJSON(student);  
         Student student1 = tester.readJSON(); 
         System.out.println(student1); 
      } 
      catch(FileNotFoundException e) { 
         e.printStackTrace(); 
      } 
      catch(IOException e) { 
         e.printStackTrace();
      } 
   } 
   
   private void writeJSON(Student student) throws IOException { 
      GsonBuilder builder = new GsonBuilder(); 
      Gson gson = builder.create(); 
      FileWriter writer = new FileWriter("student.json");   
      writer.write(gson.toJson(student));   
      writer.close(); 
   }  
   
   private Student readJSON() throws FileNotFoundException { 
      GsonBuilder builder = new GsonBuilder(); 
      Gson gson = builder.create(); 
      BufferedReader bufferedReader = new BufferedReader(
         new FileReader("student.json"));   
      
      Student student = gson.fromJson(bufferedReader, Student.class); 
      return student; 
   } 
} 

class Student { 
   private String name; 
   private int age; 
   public Student(){} 
   
   public String getName() { 
      return name; 
   } 
   
   public void setName(String name) { 
      this.name = name; 
   } 
   
   public int getAge() { 
      return age; 
   } 
   
   public void setAge(int age) { 
      this.age = age; 
   } 
   
   public String toString() { 
      return "Student [ name: "+name+", age: "+ age+ " ]";
   }  
}
```

````
Questions and Answers:

1 : Why SOAP is preferred for the applications which needs to perform certain transactions?

Answer : Because SOAP has ACID compliance which are must for any transaction to complete smoothly.
````

>Reference: [Rest Assured Video Tutorial](https://www.youtube.com/watch?v=z3Zty_aX7ZI&list=PL8VbCbavWfeE5aEeEpoXp2xiHi5K_7BMT)