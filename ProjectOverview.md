# Overview #

[Hive](http://hadoop.apache.org/hive/) ([wiki](http://wiki.apache.org/hadoop/Hive)) is a fantastic addition to [Hadoop](http://hadoop.apache.org/). From Hive's website:

> Hive is a data warehouse infrastructure built on top of Hadoop that provides tools to
> enable easy data summarization, adhoc querying and analysis of large datasets data stored
> in Hadoop files. It provides a mechanism to put structure on this data and it also
> provides a simple query language called Hive QL which is based on SQL and which enables
> users familiar with SQL to query this data. At the same time, this language also allows
> traditional map/reduce programmers to be able to plug in their custom mappers and
> reducers to do more sophisticated analysis which may not be supported by the built-in
> capabilities of the language.

Unfortunately, as at the time of writing, Hive is unable to read and write data in [JSON](http://www.json.org/) format.

To remedy this, I have created a JSON SerDe available here as source or as a JAR file you can add (See [GettingStarted](GettingStarted.md)).

The JSON library I used is the standard Java one found at [json.org](http://www.json.org/java/index.html).

# Limitations #

At the present time, the SerDe has the following limitations:
  * Cannot be used to write JSON files (need to implement Serialization: [Issue #1](https://code.google.com/p/hive-json-serde/issues/detail?id=#1))
  * Limited support for complex tables/JSON files ([Issue #2](https://code.google.com/p/hive-json-serde/issues/detail?id=#2))