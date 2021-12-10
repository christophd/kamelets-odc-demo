# Kamelet Demo bindings

Sample Kamelet bindings for demo reasons

## Installation

Make sure to have installed

* Red Hat Serverless operator
* Strimzi or Red Hat AMQ Stream operator
* Camel K operator
* kn and kamel CLI on your machine

### Create Knative broker and channel

```shell
kn broker create default
```

```shell
kn channel create messages
```

### Create Kafka cluster an topic

```shell
oc apply -f https://strimzi.io/examples/latest/kafka/kafka-ephemeral-single.yaml
```

```shell
oc apply -f https://strimzi.io/examples/latest/topic/kafka-topic.yaml
```

## Run demo bindings

### Knative broker

```shell
oc apply -f timer-broker-event-source.binding.yaml
```

```shell
oc apply -f broker-event-log-sink.binding.yaml
```

Show logs and see messages consumed

```shell
kamel logs broker-event-log-sink
```

### Knative broker 

```shell
oc apply -f timer-channel-event-source.binding.yaml
```

```shell
oc apply -f channel-event-log-sink.binding.yaml
```

Show logs and see messages consumed

```shell
kamel logs channel-event-log-sink
```

### Kafka

```shell
oc apply -f timer-kafka-event-source.binding.yaml
```

```shell
oc apply -f kafka-event-log-sink.binding.yaml
```

Show logs and see messages consumed

```shell
kamel logs kafka-event-log-sink
```

### Chuck Norris source

```shell
oc apply -f chuck-to-log-sink.binding.yaml
```

Show logs and see messages consumed

```shell
kamel logs chuck-to-log-sink
```

### Webhook source

```shell
oc apply -f webhook-to-log-sink.binding.yaml
```
