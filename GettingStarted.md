# Getting Started #

This SerDe can be used to read data in JSON format. For example, if your JSON files had the following contents:
```
{"field1":"data1","field2":100,"field3":"more data1","field4":123.001}
{"field1":"data2","field2":200,"field3":"more data2","field4":123.002}
{"field1":"data3","field2":300,"field3":"more data3","field4":123.003}
{"field1":"data4","field2":400,"field3":"more data4","field4":123.004}
```

The following steps can be used to read this data:

  1. Build this project using `ant clean build`
  1. Copy `hive-json-serde.jar` to the Hive server
  1. Inside the Hive client, run
```
       ADD JAR /path-to/hive-json-serde.jar;
```
  1. Create a table that uses files where each line is JSON object
```
       CREATE EXTERNAL TABLE IF NOT EXISTS my_table (
          field1 string, field2 int, field3 string, field4 double
       )
       ROW FORMAT SERDE 'org.apache.hadoop.hive.contrib.serde2.JsonSerde'
       LOCATION '/path-to/my_table/';
```
  1. Copy your JSON files to `/path-to/my_table/`. You can now select data using normal SELECT statements
```
       SELECT * FROM my_table LIMIT 10;
```

The table does not have to have the same columns as the JSON files, and vice-versa. If the table has a column that does not exist in the JSON object, it will have a NULL value. If the JSON file contains fields that are not columns in the table, they will be ignored and not visible to the table.

Please remember that columns names in Hive are case-insensitive, so a JSON object with two field names "field1" and "FiElD1" will match the same column.