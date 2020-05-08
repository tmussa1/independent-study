# Independent Study

- By: Tofik Mussa
- Submitted to: Professor Susan Buck

## Developing REST APIs 

Our course has revolved around the evolution of JavaScript and client-side applications from static sites to dynamic multi-page applications to what had 
become the standard today, Single Page Applications. There was, however, another evolution happening in parallel on the server-side that I thought was
worth exploring. Historically, the workload of server to server communication had been intractable. From CORBA to SOAP, the amount of boilerplate code 
needed to execute a simple request garnered the attention of a computer scientist Roy Fielding in the early 2000's. A simple SOAP request using XML as
shown below was the best that could be done with the existing technologies prior the advent of Roy's proposal.

&nbsp;

![Soap Request](https://github.com/tmussa1/independent-study/blob/master/images/soap-request.png)

&nbsp;

Photo Credit - [SOAP requests with Postman](https://medium.com/@krissparks/soap-requests-with-postman-333c61137c41)

&nbsp;

You might have wondered the opening and ending tags look like the HTML which we are mostly familiar with from working in this course. XML is indeed a 
superset of HTML with extensive capabilities like to users like the ability to define their own tags.  XML had some advantages for integrating 
semistructured data since requests don't have to exactly conform to a predefined schema. A WSDL, short for Web Service Definition Language, is a 
document defines the contract between the client and the server but not having some of the fields which are tagged as not required in the WSDL does not 
break the contract of communication. This enabled flexibility and seamless integration in its heyday. However, as can be seen in the picture above, 
there is a lot to a SOAP request than just the data elements and pure verbatim required to perform business logic. The header defines a namespace, several
endpoints, xsd (See [XML Schema Definition](https://www.w3schools.com/xml/schema_intro.asp)), version and some security metadata in the simplest example 
given above of a SOAP request. 



REST has gained popularity over traditional ways of developing software in Service Oriented Architecture (SOA) among other recently emerging 
technologies like GraphQL and grpc. REST, short for Representational State Transfer, was introduced by Roy Fielding while he was working in his PhD back 
in the early 2000's. 

REST is an unopinionated style of architecture that leaves the decision of marking the distinction between pragmatism and theory to 
the developer. Therefore, implementations of REST can vary based on the context and use-case but it must be grounded upon the fundamental bullet points 
below. 

![REST API](https://github.com/tmussa1/independent-study/blob/master/images/rest-api.png)

- Client/server separation - The universal rule of application development is enforcing loose coupling and high cohesion. In a modular architecture, components
can vary independently as long as the contract initially established (the interface) is not violated. REST lends itself to be the defacto standard for 
inter-service and client/server communications. There is no limit to how many clients the server can be consumed by as their are clear boundaries between
the modules promoting reusability and avoiding redundancy. In a large scale system, the interactions between modules are complex and the need to encapsulate 
logic exposing only what the client needs to know to be able to consume an API is essential. For example, I have worked on a project based on a mediator pattern 
where there were plenty of web services interacting in the background but the wrapper service at the front contained all of the business logic and the client 
only knew about how to consume the wrapper service. Enterprises adopting the REST architecture as such are free to add their own layers of abstraction to fit
their business needs. 

- Stateless requests - The communication is stateless, i.e. the request is short-lived, and the server doesn’t remember the state of past requests in contrast 
to say game or database programming where subsequent requests are dependent on the state changed by preceding requests. 


- Uniform interface - There must be some uniform way to discover resources behind the URIs. One of the many Http verbs must be used in the request. Http response
must be composed of status and body. 


A little background in http will also be useful since it is the protocol that REST uses to transport messages across the wire. Components of an http request
can be the following

- Content type – format of content which can be one of the non-exhaustive list of 
  - HTML, CSS, JavaScript
  - JSON, XML
  - Binary, blobs 
- Content length – size of content
- Authorization – the party’s details used by the server to verify permission
- Accept – supported format for response. It can be one or more of the types listed above 
- Cookies – information about user saved by browsers