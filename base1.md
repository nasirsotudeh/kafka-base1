

## at fisrt run ''' docker-compse up kafka_cluster '''

this command run our cluster


## next pass the app file to toturial 
``` docker run --rm -it -v "$(pwd)":/toturial --net=host landoop/fast-data-dev bash ```

## make topic demo-1-standalone with partition and replication-factor and zookeeper
fast-data-dev / $ 
``` kafka-topics --create --topic demo-1-standalone --partitions 3 --replication-factor 1 --zookeeper 127.0.0.1:2181 ```

# topics demo-2-destributed with partition
## can make  and replication-factor and zookeeper
kafka-topics --create --topic demo-2-destributed --partitions 3 --replication-factor 1 --zookeeper 127.0.0.1:2181
## properties :
```  
name=file-stream-demo-destrbuted
connector.class=org.apache.kafka.connect.file.FileStreamSourceConnector
tasks.max=1


file=demo-file.txt
topic=demo-2-destributed
      
key.converter=org.apache.kafka.connect.json.JsonConverter
key.converter.schemas.enable=true
value.converter=org.apache.kafka.connect.json.JsonConverter
value.converter.schemas.enable=true ```
cd to demo

## make workers serve app
``` connect-standalone worker.properties file-stream-demo-standalone.properties ```





