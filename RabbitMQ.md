

# RabbitMQ
RabbitMQ is a message **broker** (queue manager). It is a plataform that provides an structure to send and receives messages.

Why Messages and RabbitMQ?
By using messages as a way to transfer data among our applications, it is possible decoupling applications by send data asynchronously.

## Pub/Sub pattern


## Exchanges - Message Routing Agents
Messages are routed through exchanges, they are message routing agents, before arriveing in the queue.

## Ack or Nack or Reject ?

-   `nack`/`reject`  with  `requeue=1`: the message will be returned to the queue it came from as though it were a new message; this might be useful in case of a temporary failure on the consumer side
-   `nack`/`reject`  with  `requeue=0`  and a configured Dead Letter Exchange (DLX), will publish the message to that exchange, allowing it to be picked up by another queue
-   `nack`/`reject`  with  `requeue=0`  and no DLX will simply discard the message
-   `ack`  will remove the message from the queue even if a DLX is configured

If you have no DLX configured, always using  `ack`  will be the same as  `nack`/`reject`  with  `requeue=0`; however, using the logically correct function from the start will give you more flexibility to configure things differently later.


## References
[RabbitMQ Introduction - Medium](https://medium.com/faun/rabbitmq-an-introduction-b84370fcf31)
[An introduction to RabbitMQ, a broker that deals in messages.](https://medium.com/free-code-camp/rabbitmq-9e8f78194993)
(Rabbit MQ - Best Practices)(https://medium.com/@shivama205/rabbitmq-best-practices-67a27ef72a57)
