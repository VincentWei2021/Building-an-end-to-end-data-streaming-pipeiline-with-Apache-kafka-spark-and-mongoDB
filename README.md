# Data-streaming-with-Apache-kafka-spark-and-mongoDB
This project involves building an end to end data streaming pipeline with the use of APIs, Apache kafka, Spark and MongoDB as a document store and visualised with streamlit dashboard all together packaged in a docker enviroment with individual docker containers running.

# Introduction
A data set gotten from kaggke was used. The data set in CSV format was first transformed into  json format. A python script (input client) was used to
ingest the data into the API. Postman was used for testing. Kafka, Spark and MongoDB was hosted as a docker container. The API takes data and writes it into a Kafka topic where messages are buffered and processed with Spark. A jupyter notebook was created for Spark to listen to Kafka and takes Data out of Kafka, process it and store it into MongoDB. Streamlit was us used to access data from MongoDB and also visualize the data.
