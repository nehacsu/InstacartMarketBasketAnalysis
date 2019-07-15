## About the Project 
This project is based on Insta cart data set. The data source is https://www.kaggle.com/c/instacart-market-basket-analysis/data. As this was a huge data set consisting of 3 million orders. There were around 10 products in one order, so the total rows the order file was around 30 million. So, I connected this file to Oracle database and then access the data set with the help of SQL queries. The results were visualized using matplotlib liabrary of the python. This dataset consist of the below files.
## Data Description
### Aisles.csv
Aisle id and the name of the aisle
### Department.csv
Department name and its corresponding id.
### Products.csv
Product id, Product name and its corresponding department and aisle
### Orders.csv
Orderid, userid, odernumber, which day of the week order was place and which hour of the day it was placed.
### Order_Product table
Details of 3 million orders, One order was having approximate 10 product in it.
## Data Source
https://drive.google.com/open?id=1WR4EFPZlpuGl-POy8ddGV8Tg8Ruc599H

## How to set up Oracle connection through Python 
```
import cx_Oracle
connection = cx_Oracle.connect('<User name>/<Password>')
cursor = connection.cursor()
```
## Why there was a need of Oracle connection to Python
The data files used in this project are quite large. The Orders.csv file contains 30 million rows. I found Excel to be inefficient in opening such a large data set file. Then I tried reading the files directly through Python; but Python was also not able to read such a large file at a time. So I pushed all the data files to the Oracle Server and then analyzed the data through SQL queries. 

## How to push data files to SQL server- Demo for Aisle Table 
#### For the demo purpose we have kept the limit. As this data set is very large it will take a lot of time to upload it into Oracle data base.
## Create aisle table
```
try:
    query_String = "drop table aisles_t cascade constraints"
    cursor.execute(query_String)
    print "dropped"
except:
    print "already dropped"
    
try:
    query_String="Create table aisles_t (aisles_id number not null,aisles varchar(50),constraint aisles_id_PK PRIMARY KEY (aisles_id))"
    cursor.execute(query_String)
    print"Table created"
except:
    print"Table already there"

cursor.execute("commit")
```

## Insert data into aisles table
```
import csv
with open('aisles.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    count=0
    for row in csv_reader:
        if count==0:
            count=1
            continue
        query_String="Insert into aisles_t(aisles_id,aisles) values(" + row[0] + "," + "'" + row[1]+ "'" +")"
        cursor.execute(query_String)
        count=count+1
cursor.execute("commit")
print "Number of successful records are "+str(count)
```
