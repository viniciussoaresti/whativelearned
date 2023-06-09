# Reactive Architecture

"Cloud-native systems need to be responsive. Designing these systems requires architects to think differently, in order to build software that can be both resilient and elastic. These Reactive Systems are built on a message-driven foundation. As microservices have emerged as the gold standard of developing modern software applications, every team needs to develop a deep understanding of how to design, build, and operate software in a Reactive world if they want to remain relevant", [Cognitive Class](https://cognitiveclass.ai/learn/reactive-architecture-foundations).

Reactive architecture focus on delivering an outstanding experience to the user, that now requires that systems respond quickly and are up 24/7. No delay to page refreshes, no "system down for maintenance" messages, etc.

## Concepts:

### Reactive Manifesto:

The [Reactive Manifesto](https://www.reactivemanifesto.org/https://www.reactivemanifesto.org/) specifies that Reactive Systems are:

- Responsive: "The system responds in a timely manner if at all possible. Responsiveness is the cornerstone of usability and utility, but more than that, responsiveness means that problems may be detected quickly and dealt with effectively. Responsive systems focus on providing rapid and consistent response times, establishing reliable upper bounds so they deliver a consistent quality of service. This consistent behaviour in turn simplifies error handling, builds end user confidence, and encourages further interaction."

- Resilient: "The system stays responsive in the face of failure. This applies not only to highly-available, mission-critical systems — any system that is not resilient will be unresponsive after a failure. Resilience is achieved by replication, containment, isolation and delegation. Failures are contained within each component, isolating components from each other and thereby ensuring that parts of the system can fail and recover without compromising the system as a whole. Recovery of each component is delegated to another (external) component and high-availability is ensured by replication where necessary. The client of a component is not burdened with handling its failures."

- Elastic: "The system stays responsive under varying workload. Reactive Systems can react to changes in the input rate by increasing or decreasing the resources allocated to service these inputs. This implies designs that have no contention points or central bottlenecks, resulting in the ability to shard or replicate components and distribute inputs among them. Reactive Systems support predictive, as well as Reactive, scaling algorithms by providing relevant live performance measures. They achieve elasticity in a cost-effective way on commodity hardware and software platforms.The system stays responsive under varying workload. Reactive Systems can react to changes in the input rate by increasing or decreasing the resources allocated to service these inputs. This implies designs that have no contention points or central bottlenecks, resulting in the ability to shard or replicate components and distribute inputs among them. Reactive Systems support predictive, as well as Reactive, scaling algorithms by providing relevant live performance measures. They achieve elasticity in a cost-effective way on commodity hardware and software platforms."

- Message Driven: "Reactive Systems rely on asynchronous message-passing to establish a boundary between components that ensures loose coupling, isolation and location transparency. This boundary also provides the means to delegate failures as messages. Employing explicit message-passing enables load management, elasticity, and flow control by shaping and monitoring the message queues in the system and applying back-pressure when necessary. Location transparent messaging as a means of communication makes it possible for the management of failure to work with the same constructs and semantics across a cluster or within a single host. Non-blocking communication allows recipients to only consume resources while active, leading to less system overhead."

Just a sidenote, differentiating messages and events:

"A Message is some data sent to a specific address. In Message Driven systems, each component has a unique address other components can send messages to. Each of these components, or recipients, awaits messages and reacts to them. An Event is some data emitted from a component for anyone listening to consume", [Lightbend](https://developer.lightbend.com/docs/akka-platform-guide/concepts/message-driven-event-driven.html).

### Reactive Architecture vs Reactive Programming

It's good to separate the differences between Reactive Architecture and Reactive Programming. 

While the Reactive Architecture, which is basically defined by the Reactive Manifesto, builds Reactive Systems, Reactive Programming <b>can</b> be used to support the construction of Reactive Systems, but just because you are using it, your system isn't necessarily a Reactive System.

Reactive Programming takes a problem and breaks it up into small, discrete steps, that are executed in an async/non-blocking fashion, usually via a callback mechanism. Examples include Promises, Streams, RxJava, etc.

But if you deploy a system using Reactive Programming onto one node, for example, you've not built a Reactive System.

### The Actor Model

It's a programming paradigm that supports the construction of reactive systems. It's principles:

- All your computation will occur inside of one of those actors or across many off those actors;

- Each of those actors is addressable, having an unique address;

- All communication between actors is done using asynchronous non-blocking messages, which introduces us to location transparency:

#### Location transparency:

The actors communicate using the same technique regardless of location, as they don't know the location of where the message is going to go. So either a local or remote connection should be done the same way, let's put "with the same API". That is the essene of location transparency.

This should not be confused with transparent remoting.

##### Location Transparency vs Transparent Remoting

![Location transparency image](https://i.imgur.com/J2qDGAf.png)

"The two are actually opposites.

"Transparent Remoting" is about making remote calls look like local calls. "Location transparency" is about making local calls look like remote calls.

While this may not sound like a big deal—it is. It is all about the assumptions you can make. Typically local invocations have a much higher fidelity as there is a lot fewer possible error and failure modes. By embracing those failure and error modes in "Location transparency" it does no longer matter technically where the sender and receiver is located.

With "Transparent Remoting" it is not evident that you are crossing a asynchronous and binary boundary, and as such, whether the calling thread will be able to make progress, whether there will be a notification on communication problems or information loss or corruption", [Victor Klang](https://stackoverflow.com/questions/37043288/difference-between-transparent-remoting-and-location-transparency/37050040).

It's also possible to build Reactive Systems without actors, while adding components, rather than making them be built in:

![Reactive Systems without actors image](./reactiveArchitectureAssets/withoutActors.png?raw=true)

But the actor model can be reactive at the level of actors, which can be inserted into a microservice, as opposed to being reactive at the level of microservices. It's also possible with this approach, but harder.