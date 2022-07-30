# Building an end to end ETL data-streaming-with-Apache-kafka-spark-and-mongoDB
This project involves building an end to end data streaming pipeline with the use of APIs, Apache kafka, Spark and MongoDB as a document store and visualised with streamlit dashboard all together packaged in a docker enviroment with individual docker containers running.

# Introduction
A data set gotten from [kaggle] (https://www.kaggle.com/datasets/carrie1/ecommerce-data) was used. The data set in CSV format was first transformed into  json format. A python script (input client) was used to
ingest the data into the API. Postman was used for testing. Kafka, Spark and MongoDB was hosted as a docker container. The API takes data and writes it into a Kafka topic where messages are buffered and processed with Spark. A jupyter notebook was created for Spark to listen to Kafka and takes Data out of Kafka, process it and store it into MongoDB. Streamlit was us used to access data from MongoDB and also visualize the data.

# Getting started
The data was downloaded and transformed into the JSON data frame format using some python functions on transformer.py folder, and data is read into an output.txt file.

# Api Ingest
Two APIs were created. A root API (hello world) was first created to test if the API actually work,  Get and Post to put the data into the invoice item part.
![code img](https://user-images.githubusercontent.com/41475769/181742396-1a740e7c-754d-4a13-9109-420f3b384575.PNG)
![hello img](https://user-images.githubusercontent.com/41475769/181742437-6359a6ea-5444-4afd-81bc-d5bc2dbb1f8e.PNG)



# Testing
Postman was used for testing the API. Data was written into postman and request was sent. response 201 gotton means API is working.


![Capture](https://user-images.githubusercontent.com/41475769/179740551-29cac2b6-1c7b-4141-8743-9dbabe5d1acd.PNG)

# Starting up kafka
A docker-compose file for kafka was created and run in the docker network. Kafka producer, consumer and local injestion topics was created and enabled.
kafka producer was used to enable the topics and tested with postman where consumer received the data.
![ingestion topic 1](https://user-images.githubusercontent.com/41475769/181745863-bb98e1a9-4ad8-4468-a41e-793aee17294c.PNG)
kafka consumer
![kafka created topic](https://user-images.githubusercontent.com/41475769/181747945-8bb4d533-086e-47e0-925c-88922c132963.PNG)
testing kafka with postman
![kafka postman](https://user-images.githubusercontent.com/41475769/181748148-d27f3d13-124f-479c-ada0-135d339554ae.PNG)



# Ingesting and deploying API in docker container
A dockerfile and requirement.txt file was created to build the image API inside docker enviroment. The  Local consumer topic was sterted, request was sent to postman again, the invoice data was sent and wirking successfully.
testing api-ingest with postman
![api-ingest img2](https://user-images.githubusercontent.com/41475769/181863994-30c7c4d8-ed94-4aff-850f-10c1bda98fbd.PNG)
![api-ingest 3](https://user-images.githubusercontent.com/41475769/181863974-47489fae-4e2f-4bf2-bfcd-20082341357d.PNG)


# Setting up Apache Spark for connecting to Kafka (Apache Spark Config)
A docker-compose file that combines Kafka and Spark (with jupyter notebook interface) was created to run in a single network.
Jupyter notebook was used to stream data from kafka to spark
![Capture](https://user-images.githubusercontent.com/41475769/179778470-56cff29e-58ac-4561-95bb-b9a8c7a89ded.PNG)
the spark session was used to load data and postman was also used to test the API.

# Setting up MongoDB
A docker-compose file that combines Kafka, Spark and MongoDB was created to run on a single network, to send each message to MongoDB. MongoDB was choosen because it is the best and most used when working with Document stores (JSON documents).







