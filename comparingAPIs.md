# Choosing an API

When it comes to handling backend architecture, specifically the API endpoints for sending and receiving data, there are a lot of options. We're going to compare Client Side (GraphQL), Server Side (REST), gRPC web services, and Message Queue.

[This article](https://nordicapis.com/is-rest-still-a-relevant-api-style/) provides a nice overview of REST, GraphQL and gRPC.

<br>

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

For the most part, when using RESTful APIs, the team must understand how users will interact with the endpoint before setting it up.

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

# GraphQL (Client Side)

GraphQL differs from REST in two significant ways: it has only one endpoint that the client will send requests to, and the client dictates what data it wants in the response.

Instead of having to make multiple queries to get the exact data the client needs, and maybe over-fetching by doing so, with GraphQL, the client define the response format with `client-specified queries`.

GraphQL is not language specific (it can communicate to anyone writing in GraphQL), is best for hierarchical structures, and is strong-typing (it doesn't care how you store and handle the data response, but all queries must be formatted specifically to GraphQL's syntax).

Hierarchal is top-down data fetching, meaning clients can write their queries in a more natural way. In GraphQL, a query to fetch a specific user, their details and related friends might look like this:

```
{
  user(id: 1) {
    name
    age
    friends {
      name
    }
  }
}
```

Which matches the structure in the application well:

```
<App>
  <User>
    <Friend/>
    <Friend/>
  </User>
</App>
```

Whereas with a RESTful API endpoint, the request is less intuitive and might have to be very specific or span multiple requests to fetch all that data:

```GET /users/1 and GET /users/1/friends```
```GET /users/1?include=friends.name```

<br>

### What makes GraphQL great?

It's best when the client needs a flexible response - the same query isn't being made consistently. This allows data overhead to me minimized and avoid over-fetching and excessive requests. This allows the client to change their respond format without needing the backend to change. 

This flexiblity also allows an application to iterate quickly without having to work in tandem on the front and back end. Once the GraphQL endpoint is setup and the schema is designed, both teams can work independently. This allows the teams to set it up before doing extensive user tests, because the client can dictate their own needs.

<br>

### What are the cons?

GraphQL can be slower without the simplicity of RESTful caching and uses solely POST responses, limits the flexibility of content types that can be sent.

There is also limited endpoint security and still limited tooling with being a newer resource. Libraries like Apollo or Relay are needed on the frontend to help with sending and formatting queries on the client side. 


Because even a small amount of latency can significantly decrease user traffic, optimization is a valid concern, with complex queries requiring more time to parse and send back the client indicated response.

Learn about GraphQL in [this overview](https://blog.risingstack.com/graphql-overview-getting-started-with-graphql-and-nodejs/).  
Read more about REST v GraphQL in [this comparison](https://goodapi.co/blog/rest-vs-graphql).  

<br>
<br>

# gRPC

Developed by Google Cloud, gRPC is an open-source RPC framework. gRPC stands for `(Google) Remote Procedure Call`, aimed at being a highly performant and functional.

Unlike REST that typically uses JSON for sending data, gRPC relies on Protobuf, a more compact and data-typed format:

> Protocol buffers are Google's language-neutral, platform-neutral, extensible mechanism for serializing structured data – think XML, but smaller, faster, and simpler. You define how you want your data to be structured once, then you can use special generated source code to easily write and read your structured data to and from a variety of data streams and using a variety of languages.  
> -- [Google Docs](https://developers.google.com/protocol-buffers/)

<br>

### What's great about gRPC?

It's highly performant because of its compact data load and has low latency. It's build on HTTP/2 (which addresses some issues that HTTP/1 has) and supports bi-directional communication.


### What are the cons?

gRPC service can only communicate with gRPC clients, unlike RESTful endpoints that allow anyone using the HTTP protocol to interact. The code generation from using Protobuf is inconsistent across languages, which makes it difficult to scale in a public facing API.

Because of this limitation, it's better used for internal organizations' APIs, where there is already consistent language support, practices and docs. The uphill learning curve can slow down growth.

gRPC also doesn't have cacheability or allow for flexible content types.

Read more about [What is gRPC?](https://visualstudiomagazine.com/articles/2019/08/28/grpc-web-services.aspx). 

<br>
<br>


