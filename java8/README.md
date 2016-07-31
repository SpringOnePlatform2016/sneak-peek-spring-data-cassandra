# Spring Data Cassandra - Java 8 examples

This project contains samples of Java 8 specific features of Spring Data (Cassandra).

## Support for JDK 8's `Stream` for repository methods

Repository methods can use a Java 8 `Stream` as a return type which will cause the reading of the results and the to-object-conversion of rows to happen while iterating over the stream.

```java
public interface PersonRepository extends CrudRepository<Person, String> {

  @Override
  List<Person> findAll();

  //Custom Query method returning a Java 8 Stream
  @Query("SELECT * FROM person")
  Stream<Person> findAllByCustomQueryWithStream();
}
```

The test cases in `PersonRepositoryIntegrationTest` oppose a plain `List` based query method with one that uses a `Stream` and shows how the former pulls all data into memory first and the iteration is done over the pre-populated list. The execution of the `Stream`-based method in contrast shows that the individual elements are read and converted while iterating the stream.

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
