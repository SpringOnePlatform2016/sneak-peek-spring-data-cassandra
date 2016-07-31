# Spring Data Cassandra Example Application

## Preparation

### Install Cassandra
Before we can start we have to install Cassandra 3.4 or greater, e.g. via brew on Max OS.
```
$ brew install cassandra
```

or download Cassandra from https://www.apache.org/dist/cassandra/

```
$ wget https://www.apache.org/dist/cassandra/3.7/apache-cassandra-3.7-bin.tar.gz
$ tar xzf apache-cassandra-3.7-bin.tar.gz
```

More details can be found here: https://wiki.apache.org/cassandra/GettingStarted

### Start Cassandra
```
/usr/local/bin/cassandra -f 
```

That should be enough to get you started.
Now you can simply type `mvn clean install` to run the example.
