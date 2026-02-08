# OpenTelemetry
Current State of Observability
According to Wikipedia, "observability is a measure of how well the internal states of a system can be inferred from knowledge of its external outputs" (2024). In other words, observability refers to how easily you can understand what's happening inside a system, like an application or a service, by looking at the information it produces.

A distributed system is a network of independent computers, or nodes, working together to perform tasks as if they were a single system. These systems are widely used in applications like cloud computing, where different parts of an application run on different servers to share resources and balance the workload. Because of the complexity of distributed systems, it can be challenging to understand what's happening inside each component at any given time. This is where observability becomes crucial.

To make a distributed system observable, we must model its state in a way that lets us reason about its behavior. This model is composed of three factors:

First, there is the workload. These are the operations a system performs to fulfill its objectives. For instance, when a user sends a request, a distributed system often breaks it down into smaller tasks handled by different services. This is also often referred to as transactions.
Second, there are software abstractions that make up the structure of the distributed system. This includes elements such as load balancers, services, pods, containers and more.
Lastly, there are physical machines that provide computational resources (e.g. RAM, CPU, disk space, network) to carry out work.<br>

<img width="591" height="504" alt="1" src="https://github.com/user-attachments/assets/4dbca9bb-51a6-4706-98c1-d5183f3256bc" /> <br>
# Logs <br>
A log is an append-only data structure that records events occurring in a system. A log entry consists of a timestamp that denotes when something happened and a message to describe details about the event. However, coming up with a standardized log format is no easy task. One reason is that different types of software often convey different pieces of information. The logs of an HTTP web server are bound to look different from those of the kernel. But even for similar software, people often have different opinions on what good logs should look like.

Apart from content, log formats also vary with their consumers. Initially, text-based formats catered to human readability. However, as software systems became more complex, the volume of logs soon became unmanageable. To combat this, we started encoding events as key/value pairs to make them machine-readable, which is commonly known as structured logging. Moreover, the distribution and ephemeral nature of containerized applications meant that it was no longer feasible to log onto individual machines and sift through logs. As a result, people started to build logging agents and protocols to forward logs to dedicated services. These logging systems allowed for efficient storage as well as the ability to search and filter logs in a central location.<br>

# Metrics <br>
 

The four common types of metrics: counters, gauges, histograms and summaries
<img width="744" height="440" alt="2" src="https://github.com/user-attachments/assets/5dd80bf2-0a54-43b7-84e3-e17377ed1df1" /> <br>

Logs shine at providing detailed information about individual events. However, sometimes we need a high-level view of the current state of a system. This is where metrics come in. A metric is a single numerical value derived by applying a statistical measure to a group of events. In other words, metrics represent an aggregate. This is useful because their compact representation allows us to graph how a system changes over time. In response, the industry developed instruments to extract metrics, formats and protocols to represent and transmit data, specialized time-series databases to store them, and frontends to make this data accessible to end-users. <br>

# Traces <br>
 

Exemplary architecture of a distributed system with multiple Databases, Applications and servers working together
<img width="994" height="818" alt="3" src="https://github.com/user-attachments/assets/a3989cb1-a2c6-449a-8b81-a0737a608fb4" />

As distributed systems grew in scale, it became clear that traditional logging systems often fell short when trying to debug complex problems. The reason is that we often have to understand the chain of events in a system. On a single machine, stack traces allow us to track an exception back to a line of code. In a distributed environment, we don’t have this luxury. Instead, we perform extensive filtering to locate log events of interest. To understand the larger context, we must identify other related events, such as the specific requests or transactions that initiated the log entry and the sequence of services or microservices involved in processing that request across the system. This often results in a lot of manual labor (e.g. comparing timestamps) or requires extensive domain knowledge about the applications. Recognizing this problem, Google developed Dapper, which popularized the concept of distributed tracing.

On a fundamental level, tracing is logging on steroids. The underlying idea is to add transactional context to logs. This makes it possible to infer causality and reconstruct the journey of requests in the system.

Three Pillars of Observability
Telemetry is the process of automatically collecting and transmitting data from remote or distributed systems to monitor, measure, and track the performance or status of those systems. Telemetry data provides real-time insights into how different parts of an application are performing. Telemetry provides the data for observability tooling to help developers and system administrators observe, troubleshoot, and optimize the system without needing to manually check each component.

On the surface, logs, metrics, and traces share many similarities in their lifecycle and components. Everything starts with instrumentation that captures and emits data. The data has to have a specific structure defined by a format. Then, we need a mechanism to collect and forward a piece of telemetry. Often, there is some kind of agent to further enrich, process, and batch data before ingesting it in a backend. This process typically involves a database to efficiently store, index, and search large volumes of data. Finally, there is a frontend analysis to make the data accessible to the end-user. However, in practice, we develop dedicated systems for each type of telemetry, and for good reason: Each telemetry signal poses its own unique technical challenge. These challenges are mainly due to the different natures of the data.

The design of data models, interchange formats, and transmission protocols, highly depends on whether you are dealing with unstructured or semi-structured textual information, compact numerical values inside a time series, or graph-like structures depicting causality between events. Even for a single signal, there is no consensus on these topics.

Furthermore, how we work with and derive insights from telemetry varies dramatically. A system might need to perform full-text searches, inspect single events, analyze historical trends, visualize request flow, diagnose performance bottlenecks, and more. These requirements manifest themselves in the design and optimization of storage, access patterns, query capabilities, and more.

When addressing these technical challenges, vertical integration emerges as a pragmatic solution. In practice, observability vendors narrow the scope of the problem to a single signal and provide instrumentation to generate and tools to analyze telemetry, as a single, fully integrated solution.

 

The three pillars of observability, including metrics, traces and logs
<img width="734" height="386" alt="4" src="https://github.com/user-attachments/assets/db416b9f-e915-4d77-9461-3c740de5dfee" /> <br>

Having dedicated systems for logs, metrics, and traces is why we commonly refer to them as the three pillars of observability. The notion of pillars provides a great mental framework because it emphasizes the following:

There are different categories of telemetry
Each pillar has its own unique strengths and stands on its own
Pillars are complementary and must be combined to form a stable foundation for achieving observability
