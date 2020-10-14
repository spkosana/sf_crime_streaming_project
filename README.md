
# Beginning the Project
 This project requires creating topics, starting Zookeeper and Kafka servers, and your Kafka bootstrap server. You’ll need to choose a port number (e.g., 9092, 9093..) for your   Kafka topic, and come up with a Kafka topic name and modify the zookeeper.properties and server.properties appropriately.

# Local Environment
 Install requirements using ./start.sh if you use conda for Python. If you use pip rather than conda, then use pip install -r requirements.txt.

 Use the commands below to start the Zookeeper and Kafka servers. You can find the bin and config folder in the Kafka binary that you have downloaded and unzipped.

   bin/zookeeper-server-start.sh config/zookeeper.properties
   bin/kafka-server-start.sh config/server.properties
 
   You can start the bootstrap server using this Python command: python kafka_server.py.

# Step 1
 The first step is to build a simple Kafka server and Complete the code for the server in producer_server.py and kafka_server.py.
 
# Local Environment
 To see if you correctly implemented the server, use the command bin/kafka-console-consumer --bootstrap-server localhost:<your-port-number> --topic <your-topic-name> --from-       beginning to see your output.
  
# Step 2
Apache Spark already has an integration with Kafka brokers, so we would not normally need a separate Kafka consumer. However, create one anyway. Why? it will be good to create the consumer to demonstrate your understanding of creating a complete Kafka Module (producer and consumer) from scratch. In production, you might have to create a dummy producer or consumer to just test out your theory and this will be great practice for that.

 Implement all the TODO items in data_stream.py

# Do a spark-submit using this command: 

spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.4 --master local[*] data_stream.py.
  
  Check the progress reporter after executing a Spark job.
  
  Check the Spark Streaming UI as the streaming continues.
  
# Step 3

Write the answers to these questions in the README.md doc of your GitHub repo:

### How did changing values on the SparkSession property parameters affect the throughput and latency of the data?
    
processedRowspersecond parameter is the conroller of sparksession properties. High through put and low latency of the data is achieved by setting high number in spark.conf.set which increases the processing rows per sec. 

What were the 2-3 most efficient SparkSession property key/value pairs? Through testing multiple variations on values, how can you tell these were the most optimal?
    
* Processing efficiency should be in iterative way, which involes amount of data that is flowing through and further analysis needed as per the different scenarios.
*Infrastructure also plays a vital role when comming to processing the data such as number of node and cores for each node which is useful for scaling and also helpful in processing more number of records in less time.
* Number of Unprocessed messages can be prevented by setting the maximum rate for each partition which is controlled by maxRatePartition. This is used to make streaming process efficient

