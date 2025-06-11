# Step 1: Importing data


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Show all columns when displaying dataframes
pd.set_option('display.max_columns', None)

# Load the raw dataset
df = pd.read_csv('Superstore.csv', encoding='latin1')


# Preview the first few rows
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
      <th>Row ID</th>
      <th>Order ID</th>
      <th>Order Date</th>
      <th>Ship Date</th>
      <th>Ship Mode</th>
      <th>Customer ID</th>
      <th>Customer Name</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Product ID</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Product Name</th>
      <th>Sales</th>
      <th>Quantity</th>
      <th>Discount</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>CA-2016-152156</td>
      <td>11/8/2016</td>
      <td>11/11/2016</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>FUR-BO-10001798</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>Bush Somerset Collection Bookcase</td>
      <td>261.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>41.9136</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>CA-2016-152156</td>
      <td>11/8/2016</td>
      <td>11/11/2016</td>
      <td>Second Class</td>
      <td>CG-12520</td>
      <td>Claire Gute</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>FUR-CH-10000454</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>Hon Deluxe Fabric Upholstered Stacking Chairs,...</td>
      <td>731.9400</td>
      <td>3</td>
      <td>0.00</td>
      <td>219.5820</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>CA-2016-138688</td>
      <td>6/12/2016</td>
      <td>6/16/2016</td>
      <td>Second Class</td>
      <td>DV-13045</td>
      <td>Darrin Van Huff</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036</td>
      <td>West</td>
      <td>OFF-LA-10000240</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>Self-Adhesive Address Labels for Typewriters b...</td>
      <td>14.6200</td>
      <td>2</td>
      <td>0.00</td>
      <td>6.8714</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>US-2015-108966</td>
      <td>10/11/2015</td>
      <td>10/18/2015</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>FUR-TA-10000577</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>Bretford CR4500 Series Slim Rectangular Table</td>
      <td>957.5775</td>
      <td>5</td>
      <td>0.45</td>
      <td>-383.0310</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>US-2015-108966</td>
      <td>10/11/2015</td>
      <td>10/18/2015</td>
      <td>Standard Class</td>
      <td>SO-20335</td>
      <td>Sean O'Donnell</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>OFF-ST-10000760</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>Eldon Fold 'N Roll Cart System</td>
      <td>22.3680</td>
      <td>2</td>
      <td>0.20</td>
      <td>2.5164</td>
    </tr>
  </tbody>
</table>
</div>



## Dataset Description

* The dataset represents sales transaction records from a retail company that sells consumer goods like office supplies, technology, and furniture across various regions in the United States. Each row captures the details of an individual item sold — including the order date, shipping date, product type, quantity, discount, and resulting profit. It also contains customer information, segment classification (Consumer, Corporate, or Home Office), and geographic attributes like city, state, and region.

* This data enables analysis of sales trends, profitability, customer behavior, discount impact, and supply chain efficiency.

# Step 2: EDA and Data Cleaning


```python
# Shape of the dataset (rows x columns)
print("Dataset shape:", df.shape)

# Overview of columns, data types, and non-null values
df.info()

```

    Dataset shape: (9994, 21)
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9994 entries, 0 to 9993
    Data columns (total 21 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   Row ID         9994 non-null   int64  
     1   Order ID       9994 non-null   object 
     2   Order Date     9994 non-null   object 
     3   Ship Date      9994 non-null   object 
     4   Ship Mode      9994 non-null   object 
     5   Customer ID    9994 non-null   object 
     6   Customer Name  9994 non-null   object 
     7   Segment        9994 non-null   object 
     8   Country        9994 non-null   object 
     9   City           9994 non-null   object 
     10  State          9994 non-null   object 
     11  Postal Code    9994 non-null   int64  
     12  Region         9994 non-null   object 
     13  Product ID     9994 non-null   object 
     14  Category       9994 non-null   object 
     15  Sub-Category   9994 non-null   object 
     16  Product Name   9994 non-null   object 
     17  Sales          9994 non-null   float64
     18  Quantity       9994 non-null   int64  
     19  Discount       9994 non-null   float64
     20  Profit         9994 non-null   float64
    dtypes: float64(3), int64(3), object(15)
    memory usage: 1.6+ MB



```python
# Count duplicate rows
duplicate_rows = df.duplicated().sum()
print(f"Total duplicate rows: {duplicate_rows}")

```

    Total duplicate rows: 0



```python
# Summary stats for numeric columns
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
      <th>Row ID</th>
      <th>Postal Code</th>
      <th>Sales</th>
      <th>Quantity</th>
      <th>Discount</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9994.000000</td>
      <td>9994.000000</td>
      <td>9994.000000</td>
      <td>9994.000000</td>
      <td>9994.000000</td>
      <td>9994.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4997.500000</td>
      <td>55190.379428</td>
      <td>229.858001</td>
      <td>3.789574</td>
      <td>0.156203</td>
      <td>28.656896</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2885.163629</td>
      <td>32063.693350</td>
      <td>623.245101</td>
      <td>2.225110</td>
      <td>0.206452</td>
      <td>234.260108</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1040.000000</td>
      <td>0.444000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>-6599.978000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2499.250000</td>
      <td>23223.000000</td>
      <td>17.280000</td>
      <td>2.000000</td>
      <td>0.000000</td>
      <td>1.728750</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4997.500000</td>
      <td>56430.500000</td>
      <td>54.490000</td>
      <td>3.000000</td>
      <td>0.200000</td>
      <td>8.666500</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7495.750000</td>
      <td>90008.000000</td>
      <td>209.940000</td>
      <td>5.000000</td>
      <td>0.200000</td>
      <td>29.364000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9994.000000</td>
      <td>99301.000000</td>
      <td>22638.480000</td>
      <td>14.000000</td>
      <td>0.800000</td>
      <td>8399.976000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Check column data types
df.dtypes

```




    Row ID             int64
    Order ID          object
    Order Date        object
    Ship Date         object
    Ship Mode         object
    Customer ID       object
    Customer Name     object
    Segment           object
    Country           object
    City              object
    State             object
    Postal Code        int64
    Region            object
    Product ID        object
    Category          object
    Sub-Category      object
    Product Name      object
    Sales            float64
    Quantity           int64
    Discount         float64
    Profit           float64
    dtype: object




```python
# Dates are in object so converting them into dates
df['Order Date'] = pd.to_datetime(df['Order Date'], format='%m/%d/%Y')
df['Ship Date'] = pd.to_datetime(df['Ship Date'], format='%m/%d/%Y')
# Converting Postal Code as string
df['Postal Code'] = df['Postal Code'].astype(str)

# Drop duplicates
df = df.drop_duplicates()

# Check numeric column distributions
numeric_cols = ['Sales', 'Profit', 'Quantity', 'Discount']
df[numeric_cols].hist(bins=50, figsize=(12, 8), color='skyblue')
plt.suptitle("Distribution of Numeric Variables", fontsize=14)
plt.tight_layout()
plt.show()

```


    
![png](output_8_0.png)
    


## Interpreting distributions

1. From the above distribution plots it is visible that **sales are exteremly right skewed**, and it shows most of orders are under 1000$ but few are huge that might be from B2B or High Consumer retail. So we might have to Log-transform sales when modeling or use percentiles (to avoid models overfitting to extreme sales).

2. Profit: It's centered around 0 with sharp peak, but long tails on both sides (including negative profits). This is a red flag. High sales should ideally bring in profit but this points to profit leakage.

3. Quantity: quanitity plot is positive skewed. it's visible that huge orders are rare. This might be you're making more sales in retail instead of wholesale.

4. Discounts: sharp spikes at 0 and .2 which might be low discounts more profit but as the discounts are increasing company is bleeding their profits.


```python
# Select numeric columns only
numeric_cols = ['Sales', 'Profit', 'Quantity', 'Discount']

# Compute correlation matrix
corr_matrix = df[numeric_cols].corr()

# Plot heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, fmt=".2f", cmap="coolwarm", linewidths=0.5)
plt.title("Correlation Matrix of Numeric Variables")
plt.show()

```


    
![png](output_10_0.png)
    


The correlation heatmap revealed several important relationships. Sales and profit showed a moderate positive correlation (0.48), indicating that higher sales can lead to higher profits, though not always. More importantly, there was a weak negative correlation (–0.22) between discount and profit, suggesting that increasing discounts tends to reduce profitability. Other variable pairs showed negligible correlation, meaning no strong direct linear relationships exist among them. This pattern directly points to a potential issue in the business strategy — discounts may not be delivering the intended profitability boost, which sets the stage for hypothesis testing.


```python
plt.figure(figsize=(7, 5))
sns.scatterplot(data=df, x='Discount', y='Profit', alpha=0.4)
plt.title("Discount vs. Profit")
plt.xlabel("Discount")
plt.ylabel("Profit")
plt.grid(True)
plt.show()

```


    
![png](output_12_0.png)
    


Further exploration using a scatter plot of discount vs. profit confirmed this suspicion. At 0% discount, the spread of profit values was wide, including several highly profitable transactions. However, at discount levels between 0.2 and 0.8, profits consistently declined, and many entries dropped into deep negative territory. This suggests that excessive discounting may not only fail to incentivize profitable behavior but could actively harm margins. This pattern is a compelling foundation for a focused **“Discount Abuse Pattern”** analysis.



```python
plt.figure(figsize=(7, 5))
sns.scatterplot(data=df, x='Sales', y='Profit', alpha=0.4)
plt.title("Sales vs. Profit")
plt.xlabel("Sales")
plt.ylabel("Profit")
plt.grid(True)
plt.show()

```


    
![png](output_14_0.png)
    


A separate scatter plot of sales vs. profit revealed a triangular distribution. Most transactions clustered in the low-sale, low-profit range, while some high-sale entries still ended in loss, highlighting that strong revenue does not automatically translate into strong profit. This supports the concept of profit leakage, where certain high-revenue items or regions might be underperforming in terms of actual financial return.


```python
plt.figure(figsize=(8, 5))
sns.boxplot(data=df, x='Segment', y='Profit')
plt.title("Profit Distribution by Customer Segment")
plt.grid(True)
plt.show()

```


    
![png](output_16_0.png)
    


Boxplot of profit distribution by customer segment (Consumer, Corporate, and Home Office) showed similar median profits across all segments. However, each segment had numerous extreme outliers on both ends of the profit scale, including significant losses. This indicates that no segment is immune to unprofitable transactions, and high-risk behavior is spread across the board. It further implies that broad segmentation is not sufficient — deeper analysis at the intersection of region, product category, and discount level will likely yield more actionable insights.

# Step 3: Defining hypothesis
Based on the patterns identified during exploratory data analysis, we formulated several business-focused hypotheses aimed at uncovering inefficiencies and hidden risks in the company's retail strategy. The first hypothesis addresses profit leakage, suggesting that certain product sub-categories or geographic regions may generate high sales yet consistently yield low or even negative profit. This would indicate operational inefficiencies or poor pricing structures that mask underlying losses.

The second hypothesis revolves around a discount abuse pattern, based on the observation that higher discounts, especially those exceeding 30%, often correspond to sharp declines in profitability. This raises the possibility that discounting, instead of boosting volume or customer retention, is eroding margins without generating meaningful returns — a critical area for revenue protection.

The third hypothesis focuses on inventory optimization. By analyzing order quantities and shipping delays across product categories, we suspect that certain items are more prone to late fulfillment or stockouts. This inefficiency may lead to lost sales or poor customer experience, and highlights the need for more strategic restocking cycles.

Lastly, the time-to-profit hypothesis investigates how long it takes for a customer to become profitable. By analyzing the cumulative profit timeline per customer, we aim to identify segments or regions that require longer lead time to break even. This insight can inform smarter investments in marketing, onboarding, and retention strategies by focusing on faster-returning customer groups.
## Hypothesis 1: Profit Leakage
**“Some product sub-categories or regions generate high sales but consistently result in low or negative profit, indicating potential leakage.”**

### 1.1) Create a new feature: Profit Margin


```python
# Profit margin = profit as a percentage of sales
df['Profit Margin'] = df['Profit'] / df['Sales']

```

### 1.2) Group data by Category, Sub-Category, and Region


```python
# Group by Category, Sub-Category, and Region
grouped = df.groupby(['Category', 'Sub-Category', 'Region']).agg({
    'Sales': 'sum',
    'Profit': 'sum',
    'Profit Margin': 'mean'
}).reset_index()

```

### 1.3) Sort to spot problem areas (low or negative profit with high sales)


```python
# Sort by Sales and Profit to catch high-volume low-profit areas
grouped_sorted = grouped.sort_values(by=['Sales', 'Profit'], ascending=[False, True])

```


```python
# Show the top 15 potential profit leakage zones
grouped_sorted.head(15)

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
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Region</th>
      <th>Sales</th>
      <th>Profit</th>
      <th>Profit Margin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7</th>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>West</td>
      <td>101781.328</td>
      <td>4027.5843</td>
      <td>0.021498</td>
    </tr>
    <tr>
      <th>65</th>
      <td>Technology</td>
      <td>Phones</td>
      <td>East</td>
      <td>100614.982</td>
      <td>12314.6860</td>
      <td>0.089939</td>
    </tr>
    <tr>
      <th>67</th>
      <td>Technology</td>
      <td>Phones</td>
      <td>West</td>
      <td>98684.352</td>
      <td>9110.7426</td>
      <td>0.085740</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>East</td>
      <td>96260.683</td>
      <td>9357.7706</td>
      <td>0.063061</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>Central</td>
      <td>85230.646</td>
      <td>6592.7221</td>
      <td>0.004443</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Furniture</td>
      <td>Tables</td>
      <td>West</td>
      <td>84754.562</td>
      <td>1482.6073</td>
      <td>-0.053966</td>
    </tr>
    <tr>
      <th>64</th>
      <td>Technology</td>
      <td>Phones</td>
      <td>Central</td>
      <td>72403.282</td>
      <td>12323.0267</td>
      <td>0.166875</td>
    </tr>
    <tr>
      <th>45</th>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>East</td>
      <td>71612.584</td>
      <td>8389.3712</td>
      <td>0.096746</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>West</td>
      <td>70532.852</td>
      <td>8645.3222</td>
      <td>0.132321</td>
    </tr>
    <tr>
      <th>61</th>
      <td>Technology</td>
      <td>Machines</td>
      <td>East</td>
      <td>66106.165</td>
      <td>6928.6429</td>
      <td>-0.176847</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Technology</td>
      <td>Accessories</td>
      <td>West</td>
      <td>61114.116</td>
      <td>16484.5983</td>
      <td>0.241386</td>
    </tr>
    <tr>
      <th>66</th>
      <td>Technology</td>
      <td>Phones</td>
      <td>South</td>
      <td>58304.438</td>
      <td>10767.2753</td>
      <td>0.174286</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Office Supplies</td>
      <td>Binders</td>
      <td>Central</td>
      <td>56923.282</td>
      <td>-1043.6369</td>
      <td>-0.859399</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Office Supplies</td>
      <td>Binders</td>
      <td>West</td>
      <td>55961.113</td>
      <td>16096.8016</td>
      <td>0.166587</td>
    </tr>
    <tr>
      <th>62</th>
      <td>Technology</td>
      <td>Machines</td>
      <td>South</td>
      <td>53890.960</td>
      <td>-1438.8930</td>
      <td>0.012778</td>
    </tr>
  </tbody>
</table>
</div>



### 1.4) Visualize profit margin by sub-category


```python
plt.figure(figsize=(12, 6))
sns.barplot(data=grouped.sort_values(by='Profit Margin'), 
            x='Sub-Category', y='Profit Margin', hue='Region')
plt.xticks(rotation=45)
plt.title("Average Profit Margin by Sub-Category and Region")
plt.tight_layout()
plt.show()

```


    
![png](output_29_0.png)
    


The chart shows how much profit each product sub-category makes on average, across different regions. What stands out clearly is that some products — like Appliances, Binders, Furnishings, Tables, and Bookcases — are consistently unprofitable in certain areas, especially in the Central region. For example, Appliances in Central have a very low margin, meaning the company is likely losing money on every sale there.

On the flip side, sub-categories like Labels, Paper, and Envelopes perform well across all regions, showing strong and steady profits. These are likely the products that help keep the business healthy.

What this tells us is simple: even if some items are selling well, they’re not always making money. This is called profit leakage — and it's a hidden problem that businesses often miss. It’s worth looking deeper into pricing, discounting, or shipping costs for those underperforming products in those regions.

#### We already know sub-categories like Appliances, Binders, Furnishings, Tables are leaking profit.But now we will filter the products which are loss making or affecting profits.

### 1.5) Filter only those sub-categories


```python
# Focus on sub-categories where margin is suspicious
leaking_subs = ['Appliances', 'Binders', 'Furnishings', 'Tables', 'Bookcases']
df_leak = df[df['Sub-Category'].isin(leaking_subs)]

```

### 1.6) Group by Product Name and Region


```python
# Group by product and region to see detailed trends
leaky_products = df_leak.groupby(['Product Name', 'Region']).agg({
    'Sales': 'sum',
    'Profit': 'sum',
    'Profit Margin': 'mean',
    'Quantity': 'sum'
}).reset_index()

```

### 1.7)  Filter products with negative or low margins


```python
# Filter to show only products with profit margin < 0 (loss-making)
loss_products = leaky_products[leaky_products['Profit Margin'] < 0]

# Sort by most negative profit
loss_products = loss_products.sort_values(by='Profit', ascending=True)

```


```python
loss_products.head(10)

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
      <th>Product Name</th>
      <th>Region</th>
      <th>Sales</th>
      <th>Profit</th>
      <th>Profit Margin</th>
      <th>Quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>901</th>
      <td>GBC DocuBind P400 Electric Binding System</td>
      <td>Central</td>
      <td>8710.336</td>
      <td>-3048.6176</td>
      <td>-0.980000</td>
      <td>16</td>
    </tr>
    <tr>
      <th>506</th>
      <td>Chromcraft Bull-Nose Wood Oval Conference Tabl...</td>
      <td>South</td>
      <td>6611.760</td>
      <td>-2865.0960</td>
      <td>-0.433333</td>
      <td>20</td>
    </tr>
    <tr>
      <th>922</th>
      <td>GBC Ibimaster 500 Manual ProClick Binding System</td>
      <td>South</td>
      <td>2967.822</td>
      <td>-1978.5480</td>
      <td>-0.666667</td>
      <td>13</td>
    </tr>
    <tr>
      <th>850</th>
      <td>Fellowes PB500 Electric Punch Plastic Comb Bin...</td>
      <td>Central</td>
      <td>6100.752</td>
      <td>-1525.1880</td>
      <td>-0.833333</td>
      <td>12</td>
    </tr>
    <tr>
      <th>13</th>
      <td>3.6 Cubic Foot Counter Height Office Refrigerator</td>
      <td>Central</td>
      <td>530.316</td>
      <td>-1378.8216</td>
      <td>-2.600000</td>
      <td>9</td>
    </tr>
    <tr>
      <th>903</th>
      <td>GBC DocuBind P400 Electric Binding System</td>
      <td>South</td>
      <td>1633.188</td>
      <td>-1306.5504</td>
      <td>-0.800000</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1221</th>
      <td>Ibico Hi-Tech Manual Binding System</td>
      <td>Central</td>
      <td>1829.940</td>
      <td>-1189.4610</td>
      <td>-1.310000</td>
      <td>18</td>
    </tr>
    <tr>
      <th>1472</th>
      <td>Riverside Furniture Oval Coffee Table, Oval En...</td>
      <td>East</td>
      <td>3958.530</td>
      <td>-1187.5590</td>
      <td>-0.300000</td>
      <td>23</td>
    </tr>
    <tr>
      <th>969</th>
      <td>GBC ProClick 150 Presentation Binding System</td>
      <td>Central</td>
      <td>695.156</td>
      <td>-1147.0074</td>
      <td>-1.650000</td>
      <td>11</td>
    </tr>
    <tr>
      <th>412</th>
      <td>Bush Advantage Collection Racetrack Conference...</td>
      <td>South</td>
      <td>2714.944</td>
      <td>-1111.4302</td>
      <td>-0.428788</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
pivot = df.groupby(['Sub-Category', 'Region'])['Profit Margin'].mean().unstack()
plt.figure(figsize=(12, 6))
sns.heatmap(pivot, annot=True, cmap='RdYlGn', center=0, fmt=".2f")
plt.title("Average Profit Margin by Sub-Category and Region")
plt.show()

```


    
![png](output_39_0.png)
    


The heatmap shows how profitable each product sub-category is across regions. Green means good margins, red means losses, and yellow is neutral.

The most noticeable issue is Appliances in the Central region, with a highly **negative margin of –1.25**. Other loss-making areas include Binders and Furnishings, especially in Central and South.

On the positive side, **Labels, Paper, Envelopes, and Copiers perform well across all regions, showing consistently strong margins**.

Overall, this confirms that some products are dragging down profits, and specific regions need closer attention. It’s a clear signal of profit leakage, and a strong starting point for business decisions.

## Hypothesis 2: Discount Abuse

**“Giving higher discounts (especially above 30%) leads to lower or negative profit, meaning discounts may be hurting the business instead of helping.”**

### 2.1) Bin Discount into Ranges


```python
# Create discount buckets
df['Discount Bucket'] = pd.cut(df['Discount'],
    bins=[-0.01, 0, 0.1, 0.3, 0.5, 1],
    labels=['0%', '0-10%', '10-30%', '30-50%', '>50%']
)

```

### 2.2) Calculate Average Profit per Discount Bucket


```python
# Group by discount bucket
discount_analysis = df.groupby('Discount Bucket').agg({
    'Profit': ['mean', 'sum'],
    'Sales': 'sum',
    'Quantity': 'sum',
    'Discount': 'count'
}).reset_index()

# Clean column names
discount_analysis.columns = ['Discount Bucket', 'Avg Profit', 'Total Profit', 'Total Sales', 'Total Quantity', 'Order Count']
discount_analysis.sort_values(by='Discount Bucket', inplace=True)
discount_analysis

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
      <th>Discount Bucket</th>
      <th>Avg Profit</th>
      <th>Total Profit</th>
      <th>Total Sales</th>
      <th>Total Quantity</th>
      <th>Order Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0%</td>
      <td>66.900292</td>
      <td>320987.6032</td>
      <td>1.087908e+06</td>
      <td>18267</td>
      <td>4798</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0-10%</td>
      <td>96.055074</td>
      <td>9029.1770</td>
      <td>5.436935e+04</td>
      <td>373</td>
      <td>94</td>
    </tr>
    <tr>
      <th>2</th>
      <td>10-30%</td>
      <td>20.677597</td>
      <td>81387.0201</td>
      <td>8.953795e+05</td>
      <td>14707</td>
      <td>3936</td>
    </tr>
    <tr>
      <th>3</th>
      <td>30-50%</td>
      <td>-156.282991</td>
      <td>-48447.7273</td>
      <td>1.953148e+05</td>
      <td>1177</td>
      <td>310</td>
    </tr>
    <tr>
      <th>4</th>
      <td>&gt;50%</td>
      <td>-89.438144</td>
      <td>-76559.0513</td>
      <td>6.422874e+04</td>
      <td>3349</td>
      <td>856</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(8, 5))
sns.lineplot(data=discount_analysis, x='Discount Bucket', y='Avg Profit', marker='o')
plt.title("Profit Trend by Discount Level")
plt.ylabel("Average Profit per Order")
plt.xlabel("Discount Bucket")
plt.grid(True)
plt.tight_layout()
plt.show()

```


    
![png](output_46_0.png)
    



```python
# Reshape data for stacked bar
discount_bar = discount_analysis[['Discount Bucket', 'Total Sales', 'Total Profit']].set_index('Discount Bucket')

# Plot
discount_bar.plot(kind='bar', stacked=True, figsize=(10, 6), color=['skyblue', 'salmon'])
plt.title("Sales and Profit by Discount Bucket")
plt.ylabel("Amount ($)")
plt.xlabel("Discount Bucket")
plt.axhline(0, color='black', linestyle='--')
plt.tight_layout()
plt.show()

```


    
![png](output_47_0.png)
    


The two charts clearly show that higher discounts don’t always lead to higher profits — in fact, they often lead to losses.

In the line chart, we see that orders with no discount or very low discounts (0–10%) bring in the highest average profit. But as soon as the discount increases beyond 10%, profits start to fall — and beyond 30%, the average profit becomes negative, hitting the lowest point in the 30–50% range.

The stacked bar chart makes it even clearer. While total sales still look high in the 10–30% discount group, the total profit from those orders is much smaller. For discounts above 30%, sales are still happening, but profits actually turn negative — which means the company is losing money even while generating revenue.

### 2.3) Average Profit by Region and Discount Bucket


```python
region_discount = df.groupby(['Region', 'Discount Bucket']).agg({
    'Profit': 'mean'
}).reset_index()

```


```python
plt.figure(figsize=(8, 5))
sns.barplot(data=region_discount, x='Discount Bucket', y='Profit', hue='Region')
plt.axhline(0, color='black', linestyle='--')
plt.title("Average Profit by Discount Level and Region")
plt.ylabel("Average Profit")
plt.tight_layout()
plt.show()

```


    
![png](output_51_0.png)
    


### 2.4) Average Profit by Sub-Category and Discount Bucket


```python
sub_discount = df.groupby(['Sub-Category', 'Discount Bucket']).agg({
    'Profit': 'mean'
}).reset_index()

```


```python
plt.figure(figsize=(12, 8))
sns.barplot(data=sub_discount, x='Discount Bucket', y='Profit', hue='Sub-Category')
plt.axhline(0, color='black', linestyle='--')
plt.title("Average Profit by Discount Level and Sub-Category")
plt.ylabel("Average Profit")
8plt.tight_layout()
plt.show()

```


    
![png](output_54_0.png)
    


The region-wise breakdown shows that profit drops sharply across all regions once the discount crosses 30%. The South region is hit the hardest, with the average profit falling below –$400 per order in the 30–50% discount range. Central and West regions also show strong negative profit trends at higher discount levels. Even at >50% discounts, no region is profitable, clearly signaling that deep discounts are hurting the business across the board.

The sub-category breakdown adds another important layer. Categories like Tables, Supplies, and Binders show consistently negative profits at high discount ranges. Meanwhile, Copiers and Envelopes seem to hold up well — even at moderate discounts — suggesting some products are more resilient to pricing strategies than others.

## Hypothesis 3: Inventory Optimization
**“High-quantity orders and long shipping delays occur more frequently in specific sub-categories, suggesting a need for better inventory planning.”**

### 3.1) Create a Feature: Shipping Delay


```python
df['Shipping Delay'] = (df['Ship Date'] - df['Order Date']).dt.days

```

### 3.2) Group by Sub-Category


```python
inventory_check = df.groupby('Sub-Category').agg({
    'Quantity': 'mean',
    'Shipping Delay': 'mean',
    'Sales': 'sum',
    'Profit': 'sum'
}).reset_index().sort_values(by='Shipping Delay', ascending=False)

```

### 3.3) Shipping Delay vs Quantity


```python
plt.figure(figsize=(12, 6))
sns.scatterplot(
    data=inventory_check,
    x='Quantity', y='Shipping Delay',
    size='Sales', hue='Profit',
    palette='coolwarm', sizes=(100, 800), legend=False
)

# Add labels
for i in range(len(inventory_check)):
    plt.text(
        x=inventory_check['Quantity'].iloc[i] + 0.01,
        y=inventory_check['Shipping Delay'].iloc[i],
        s=inventory_check['Sub-Category'].iloc[i],
        fontsize=9
    )

plt.title("Shipping Delay vs Quantity (Bubble = Sales, Color = Profit)")
plt.xlabel("Avg Quantity Ordered")
plt.ylabel("Avg Shipping Delay (days)")
plt.grid(True)
plt.tight_layout()
plt.show()

```


    
![png](output_62_0.png)
    


Not all inventory delays are bad — some high-demand items like Phones and Chairs are profitable despite their shipping lag, suggesting they deserve better stock planning, not cuts. However, categories like Appliances and Tables show both operational delays and consistent losses across regions, making them strong candidates for pricing reviews, vendor renegotiation, or removal from key warehouses. Binders present a mixed case: they're profitable in some regions but severely unprofitable in Central, indicating a need for regional pricing or promotion adjustments.

## Hypothesis 4: Time to Profit Curve
**“The company’s profitability improves over time as order volume grows — but some months or seasons may bring losses or volatility.”**

### 4.1)  Extract Year-Month from Order Date


```python
df['Order Month'] = df['Order Date'].dt.to_period('M')

```

### 4.2) Group by Month: Sales, Profit, Orders


```python
monthly = df.groupby('Order Month').agg({
    'Sales': 'sum',
    'Profit': 'sum',
    'Order ID': 'nunique'
}).reset_index()
monthly['Order Month'] = monthly['Order Month'].dt.to_timestamp()

```

### 4.3) Plot: Time Series of Sales and Profit


```python
plt.figure(figsize=(12, 6))
sns.lineplot(data=monthly, x='Order Month', y='Profit', label='Profit', color='crimson')
sns.lineplot(data=monthly, x='Order Month', y='Sales', label='Sales', color='steelblue')
plt.title("Monthly Sales vs Profit Over Time")
plt.ylabel("Amount ($)")
plt.xlabel("Order Month")
plt.axhline(0, color='black', linestyle='--')
plt.grid(True)
plt.tight_layout()
plt.show()

```


    
![png](output_70_0.png)
    


The business is growing, but not always profiting. To truly scale, it needs to tighten operations, optimize discounting, and focus on profitable SKUs — especially during high-volume months where volume may be masking value loss.


```python

```
