# Report on Findings and Analysis

## Summary of Findings

In this analysis, a series of SQL queries were executed on a database consisting of two main tables: **products** and **sales**, with the aim of extracting insights related to sales performance. The queries were designed to identify the products generating the highest revenue, the best-selling fruits, the least sold products, and several other key performance indicators. Here is a summary of the results obtained:

### 1. Product with the Highest Revenue
The query to identify the product that generated the highest revenue worked as expected. The total revenue for each product was calculated by multiplying the quantity sold by the product's price, followed by grouping the results by `product_name`. After ordering the results by total revenue in descending order, the product generating the highest revenue was identified accurately.

### 2. Best-Selling Fruit
The query to determine the best-selling fruit also performed well. By filtering the products for those categorized as "Fruit," the query summed the quantities sold and ordered the results to find the fruit with the highest sales volume. This approach gave us an accurate identification of the top-selling fruit.

### 3. Least Sold Product
The query to find the least sold product worked as intended, using a `LEFT JOIN` to ensure that even products with zero sales were included. The results were correctly ordered by total sales to find the least sold product.

### 4. Product Sold More Than 5 Times in the Current Month
This query, which filtered sales to the current month and year, successfully identified the products that had been sold more than five times. It was effective in capturing products that met the specified criteria.

## Creative Queries:

- **Query 1:** The query to identify the product with the highest monthly sales rate in the current year worked seamlessly. By grouping by both product and month, it provided a comprehensive view of which products had the highest sales rates each month.
  
- **Query 2:** The query to determine which category generated the highest revenue this year also performed well, calculating total revenue per category and providing the right result.

## Challenges and Variations

While the majority of the queries worked flawlessly, there was one notable issue with the query asking for the product with the biggest drop in sales compared to last year. This query encountered a limitation due to the absence of a year column or any direct way to easily differentiate between sales from different years. The schema did not provide enough information to compare sales from this year to the previous year. This highlighted a gap in the data schema that could be addressed by adding a column for the year or modifying the `sale_date` format.

## What Did I Learn?

### 1. Importance of Data Schema Design
The lack of a year column in the schema prevented us from comparing sales across different years, which showed how crucial it is to have a well-structured database schema for performing time-based analyses.

### 2. Flexibility of SQL for Business Insights
The various queries demonstrated how SQL can be used flexibly to generate valuable business insights, from identifying top-performing products to calculating monthly sales rates and revenue by category.

### 3. Critical Thinking in Data Analysis
The exercise also emphasized the importance of critical thinking in data analysis. While most queries were straightforward, the limitations in the data schema required creative problem-solving to work around. This reinforces the idea that data analysis is not only about querying the database but also about understanding the context, data structure, and limitations.

## Conclusion
In conclusion, this exercise showcased the power of SQL for querying databases to derive useful business insights. It also highlighted the importance of maintaining a robust and well-structured database for more complex analyses, especially those involving time series or comparisons over multiple years.
