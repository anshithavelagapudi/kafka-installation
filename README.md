# kafka-installation
- [Download](https://apache.claz.org/kafka/2.7.0/kafka_2.13-2.7.0.tgz) and copy to C:\
- Open Git Bash here and run 
  - $ tar -xzf kafka_2.13-2.7.0.tgz
  - $ cd kafka_2.13-2.7.0
- Check Environment variables
  - JAVA_HOME = C:\Program Files\OpenJDK\jdk-version folder
  - KAFKA_HOME =  C:\kafka-version folder
  - M2_HOME = C:\ProgramData\chocolatey\lib\maven\apache-maven-version
  - Path - must include (make sure you have only one JDK location in your path!)
    > - %JAVA_HOME%\bin OR C:\Program Files\OpenJDK\jdk-version\bin (or similar, NOT both!)
    > - %M2_HOME%\bin
    > - %KAFKA_HOME%\bin
    > - %KAFKA_HOME%\bin\windows
- Open powershell as admin in C:\Kafka-version(new window for each command)
- Window 1 - Run Zookeeper Service  (keep window open)

> .\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties

- Window 2 - Run Kafka Service (keep window open)

> .\bin\windows\kafka-server-start.bat .\config\server.properties

- Window 3 (temporary) - Execute One-Time Commands - create, list, delete topics 

> .\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic bearcat-messages
> .\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --list

- Window 4 - Run Kafka Producer (will provide a > prompt for writing messages)

> .\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic bearcat-messages

- Window 5 - Run Kafka Consumer (to show messages from the beginning)

> .\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic bearcat-messages --from-beginning
