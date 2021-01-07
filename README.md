# Getting Started with Amazon Athena

![Powered by Jupyter Logo](https://cdn.oreillystatic.com/images/icons/powered_by_jupyter.png)

This project contains the Jupyter Notebooks and supporting files for _Getting Started with Amazon Athena_ with Sunny Srinidhi. 

These notebooks can be run on the O'Reilly Learning Platform [here](https://learning.oreilly.com/jupyter-notebooks/~/${NOTEBOOK_FPID}).

It contains both the exercises (/notebooks), possibly the solutions (/solutions), as well as any data or files needed (/data). If you are familiar with docker, there is also a dockerfile included for your convenience. 

This is a public repository so there is no need to create an account to download its contents. To download the source code from this page, click the 'Cloud' icon on the top right hand, above where the latest commit is detailed.

To download via git from your preferred terminal application, type:

```git clone https://resources.oreilly.com/binderhub/getting-started-with-amazon-athena```


# Schema of the sample data

```sh
Transaction_date string, Product string, Price int, Payment_Type string, Name string, City string, State string, Country string, Account_Created string, Last_Login string, Latitude float, Longitude float, US_Zip bigint
```

# Create ```External Table``` Cable Command for Athena

```sql
CREATE EXTERNAL TABLE `sales`(
  `transaction_date` string, 
  `product` string, 
  `price` int, 
  `payment_type` string, 
  `name` string, 
  `city` string, 
  `state` string, 
  `country` string, 
  `account_created` string, 
  `last_login` string, 
  `latitude` float, 
  `longitude` float, 
  `us_zip` bigint)
ROW FORMAT DELIMITED 
  FIELDS TERMINATED BY ',' 
STORED AS INPUTFORMAT 
  'org.apache.hadoop.mapred.TextInputFormat' 
OUTPUTFORMAT 
  'org.apache.hadoop.hive.ql.io.HiveIgnoreKeyTextOutputFormat'
LOCATION
  's3://test-bucket-nv/getting_started_with_athena'
TBLPROPERTIES (
  'has_encrypted_data'='false', 
  'transient_lastDdlTime'='1609994120')
```