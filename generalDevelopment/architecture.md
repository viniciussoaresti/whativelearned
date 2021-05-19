# Architecture:

"Software architecture refers to the fundamental structures of a software system and the discipline of creating such structures and systems. Each structure comprises software elements, relations among them, and properties of both elements and relations", [Wikipedia](https://en.wikipedia.org/wiki/Software_architecture#:~:text=Software%20architecture%20refers%20to%20the,of%20both%20elements%20and%20relations).

## Application Architecture:

![Monolithic vs Microservices](https://miro.medium.com/max/1516/1*0Qq07wT-J9K3-HviORIvjA.png)

### Monolithic Application:

"In software engineering, a monolithic application describes a single-tiered software application in which the user interface and data access code are combined into a single program from a single platform.

A monolithic application is self-contained and independent from other computing applications. The design philosophy is that the application is responsible not just for a particular task, but can perform every step needed to complete a particular function", [Wikipedia](https://en.wikipedia.org/wiki/Monolithic_application).

Monolithic applications are less complex to develop and debug, but that comes at the cost of sharing resources, having only one development stack, and it's more difficult to scale.

### Microservices Application:

"Microservices are both an architecture and an approach to writing software. With microservices, applications are broken down into their smallest components, independent from each other. Instead of a traditional, monolithic, approach to apps, where everything is built into a single piece, microservices are all separated and work together to accomplish the same tasks. Each of these components, or processes, is a microservice. This approach to software development values granularity, being lightweight, and the ability to share similar process across multiple apps. It is a major component of optimizing application development towards a cloud-native model", [RedHat](https://www.redhat.com/en/topics/microservices).

Here we're able to work with multiple development stacks, and it's easier to scale, but coupling and monitoring problems are more difficult to avoid, but possible (coupling can be handled with a message broker, for example).