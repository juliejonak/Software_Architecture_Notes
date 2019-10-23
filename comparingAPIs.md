# Choosing an API

When it comes to handling backend architecture, specifically the API endpoints for sending and receiving data, there are a lot of options. We're going to compare Client Side (GraphQL), Server Side (REST), gRPC web services, and Message Queue.

# Server Side (RESTful)

REST stands for `REpresentational State Transfer` and is an architecture system that provides universal standards so different computer systems can communicate on the web.

The main characteristic of RESTful systems is the separation of the client and server. This means that the client side code is separate and can change without impacting the server side code. This allows development to be more agile and modular; while also allowing multiple clients to hit the same REST server endpoints. 

This is how public facing APIs came into existence -- open sourcing data.

REST is stateless, meaning the server does not need to know what state the client is in (and vice versa), allowing both sides to communicate without needing previous data context.

<br>

RESTful systems interact through standardized operations on URI web Resources (Uniform Resource Identifier: a string of characters identifying any object, document or thing we need to store or send to other services). Through this, they are reliable, quick and scalable because components can be updated and managed without affecting the entire system.

> "HTTP provides URLs that allow us to define resource paths. There are verbs (GET, POST, PUT, and PATCH) to enable acting on such resources, there are response codes, and there are headers that allow us to define client/server relationships"  
> -- [Is REST still a relevant API style?](https://nordicapis.com/is-rest-still-a-relevant-api-style/) 

<br>

Client side makes a Request to a RESTful endpoint that includes the HTTP action to perform, a header (passes information about the request), a path to the resource, and an optional message body containing data.

The four main HTTP actions are GET, PUT, POST, and DELETE.

For more details on how RESTful systems work, [read here](https://www.codecademy.com/articles/what-is-rest). 

<br>

### What makes REST great?

It's easy to for clients to work with -- given a data model and end points, most developers can work with a RESTful API quickly.

REST also follows HTTP protocol, which makes error handling and standardization easy. If there's an error, the client will receive back some form of a 400 or 500 error, helping them debug. 

It is also cacheable, so if latency is a concern, responses can be cached to avoid it being noticeable for freqently made requests.

<br>

### What are the cons?

The API tends to be inflexible, with predefined data loads sent with specific requests on particular endpoints.

This results in over-fetching on the client side. If an endpoint provides information about all parrots, but not parakeets, and a client is trying to find out about both, they'll have to make two requests to fetch all relevant data.

There isn't a way for the client to specify what data they do (or don't) need. This results in receiving too little information or having to make too many requests.

If there are major changes to how information is handled or consumed on the client side, it could result in needing to tweak the REST endpoint. This can slow down iterations. The frontend and backend teams tend to need consistent communication about the data models and how they change.

<br>

> Overfetching: Downloading superfluous data  
>  
> Overfetching means that a client downloads more information than is actually required in the app. Imagine for example a screen that needs to display a list of users only with their names. In a REST API, this app would usually hit the /users endpoint and receive a JSON array with user data. This response however might contain more info about the users that are returned, e.g. their birthdays or addresses - information that is useless for the client because it only needs to display the users’ names.  
>  
> Underfetching and the n+1 problem  
>  
> Another issue is underfetching and the n+1-requests problem. Underfetching generally means that a specific endpoint doesn’t provide enough of the required information. The client will have to make additional requests to fetch everything it needs. This can escalate to a situation where a client needs to first download a list of elements, but then needs to make one additional request per element to fetch the required data.
> -- [How to GraphQL](https://www.howtographql.com/basics/1-graphql-is-the-better-rest/)  

<br>
<br>


