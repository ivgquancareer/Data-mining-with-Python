# DATA ANALYST: USING PYTHON

![image](https://user-images.githubusercontent.com/131565885/235279847-004e84e3-7395-48fd-ad6e-653740bd7bc6.png)


# I. BACKGROUND
You are a **Data Analyst** working for an **E-commerce company**.

* **The Sales Manager and Operations Manager** request you to present an overview of the business and operations of the company up to now.

* **The presentation should include the following information:** business overview, customer satisfaction, and 2 to 3 suggestions (areas) where the company can improve.

# II. DATA ANALYSIS
# 1. Overall performance through years
```php
import plotly.express as px
fig = px.bar(sales_by_month, x="Year", y="total_payment_value",
             color='Month', barmode='group' , width=1300,
             height=800,
             title = ('<b>Total Payment Value Overview<b>'),
             category_orders={ # replaces default order by column name
              "Year": ["2016", "2017", "2018"],
              "Month": ["01", "02", "03", "04",'05','06','07','08','09','10','11','12']},
             labels={ # replaces default labels by column name
                 "total_payment_value": "<b>Total Payment Value<b>",'Year':'<b>Year<b>'},
             template='plotly_white')
fig.update_xaxes(minor_ticks="inside")  
fig.update_xaxes(showline=True, linewidth=2, linecolor='black')
fig.update_yaxes(showline=True, linewidth=2, linecolor='black')
fig.update_layout(xaxis = dict(tickfont = dict(size=15)))
fig.update_layout(yaxis = dict(tickfont = dict(size=15)))
fig.update_layout(font = dict(size=20))
fig.update_layout(bargap=0.1)
fig.update_layout(title=dict(font=dict(color='black', size=30)))
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234194726-9ae13ba5-e8db-4fe6-ae4c-0a4732e1789a.png)
# 2. Business performance by Year 
```php
fig = px.bar(revenues_by_year,x='Year',  y="total_payment_value",
             width=1300, 
             height=800,
             title = '<b>Total Payment Value according to Year<b>',
             color_discrete_sequence =['#00cc96'],
             labels={ # replaces default labels by column name
                 "total_payment_value": "<b>Total Payment Value<b>",'Year':'<b>Year<b>'},
             template='plotly_white')
fig.update_yaxes(ticks="inside") 
fig.update_xaxes(minor_ticks="inside")  
fig.update_xaxes(showline=True, linewidth=2, linecolor='black')
fig.update_yaxes(showline=True, linewidth=2, linecolor='black')
fig.update_traces(textposition='outside',text=revenues_by_year['total_payment_value'])
fig.update_layout(bargap=0.5)
fig.update_layout(title=dict(font=dict(color='black', size=30)))
fig.update_layout(xaxis = dict(tickfont = dict(size=15)))
fig.update_layout(yaxis = dict(tickfont = dict(size=15)))
fig.update_layout(font = dict(size=20))
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234192017-d47317b4-ce21-4e02-b683-b124a6212401.png)
# 3. Business performance by Month 
```php
fig = px.line(revenues_by_month,x='Month',  y="total_payment_value",
              width=1300, height=800, markers=True,
              title = '<b>Total Payment Value according to Month<b>',
             labels={ # replaces default labels by column name
                 "total_payment_value": "<b>Total Payment Value<b>", 'Month':'<b>Month<b>'},
             template='plotly_white')
fig.update_xaxes(minor_ticks="inside")  
fig.update_xaxes(showline=True, linewidth=2, linecolor='black')
fig.update_yaxes(showline=True, linewidth=2, linecolor='black')
fig.update_layout(title=dict(font=dict(color='black', size=30)))
fig.update_layout(xaxis = dict(tickfont = dict(size=15)))
fig.update_layout(yaxis = dict(tickfont = dict(size=15)))
fig.update_layout(font = dict(size=20))
fig.update_traces(marker=dict(size=8, color ='light blue'))
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234169077-4142e110-0a15-4c41-8b01-747c087da2cd.png)
# 4. Top Product Category bring the most revenue for the company
```php
fig = px.pie(top5_product_category, values='sum_rev', names='product_category_name_english', 
             width=1000,
             height=500,
             title='<b>Top 5 Product Category by Revenue<b>',
             template='plotly_white')
fig.update_traces(hoverinfo='name +value', textfont_size=15,
                  marker=dict( line=dict(color='#000000', width=1)))
fig.update_traces(textfont=dict(color="White"))
fig.update_layout(legend_title_text='<b>Product Category <b>')
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234162959-28c8639b-a05a-4252-bd21-36b38b607974.png)

**The graphic above show the top-selling product category based on the revenue of the company. There are some ideas can be developed:**

*  Handling inventory by providing vouchers for additional products when purchasing with top-selling products, to stimulate the demand of buying additional products which have low volumn of sales
*  Develop product ecosystem, focus on add-ons products or accessories for these top-selling products

# 5. Payments Methods
```php
fig = px.pie(payment_method, values='count', names='payment_type', 
             width=1000,
             height=500,
             title='<b>Payment methods<b>',
             template='plotly_white')
fig.update_traces( textfont_size=15, marker=dict( line=dict(color='#000000', width=1)))
fig.update_traces(textfont=dict(color="White"))
fig.update_layout(legend_title_text='<b>Payment Methods <b>')
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234163167-27d48f75-cea6-4ae5-b5c0-c6e1e3dcae02.png)

**Based on the pie chart above, the payment methods that customers use the most to pay for their orders is Credit card.**
This shows the habit of shopping online with credit cards of our customers.
*   Prioritize payment via Credit card or Debit card can minimize the rate of not receiving the goods by customers
*   Work with financial intermediates to provide promotions for customer that us credit card or debit card as their payment methods
# 6. Customer Satisfaction Level
```php
fig = px.pie(customer_satisfaction_level, values='count', names='review_score', 
             width=1000,
             height=500,
             title='<b>Customer Satisfaction Level<b>',
             template='plotly_white')
fig.update_traces(textfont_size=15, marker=dict( line=dict(color='#000000', width=1)))
fig.update_traces(textfont=dict(color="White"))
fig.update_layout(legend_title_text='<b>Star<b>')
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234163433-9685ae12-e105-49a6-8639-a970223f6c7b.png)

**Rate of 1, 2 star rating is quite large percentage with 11.8% and 19.2% respectively.**

This shows that the quality and both products and services of the business are not that good.
* Customer reviews not only help businesses realize the quality of the product, 
but also the strengths and weaknesses of the service that the company provides
* From there, the company can know what sector is in need of improving to increase customers satisfaction level
* Company can change the source of low quality product in time, to avoid losing trust with customers, directing them to stick with the brand for a long time
# 7. Low Rated Product Category
```php
fig = px.bar(low_rate_product, x=low_rate_product.index, y=[1,2], text_auto=True, 
             width=1300, 
             height=600,
             labels= { 'value': "<b>Số lượt đánh giá<b>", 'product_category_name_english':'<b>Product Category<b>'},
             title='<b>Top 5 Low Rate Product Category<b>',
             color_discrete_sequence=['#D62728','#FF9900'],
             template='plotly_white')
fig.update_layout(title=dict(font=dict(color='black', size=20)))
fig.update_traces(textfont=dict( color="White"), textposition = 'inside')
fig.update_layout(legend_title_text='<b>Star<b>')
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234169336-96207e09-cee6-42c9-926c-e679dd3058c0.png)

**The chart above shows top 5 product category that are rated 1-2 star.** 
Company need to collect customer feedback, reviews to find out the root cause.
Then, classify the causes to know whether it is due to quality of products or quality of services that bring low-rate reviews.

* If it is due to the product quality, the company have to work with supplier for mutual adjustment or find new sources of goods supplier with better quality

* If it is due to the service quality, the company have to work with customer service department to know difficulties customer might face

* It is necessary to compensate customers that have the legit reasons for low-rate reviews by providing voucher with an apologize and a promise to improve the quality of products and service
# 8. Low Rated Seller ID
```php
fig = px.pie(top_5_low_rate_seller, values='Số_lần_rate_xấu', names='seller_id', 
             width=1000,
             height=500,
             title='<b>Top 5 Low rate Seller <b>',
             template='plotly_white')
fig.update_traces(textfont_size=15,marker=dict( line=dict(color='#000000', width=1)))
fig.update_traces(textfont=dict(color="White"))
fig.update_layout(legend_title_text='<b>Seller ID <b>')
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234164429-6e00135e-2420-47eb-9f27-08ac6794514a.png)

**The company need to ask for explanations from top seller for low-rate reviews.** 

* Seller needs to present ways to solve the customers problems about products and to commit about quality of product next time

* Compensate customers with bad experiences by providing discount voucher, product exchange or refund if needed 

* Re-evaluate the ability of sellers. Set the limit for low-rates review count in  each month. If any seller exceed the limit number, they will be banned. This way can make seller spend time to ensure their own product quality
# 9. Customers who bring the highest revenue for the company
```php
fig = px.bar(top_10_customer,x='customer_id',  y="Số_tiền_đã_trả",
              width=1000, 
             height=700,
             title = '<b>Top 10 Customer with Highest payment value<b>',
              labels={ # replaces default labels by column name
                 "Số_tiền_đã_trả": "<b>Total Payment Value<b>", 'customer_id' : '<b>CUSTOMER ID<b>'},
             template='plotly_white',
             color_discrete_sequence =['#00cc96'])
fig.update_traces(textposition='outside',text=top_10_customer['Số_tiền_đã_trả'])
fig.update_xaxes(minor_ticks="inside")  
fig.update_xaxes(showline=True, linewidth=2, linecolor='black')
fig.update_yaxes(showline=True, linewidth=2, linecolor='black')
fig.update_layout(title=dict(font=dict(color='black', size=20)))
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234170285-08a4e504-96d5-44db-9af4-de01ca682f07.png)

**The chart above shows ten customers with highest payment value, also known as vip customers.**

Because the cost of acquiring a new customer is 10 times higher than the cost of keeping current customers, the company should apply ideas below.

* Offer the most attractive incentives for this customer 

* Give these customers gifts of high spiritual value to express the brand's gratitude to them .Giving surprise gifts is a way to increase the emotions, impressions and satisfaction of VIP customers with the quality of care of the business

* On special occasions, company should not only organize special discount programs but also give VIP customers the opportunity to experience new products or services first
# 10. Installments and One-time payment
```php
fig = px.pie(df_data_payment, values='Số khách', names='Payment method', 
             width=1000,
             height=500,
             title='<b>Installments vs One time Payment<b>',
             template='plotly_white')
fig.update_traces(textfont_size=15, marker=dict( line=dict(color='#000000', width=1)))
fig.update_traces(textfont=dict(color="White"))
fig.show()
```
![image](https://user-images.githubusercontent.com/131565330/234164904-ad9039fc-ec43-4f9a-ad70-afb1aff5723e.png)

**The chart shows that the number of customers choosing installments and one-time payment are almost the same.**

The company can have long-term cooperation with financial companies to bring favorable interest rates to customers who use installments.

This is a 3-party relationship.
* Customers can immediately own the product they want despite not having enough money to buy it.

* The company can increase sales volume by stimulating demand with low-interest installment purchase programs
 
* Finance companies have new sources of customers


