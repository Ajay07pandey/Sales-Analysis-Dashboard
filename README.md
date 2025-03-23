I am creating a Dashboard i have 5 data files Namely Shipments Table, Date Table, Sales Person Table, Product table, Geography table.
Fact Table -- Shipment table.
Dimension Table -- Sales table, Calendar table, Geography table, Product table.
Here I am following a Star schema/Snow Flake schema

 Sales Analytics Dashboard
 
The Dashboards is related to Chocolate sales analytics we have given data where sales person names is mentioned along with sales and the Geography in which it has delivered boxes, their cost and profit.

**Fact Tables:**

We have a Fact table called Shipments table having fields as mentioned below:
            a. Sales Person
            b. Geography
            c. Product
            d. Date
            e. Sales
            f. Boxes
            
**Dimension Table:**

We have another 4 Dimension Tables as mentioned below:
1.	Product Table
  a.	Product
  b.	Category
  c.	Cost per box

2.	Location Table
  a.	Geo
  b.	Region

3.	Sales Person Table
  a.	Sales person
  b.	Team
  c.	Picture

4.	Calendar Table
  a.	Date

Here for building the Relationship I have used Star Schema
Relationship - One to Many

**Measure Tables**
1.	Total Sales
2.	Total Boxes
3.	Total Shipments – Count Rows of the Shipment Table.
4.	Total Costs for each shipment 
We Can approach with two methods:
a. By creating a DAX measure
b. By creating a New column in the Shipment table.
 Costs = Related (products [cost per box])*[Boxes])
“Here we have multiply cost per box from the Products table and then Multiplied it with the Boxes fields in the Shipment Table then we will create a Measure called Total Costs”
Total Costs = Sum(‘Shipment’[Costs])
5.	Total Profit = [Total Sales] – [Total Costs]
6.	Profit percentage 
7.	Low Box Shipment

We want to know how Many shipment have less than 50 boxes of Chocolates.
LBS Count = Calculate ( [Total Shipment], shipments[Boxes] < 50 )

8.	Low box Shipment Percentage
LBS % = Divide ([LBS Count], [Total shipment])

**Outline Work Flow:**

a.	Chocolate Sales Analytics.

b.	Sales, Boxes, Cost and Profits.

c.	Performance of Sales persons and Products.

d.	Low Box Shipment analysis.

e.	MOM/YOY Changes.

**FLOW:**

Data Loading – Loaded the data present in CSV files.

Data Manipulation and Cleaning – Using Power Query I have cleaned the Data and put appropriate data types, and removed null values.

Data Modelling – Using Star schema (One to Many) I have created the relationship between the tables.

Data Transformation - Using DAX functions, I have created new measures.

Data Analysis – By combining measures we have created live interactive dashboards for giving the overview of the analysis.

**Time Intelligence Analysis** – 
Before we are starting the time Intelligence Analysis firstly we convert it into the Date format.
Then I have did the Derived calculations by adding the columns in the Date Table and added columns like Year, Day, Date.

**Insights:**
1.	Peanut Butter is our highest profit making product.
2.	Low Box count – From all the 6,113 Total shipments 624 Shipment has Low box count.
3.	Overall 10.2 % of LBS (low box shipment) present in the data.
4.	Milk Bars has the Highest Low box shipment percentage of 16.5%
