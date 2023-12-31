#### Scenario
A project that aims to de-congest the national highways by analyzing the road traffic data from different toll plazas. As a vehicle passes a toll plaza, the vehicle’s data like vehicle_id,vehicle_type,toll_plaza_id and timestamp are streamed to Kafka. The job is to create a data pipe line that collects the streaming data and loads it into a database.

#### Objectives
In this assignment create a streaming data pipe by performing these steps:

* Start a MySQL Database server.
* Create a table to hold the toll data.
* Start the Kafka server.
* Install the Kafka python driver.
* Install the MySQL python driver.
* Create a topic named toll in kafka.
* Download streaming data generator program.
* Customize the generator program to steam to toll topic.
* Download and customise streaming data consumer.
* Customize the consumer program to write into a MySQL database table.
* Verify that streamed data is being collected in the database table.

#### Exercise 1 

Step 1: Download Kafka.

    wget https://archive.apache.org/dist/kafka/2.8.0/kafka_2.12-2.8.0.tgz

Step 2: Extract Kafka.

    tar -xzf kafka_2.12-2.8.0.tgz

Step 3: Start MySQL server.

        start_mysql

Step 4: Connect to the mysql server, using the command below. Make sure you use the password given to you when the MySQL server starts.
    
    mysql --host=127.0.0.1 --port=3306 --user=root --password=*********

Step 5: Create a database named tolldata.
    At the ‘mysql>’ prompt, run the command below to create the database.
    
    create database tolldata;

Step 6: Create a table named livetolldata with the schema to store the data generated by the traffic simulator.
    Run the following command to create the table:
    

    use tolldata;

    create table livetolldata(timestamp datetime,vehicle_id int,vehicle_type char(15),toll_plaza_id smallint);

This is the table to store all the streamed data that comes from kafka. Each row is a record of when a vehicle has passed through a certain toll plaza along with its type and anonymized id.

Step 7: Disconnect from MySQL server. 

    exit

Step 8: Install the python module kafka-python using the pip command.

    python3 -m pip install kafka-python

This python module will help you to communicate with kafka server. It can used to send and receive messages from kafka.

Step 9: Install the python module mysql-connector-python using the pip command.

    python3 -m pip install mysql-connector-python==8.0.31

This python module will help to interact with mysql server.

Exercise 2 - Start Kafka

Task 2.1 - Start Zookeeper
Start zookeeper server.

Task 2.2 - Start Kafka server
Start Kafka server

Task 2.3 - Create a topic named toll
Create a Kakfa topic named toll

Task 2.4 - Download the Toll Traffic Simulator

Task 2.5 - Configure the Toll Traffic Simulator
Open the toll_traffic_generator.py and set the topic to toll.

Task 2.6 - Run the Toll Traffic Simulator
Run the toll_traffic_generator.py.

Task 2.7 - Configure streaming_data_reader.py

Open the streaming_data_reader.py and modify the following details so that the program can connect to your mysql server.
* TOPIC
* DATABASE
* USERNAME
* PASSWORD

Task 2.8 - Run streaming_data_reader.py

Run the streaming_data_reader.py

    python3 streaming_data_reader.py

Task 2.9 - Health check of the streaming data pipeline.
The streaming toll data would get stored in the table livetolldata.

List the top 10 rows in the table livetolldata.