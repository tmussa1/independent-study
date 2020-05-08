# Independent Study

- By: Tofik Mussa
- Submitted to: Professor Susan Buck

## Developing REST APIs 

Our course has revolved around the evolution of JavaScript and client-side applications from static sites to dynamic multi-page applications to what had 
become the standard today, Single Page Applications. There was, however, another evolution happening in parallel on the server-side that I thought is
worth exploring. Historically, the workload of server to server communication had been intractable. Progressing from CORBA to SOAP, the amount of boilerplate 
code needed to execute a simple request garnered the attention of a computer scientist named Roy Fielding in the early 2000's. A simple SOAP request using XML as
shown below was the best that could be done with the existing technologies prior to the advent of Roy's breakthrough.

&nbsp;

![Soap Request](https://github.com/tmussa1/independent-study/blob/master/images/soap-request.png)

&nbsp;

Photo Credit - [SOAP requests with Postman](https://medium.com/@krissparks/soap-requests-with-postman-333c61137c41)

&nbsp;

You might have wondered that the opening and ending tags look similar to the HTML which we are mostly familiar with from working in this course. XML is indeed a 
superset of HTML with extensive capabilities to users like the ability to define custom tags.  XML had some advantages for integrating 
semistructured data since requests don't have to exactly conform to a predefined schema. A WSDL, short for Web Service Definition Language, is a 
document which defines the contract between a client and the server. In a WSDL based communication, fields that are tagged as not required can be safely omitted 
without breaking the contract. This enabled flexibility and seamless integration in its heyday. However, as can be seen in the picture above, 
there is a lot to a SOAP request than just the data elements and pure verbatim required to perform business logic. The SOAP envelope defines a namespace, several
endpoints, xsd (See [XML Schema Definition](https://www.w3schools.com/xml/schema_intro.asp)), versions and some security metadata in the simplest usecase above. 
This hard to use and hard to debug approach is what triggered industry veterans to look for alternatives. The philosophy of REST was popularized by Roy Fielding 
after his PhD dissertation in 2000 as an unopinionated style of architecture grounded upon some fundamental principles. 

###### what are the components of HTTP? 

- **Content type** – format of content which can be some of 
  - HTML, CSS, JavaScript
  - JSON, XML
  - Binary, blobs 
- **Content length** – size of content
- **Authorization** – the party’s details used by the server to verify permission
- **Accept** – supported format for response. It can be one or more of the content types listed above 
- **Cookies** – additional information about the user saved by browsers. For example, user preference information. See - 
([Cookies](https://support.mozilla.org/en-US/kb/cookies-information-websites-store-on-your-computer))

&nbsp;

###### REST stands for Representational State Transfer and it is based on the HTTP protocol. 

&nbsp;

![REST DEMO](https://github.com/tmussa1/independent-study/blob/master/images/rest-image.png)

&nbsp;

Photo Credit - [What is REST API](https://phpenthusiast.com/blog/what-is-rest-api)

&nbsp;

###### What does it mean to be RESTful?

- **Client/server separation** - The universal rule of application development is enforcing loose coupling and high cohesion. In a modular architecture, components
can change their internal implementations as long as their API 
(See - [Application Programming Interface](https://www.freecodecamp.org/news/what-is-an-api-in-english-please-b880a3214a82/)) remains stable. REST lends itself 
to be the defacto standard for client/server communication by defining clear boundaries between a consumer and the producer. The server can be consumed by 
multiple clients which promotes reuse and avoids redundancy. This becomes critical in a large scale system where pieces of software fit like a jigsaw puzzle.
Enterprises are free to add their own layer of abstractions on top of REST as they see it fit to their own business needs. There are also recent trends on 
glorified RESTful web services (See - [Microservices](https://microservices.io/), [GraphQL](https://graphql.org/), [gRPC](https://grpc.io/)).

- **Stateless requests** - Each of the requests are independent of each other and must provide enough context in order for the server to respond. The requests 
are short-lived, and the server doesn’t remember the state of past requests. This is in contrast to game or database programming where a request determines the 
fate of subsequent requests. 

- **Uniform interface** - There must be some uniform way to discover resources behind the URIs. One of the few HTTP verbs must be used in a request. An HTTP 
response must be accompanied by a status and a body. 

- **Cacheable** - the client is free to store the details of HTTP response. 

###### What are the common HTTP verbs and some common implementations?

- **GET** – A get request is one of the simplest operations. In layman’s terms, a client commonly a browser makes a request to a server.
The server checks if the client is a known user with valid permissions and if the resource is available, then the server sends a response. The server might 
respond with defined categories of error codes in case of having the above preconditions unfulfilled. The error code response might suggest an unauthorized user, 
or a resource not found to say the least. More on error codes later. A get request is supposed to be designed to not have side effects of modifying a resource. 
- **POST** – A post operation is used for creating a new resource. The data to be added is commonly obtained using an html form or through another client service but 
getting data through other testing tools like CURL, POSTMAN and SOAPUI are also common. The API may do some validation based on the implementation such as 
checking for a duplicate resource or if all the required fields are populated with the correct format before storing the resource.  
- **PUT** – A put request is made to modify an existing resource. The implementation might pull the resource based on a parameter passed in from the client and make 
the appropriate modifications. Unlike a post request, put requests are idempotent, meaning trying to modify a resource that has already been modified doesn’t 
change anything. 
- **DELETE** – A delete request is made when trying to delete a resource. If persistence is part of the application, the resource will be deleted from disk. 
Trying to delete a resource that doesn’t exist, or other constraints may throw exceptions based on the implementation. 

###### What are HTTP status codes and what do they signify 

- **1XX** – informational. Error code of the 100s provides the client additional information when a request is being processed and can be safely ignored 
after the process is complete. 
- **2XX** – success. The classic 200 error code is used when a request is successful. 204 is also commonly used when a delete request is the successful and there is 
no content to displayed back in response. 
- **3XX** – redirection. Further action needed from user to complete request. 
- **4XX** – client error. The most common 404 error code is displayed when client tries to request a request that doesn’t exist. 403 is also common when a user is not 
authorized to obtain a resource.
- **5XX** – server error. The most common 500 error code is displayed when the server is not available to serve resource. This is a generic response which may result 
from different types of outages. 

###### What are query strings and what are they used for? 

- Sometimes query strings give additional functionality to influence how data is being rendered. Query strings are most commonly used for pagination, formatting
and sorting to name a few

###### What tools are available to implement REST APIs?

- There are numerous tools to implement REST APIs in most of the major languages. This [page](https://www.tecmint.com/best-nodejs-frameworks-for-developers/) contains
some of the tools available to implement REST APIs in JavaScript. 

#### Outside Resources

[Understanding RESTful API](https://mlsdev.com/blog/81-a-beginner-s-tutorial-for-understanding-restful-api)

[What is meant by uniform interface](https://stackoverflow.com/questions/25172600/rest-what-exactly-is-meant-by-uniform-interface)

[How I taught REST APIs to my wife](http://www.looah.com/source/view/2284)

[Introduction to REST APIs](https://itnext.io/javascript-fundamentals-an-introduction-to-rest-apis-7cbe8a809d3b)

[Idempotency in REST APIs](https://restfulapi.net/idempotent-rest-apis/)

[Http status codes](https://www.restapitutorial.com/httpstatuscodes.html)