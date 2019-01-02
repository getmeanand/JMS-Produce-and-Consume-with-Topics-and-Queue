# JMS-Produce-and-Consume-with-Topics-and-Queue

Run and check results
– Start ActiveMQ server with commandline: C:\apache-activemq-5.14.5>.\bin\activemq start.
– Build and Run the SpringBoot applications by commandlines: {mvn clean install, mvn spring-boot:run} with the following order:

Enable one active subscriber
– Start an instance of SpringBoot Subcriber on ActiveMQ topic: jsa-topic
– Then start an instance of SpringBoot Publiser.

-> We receive 2 Company messages {apple, samsung}. See the subscriber’s console logs:


Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}

Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}

Enable two active subcribers
Again, we start another instance of SpringBoot Subcriber on ActiveMQ topic: jsa-topic.
-> Now having 2 active subcribers on jsa-topic topic.

Start the SpringBoot Publiser application again for sending messages.

-> Results: we receive 2 new Company messages for each Subcribers.
So with the first Subcriber, it had recieved total 4 Company messages:


Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}
Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}

Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}
Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}

 
And with the second Subcriber (the newer), it had recieved 2 Company messages:


Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}
1
2
Recieved Message: {"name":"Apple","products":[{"name":"Iphone 7"},{"name":"IPadPro"}]}
Recieved Message: {"name":"Samsung","products":[{"name":"Galaxy S8"},{"name":"Gear S3"}]}


https://grokonez.com/java-integration/activemq-work-spring-jms-activemq-topic-publisher-subcribers-pattern-using-springboot
