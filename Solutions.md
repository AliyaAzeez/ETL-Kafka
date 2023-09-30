
Exercise 2 - Start Kafka (start_zookeeper.jpg)

Task 2.1 - Start Zookeeper

```
cd kafka_2.12-2.8.0

bin/zookeeper-server-start.sh config/zookeeper.properties
```

Task 2.2 - Start Kafka server (start_kafka.jpg)

```
cd kafka_2.12-2.8.0

bin/kafka-server-start.sh config/server.properties
```

Task 2.3 - Create a topic named toll (create_toll_topic.jpg)
```
cd kafka_2.12-2.8.0

bin/kafka-topics.sh --create --topic toll --bootstrap-server localhost:9092
```

Task 2.4 - Download the Toll Traffic Simulator using 
`wget ` (download_simulator.jpg)

Task 2.5 - Configure the Toll Traffic Simulator (configure_simulator.jpg)
Open the toll_traffic_generator.py and set the topic to toll.

` TOPIC = 'toll'`

Task 2.6 - Run the Toll Traffic Simulator (simulator_output.jpg)
Run the toll_traffic_generator.py.

`python3 toll_traffic_generator.py`

Task 2.7 - Configure streaming_data_reader.py (streaming_reader_code.jpg)

Open the streaming_data_reader.py and modify the following details so that the program can connect to your mysql server.
* TOPIC
* DATABASE
* USERNAME
* PASSWORD

```
TOPIC = 'toll'
DATABASE = 'tolldata'
USERNAME = 'root'
PASSWORD = '**********'
```

Task 2.8 - Run streaming_data_reader.py(data_reader_output.jpg)

`python3 streaming_data_reader.py`

Task 2.9 - Health check of the streaming data pipeline.
The streaming toll data would get stored in the table livetolldata. (output_rows.jpg)

```
select * from livetolldata limit 10;
```
