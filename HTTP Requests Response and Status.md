# HTTP Requests

## Do you also love travelling like HTTP Requests?

Haha, that's a creative way to relate HTTP requests to traveling! It's a fun analogy, and it does help illustrate how HTTP methods are used to interact with web servers. Just as you plan and execute your travels, web developers use these HTTP methods to request and manipulate data on the internet. If you have any questions about HTTP or travel-related topics, feel free to ask!

## Let's explore how HTTP requests help you to travel

1. **GET - Exploring Destinations:** When you're planning a trip, you start by gathering information about various destinations. You "GET" information like tourist spots, weather conditions, and local attractions. Similarly, the HTTP GET method retrieves data from a server without making any changes.
**Endpoint:** GET /api/destinations/1

2. **POST - Booking Accommodation:** Imagine you're booking accommodations for your trip. You "POST" your booking details to the hotel's website. Similarly, the HTTP POST method sends data to the server to create or update a resource, like submitting a form.
**Endpoint:** POST /api/itineraries

3. **PUT - Replacing Your Itinerary: ** If you decide to completely change your travel plans, you might "PUT" a new itinerary in place, essentially replacing the old one. Similarly, the HTTP PUT method replaces a resource on the server with a new version.
**Endpoint:** PUT /api/itineraries/5

4. **PATCH - Modifying Plans:** Sometimes, you might make minor adjustments to your travel plans without changing the whole itinerary. Just like how you might "patch" your plans by adjusting certain details, the HTTP PATCH method modifies specific parts of a resource.
**Endpoint:** PATCH /api/flights/10

5. **DELETE - Cancelling Reservations:** If you need to cancel a reservation for a show or activity, you "DELETE" it from your schedule. In the same way, the HTTP DELETE method requests the removal of a resource on the server.
**Endpoint:** DELETE /api/reservations/25

6. **HEAD - Checking Flight Availability:** When you're interested in a flight, you might want to know if it's available, without getting the full details yet. Similarly, the HTTP HEAD method retrieves only the headers of a response, giving you metadata without the full data.
**Endpoint:** HEAD /api/attractions/7

7. **OPTIONS = Choosing Activities:** Just as you might inquire about the available activities at your destination, the HTTP OPTIONS method asks the server what communication options and methods are supported.
**Endpoint:** OPTIONS /api/tours/3

8. **CONNECT - Establishing Connectins:** In the realm of travel, this could be likened to connecting to a travel agent's network to access their services. The HTTP CONNECT method is used to establish network connections through proxies.
**Endpoint:** CONNECT https://lnkd.in/dK8nsSs5

9. **TRACE - Following Your Route:** Think of TRACE as retracing your steps during your trip. In HTTP, the TRACE method echoes back the received request, letting you see how it changes as it travels through intermediaries.
**Endpoint:** TRACE /api/weather?location=city

### Is it not common to use https head, options, trace and connect? 

You're absolutely right. The HTTP methods HEAD, OPTIONS, TRACE, and CONNECT are not as commonly used as GET, POST, PUT, PATCH, and DELETE in typical web development scenarios. However, they do have specific use cases in more specialized or advanced situations:

1. **HEAD:** This method is used to retrieve only the headers of a resource without the actual data. It can be useful to check if a resource exists or to retrieve metadata about it, but it doesn't transfer the full content.

2. **OPTIONS:** OPTIONS is used to inquire about the communication options and methods supported by a server for a particular resource. It's often used in the context of Cross-Origin Resource Sharing (CORS) to determine if a client can make a particular request to a server.

3. **TRACE:** TRACE is primarily a diagnostic tool used to trace the request-response cycle. It's not commonly used in production but can be helpful for debugging and understanding how requests are modified by intermediaries (such as proxies).

4. **CONNECT:** CONNECT is used to establish network connections through proxies, typically for HTTPS tunneling. It's used in cases where a client wants to establish a secure connection through a proxy server.

While these methods are not frequently used in everyday web development, they serve important purposes in specific situations where their functionality is required. Most developers primarily work with GET, POST, PUT, PATCH, and DELETE to interact with web resources.

### the http head to work needs to get to the resource in the database, right? so the only benefits I can think of to retrieving just the header or metadata must be something network related or not?

You are correct that when an HTTP HEAD request is made, the server still needs to access the resource in the database or wherever it's stored. However, the key benefit of using an HTTP HEAD request is primarily related to reducing the amount of data transferred over the network and saving bandwidth.

Here are some benefits and use cases for HTTP HEAD requests:

1. **Reduced Data Transfer:** The HEAD request retrieves only the headers of the response, not the actual content. This can be particularly useful when you're concerned about the amount of data being transferred over the network. For example, if you want to check if a resource has been modified since your last request (using the "If-Modified-Since" header), you can use a HEAD request to retrieve just the headers and avoid downloading the full content if it hasn't changed.

2. **Resource Availability Check:** HEAD requests can be used to check if a resource exists on the server without downloading the entire resource. If the resource is not found, the server can respond with an appropriate status code (e.g., 404 Not Found).

3. **Metadata Retrieval:** When you need to obtain metadata about a resource, such as its content type, content length, or last modification date, a HEAD request can be sufficient. You can use the headers of the response to gather this information.

4. **CORS Preflight Requests:** In Cross-Origin Resource Sharing (CORS), browsers may send an OPTIONS preflight request to determine whether a cross-origin request is permitted. In such cases, the server can respond with headers in the OPTIONS response without actually processing the full request, allowing the browser to check permissions.

So, while the server still accesses the resource when handling an HTTP HEAD request, the main advantage is the reduction in network data transfer and the ability to quickly check resource availability and metadata.

### I think opentelemetry uses the http trace a lot when we instrumentalize the code, right?

Yes, OpenTelemetry is a popular observability framework used for monitoring and tracing applications, and it often utilizes the HTTP TRACE method (along with other techniques) to collect trace data and provide insights into the performance of distributed systems and microservices.

Here's how OpenTelemetry and HTTP TRACE are related:

1. **Distributed Tracing:** OpenTelemetry allows developers to instrument their applications to generate traces. These traces provide a detailed view of requests as they traverse through various services and components in a distributed system. Each trace typically consists of a series of spans, each representing an individual operation or service call.

2. **HTTP TRACE Method:** While the HTTP TRACE method isn't commonly used in production web applications, it can be useful for diagnostic purposes. In the context of OpenTelemetry, HTTP TRACE requests can be leveraged to collect additional information about the route that an HTTP request takes through a distributed system.

3. **Tracing Headers:** OpenTelemetry typically adds tracing headers to HTTP requests, such as "traceparent" and "tracestate" headers, which carry trace context information. These headers are used to correlate and link spans together as requests propagate through different services. This trace context allows for end-to-end tracing of requests.

4. **Propagation:** OpenTelemetry libraries provide support for automatically injecting and extracting trace context from HTTP requests and responses. This allows tracing information to be passed between different services, even across different programming languages and platforms.

5. **Analysis and Visualization:** OpenTelemetry integrates with observability tools like Jaeger, Zipkin, and Prometheus to collect, analyze, and visualize trace data. Developers and operations teams can use these tools to monitor the performance of their applications and identify bottlenecks or issues in a distributed system.

In summary, OpenTelemetry is a powerful tool for collecting and visualizing trace data in distributed systems, and it leverages HTTP TRACE, among other techniques, to provide comprehensive insights into how requests flow through a system and where latency or errors may occur.

## what types of errors are provided by the HTTP/HTTPS specification that should be handled?
HTTP and HTTPS specify several types of errors that can occur when making requests to a web server, and these errors should be handled by the client application to ensure a smooth user experience. Some of the most common errors include:

1. 4xx Client Error: These errors indicate that there is an issue with the request made by the client, such as a missing or incorrect parameter. Common 4xx error codes include 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, and 409 Conflict.

2. 5xx Server Error: These errors indicate that there is an issue with the server and it is unable to process the request. Common 5xx error codes include 500 Internal Server Error, 502 Bad Gateway, and 503 Service Unavailable.

3. SSL/TLS Certificate Errors: These errors occur when the SSL or TLS certificate presented by the server is invalid or has expired, and the client is unable to establish a secure connection.

It's important to handle these errors appropriately, such as by providing helpful error messages to the user, retrying the request if appropriate, or falling back to an alternative server if the original server is unavailable. Proper error handling helps to ensure a positive user experience and can also provide valuable information for debugging and troubleshooting purposes.

## How do HTTP status codes work, and which are most important?

When a client sends a request to a server, the server responds with both the requested data and a 3-digit status code, which succinctly indicates the outcome of the request.

Clients rely on these standardized codes to determine if their requests were handled properly, if further action is needed, or if an error occurred.

HTTP status codes are divided into five categories based on their first digit:

* 🟣 Informational (1xx): Indicates that the request was received and the process is ongoing.
* 🟢 Success (2xx): Signifies that the request was successfully received, understood, and accepted.
* 🔵 Redirection (3xx): Indicates that further action is needed to complete the request.
* 🟠 Client error (4xx): Indicates that there was an issue with the request, such as incorrect syntax or inability to fulfill it.
* 🔴 Server error (5xx): Indicates that the server failed to fulfill a valid request.

Effective use of HTTP status codes is crucial for various functions in web development, including efficient communication, reliability, troubleshooting, error identification, automation, user feedback, and more.

Here are some best practices for working with status codes:

🔹 Use specific status codes that accurately describe the outcome of an operation.
🔹 Maintain consistency in how status codes are used across your application.
🔹 Provide additional information in the response body or headers when necessary.
🔹 Log and monitor the status codes your application sends and receives for performance tuning, anomaly detection, and debugging.

While HTTP status codes might seem minor, they play a vital role in client-server communication. Understanding and effectively utilizing these codes is essential for developing robust applications.

![HTTP Status COde](./img/API/HTTPStatusCode.jpg)

## References
1. https://www.httpstatus.com.br/
2. https://kinsta.com/blog/http-status-codes/
3. https://restfulapi.net/http-status-codes/
4. https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status
5. https://www.rfc-editor.org/rfc/rfc9110.html
6. https://twitter.com/ChrisStaud/status/1778713036326662254
