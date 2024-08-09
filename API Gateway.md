# API Gateway

## What does an API gateway do?

API Gateway is a server that acts as an intermediary between client applications and a set of microservices. It is responsible for request routing, composition, and protocol translation, among other things. The API Gateway is an essential component of a microservice architecture, allowing multiple services to be combined into a single cohesive application. 

## What does an API gateway do? Why do we need it?

An API Gateway acts as an intermediary between client applications and a collection of microservices. Its main responsibilities include:

1. Request Routing: It routes client requests to the appropriate microservice based on the URL and any additional routing rules specified.

2. Load Balancing: It distributes incoming requests to multiple instances of a microservice for better performance and availability.

3. Protocol Translation: It allows for communication between different protocols used by the client and the microservices.

4. Authentication and Authorization: It ensures that only authorized clients can access the microservices and specific resources.

5. Caching: It improves response times by caching frequently-requested data.

6. Request and Response Transformation: It converts incoming requests into a format that can be processed by the microservices and converts the responses back into a format that can be understood by the client.

We need an API Gateway to handle these responsibilities because it reduces the amount of work that must be done by each individual microservice. Additionally, it improves security, performance, and scalability by acting as a centralized entry point for client requests.

Yes, those are additional responsibilities that an API Gateway can handle.

1. Security Policy Enforcement: API Gateway can enforce security policies such as authentication, authorization, and encryption to secure the communication between the client and the microservices.

2. Circuit Breaking: It can prevent service failure cascades by implementing a circuit breaker pattern, which stops sending requests to a microservice that is failing and instead returns an error to the client.

3. Protocol Translation and Service Discovery: API Gateway can translate between different protocols used by the client and the microservices and can also assist in service discovery by maintaining a registry of available microservices and their locations.

4. Monitoring, Logging, Analytics, and Billing: API Gateway can collect and aggregate logs and metrics from multiple microservices and provide insights into the overall health and performance of the system. It can also enforce billing policies by tracking usage and rate-limiting requests from clients.

## What should be a typical flow of a client request through the API gateway and onto the backend service, step-by-step?

Here is a typical flow of a client request through an API Gateway to a backend service:

1. Client sends a request to the API Gateway with a specific URL and HTTP method.

2. API Gateway routes the request to the appropriate microservice based on the URL and any additional routing rules specified.

3. API Gateway performs authentication and authorization checks to ensure that only authorized clients can access the microservices and specific resources.

4. API Gateway applies any request transformations, such as converting the request into a format that can be processed by the microservice.

5. API Gateway forwards the request to the target microservice and balances the load between multiple instances of the microservice if necessary.

6. The target microservice processes the request and returns a response to the API Gateway.

7. API Gateway applies any response transformations, such as converting the response into a format that can be understood by the client.

8. API Gateway returns the response to the client.

9. API Gateway logs the request and response for monitoring, logging, analytics, and billing purposes.

This flow shows the role of the API Gateway as an intermediary between the client and the microservices, providing a unified entry point for all client requests and handling important tasks such as security, protocol translation, and request routing.

## API Gateway Vs. Service Mesh

* [API Gateway Vs. Service Mesh: What’s the Difference?](https://devops.com/api-gateway-vs-service-mesh-whats-the-difference/)
* [How do you choose between service mesh and API gateway for microservices?](https://www.linkedin.com/advice/3/how-do-you-choose-between-service-mesh-api#:~:text=Service%20mesh%20and%20API%20gateway%20have%20some%20overlapping%20functionalities%2C%20but,and%20usability%20of%20the%20microservices.)
* [Sidecar pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sidecar)

## A typical flow
Here is a typical flow of a client request through an API Gateway to a backend service:
1. **HTTP Request**: Client sends a request to the API Gateway with a specific URL and HTTP method. It could be REST, GraphQL, or some other higher-level abstractions.
2. **Parameter Validation**: The API gateway validates the HTTP request.
3. **Allow-list / Deny-list**: The API gateway checks the caller's IP address and other HTTP headers against its allow-list and deny-list. It could also perform basic rate limit checks against attributes such as IP address and HTTP headers. For example, it could reject requests from an IP address exceeding a certain rate.
4. **Authentication and Authorization**: The API gateway passes the request to *Identity Provider* for authentication and authorization. The API gateway receives an authenticated session back from the provider with the scope of what the request is allowed to do.
5. **Rate-limit**: A higher level rate-limit check is applied against the authenticated session. If it is over the limit, the request is rejected at this point.
6. **Dynamic routing**: API Gateway routes the request to the appropriate microservice based on the URL and any additional routing rules specified.
7. **Service discovery**: With the help of a service discovery component, the API gateway locates the appropriate backend service to handle the request by path matching. 
> * [Zookeeper](https://zookeeper.apache.org/):  is a centralized service for maintaining configuration information, naming, providing distributed synchronization, and providing group services. All of these kinds of services are used in some form or another by distributed applications.

8. **Protocol conversion**: API Gateway applies any request transformations, such as converting the request into a format that can be processed by the microservice, transforms the request into the appropriate protocol and sends the transformed request to the backend service. An example protocol would be gRPC. 
9. **Load balancing**: API Gateway forwards the request to the target microservice and balances the load between multiple instances of the microservice if necessary.
> * [Traefik](https://github.com/traefik/traefik) : is a modern HTTP reverse proxy and load balancer that makes deploying microservices easy.
> https://blog.coderco.io/p/traefik-canary-deployments-by-using
> 

10. The target microservice processes the request and returns a response to the API Gateway. When the response comes back from the backend service, the API gateway transforms the response back to the public-facing protocol and returns the response to the client.
11. **Logs the request**: API Gateway logs the request and response for monitoring, logging, analytics, and billing purposes for operational observability.
12. **circuit-breaking**: the API gateway should track errors and provide circuit-breaking functionality to protect the services from overloading.
> * 

This flow shows the role of the API Gateway as an intermediary between the client and the microservices, providing a unified entry point for all client requests and handling important tasks such as security, protocol translation, and request routing.


## Tools
> * [Kong](https://github.com/Kong/kong)
> * [Zuul](https://github.com/Netflix/zuul)
> * [Tyk](https://tyk.io/)
> * [Krakend](https://www.krakend.io/)
> * [Express-gateway](https://www.express-gateway.io/)
> * [Traefik](https://traefik.io/glossary/api-gateway-101/)

## Learning 
> * [Learn API Gateway](https://www.nginx.com/learn/api-gateway)
> * [Pattern: API Gateway / Backends for Frontends](https://microservices.io/patterns/apigateway.html)
> * [IBM API Connect](https://www.ibm.com/br-pt/products/api-connect?utm_content=SRCWW&p1=Search&p4=43700074940264083&p5=p&gclid=CjwKCAiA85efBhBbEiwAD7oLQNEZn7kA6U6-gq6Im8mhQMw8HsbwRKZH7YEFZ5vj9Tm2E25Gr-5CkRoCGYUQAvD_BwE&gclsrc=aw.ds)
> * [Microservices Gateway](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/gateway)
> * [Api Gateway](https://aws.amazon.com/pt/api-gateway/)
> * [Spring Cloud Zookeeper](https://cloud.spring.io/spring-cloud-zookeeper/reference/html/)

## Vídeos
> * [IBM - What is an API Gateway?](https://www.youtube.com/watch?v=hWRRdICvMNs&list=PLOspHqNVtKAAAq9pHWlEiRUVcYMCcu4X0)
> * [O que é API Gateway? - Full Cycle](https://www.youtube.com/watch?v=2YNelyDZBDM)
> * [Entenda API Gateway DO ZERO - Full Cycle](https://www.youtube.com/watch?v=crMkXkLIGX8&t=93s)
> * [API Gateway na Prática utilizando Kong e Elastic Stack - Full Cycle](https://www.youtube.com/watch?v=ZBUxdqQF0vs)
> * [Iniciando com API Gateway e Kong - Full Cycle](https://www.youtube.com/watch?v=_2GRXgYswhI)
 * [Envoy Proxy and Modern API Gateway Architecture](https://www.youtube.com/watch?v=nl-vnjnpLxU)
	> [<img src="https://img.youtube.com/vi/nl-vnjnpLxU/0.jpg" width="200">](https://www.youtube.com/watch?v=nl-vnjnpLxU "Envoy Proxy and Modern API Gateway Architecture by solo.io 7,432 views 52 minutes")
 * [Entenda API Gateway DO ZERO](https://www.youtube.com/watch?v=crMkXkLIGX8)
	> [<img src="https://img.youtube.com/vi/crMkXkLIGX8/0.jpg" width="200">](https://www.youtube.com/watch?v=crMkXkLIGX8 "Entenda API Gateway DO ZERO by Full Cycle 52,952 views 42 minutes")
 * [O que é API Gateway?](https://www.youtube.com/watch?v=2YNelyDZBDM)
	> [<img src="https://img.youtube.com/vi/2YNelyDZBDM/0.jpg" width="200">](https://www.youtube.com/watch?v=2YNelyDZBDM "O que é API Gateway? by Full Cycle 25,511 views 5 minutes, 43 seconds")
 * [Iniciando com API Gateway e Kong](https://www.youtube.com/watch?v=_2GRXgYswhI)
	> [<img src="https://img.youtube.com/vi/_2GRXgYswhI/0.jpg" width="200">](https://www.youtube.com/watch?v=_2GRXgYswhI "Iniciando com API Gateway e Kong by Full Cycle 40,893 views 36 minutes")
 * [API Gateway na Prática utilizando Kong e Elastic Stack](https://www.youtube.com/watch?v=ZBUxdqQF0vs)
	> [<img src="https://img.youtube.com/vi/ZBUxdqQF0vs/0.jpg" width="200">](https://www.youtube.com/watch?v=ZBUxdqQF0vs "API Gateway na Prática utilizando Kong e Elastic Stack by Full Cycle 35,320 views 2 hours, 11 minutes")
 * [O que é API Gateway?](https://www.youtube.com/watch?v=2YNelyDZBDM)
	> [<img src="https://img.youtube.com/vi/2YNelyDZBDM/0.jpg" width="200">](https://www.youtube.com/watch?v=2YNelyDZBDM "O que é API Gateway? by Full Cycle 25,511 views 5 minutes, 43 seconds")
 * [Entenda API Gateway DO ZERO](https://www.youtube.com/watch?v=crMkXkLIGX8)
	> [<img src="https://img.youtube.com/vi/crMkXkLIGX8/0.jpg" width="200">](https://www.youtube.com/watch?v=crMkXkLIGX8 "Entenda API Gateway DO ZERO by Full Cycle 52,952 views 42 minutes")
 * [What is an API Gateway?](https://www.youtube.com/watch?v=hWRRdICvMNs)
	> [<img src="https://img.youtube.com/vi/hWRRdICvMNs/0.jpg" width="200">](https://www.youtube.com/watch?v=hWRRdICvMNs "What is an API Gateway? by IBM Technology 267,611 views 10 minutes, 19 seconds")

https://www.youtube.com/watch?v=2YNelyDZBDM
https://www.youtube.com/watch?v=crMkXkLIGX8&t=93s
https://www.youtube.com/watch?v=ZBUxdqQF0vs
https://www.youtube.com/watch?v=hWRRdICvMNs&
https://www.youtube.com/watch?v=_2GRXgYswhI

## References

1. https://microservices.io/patterns/apigateway.html
2. https://github.com/Kong/kong
3. https://www.nginx.com/learn/api-gateway
4. https://github.com/Netflix/zuul
5. https://tyk.io/
6. https://www.krakend.io/
7. https://www.express-gateway.io/
8. https://traefik.io/glossary/api-gateway-101/
9. https://learn.microsoft.com/en-us/azure/architecture/microservices/design/gateway
10. https://aws.amazon.com/pt/api-gateway/
11. https://cloud.spring.io/spring-cloud-gateway/reference/html/
12. https://learn.microsoft.com/pt-br/dotnet/architecture/microservices/multi-container-microservice-net-applications/implement-api-gateways-with-ocelot
