

# RabbitMQ
RabbitMQ is a message **broker** (queue manager). It is a plataform that provides an structure to send and receives messages.

Why Messages and RabbitMQ?
By using messages as a way to transfer data among our applications, it is possible decoupling applications by send data asynchronously.

1.  Q: What is RabbitMQ?
## How RabbitMQ works, and it's Standard message flow?
An exchange must accept messages from the supplier request and route them to message queues using **header attributes, bindings and routing keys.** A binding is set up to connect the queue to an exchange.

**1)** The producer publishes a message to an exchange. When you create the exchange, you have to specify the type of it. 
**2)** The exchange receives the message and is now responsible for the routing of the message. The exchange takes different message attributes into account, such as routing key, depending on the exchange type.  
**3)** Bindings have to be created from the exchange to queues. In this case, we see two bindings to two different queues from the exchange. The Exchange routes the message into the queues depending on message attributes.  
**4)** The messages stay in the queue until they are handled by a consumer  
**5)** The consumer handles the message.



3.  Q: When and why to use RabbitMQ?
What Is binding And routing Key?
A binding is a "bridge" that you set up to connect a queue to an exchange.
The routing key is an attribute message that the exchange examines when determining how to route the message to queues.

4. 1.  Q: What is a RabbitMQ channel?
## Q: What is a dead letter queue in rabbitmq?
To be considered a dead letter queue in rabbitmq it must satisfy one or more of the following failure criteria.
* Message that is sent to a queue that does not exist.
* Queue length limit exceeded.
* Message length limit exceeded.
* Message is rejected by another queue exchange.
* Message reaches a threshold read counter number, because it is not consumed. Sometimes this is called a "back out queue".
* 
## What is Exchange?
Messages are not posted directly in the queue; rather, the user sends messages to the exchange. An exchange is responsible for routing the messages to the various queues. An exchange receives messages from the producer request and routes them by bindings and routing keys to message queues. A binding is a linkage between an exchange and a queue.

8.  Q: Types of Exchange?
* **Direct**: Direct exchange transfers messages to queues on the basis of a message routing key. The message is routed in a direct exchange to the queues whose binding key exactly matches the message's routing key. If the queue is bound to the binding key exchange, a message will be sent to the exchange with a routing key to the queue.
* **Fanout**: A fanout sends messages to all the queues linked to it.
* **Topic**: The topic exchange matches the wildcard between the routing key and the binding routing pattern.
* **Headers**: Headers exchanges use the routing attributes of the message header.

9. : Which Protocol RabbitMQ uses?
RabbitMQ uses **Advanced Message Queuing Protocol (AMQP)**. Its an open standard layer used to communicates date across network by means of byte stream. 

10.Does RabbitMQ is PUSH or PULL? 
RabbitMQ uses a PUSH template and prevents exhausting consumers through the prefetch configured limit.

10.  Q: What is Dead Letter Exchange in Rabbitmq?
If there is no appropriate queue for the message, the message will be dropped quietly. RabbitMQ offers an AMQP extension known as the "Dead Letter Exchange". The dead letter exchange provides features for collecting non-deliverable messages.

## What is Synchronous and Asychronous messaging? 
Synchronous messaging is a two way communication, where sender sends a message to receiver and receiver receives message and gives reply to the sender. Where as Asynchronous Messaging is a communication where a message is placed in a message queue and does not require an immediate response from receiver.

11.  Q: What is pub sub, how it works?
pub/sub messaging is a asynchronous service-to-service communication, it's a two way communication.
Mainly used in statelss, microservices. In this type of model, once message published to a topic, it gets received immediately by all subscriber to the topic.

Q: How RabbitMQ differs from Kafka?
What is Pub Sub Communication?

: How to install and configure RabbitMQ at local?

## Pub/Sub pattern

## Exchanges - Message Routing Agents
Messages are routed through exchanges, they are message routing agents, before arriveing in the queue.

## Ack or Nack or Reject ?

-   `nack`/`reject`  with  `requeue=1`: the message will be returned to the queue it came from as though it were a new message; this might be useful in case of a temporary failure on the consumer side
-   `nack`/`reject`  with  `requeue=0`  and a configured Dead Letter Exchange (DLX), will publish the message to that exchange, allowing it to be picked up by another queue
-   `nack`/`reject`  with  `requeue=0`  and no DLX will simply discard the message
-   `ack`  will remove the message from the queue even if a DLX is configured

If you have no DLX configured, always using  `ack`  will be the same as  `nack`/`reject`  with  `requeue=0`; however, using the logically correct function from the start will give you more flexibility to configure things differently later.

// **TODO** - Spring Application
https://www.techgeeknext.com/pcf-tutorials/pcf-spring-boot-rabbitmq


## References
[RabbitMQ Introduction - Medium](https://medium.com/faun/rabbitmq-an-introduction-b84370fcf31)
[An introduction to RabbitMQ, a broker that deals in messages.](https://medium.com/free-code-camp/rabbitmq-9e8f78194993)
[Rabbit MQ - Best Practices](https://medium.com/@shivama205/rabbitmq-best-practices-67a27ef72a57)
[https://www.techgeeknext.com/java/rabbitmq-interview-questions](https://www.techgeeknext.com/java/rabbitmq-interview-questions)
