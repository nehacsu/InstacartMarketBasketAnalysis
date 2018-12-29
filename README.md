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

## How to push data files to SQL server
Read each file 
