# 1. What is ASP.NET Web API?



1. It is a Framework from Microsoft that through which we can create HTTP based services.

2. We can make RESTful services on top of .NET Framework.

3. These web services can be consumed in Browsers, Mobiles, Desktop apps & IOT's.

4. We can create both RESTful & RESTless services, but the earlier is mostly used.

   

# 2. What is REST?



1. REST stands for Representational State Transfer.

2. It is an architectural pattern used for creating HTTP based web services.

3. It specifies a set of constraints, that a web service should follow to become RESTful service:

   ​	a. **Client Server** 

   ​		Separation of concerns between client & server should be there to support loose coupling.

   ​	b. **Stateless** 

   ​		We should not be storing any client info on the server (sessions). The request should contain all the info necessary to 		process the request so that the application can be scalable.

   ​	c. **Cacheable**

   ​		Let the client decide how long it want to cache frequently used data (List of countries, user profile etc)

   ​	d. **Uniform Interface**

   ​		It defines an interface between client & server. We should send proper HTTP verbs with each request so that the server 		can identify what to do with the resource.

   ​	e. **Layered System**

   ​		This constraint let us create layered architecture in while our API is deployed on server A, Database is deployed on server 		B and requests are authenticated on server C.

   ​	f. **Code on demand**

   

# 3. Difference between REST & SOAP



1. SOAP is a protocol, REST is an architectural pattern ( resource based architecture).
2. SOAP uses HTTP, TCP/IP & SMTP. REST use HTTP only.
3. SOAP has both stateless & state, REST has only stateless implementation.
4. SOAP enforces XML response, client specify the response in REST.
5. SOAP uses XML envelopes to store SOAP headers & SOAP body, REST use HTTP headers.
6. SOAP uses interfaces, REST uses URI's.



# 4. When should we use WCF?



1. If we are stuck with .NET Framework 3.5  or below.
2. If we're working with a WCF service that we need to convert to REST.
3. If we want to transport data over HTTP, TCP, UDP channels.
4. If we want to support special scenarios such as one way messaging, messaging queues, duplex communication.



# 5. When should we use Web API?



1. If we want to create resource-oriented HTTP services that use full features of HTTP like URI, Request/Response headers, Caching, versioning, content formatting.
2. When we want to expose data to broad range of clients like browsers, mobiles, Desktops & IOT's.



# 6. Difference between WCF & Web API



1. WCF returns data in XML, REST returns data in XML, JSON or client specified.
2. WCF works on HTTP, TCP, UDP, SMTP protocols, Web API works on HTTP protocol.
3. WCF is SOAP based, Web API is REST based.
4. MVC features are not available, MVC features are available in Web API.



# 7. Difference between ASP.NET MVC & Web API?



1. MVC is used to create web applications that returns both view & data.
2. Web API is used to create HTTP services that return only data.



3. Web API use content negotiation in which client decides the response.
4. MVC send fixed data format.



	5. Web API send response based on "ACCEPT" header, it can be of JSON or XML etc.
 	6. MVC will send only JSON using JSONResult.



# 8. What is Web API self hosting?



1. Creating MVC & Web API in a single project to handle AJAX requests is called self hosting.





# 9. Controller vs APICOntroller class?



1. MVC controllers are inherited from Controller class (**System.Web.MVC)**
2. Web API Controllers are inherited from **APIController** class (System.Web.HTTP)



3. Controller class has ViewResult() method that returns view.
4. APIController class does not have ViewResult method() and also not have ActionResult() method.



# 10. What are Request Headers?



1. Each request has a header & a body.

2. The header of request contains some additional info that we send to the API, like what type of content I'm sending & what type of response I'll accept back.

   

# 11. What is Request Body?



1. It contains the data client is sending to the server.
2. Like the form data sent in POST request.



# 12. What is a Response Body?



1. Contains data sent by server in XML or JSON format.



# 13. What are Response Status Codes?



1. Status code specifies the status of the request.
2. Common status codes are:
   1. 200 (OK)
   2. 204 (No Content)
   3. 500 (Internal Server Error)
   4. 404 (Not Found)
   5. 302 (Redirect)



# 14. What is Content Negotiation?



1. Content negotiation means the client have the ability to decide in which format they want the response. Whether they want it in XML or JSON or CSV etc.

2. It means the client & server can negotiate. It is not possible always to send data in requested format therefore it is not called as demand. In such cases default format is sent.

3. We use certain HTTP headers for this:

   1. **Content-type** Specify the format in which client is sending the data. application/json, application/xml

   2. **Accept** - Specify in which format the data is requested by client. application/json, application/xml

      











































