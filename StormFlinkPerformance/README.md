#Overview
This task will test several areas
* Your ability to use Docker and set up Kafka (DevOps)
* Your ability to learn and use Storm or Flink (Java)
* Your ability to analyze performance (Performance analysis)
* Your ability to use a git workflow (Version Control)
* Your ability to automate running/building (Automation)

#Prerequisites
* Python 2.7 (Other versions may worked, but script was tested on 2.7)
* pip
* Java 7
* Eclipse

#Working/Sharing
* Fork this repo into your own git repo
* Make this repo PRIVATE
* Give read access to smorin and kingofpoptart to this repo
* Check your code into your repo, this is how we will share and look at your code during your demo

#Setup Requirements
* Set up docker on your local machine
  * https://docs.docker.com/installation/
* Create a docker container running a single node kafka instance
* Feel free to tweak the Kafka configuration

#Send avro data to Kafka 
```
sudo ./setup.sh
python KafkaGenerator.py -q

#For full usage details
$ python KafkaGenerator.py -h
usage: KafkaGenerator.py [-h] [-m M] [-k K] [-t T] [-v] [-q]

Push Avro messages into Kafka

optional arguments:
  -h, --help            show this help message and exit
  -m M, -maxMessages M  max number of avro messages to write to kafka
  -k K, -kafkaConnect K
                        Kafka connect string
  -t T, -topic T        Kafka topic
  -q, -quiet            Disable output to stdout
```


#Programming assignment (Java)
* You will choose **one** of the following:
  * Create a Storm topology
  * Create a flink stream
* Set up your project in Eclipse
* Use the KafkaGenerator python script to push data into Kafka
* **Option 1**: Create a Storm topology to move data out of the "neverwinter" topic in Kafka
  * https://storm.apache.org/
  * The data will be read from the topic "neverwinter"
  * Storm will write the data back into Kafka to three topics based on the field in avro called "random"
    * Messages with the "random" field set to "1" will be moved to topic "random1"
    * Messages with the "random" field set to "2" will be moved to topic "random2"
    * Messages with the "random" field set to "3" will be moved to topic "random3"
* **Option 2** : Perform the same task as above using Flink
  * https://flink.apache.org/
* Verification - Within your Storm/Flink solutions:
  * Verify that all the records have made it to the topics "random[1-3]"
  * Verify that all the records have made it to the correct topic
* Include metrics in your code
  * Determine the throughput of your system in bytes/second
  * Determine the rate of records/second
* Automation
  * Building and running should be automated and simple

#And then...
* You will present your solution to the nvent team
* You will need to explain your solution
* You will need to explain how to build and run your code
* You will need to explain your performance and verification findings
* You will need to run a live demo of your code working
