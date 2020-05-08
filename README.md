# Independent Study

- By: Tofik Mussa
- Submitted to: Professor Susan Buck

## Developing REST APIs 

Our course had revolved around the evolution of JavaScript and client-side applications from static sites to dynamic multi-page applications to what had 
become the standard today, Single Page Applications. There was, however, another evolution happening in parallel on the server-side that I thought was
worth exploring. Historically, the workload of server to server communication had been intractable. From CORBA to SOAP, the amount of boilerplate code 
needed to execute a simple request garnered the attention of a computer scientist Roy Fielding in the early 2000's. A simple SOAP request using XML as
shown below was the best that could be done with the existing technologies prior the advent of Roy's proposal.

&nbsp;

![Soap Request](https://github.com/tmussa1/independent-study/blob/master/images/soap-request.png)

&nbsp;

Photo Credit - [SOAP requests with Postman](https://medium.com/@krissparks/soap-requests-with-postman-333c61137c41)

![REST API](https://github.com/tmussa1/independent-study/blob/master/images/rest-api.png)


REST has gained popularity over traditional ways of developing software in Service Oriented Architecture (SOA) among other recently emerging 
technologies like GraphQL and grpc. REST, short for Representational State Transfer, was introduced by Roy Fielding while he was working in his PhD back 
in the early 2000's. 

REST is an unopinionated style of architecture that leaves the decision of marking the distinction between pragmatism and theory to 
the developer. Therefore, implementations of REST can vary based on the context and use-case but it must be grounded upon the fundamental bullet points 
below. 

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