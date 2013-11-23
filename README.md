RabbitMQ Utilities
==================

This repository contains two utilities- one for consuming messages and the other to produce messages onto the rabbitmq queue.

*Usage*
=======
Consumer
```
go run amqpclient.go --help

Usage of ./amqpclient:
  -auto-delete=false: Auto Delete Exchange true|false
  -consumer-tag="simple-consumer": AMQP consumer tag (should not be blank)
  -durable=false: Durable exchange true|false
  -exchange="test-exchange": Durable, non-auto-deleted AMQP exchange name
  -exchange-declare=false: Declare Exchange true|false
  -exchange-type="direct": Exchange type - direct|fanout|topic|x-custom
  -key="test-key": AMQP binding key
  -lifetime=5s: lifetime of process before shutdown (0s=infinite)
  -msg-ack=false: Consume messages in queue true|false
  -queue="test-queue": Ephemeral AMQP queue name
  -queue-declare=false: Declare Queue true|false
  -uri="amqp://guest:guest@localhost:5672/": AMQP URI
```
Producer
```
Usage of /tmp/go-build278233220/command-line-arguments/_obj/a.out:
  -body="foobar": Body of message
  -exchange="cloud-init": Durable AMQP exchange name
  -exchange-type="fanout": Exchange type - direct|fanout|topic|x-custom
  -key="cloudinit-key": AMQP routing key
  -reliable=true: Wait for the publisher confirmation before exiting
  -uri="amqp://guest:guest@localhost:5672/": AMQP URI
```
  
*How to Build*
==============

```
  go get github.com/kumarcv/rabbitmq-utilities
  go run amqpclient.go 
```

I run this on my devstack setup and messages will be printed on the console.

```
go run amqpclient.go --uri amqp://guest:ravi@localhost:5672/ --exchange l3_agent_fanout --exchange-type fanout  --queue  custom  --key l3_agent  --lifetime 0 --queue-declare  --auto-delete
2013/11/22 15:39:09 dialing "amqp://guest:ravi@localhost:5672/"
2013/11/22 15:39:09 got Connection, getting Channel
2013/11/22 15:39:09 got Channel, declaring Exchange ("l3_agent_fanout") false
2013/11/22 15:39:09 declaring Queue "custom" true
2013/11/22 15:39:09 declared Queue ("custom" 0 messages, 0 consumers), binding to Exchange (key "l3_agent")
2013/11/22 15:39:09 Queue bound to Exchange, starting Consume (consumer tag "simple-consumer")
2013/11/22 15:39:09 running forever

```




  
  
