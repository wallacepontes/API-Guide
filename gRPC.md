# gRPC

## What is gRPC? When should we use it?

gRPC is a high-performance, open-source framework for building scalable, modern, and efficient server-client applications. It is based on the Protocol Buffers data format and uses HTTP/2 for transport. It supports a variety of programming languages and is designed for inter-service communication in microservices architectures. Use gRPC when you need a fast, efficient, and scalable solution for connecting services, especially in microservices architecture where performance and low latency are critical.

## But first, what is an RPC or remote procedure call?

A remote procedure call (RPC) is a communication protocol that enables a computer program to request services from a remote server, effectively allowing the remote server to behave as if it were a local program. The client program sends a request to the server to execute a specified function, and the server returns the results to the client. This allows for the client and server to reside on different machines and interact over a network.

## What makes gRPC so popular?

gRPC has gained popularity due to several key factors:

1. High performance: gRPC uses HTTP/2 as the transport protocol and Protocol Buffers as the data format, resulting in fast and efficient communication.

2. Cross-language compatibility: gRPC supports multiple programming languages, including C++, Java, Python, Go, and many others, making it easy to integrate with existing systems.

3. Strong typing: gRPC uses Protocol Buffers to define the service interface, which provides strong typing and allows for easy code generation.

4. Efficient bi-directional streaming: gRPC supports bi-directional streaming, which enables efficient communication between client and server, even in cases where a large amount of data needs to be exchanged.

5. Improved security: gRPC supports encrypted communication, authentication, and authorization.

6. Wide adoption: gRPC has been widely adopted by many companies and organizations, including Google, Square, and Dropbox, which has helped establish it as a leading technology for building efficient and scalable microservices.

## First, gRPC has a thriving developer ecosystem.

Yes, that is correct. The gRPC project has a strong and active community of developers who contribute to its development and maintenance, resulting in a thriving ecosystem with a wealth of resources and support for users. Additionally, the open-source nature of gRPC makes it easy for developers to customize and extend its functionality to meet their specific needs.

## The core of this ecosystem is the use of Protocol Buffers as its data interchange format.

Yes, that is correct. Protocol Buffers, also known as protobuf, is a compact binary format for encoding structured data that is used as the data interchange format in gRPC. Its compact and efficient encoding, combined with language-agnostic and platform-agnostic design, make it an ideal choice for inter-service communication in microservices architecture. Additionally, protobuf provides support for strong typing, which helps to ensure that data is correctly interpreted and prevents errors due to type mismatches. The use of protobuf is a key factor in the success of gRPC and its popularity among developers.

The proto file is a text file that defines the data structures, services, and the APIs for gRPC. It is written in the Protocol Buffers language, which is a simple and efficient language for defining data structures. The proto file serves as the contract between the client and server, specifying the data that will be exchanged and the operations that will be performed.

Once the proto file is defined, the gRPC framework can use it to generate the necessary code for client and server implementations in the target programming language. This helps to ensure that the client and server are consistent with each other and reduces the risk of errors due to mismatched data or API definitions. The proto file also makes it easier to maintain and evolve the service API over time, as changes can be made in one place and automatically propagated to the client and server implementations.

##  two factors contribute to its performance

Two factors that contribute to the performance of gRPC are:

1. HTTP/2: gRPC uses HTTP/2 as the transport protocol, which provides several performance benefits over its predecessor, HTTP/1.1. HTTP/2 supports multiplexing, allowing multiple requests to be sent and received at the same time over a single connection, reducing the overhead of opening and closing separate connections for each request.

2. Protocol Buffers: gRPC uses Protocol Buffers, or protobuf, as the data format, which provides several performance benefits. Protobuf is a compact binary format that uses a schema to define the data structure, allowing for efficient and fast serialization and deserialization of data. Additionally, protobuf provides support for encoding and decoding data directly to and from binary, which eliminates the need for parsing and reduces the overhead of text-based formats such as JSON or XML.

These two factors help gRPC to provide high-performance communication between services, even for large amounts of data, making it well-suited for use in microservices architecture and other high-performance environments.

## To understand how gRPC works, let's walk through a typical flow from a gRPC client to a gRPC server.

Sure, here is a simplified overview of the typical flow for a gRPC client-server interaction:

1. The client sends a request to the server, specifying the method to be called and the data to be passed as parameters.

2. The server receives the request, performs the requested operation, and returns a response to the client.

3. The client receives the response from the server and processes it, either by displaying the result or by performing additional actions based on the response.

Here's what each step in this flow might look like in more detail:

1. The client defines the API using a proto file and generates the client stub code using the gRPC framework. The client then uses the generated stub code to create a request and send it to the server.

2. The server defines the API using the same proto file and generates the server stub code using the gRPC framework. The server uses the generated stub code to implement the service and listen for incoming requests.

3. When the client sends a request to the server, the gRPC framework serializes the request data using protobuf and sends it over an HTTP/2 connection.

4. The server receives the request and deserializes the protobuf data using the gRPC framework. The server then performs the requested operation and generates a response.

5. The server serializes the response data using protobuf and sends it back to the client over the same HTTP/2 connection.

6. The client receives the response, deserializes the protobuf data, and processes the result.

This is a high-level overview of the typical flow for a gRPC client-server interaction. The exact details of the flow may vary depending on the specific requirements of the application, but the basic process remains the same.

## If it is so easy, why do we not see wide-spread use of gRPC between web clients and web servers?

While gRPC is a powerful and efficient framework for communication between services, it is not yet widely used for communication between web clients and web servers for a few reasons:

1. Browser compatibility: gRPC requires HTTP/2 for efficient communication, which is not supported by all web browsers. This makes it difficult to use gRPC directly from the browser.

2. Legacy support: Many existing web applications use HTTP/1.1 and are not easily able to switch to HTTP/2 and gRPC without significant refactoring.

3. Adoption rate: gRPC is a relatively new technology and its adoption rate is still growing. It may take some time for it to become widely used for communication between web clients and web servers.

4. Security concerns: gRPC uses binary data for communication, which may raise security concerns for some organizations. This can be mitigated by using encryption and secure transport protocols, but this adds complexity to the implementation.

5. API design: gRPC is designed for use with microservices and is optimized for high-performance communication between services. It may not be the best choice for communication between web clients and web servers, which often have different requirements.

These are some of the reasons why gRPC is not yet widely used for communication between web clients and web servers. However, as gRPC continues to evolve and gain wider adoption, it is possible that we will see increased use of gRPC for this purpose in the future.

## So, where does gRPC shine, and when should we use it?

gRPC shines in the following scenarios and is well-suited for:

1. Microservices architecture: gRPC is designed for communication between microservices, and its efficient binary format and support for bi-directional streaming make it well-suited for this use case.

2. High-performance communication: gRPC is optimized for high-performance communication and can handle high-volume and high-velocity data streams with low latency and overhead.

3. Inter-process communication: gRPC can be used for communication between different processes within a single machine, as well as between machines in a network.

4. Cross-platform communication: gRPC supports multiple programming languages, making it easy to implement services and clients on different platforms.

5. Mobile and IoT devices: gRPC's compact binary format and low overhead make it well-suited for communication between mobile and IoT devices with limited resources.

6. Low-level system programming: gRPC can be used for low-level system programming, such as communication between kernel space and user space.

In general, gRPC is well-suited for communication between services where high performance, efficiency, and scalability are required. If these are important requirements for your application, gRPC may be a good choice for you.

## Videos
 * [Efficient IoT with Protocol Buffers and gRPC - Vladimir Vivien, {code} (Beginner Skill Level)](https://www.youtube.com/watch?v=c9z_o5lu0dI)
	> [<img src="https://img.youtube.com/vi/c9z_o5lu0dI/0.jpg" width="200">](https://www.youtube.com/watch?v=c9z_o5lu0dI "Efficient IoT with Protocol Buffers and gRPC - Vladimir Vivien, {code} (Beginner Skill Level) by CNCF [Cloud Native Computing Foundation] 5,531 views 37 minutes")
 * [What is RPC? gRPC Introduction.](https://www.youtube.com/watch?v=gnchfOojMk4)
	> [<img src="https://img.youtube.com/vi/gnchfOojMk4/0.jpg" width="200">](https://www.youtube.com/watch?v=gnchfOojMk4 "What is RPC? gRPC Introduction. by ByteByteGo 414,163 views 6 minutes, 9 seconds")

## References

1. https://grpc.io/docs/languages/java/quickstart/#get-the-example-code

