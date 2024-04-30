# Reflection
### Ferdinand Raja Kenedy - 2206046683

### 1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
- Unary is the simplest one,  when a client sent a request and server also response qith a request. Unary is most suitable when client only need to send 1 request and receive 1 response from the server
- Server Streaming is when a client sent a request and server response with a data stream. This RPC is useful in scenarios where the server needs to push a large amount of data or a continuous stream of updates to the client.
- Bi-directional streaming is a communication pattern in which both the client and server can send multiple messages to each other in a continuous stream. This pattern is commonly used in scenarios where there is a need for ongoing, interactive communication. For example, in a chat application, bidirectional streaming gRPC can be used to send and receive messages in real-time between the client and server.

### 2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?
- Authentication : gRPC supports  authentication through various methods such as SS/TLS, token-based auth, and username and password auth.
- Authorization : Define access control policies based on user authorization. Implements role-based access control (RBAC) or attribute-based access control (ABAC) mechanisms to manage permissions effectively.
- Data Encryption : Utilize TLS to encrypt data in transit, ensuring confidentiality and integrity of communication.Can utilize SS/TLS to prevent eavesdropping and tampering.

### 3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?
- Load Balancing and Scalability:
Scaling bidirectional streaming services horizontally across multiple instances or nodes requires careful consideration of load balancing and distributed communication.
- Concurrency and Asynchronous Programming:
Managing concurrent streams and asynchronous operations can be complex, especially in scenarios with a large number of active connections

### 4. What are the advantages and disadvantages of using the `tokio_stream::wrappers::ReceiverStream` for streaming responses in Rust gRPC services?
- Advantages :
1. Easier to handle error handling because of `ReceiverStream` returns a wrapped result.
2. Compatible because `ReceiverStream` compatibles with `tonic::streaming`
- Disadvantages:
1. `ReceiverStream` doesn't have innate error hendling, therefore we need to do it manually.

### 5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
- Creating services and messages in different .proto files enables sharing message definitions across multiple services.
- Defining reusable functions and structures in separate .rs files allows them to be utilized by other services.

### 6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?
- Create functions that works on more complex logic.
- Create unit testing for that functions.
- Deploy the database
- Integrate the program into the database

### 7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
Adopting gRPC affects how systems communicate with each other by making communication faster with HTTP/2. It works with many languages and systems, making it easy for them to understand each other. Tools help write code faster, and it's good at balancing work between different parts of a system. It also helps keep things safe and lets you use different languages together smoothly.

### 8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
- Advantages:
1. More control over how data is processed.
2. Can use multiple threads at once by multiplexing.

- Disadvantages:
1. Need to manage concurrency by hand.
2. More complex than HTTP/1.1

### 9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
- REST APIs :
In REST APIs, clients typically send a request to the server, and the server responds with a single response. This model follows a stateless client-server interaction pattern.
- gRPC :
gRPC supports bidirectional streaming, allowing both clients and servers to send multiple messages over a single connection asynchronously. This enables real-time communication between client and server without the need for polling or additional overhead.

### 10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
- Schema-based approach of gRPC :
1. gRPC enforces a strict structure for data using Protocol Buffers, reducing errors and ensuring consistency.
2. gRPC supports easier versioning and compatibility between different message formats. 
- Schema-less nature of JSON in REST API payloads :
1. JSON in REST APIs allows for more flexible data formats, which can lead to inconsistencies.
2. With REST APIs, managing changes to data structures can be trickier and may require additional strategies.