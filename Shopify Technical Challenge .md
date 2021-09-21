## Loading the DataSet ##

Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 



```python
import pandas as pd 

```


```python
df = pd.read_csv('shopifySheet1.csv')
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
      <th>payment_method</th>
      <th>created_at</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>53</td>
      <td>746</td>
      <td>224</td>
      <td>2</td>
      <td>cash</td>
      <td>2017-03-13 12:36:56</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>92</td>
      <td>925</td>
      <td>90</td>
      <td>1</td>
      <td>cash</td>
      <td>2017-03-03 17:38:52</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>44</td>
      <td>861</td>
      <td>144</td>
      <td>1</td>
      <td>cash</td>
      <td>2017-03-14 4:23:56</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>18</td>
      <td>935</td>
      <td>156</td>
      <td>1</td>
      <td>credit_card</td>
      <td>2017-03-26 12:43:37</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>18</td>
      <td>883</td>
      <td>156</td>
      <td>1</td>
      <td>credit_card</td>
      <td>2017-03-01 4:35:11</td>
    </tr>
  </tbody>
</table>
</div>




 ## A.) Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 



```python
print(df.total_items)
```

    0       2
    1       1
    2       1
    3       1
    4       1
           ..
    4995    2
    4996    2
    4997    3
    4998    2
    4999    2
    Name: total_items, Length: 5000, dtype: int64



```python
items_sale = df['total_items'].sum()
print (items_sale)
```

    43936



```python
total_order_amount = df['order_amount'].sum()
print (total_order_amount)
```

    15725640



```python
aov = total_order_amount / items_sale
print (aov)
```

    357.92152221412965



```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>5000.000000</td>
      <td>5000.000000</td>
      <td>5000.000000</td>
      <td>5000.000000</td>
      <td>5000.00000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2500.500000</td>
      <td>50.078800</td>
      <td>849.092400</td>
      <td>3145.128000</td>
      <td>8.78720</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1443.520003</td>
      <td>29.006118</td>
      <td>87.798982</td>
      <td>41282.539349</td>
      <td>116.32032</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>607.000000</td>
      <td>90.000000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1250.750000</td>
      <td>24.000000</td>
      <td>775.000000</td>
      <td>163.000000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2500.500000</td>
      <td>50.000000</td>
      <td>849.000000</td>
      <td>284.000000</td>
      <td>2.00000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3750.250000</td>
      <td>75.000000</td>
      <td>925.000000</td>
      <td>390.000000</td>
      <td>3.00000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>5000.000000</td>
      <td>100.000000</td>
      <td>999.000000</td>
      <td>704000.000000</td>
      <td>2000.00000</td>
    </tr>
  </tbody>
</table>
</div>




```python
## From above we can report that average order was mis calculated. To Calculate the AOV we calculate total value of items sold divide by total items bought. ##
```


```python
###B.)What metric would you report for this dataset?###
   ## i will be reporting the mean with respect to the new AOV ##
```


```python
# c. What is its value? #

```


```python
aov = total_order_amount / items_sale
print (aov)
```

    357.92152221412965



```python

```


```python

```
