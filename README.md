2. Develop a sales analytics program to analyze product performance and revenue trends.
1. Calculate daily sales revenue.
2. Compute monthly sales.
3. Identify most sold product (based on quantity).
4. Perform category-wise revenue analysis.
5. Visualize monthly sales using a line chart.
PROGRAM:-
import matplotlib.pyplot as plt
from collections import defaultdict
from datetime import datetime
sales_data = [
{"date":"2026-03-01","product":"Apple","category":"Fruits","price":2,"quantity":50},
{"date":"2026-03-01","product":"Banana","category":"Fruits","price":1,"quantity":80},
{"date":"2026-03-02","product":"Milk","category":"Dairy","price":3,"quantity":40},
{"date":"2026-03-03","product":"Bread","category":"Bakery","price":2.5,"quantity":30},
{"date":"2026-03-05","product":"Apple","category":"Fruits","price":2,"quantity":60},
{"date":"2026-04-01","product":"Milk","category":"Dairy","price":3,"quantity":50},
{"date":"2026-04-03","product":"Bread","category":"Bakery","price":2.5,"quantity":40}
]
daily_revenue=defaultdict(float)
monthly_sales=defaultdict(float)
product_quantity=defaultdict(int)
category_revenue=defaultdict(float)
for sale in sales_data:
revenue=sale["price"]*sale["quantity"]
date=sale["date"]
month=date[:7]
daily_revenue[date]+=revenue
monthly_sales[month]+=revenue
product_quantity[sale["product"]]+=sale["quantity"]
category_revenue[sale["category"]]+=revenue
most_sold=max(product_quantity,key=product_quantity.get)
output="DAILY SALES REVENUE\n"
for d,r in daily_revenue.items():
output+=f"{d} : {r}\n"
output+="\nMONTHLY SALES\n"
for m,s in monthly_sales.items():
output+=f"{m} : {s}\n"
output+="\nMOST SOLD PRODUCT\n"
output+=most_sold+" ("+str(product_quantity[most_sold])+" units)\n"
output+="\nCATEGORY WISE REVENUE\n"
for c,r in category_revenue.items():
output+=f"{c} : {r}\n"
print(output)
f=open("sales_analytics_output.txt","w")
f.write(output)
f.close()
months=list(monthly_sales.keys())
values=list(monthly_sales.values())
plt.plot(months,values,marker='o')
plt.title("Monthly Sales Revenue")
plt.xlabel("Month")
plt.ylabel("Revenue")
plt.grid(True)
plt.show()
OUTPUT:-
DAILY SALES REVENUE
2026-03-01 : 180.0
2026-03-02 : 120.0
2026-03-03 : 75.0
2026-03-05 : 120.0
2026-04-01 : 150.0
2026-04-03 : 100.0
MONTHLY SALES
2026-03 : 495.0
2026-04 : 250.0
MOST SOLD PRODUCT
Apple (110 units)
CATEGORY WISE REVENUE
Fruits : 300.0
Dairy : 270.0
Bakery : 175.0
