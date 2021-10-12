# odsl-camel-kafka
An example of sending messages from OpenDataDSL queues to an internal Kafka topic

## Tutorial
See [ODSL Tutorial](https://opendatadsl.com/docs/tutorials/gettingstarted1)

## Configuration
There are 3 configuration items that need to be set

### application.yml
Replace the azure.connection with your queue connection string 

```yml
azure:
  connection: Endpoint=sb://sb-odsl.servicebus.windows.net/;
```

Replace the kafka.connection with your Kafka broker connection string
```yml
kafka:
  connection: localhost:29092
```

### routing.xml
Replace the word `company` with your assigned company tenant id

```xml
        <from uri="azureServiceBus:prod/company/tutorial" />
```

### Kafka Configuration
You will also need to add a topic to Kafka called ecb_fx, or else change the routing to the name of the topic you want to send the messages to in the routing.xml file

```xml
        <to uri="kafka:ecb_fx" />
```


## Running
Once all the configuration is complete, you can run this project with:

```
mvn spring-boot:run
```
