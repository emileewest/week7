sales_data=[
{"region": "North America", "product": "widgets", "sales": 150},
{"region": "North America", "product": "bobbles", "sales": 200},
{"region": "Europe", "product": "widgets", "sales": 120},
{"region": "Europe", "product": "bobbles", "sales": 180},
{"region": "Asia", "product": "widgets", "sales": 300},
{"region": "Asia", "product": "bobbles", "sales": 250},
{"region": "North America", "product": "widgets", "sales": 175},
{"region": "North America", "product": "bobbles", "sales": 220},
{"region": "Europe", "product": "widgets", "sales": 130},
{"region": "Europe", "product": "bobbles", "sales": 190},
{"region": "Asia", "product": "widgets", "sales": 310},
{"region": "Asia", "product": "bobbles", "sales": 260},
{"region": "North America", "product": "widgets", "sales": 160},
{"region": "North America", "product": "bobbles", "sales": 155},
{"region": "Europe", "product": "widgets", "sales": 140},
{"region": "Europe", "product": "bobbles", "sales": 200},
{"region": "Asia", "product": "widgets", "sales": 320},
{"region": "Asia", "product": "bobbles", "sales": 270},
{"region": "North America", "product": "bobbles", "sales": 215},
{"region": "Europe", "product": "bobbles", "sales": 135},
{"region": "Europe", "product": "bobbles", "sales": 210},
{"region": "Asia", "product": "widgets", "sales": 330},
{"region": "Asia", "product": "bobbles", "sales": 290},
{"region": "North America", "product": "widgets", "sales": 165},
{"region": "North America", "product": "bobbles", "sales": 225},
{"region": "Europe", "product": "widgets", "sales": 210},
{"region": "Europe", "product": "bobbles", "sales": 310},
{"region": "Asia", "product": "bobbles", "sales": 280},
{"region": "North America", "product": "widgets", "sales": 170}]

import pandas as pd
df = pd.DataFrame(sales_data)
import matplotlib.pyplot as plt

# 1. How many total sales were there?
total_sales = sum(item["sales"] for item in sales_data)

# 2. List the top three countries by overall products sold:
sales_by_region = {}
for item in sales_data:
    region = item["region"]
    sales_by_region[region] = sales_by_region.get(region, 0) + item["sales"]
top_three_regions = sorted(sales_by_region.items(), key=lambda x: x[1], reverse=True)[:3]


# 3. Which sold more, bobbles or widgets?
sales_by_product = {"bobbles": 0, "widgets": 0}
for item in sales_data:
    sales_by_product[item["product"]] += item["sales"]
most_sold_product = max(sales_by_product, key=sales_by_product.get)


# 4. If Bobbles are $10.99 and Widgets are $15.99, calculate the overall revenue for each product (sales x price). Which product made the most revenue?
prices = {"bobbles": 10.99, "widgets": 15.99}
revenue_by_product = {product: sales * prices[product] for product, sales in sales_by_product.items()}
most_revenue_product = max(revenue_by_product, key=revenue_by_product.get)


# 5. Which region and product sold the least?
least_sold_item = min(sales_data, key=lambda x: x["sales"])


print(f"Total Sales: {total_sales}")

print("\nTop three regions by number of sales:")

for region, sales in top_three_regions:
    print(f"{region}: {sales}")

print(f"\nTotal Sales by Product:\nBobbles: {sales_by_product['bobbles']}\nWidgets: {sales_by_product['widgets']}")

print(f"\nWere more bobbles or widgets sold? \n{most_sold_product}")

print("\nRevenue by Product:")

for product, revenue in revenue_by_product.items():
    print(f"{product}: ${revenue:.2f}")

print(f"\nWhich product made the most revenue, bobbles or widgets? \n{most_revenue_product}")

print(f"\nWhich region and product sold the least and what was the sales total? \n{least_sold_item}")

# 6. Please create a bar chart comparing overall sales by country
df = pd.DataFrame(sales_data)
sales_by_country = df.groupby('region')['sales'].sum()
sales_by_country.plot(kind='bar', title='Overall Sales by Country')
plt.xlabel('Country')
plt.ylabel('Total Sales')
plt.show()

# 7. Please create a pie chart comparing overall sales by product

df = pd.DataFrame(sales_data)
sales_by_product = df.groupby('product')['sales'].sum()
plt.figure(figsize=(8, 8))  
plt.pie(sales_by_product, labels=sales_by_product.index, autopct='%1.1f%%', startangle=90)
plt.title('Overall Sales by Product')
plt.axis('equal')  
plt.show()


