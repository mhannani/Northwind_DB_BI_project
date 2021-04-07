# Data warehouse design of Northwind database

Design a data warehouse of Northwind database. And use business analysis to get useful information.

#### 1. Design of the logical and dimensional schema of the data warehouse / data mart (MySQL / MySQLWorkbench) :
+ #### 1.1. Analysis of business drivers and business objectives:
    <p style=" font-size:13.2pt;">
    Identify the factors that drive the business, these factors that change, affect the company in some manner.
    Thus they play a vital role in business decision, which may in turn give rise to more business requirements,
    and thus called business drivers.
    </p>
    Here is our Business drivers and the corresponding Business objectives in the table below:
      <p>
      
        |       Business drivers          |         Business objectives          |
        | ------------------------------- | ------------------------------------ |   
        |    Addition of new customers    |     Manage the increase in volume    |
        |  Addition/removal of products   |  Manage the change within the budget |
        |     Entry of new competitors    |          Customers retention         |
  
    </p>
+ #### 1.2. Identify key business processes:
    <p style=" font-size:13.2pt;">
        ????
    </p>
+ #### 1.3. The key performance indicator:
    <p style=" font-size:13.2pt;">
        The quantifiable measurements that reflect the critical success factor of an organisation and help an organisation
        define and measure progress toward organizational goals.
    </p>
    <br>
    <b>A . Sales performance: </b>
    <p>
      Measures the monthly sales amount with respect to the same month of the previous year the goal consists in achieving 15%
      for example growth year over year.
    </p>
    <br>
    <b>B . Number of orders: </b>
    <p>
      Measures the activity in terms of orders received; it is computed as the number of orders submitted per month.
      And the goal is to achieve a 5% monthly increase for example.
    </p>
    <b>C . Shipping efficiency : </b>
    <p>
      Measures the delay in the shipping of orders, therefore, it is a measure of customers satisfaction.
    </p>
+ #### 1.3. decision-making queries:

    <p>
    <b style=" font-size:13.2pt;">1. Total sales amount per customer, year, and product category.</b>
    </p>
    <p>
    <b style=" font-size:13.2pt;">2. Yearly sales amount for each pair of customer country and supplier countries.</b>
    </p>
    <p>
    <b style=" font-size:13.2pt;">3. Monthly sales by customer state compared to those of the previous year.</b>
    </p>
    <p>
    <b style=" font-size:13.2pt;">4. Three best-selling employees.</b>
    </p>
    <p>
    <b style=" font-size:13.2pt;">5. Best-selling employee per product and year.</b>
    </p>
    <p>
    <b style=" font-size:13.2pt;">6. Total sales and average monthly sales by employee and year.</b>
    </p>
  
+ #### 1.3. dimensional for the data warehouse / data mart:
!["dimensional_schema_northwind"](screenshots/start_schema.png)
+ #### 1.3. Estimate the size of the data mart / data warehouse:
    <p>
    The size of the data warehouse is estimated by calculating the storage requirements of the designed table schema and the number
    of rows the database contains. The most important table to consider is the fact table as it requires the maximum amount of storage,
    and the space requirements of the dimension tables could be neglected in the estimation .
    </p>
    <p>
      Let us now estimate the size of the Sales_Fact table. The Sales_Fact table stores details of transactions by customers over a 
      period of 2.5 years. Let us assume that a customer has an average of 8 transactions per year.
    </p>
    <p>
  
      Customers = 91
      Average transaction per customer per year = 8
      year of Data = 2.5 years 
      Number of dimension = 4
      Other keys = 2
      Number of rows in the sales_fact = 91 * 8 * 2.5 = 1820
      Estimated Data size per row = (9 keys * 4 bytes ) + (1 nvchar * 50) + (2 datetime * 8) + 
                                    (1 smallint * 2) + (1 money * 8) + (1 real * 4) = 116 bytes
    </p>