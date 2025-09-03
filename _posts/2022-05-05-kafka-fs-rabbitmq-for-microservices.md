---
layout: single
title:  "Notes: Kafka vs RabbitMQ for inter-microservice communication"
date:   2022-05-05 16:55:24 +0200
tags: rabbitmq kafka microservices ddd
excerpt: Comparing 2 most popular choices for async microservice communication
---

[good short video about kafka](https://www.youtube.com/watch?v=Ch5VhJzaoaI)

**AWESOME comparison:**
- [part 1](https://www.youtube.com/watch?v=sjDnqrnnYNM)
- [part 2](https://www.youtube.com/watch?v=faAtGVJi--E)

[problem with Kafka topics being shared resources](https://jack-vanlightly.com/sketches/2019/10/7/kafka-topics-are-shared-resources) 😆

#### Kafka
- 1 topic by bounded context / aggregate (e.g. multiple events about 1 aggregate go to same topic)
- consumers should receive all messages and filter what messages they handle
- topic is partitioned by the aggregate ID, so in each partition the events will be in order for particular aggregate
- consumer group assigns consumers to partitions, so during processing messages from a single partition by the same consumer - **processing ordering is guaranteed**
- consumers have to implement retries / dead letter queue
- easy to attach new consumer group to the existing topic and experiment / test in production the newly deployed build etc.

#### RabbitMQ:
- easy routing, consumers only receive what they want
- to ensure ordering guarantees when scaling consumers - **have to use** [**consistent hashing topic**](https://github.com/rabbitmq/rabbitmq-server/tree/master/deps/rabbitmq_consistent_hash_exchange#code-example-in-ruby) **/** [**sharding plugin**](https://github.com/rabbitmq/rabbitmq-server/tree/master/deps/rabbitmq_sharding) ([but be careful](https://jack-vanlightly.com/blog/2018/11/14/why-i-am-not-a-fan-of-the-rabbitmq-sharding-plugin) - it's hard to properly assign consumers)
- **without above** - no way to provide ordering guarantees with the “competing consumers” pattern, because 1) 2nd consumer can start processing 2nd event before 1st one finished processing 1st one 2) if 1st consumer dies - 1st event is put back to the queue and processed AFTER 2nd one was already processed. This all means **consumers have to deal with possibly wrong events order**
- retries/DLQ is available by the protocol (not sure about Ruby implementation though)
- cannot attach new consumer group to the existing production queue and experiment (only if probably you’ll duplicate the queue ?)