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
