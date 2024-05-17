# AWS_Snowflake_pipeline
 ## Data pipeline which interacts with AWS and snowflake using the astro SDK

### First step is to create a snowflake account
### The following database,warehouse,schema and tbales need to be created in snowflake via a sql worksheet

```
CREATE DATABASE ASTRO_SDK_DB;

CREATE WAREHOUSE ASTRO_SDK_DW;

CREATE SCHEMA ASTRO_SDK_SCHEMA;


CREATE OR REPLACE TABLE customers_table (customer_id CHAR(10), customer_name VARCHAR(100), type VARCHAR(10) );

INSERT INTO customers_table (CUSTOMER_ID, CUSTOMER_NAME,TYPE) VALUES ('CUST1','NAME1','TYPE1'),('CUST2','NAME2','TYPE1'),('CUST3','NAME3','TYPE2');


CREATE OR REPLACE TABLE reporting_table (
CUSTOMER_ID CHAR(30), CUSTOMER_NAME VARCHAR(100), ORDER_ID CHAR(10), PURCHASE_DATE DATE, AMOUNT FLOAT, TYPE CHAR(10));

INSERT INTO reporting_table (CUSTOMER_ID, CUSTOMER_NAME, ORDER_ID, PURCHASE_DATE, AMOUNT, TYPE) VALUES
('INCORRECT_CUSTOMER_ID','INCORRECT_CUSTOMER_NAME','ORDER2','2/2/2022',200,'TYPE1'),
('CUST3','NAME3','ORDER3','3/3/2023',300,'TYPE2'),
('CUST4','NAME4','ORDER4','4/4/2022',400,'TYPE2');
```

### Next would be createa  aws account ans store the below csv file in a s3 bucket

```
order_id,customer_id,purchase_date,amount
ORDER1,CUST1,1/1/2021,100
ORDER2,CUST2,2/2/2022,200
ORDER3,CUST3,3/3/2023,300

```

### Install the asto cli by referring the doc link :->([GitHub Pages](https://docs.astronomer.io/astro/cli/get-started-cli))

### once astro env is set up create connection to snowflake and aws via airflow and test them
![](https://github.com/ansel9618/AWS_Snowflake_pipeline/blob/main/images/7.0_%20(2).png)
![](https://github.com/ansel9618/AWS_Snowflake_pipeline/blob/main/images/8.0_%20(2).png)
![](https://github.com/ansel9618/AWS_Snowflake_pipeline/blob/main/images/6.0_.png)

### Dag to be created

![](https://github.com/ansel9618/AWS_Snowflake_pipeline/blob/main/images/10.0_.png)
** refer code :- astro_orders_airflowcode.py


### Dag Execution and output

![](https://github.com/ansel9618/AWS_Snowflake_pipeline/blob/main/images/10.0_.png)
![](https://github.com/ansel9618/AWS_Snowflake_pipeline/blob/main/images/output.png)





  
