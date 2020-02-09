## Broker起動
```
kafka-server-start conf/server-1.properties
kafka-server-start conf/server-2.properties
```

## Topic作成
```
kafka-topics --create --zookeeper localhost:2181 --replication-factor 2 --partitions 3 --topic mytopic

kafka-topics --zookeeper localhost:2181 --describe --topic my-topic

## producer
kafka-console-producer --broker-list localhost:9093 --topic my-topic

## consumer
kafka-console-consumer --bootstrap-server localhost:9093 --topic my-topic --from-beginning --partition 0

kafka-console-consumer --bootstrap-server localhost:9093 --topic my-topic --from-beginning --partition 1

kafka-console-consumer --bootstrap-server localhost:9093 --topic my-topic --from-beginning --partition 2
```

## フェールオーバー
```
## after kill the process of broker.id=1, check the consumers
kafka-console-producer --broker-list localhost:9093 --topic my-topic

## recover the broker
kafka-server-start conf/server-1.properties
```