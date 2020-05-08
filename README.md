# Independent Study

- By: Tofik Mussa
- Submitted to: Professor Susan Buck

## Developing REST APIs 

Our course has revolved around the evolution of JavaScript and client-side applications from static sites to dynamic multi-page applications to what had 
become the standard today, Single Page Applications. There was, however, another evolution happening in parallel on the server-side that I thought was
worth exploring. Historically, the workload of server to server communication had been intractable. From CORBA to SOAP, the amount of boilerplate code 
needed to execute a simple request garnered the attention of a computer scientist named Roy Fielding in the early 2000's. A simple SOAP request using XML as
shown below was the best that could be done with the existing technologies prior the advent of Roy's breakthrough.

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

A little background in HTTP will also be useful since it is the protocol that REST uses to transport messages across the wire. Components of an HTTP request
can be the following

- **Content type** – format of content which can be one of the non-exhaustive list of 
  - HTML, CSS, JavaScript
  - JSON, XML
  - Binary, blobs 
- **Content length** – size of content
- **Authorization** – the party’s details used by the server to verify permission
- **Accept** – supported format for response. It can be one or more of the types listed above 
- **Cookies** – additional information about user saved by browsers

REST stands for Representational State Transfer and the bullet points below constitute what it means to be RESTful.  

- **Client/server separation** - The universal rule of application development is enforcing loose coupling and high cohesion. In a modular architecture, components
can change their internal implementations as long as their API 
(See - [Application Programming Interface](https://www.freecodecamp.org/news/what-is-an-api-in-english-please-b880a3214a82/)) remains stable. REST lends itself 
to be the defacto standard for client/server communication by defining clear boundaries between a consumer and the producer. The server can be consumed by 
multiple clients which promotes reuse and avoids redundancy. This becomes critical in a large scale system making pieces of software fit like a jigsaw puzzle.
Enterprises are free to add their own layer of abstractions on top of REST as they see it fit to their own business needs. There are also recent trends on 
glorified RESTful web services (See - [Microservices](https://microservices.io/), [GraphQL](https://graphql.org/), [gRPC](https://grpc.io/) ).

- **Stateless requests** - Each request is independent of each other and must provide enough context for the server to respond. The request is short-lived, 
and the server doesn’t remember the state of past requests. This is in contrast to game or database programming where a request determines the fate of 
subsequent requests. 

- **Uniform interface** - There must be some uniform way to discover resources behind the URIs. One of the few HTTP verbs must be used in a request. HTTP 
response must be accompanied by status and body. 


#### Outside Resources

[Understanding RESTful API](https://mlsdev.com/blog/81-a-beginner-s-tutorial-for-understanding-restful-api)

[What is meant by uniform interface](https://stackoverflow.com/questions/25172600/rest-what-exactly-is-meant-by-uniform-interface)

[How I taught REST APIs to my wife](http://www.looah.com/source/view/2284)

[Introduction to REST APIs](https://itnext.io/javascript-fundamentals-an-introduction-to-rest-apis-7cbe8a809d3b)

[Idempotency in REST APIs](https://restfulapi.net/idempotent-rest-apis/)

[Http status codes](https://www.restapitutorial.com/httpstatuscodes.html)

![REST API](https://github.com/tmussa1/independent-study/blob/master/images/rest-api.png)