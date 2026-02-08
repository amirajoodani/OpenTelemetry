# OpenTelemetry
Current State of Observability
According to Wikipedia, "observability is a measure of how well the internal states of a system can be inferred from knowledge of its external outputs" (2024). In other words, observability refers to how easily you can understand what's happening inside a system, like an application or a service, by looking at the information it produces.

A distributed system is a network of independent computers, or nodes, working together to perform tasks as if they were a single system. These systems are widely used in applications like cloud computing, where different parts of an application run on different servers to share resources and balance the workload. Because of the complexity of distributed systems, it can be challenging to understand what's happening inside each component at any given time. This is where observability becomes crucial.

To make a distributed system observable, we must model its state in a way that lets us reason about its behavior. This model is composed of three factors:

First, there is the workload. These are the operations a system performs to fulfill its objectives. For instance, when a user sends a request, a distributed system often breaks it down into smaller tasks handled by different services. This is also often referred to as transactions.
Second, there are software abstractions that make up the structure of the distributed system. This includes elements such as load balancers, services, pods, containers and more.
Lastly, there are physical machines that provide computational resources (e.g. RAM, CPU, disk space, network) to carry out work.<br>

<img width="591" height="504" alt="1" src="https://github.com/user-attachments/assets/4dbca9bb-51a6-4706-98c1-d5183f3256bc" /> <br>
