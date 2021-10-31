---
layout: post
title: Using SQL in Different Programming Languages
author: tunasaladx
post-image: /assets/images/blogimages/figs-10-12/newTitlePic.png
description: Ways to perform SQL queries on data that's already been imported. 
tags:
- SQL
- Data cleaning
- Programming languages
---

SQL, short for Structured Query Language, is a programming language used for database management. 
It's language was standardized around the time the first personal computers were being released, and
since then it's continued to be used for managing most large datasets. While many people are familiar with
using SQL to query data warehouses, there are ways to take advantage of its language in other programming
applications. 

![MySQL](/assets/images/blogimages/figs-10-12/mysql.jpeg)

## Using SQL through a database

When someone uses SQL, they're usually using it to query a database. Most database management engines, such
as MySQL, PostgreSQL, SQLite, Oracle, and Microsoft Access each use SQL to perform their queries. APIs
for databases also often use SQL. Although some specifics may vary from program to program, the overall
language tends to be very standardized. For example, the following query will return the petal length
of every setosa in the "iris" dataset: 

```sql
SELECT Petal_Length FROM iris WHERE Species = setosa
```

If you're pulling data directly from a data warehouse, you can typically use queries like this to format 
and filter the data so you only download what you need. However, sometimes you are obtaining the data
from another source, such as a csv file. Most of these files will need some sort of data cleaning, and 
while the language you're using likely has methods for this cleaning built in, the queries provided by
SQL might seem like a desirable alternative. Thankfully, most programming languages have some way to
perform SQL queries on data that's already been imported. 

## SQL in Python: pandasql

In Python, the [pandasql](https://pypi.org/project/pandasql/) package lets you query pandas dataframes
as if they were in your data warehouse, and will return another pandas dataframe. The `sqldf` method
in the package requires two arguments. The first argument is a string containing the query you want to
submit, while the second indicates whether the dataframe you want to query is in `locals()` or `globals()`.
Running the method will perform that query, returning a dataframe. 

```python
from pandasql import sqldf
setosaPetals = sqldf("SELECT Petal_Length FROM iris WHERE Species = setosa", globals())
```
If you're doing several queries in one program, it may be tedious to include `locals()` or `globals()` in
every instance. In that case, you can define a function to include it for you:

```python
from pandasql import sqldf
pysqldf = lambda q: sqldf(q, globals())
setosaPetals = pysqldf("SELECT Petal_Length FROM iris WHERE Species = setosa")
```

## SQL in R: sqldf

The [sqldf](https://www.rdocumentation.org/packages/sqldf/) package in R is very similar to the pandasql 
package in Python. Because R doesn't use methods and doesn't typically distinguish between 
local and global variables, sqldf takes less code than pandasql. Otherwise, they are essentially the
same; simply input a string query, and it will be run on the specified data frame so long as it's been
defined in your local environment. 

```splus
library(sqldf)
setosaPetals <- sqldf("SELECT Petal_Length FROM iris WHERE Species = setosa")
```

## SQL in SAS: PROC SQL

Another programming language you may wish to use SQL in is SAS. SAS is set up quite differently than
most other programming languages, since it's already very focused on manipulating tables. In fact, a
method of manipulating tables using SQL is built in to SAS! 

The 
[PROC SQL](https://documentation.sas.com/doc/en/pgmsascdc/9.4_3.5/sqlproc/n1lhnlzhrmrqggn1rz570u89oq2m.htm)
step works similarly to other `proc` steps, but with a few differences. Most notably, you need to end your 
step with `quit;` instead of `run;`. Otherwise, simply input your query as a single statement to send the
result to your output: 

```sas
PROC SQL;
  SELECT Petal_Length FROM iris 
  WHERE Species = setosa;
QUIT;
```

If you'd rather send the query results to another table, simply start the query with `create table`
followed by the name of the new table:

```sas
PROC SQL;
  CREATE TABLE setosaPetals AS
  SELECT Petal_Length FROM iris 
  WHERE Species = setosa;
QUIT;
```

## Conclusion

SQL queries are a versatile tool for manipulating data from data warehouses, but that's not their only
usage. Even if you already have data loaded into your environment, you can often perform queries on that
data. While other tools exist that can reshape the data into what you need, SQL is a simple and 
consistent tool that can be used in many different programs.  
