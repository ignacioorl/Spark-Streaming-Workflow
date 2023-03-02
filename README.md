# Spark-Streaming-Workflow

As part of a proof of concept, this notebook tries to create two tables that will be useful for the Transport for London (TFL):

1. Alarm Table: The Underground system works with a rigorous schedule, which must be respected to successfully respond to the huge demand of users (arround 1.8 millions daily). In this line, the "Alarm Table" will be able to show if a particular vehicle presents a delay. As it will be updated every two minutes and a half, this high frequency will allow the responsibles of keeping track to act quickly, increasing the probability of success.
2. Frequency Table: Transport for London does not recieve a constant demand through the entire day, and the Underground system is not an exception. There are clearly hours of high people's waves (8 am - 10 am) while in other moments the demand is quite low (10 pm - 1 am). That is why we see different frequencies depending on the time of the day. Keeping a track of this is crucial for the good behaviour of the subway and this is what the "Frequency Table" aims to tackle. If we constantly show these numbers, the responsibles can act quickly if they see that something is not correct, disminuishing the impact of any unexpected event.

The whole architecture for this streaming process, follows the below steps:

1. NiFi connects to the API of TFL. After some changes, it sends the JSONs files into Kafka.
2. From Kafka, Spark Streaming will grab the files and create the final tables.
