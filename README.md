<img src="https://github.com/AlienOneSecurityLLC/vagrant-kafka/blob/master/images/Kafka-Zookeeper-Pub-Sub.png" alt="hi" class="inline"/>

## E-SIEM Project Dev/Test Data Pipeline
=========================

### Vagrant Kafka/Zookeeper 
=============
#### Vagrant Configuration: 5 VMs Total 
    + CentOS 7.3 VMs
    + Three Apache Zookeeper Quorum (Replicated ZooKeeper)
    + Three Confluent Kafka Brokers 
    + JDK 8u112
    + Kafka 0.10.1.1-1
    + Scala 2.11
    + Zookeeper 3.4.9 
    + One Logstash 5.2.1 Node 
    + One ArcSight Smart Connector 7.3.0.7886.0 Node 

##### Prerequisites - Install the following prerequisites 
-------------------------
+ [Vagrant](https://www.vagrantup.com/downloads.html)
+ [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

##### Install Some Useful Vagrant Plugins
-------------------------

```
vagrant plugin install vagrant-cachier
vagrant plugin install vagrant-hostmanager

```

#### Setup
-------------------------
```
git clone https://github.com/AlienOneSecurityLLC/SnowBlossom.git
git pull
cd SnowBlossom/vagrant-confluent-rhel-73
for i in $(vagrant global-status|grep virtualbox|awk '{ print $1 }');do vagrant destroy $i;done
rm -rf .vagrant 
vagrant up --provider virtualbox
```
#### Node Setup 
--------------------------
```
rpm -qal kafka | less
rpm -qal zookeeper | less
```

#### VM Mappings & IP Addresses:
--------------------------

| Name        | Address   | 
|-------------|-----------|
|zkafka1      | 10.30.3.2 | 
|zkafka2      | 10.30.3.3 |
|zkafka3      | 10.30.3.4 |
|logstash1    | 10.30.3.5 |
|connector1   | 10.30.3.6 |


#### Unit Status Test 
-------------------------

+ Test all VM nodes are in state RUNNING 

```
vagrant status
```

```
Current machine states:

zkafka1                running (virtualbox)
zkafka2                running (virtualbox)
zkafka3                running (virtualbox)
logstash1              running (virtualbox)
connector1             running (virtualbox)


This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run 'vagrant status NAME''.
```

#### Apache Zookeeper 
---------------------------
+ [Apache Zookeeper](https://zookeeper.apache.org/doc/r3.4.9/)

#### Confluent Platform
---------------------------
+ [Confluent Platform](http://docs.confluent.io/3.2.0/)

+ [Confluent Kafka Security](http://docs.confluent.io/3.2.0/kafka/security.html)

+ [Confluent Kafka Schema Registry](http://docs.confluent.io/3.2.0/schema-registry/docs/index.html)

+ [Confluent Kafka REST Proxy](http://docs.confluent.io/3.2.0/kafka-rest/docs/index.html)

+ [Confluent Kafka Streams](http://docs.confluent.io/3.2.0/streams/index.html)

+ [Confluent Kafka Client Libraries](http://docs.confluent.io/3.2.0/clients/index.html)

+ [Confluent Kafka Connect](http://docs.confluent.io/3.2.0/connect/index.html)

#### Elastic Logstash
--------------------------
+ [Logstash 5.2.1](https://www.elastic.co/guide/en/logstash/current/getting-started-with-logstash.html)

#### ArcSight Smart Connector
--------------------------
+ [Smart Connectors](https://www.protect724.hpe.com/community/arcsight/productdocs/connectors)
