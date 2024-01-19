---
title: "What Is gRPC and Different Types of gRPC Services"
datePublished: Fri Jan 19 2024 15:46:09 GMT+0000 (Coordinated Universal Time)
cuid: clrktc5xv000108l85z74bwg1
slug: what-is-grpc-and-different-types-of-grpc-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705679062956/b8ca0b20-0780-4949-8930-f705ded72cff.png
tags: aws, aws-lambda, grpc, aws-certified-solutions-architect-associate, aws-community-builder, aws-cloud-practitioner, wemakedevs, twsbashblazechallenge-trainwithshubham

---

## Introduction

Remote Procedure Call (RPC) is a network protocol for establishing procedure calls on a remote computer using an application server — also known as a client/server model. The first description of Remote Procedure Call dates back to 1976 in the RFC 707 standard ([https://www.rfc-editor.org/info/rfc707](https://github.com/ARFarokhi/gRPC.git?source=post_page-----9b86a7267064--------------------------------)). Understanding the RPC principles and the RFC 707 standard was helpful for me to understand gRPC. It’s always good to understand the basis of a system. With RPC, a client invokes a function, a server procedure with parameters. When the server receives the request, it sends the required response back to the client. The client waits for the server to respond and cannot perform other operations until the server has finished the request. gRPC is influenced by this RPC model established long before gRPC Figure bellow shows the RPC model principle:

![](https://miro.medium.com/v2/resize:fit:635/1*0T2wZ8t5y9qWJxPY9lLJag.png align="left")

The RPC model principle

### **What is gRPC ?**

gRPC is a Google-created, open source, schema-first Remote Procedure Call framework that takes advantage of the HTTP/2 protocol to transport messages in binary. These messages are serialized and deserialized using Protocol Buffers, which are a type of Interface Definition Language (IDL).

### **Deffirrent Types of gRPC Services**

gRPC supports four types of calls to the server:

* Unary
    
* Server-streaming
    
* Client-streaming
    
* Bidirectional
    

Unlike a REST API, which only supports **unary** type calls (**unary :the client sends a request, and the server receives it and returns the response with its status to the client**), gRPC supports all four types, as described next.

### **Unary Calls**

The client initiates the remote procedure call with the method name, metadata, and the request message. Then the server returns the response with the gRPC status, the response message, and metadata

![](https://miro.medium.com/v2/resize:fit:700/1*UWYE-CwblZHH_dGArLjIhw.png align="left")

gRPC Unary service type

### **Server-Streaming Calls**

The client initiates the remote procedure call with the method name, metadata, and the request message. Then it receives a streaming response from the server. The request’s status is sent to the client at the end of the streaming response (all data has been transmitted to the client along with its metadata)

![](https://miro.medium.com/v2/resize:fit:700/1*A_7TvcH-UfIt5b8UyAl8Ng.png align="left")

gRPC server-streaming service type

### **Client-Streaming Calls**

The client initiates the remote procedure call with the method name and metadata. Then the client sends streaming messages. However, the server can send the request status code and metadata before sending the client’s messages. If a problem occurs on the server and it has already sent the status and metadata, detecting errors is difficult.

![](https://miro.medium.com/v2/resize:fit:700/1*Ie9AMKKxCPGhEmyN6YoQcg.png align="left")

gRPC client-streaming service type

### **Bidirectional Streaming Calls**

Each party sends its messages by streaming, and this can be done in parallel, which means there is no order in which client/server messages are sent and received. The client initiates the remote procedure call with the method name and metadata. Then the server can respond to it immediately by returning the status and its metadata (or when the client has finished sending all of its messages)

![](https://miro.medium.com/v2/resize:fit:700/1*r3oerJqZEuM4AEDyj-4Gjg.png align="left")

gRPC bidirectional service type

As sample bellow are CRUD operations with all possible gRPC services

### **Messages Declaration**

all messages share the same rule:

* any message must be defined with the message keyword
    
* each property is optional by default
    
* each property must be assigned a position required for the serialization/deserialization process and must be **unique**
    

### **Empty Parameter**

if you have no parameter to send to the server or to return to the  
client, it is mandatory to create an empty message without properties. like for GetAll() for input parameter(request type) and Update() output parameter(response type) in country.poroto .

so first **import “google/protobuf/Empty.proto”;**

then use it like :

**Collections**

Collections, also essential in any project type, are supported in the Protobuf syntax with

the following two types:

* List
    
* Dictionary
    

for List “**repeated**” and for Dictionary “**map&lt;key,value&gt;**” keyword must be used.

### **Protocol buffer supported types and their default values with C# equivalent**

![](https://miro.medium.com/v2/resize:fit:623/1*CwFVDDOZ0uOP0dPqs-tL7A.png align="left")

Protocol buffer supported types and their default values with C# equivalent

The .NET types DateTimeOffset, DateTime, and TimeSpan have no equivalent in Protobuf languages, so Protobuf provides some Well-Known Types to manage these unsupported types in .NET.

![](https://miro.medium.com/v2/resize:fit:630/1*1QwnBmHkw7QqV2N4JaLuVg.png align="left")

😊 Thank you so much for reading my blog! 😊 I hope you found it helpful and informative. If you did, please 👍 give it a like and 💌 subscribe to my newsletter for more of this type of content. 💌

I'm always looking for ways to improve my blog, so please feel free to leave me a comment or suggestion. 💬

Thanks again for your support! 😊