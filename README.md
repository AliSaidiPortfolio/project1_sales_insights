# project1_sales_insights


SQL database dump is in db_dump.sql file. Download db_dump.sql file to your local computer and import it 

Data Analysis Using SQL

->Show all customer records
SELECT * FROM customers;

->Show total number of customers:
SELECT count(*) FROM customers;

->Show transactions for Chennai market (market code for chennai is Mark001:
SELECT * FROM transactions  where market_code='Mark001';

->Show distrinct product codes that were sold in chennai:
SELECT distinct product_code FROM transactions where market_code='Mark001';

->Show transactions where currency is US dollars:
SELECT * from transactions where currency="USD"

->Show transactions in 2020 join by date table:
SELECT *  FROM transactions t INNER JOIN date d ON t.order_date=d.date where d.year=2020;

->Show total revenue in year 2020:
SELECT SUM(t.sales_amount) FROM transactions t INNER JOIN date d ON t.order_date=d.date where d.year=2020 and (t.currency="INR\r" or t.currency="USD\r");

->Show total revenue in year 2020, January Month:
SELECT SUM(t.sales_amount) FROM transactions t INNER JOIN date d ON t.order_date=d.date where d.year=2020  and d.month_name="January" and (t.currency="INR\r" or t.currency="USD\r");

->Show total revenue in year 2020 in Chennai:
SELECT SUM(t.sales_amount) FROM transactions t INNER JOIN date d ON t.order_date=d.date where d.year=2020 and t.market_code="Mark001";

Data Analysis Using Power BI
Formula to create norm_amount column
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type decimal number)
