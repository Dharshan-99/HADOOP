# HADOOP
Using SQOOP to export table from Hive external table to Mysql

NOTE:This is based on CLOUDERA.
**********************************************
Open cloudera and change directory to hadoop Location

```

cd /etc/hadoop/

```
Move file from local wheather it may be a txt file or csv file

```
Hdfs dfs -copyFromLocal /location/of/file

```
Then create external table in hive to move the file.
```
create table tablename
    ( colname string,
     colname int,
     colname int,
     colname int,
    )
     row format delimitedl
     fields terminated by ',';
     
  ```
  Then methion the path for the file in HDFS
  
  ```
  load data inpath '/location/file.txt' into table tablename;
  
  ```
  See wheather the data is upload in the hive table by the following comment.Same as the sql comment✨
  
  ```
  select * from tablename;
  ```
Once the above step is completed........
Then move to mysql to create table

```
mysql -u root -p

```

Create table with the same columns as we created in in hive. 
```
CREATE TABLE tablename(colname datatype,colname2 datatype);

```
And finally move to sqoop..to transfer data from hive to sqoop

```
sqoop export
--connect jdbc:mysql://localhost/databasename 
--driver com.mysql.jdbc.Driver 
--username root 
--password cloudera 
--table  tablename in sql
--hcatalog-table tablename in hive 
--input-fields-terminated-by '|' 
--input-lines-terminated-by '#'
```
#Note:In cloudera use the username & password as root & cloudera.It may change according to your use.



