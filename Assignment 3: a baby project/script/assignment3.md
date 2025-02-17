```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
file_path = "travelq.csv"  # Change this to the correct path
df = pd.read_csv(file_path)

# Display basic info
df.info()
df.head()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 126761 entries, 0 to 126760
    Data columns (total 21 columns):
     #   Column                  Non-Null Count   Dtype  
    ---  ------                  --------------   -----  
     0   ref_number              126759 non-null  object 
     1   disclosure_group        105235 non-null  object 
     2   title_en                126053 non-null  object 
     3   title_fr                126027 non-null  object 
     4   name                    126213 non-null  object 
     5   purpose_en              126743 non-null  object 
     6   purpose_fr              126650 non-null  object 
     7   start_date              126761 non-null  object 
     8   end_date                125957 non-null  object 
     9   destination_en          126113 non-null  object 
     10  destination_fr          126045 non-null  object 
     11  airfare                 122129 non-null  float64
     12  other_transport         123310 non-null  float64
     13  lodging                 124301 non-null  float64
     14  meals                   125561 non-null  float64
     15  other_expenses          115738 non-null  float64
     16  total                   126572 non-null  float64
     17  additional_comments_en  19295 non-null   object 
     18  additional_comments_fr  18095 non-null   object 
     19  owner_org               126761 non-null  object 
     20  owner_org_title         126761 non-null  object 
    dtypes: float64(6), object(15)
    memory usage: 20.3+ MB
    




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
      <th>ref_number</th>
      <th>disclosure_group</th>
      <th>title_en</th>
      <th>title_fr</th>
      <th>name</th>
      <th>purpose_en</th>
      <th>purpose_fr</th>
      <th>start_date</th>
      <th>end_date</th>
      <th>destination_en</th>
      <th>...</th>
      <th>airfare</th>
      <th>other_transport</th>
      <th>lodging</th>
      <th>meals</th>
      <th>other_expenses</th>
      <th>total</th>
      <th>additional_comments_en</th>
      <th>additional_comments_fr</th>
      <th>owner_org</th>
      <th>owner_org_title</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>T-20120-P11-001</td>
      <td>SLE</td>
      <td>Chief Executive Officer</td>
      <td>Président directeur-général</td>
      <td>Philip Rizcallah</td>
      <td>To attend meeting with Saskatchewan Provincial...</td>
      <td>Pour assister à une réunion avec le gouverneme...</td>
      <td>2020-02-03</td>
      <td>2020-02-04</td>
      <td>Regina, Saskatchewan, Canada</td>
      <td>...</td>
      <td>646.17</td>
      <td>117.26</td>
      <td>157.78</td>
      <td>197.25</td>
      <td>0.0</td>
      <td>1118.46</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>casdo-ocena</td>
      <td>Accessibility Standards Canada | Normes d’acce...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>T-2020-P11-0001</td>
      <td>SLE</td>
      <td>Chair</td>
      <td>Président</td>
      <td>Bérubé, Paul-Claude</td>
      <td>Board members meeting</td>
      <td>Réunion du conseil</td>
      <td>2020-02-09</td>
      <td>2020-02-13</td>
      <td>Vancouver, British Columbia, Canada</td>
      <td>...</td>
      <td>1104.27</td>
      <td>189.72</td>
      <td>841.31</td>
      <td>461.84</td>
      <td>NaN</td>
      <td>2597.14</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>casdo-ocena</td>
      <td>Accessibility Standards Canada | Normes d’acce...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>T-2020-P11-0002</td>
      <td>SLE</td>
      <td>Vice Chair</td>
      <td>vice-présidente</td>
      <td>Reid, Mary</td>
      <td>Board members meeting</td>
      <td>Réunion du conseil</td>
      <td>2020-02-09</td>
      <td>2020-02-14</td>
      <td>Vancouver, British Columbia, Canada</td>
      <td>...</td>
      <td>2511.31</td>
      <td>132.48</td>
      <td>785.65</td>
      <td>591.00</td>
      <td>108.3</td>
      <td>4128.74</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>casdo-ocena</td>
      <td>Accessibility Standards Canada | Normes d’acce...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>T-2020-P11-0003</td>
      <td>SLE</td>
      <td>Board Of Directors</td>
      <td>Membre du conseil de direction</td>
      <td>McLaughlin, Joseph</td>
      <td>Board members meeting</td>
      <td>Réunion du conseil</td>
      <td>2020-02-09</td>
      <td>2020-02-12</td>
      <td>Vancouver, British Columbia, Canada</td>
      <td>...</td>
      <td>NaN</td>
      <td>58.32</td>
      <td>630.99</td>
      <td>264.60</td>
      <td>123.0</td>
      <td>1076.91</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>casdo-ocena</td>
      <td>Accessibility Standards Canada | Normes d’acce...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>T-2020-P11-0004</td>
      <td>SLE</td>
      <td>Board Of Directors</td>
      <td>Membre du conseil de direction</td>
      <td>Haan, Maureen</td>
      <td>Board members meeting</td>
      <td>Réunion du conseil</td>
      <td>2020-02-09</td>
      <td>2020-02-12</td>
      <td>Vancouver, British Columbia, Canada</td>
      <td>...</td>
      <td>880.99</td>
      <td>192.76</td>
      <td>630.99</td>
      <td>332.45</td>
      <td>NaN</td>
      <td>2037.19</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>casdo-ocena</td>
      <td>Accessibility Standards Canada | Normes d’acce...</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>



The most expensive trip in the dataset belongs to John Murray, totaling `$51,393.34`. This is significantly higher than the second most expensive trip at `$38,983.15`. Interestingly, Global Affairs Canada appears multiple times in the top 10, suggesting that diplomatic and international engagements drive up travel costs. The high expenses could be due to multi-country visits, extended stays, or premium travel requirements. Further analysis into airfare, lodging, and transportation costs for these trips could provide insights into why they are so costly


```python
# Top 10 most expensive trips
top_expensive_trips = df.sort_values(by="total", ascending=False).head(10)

# Display relevant columns
top_expensive_trips[["name", "owner_org_title", "destination_en", "total"]]
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
      <th>name</th>
      <th>owner_org_title</th>
      <th>destination_en</th>
      <th>total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>26597</th>
      <td>Murray, John</td>
      <td>College of Immigration and Citizenship Consult...</td>
      <td>Toronto, Ontario, Canada</td>
      <td>51393.34</td>
    </tr>
    <tr>
      <th>76689</th>
      <td>Heidi Hulan</td>
      <td>Global Affairs Canada | Affaires mondiales Canada</td>
      <td>Vilnius and Jakarta</td>
      <td>38983.15</td>
    </tr>
    <tr>
      <th>26391</th>
      <td>Murray, John</td>
      <td>College of Immigration and Citizenship Consult...</td>
      <td>Toronto, Ontario, Canada</td>
      <td>38516.95</td>
    </tr>
    <tr>
      <th>76256</th>
      <td>Heidi Hulan</td>
      <td>Global Affairs Canada | Affaires mondiales Canada</td>
      <td>Japan</td>
      <td>38248.20</td>
    </tr>
    <tr>
      <th>67523</th>
      <td>Melissa Lantsman</td>
      <td>Global Affairs Canada | Affaires mondiales Canada</td>
      <td>Kazakhstan, UAE, Afghanistan, Vietnam and Hong...</td>
      <td>37957.87</td>
    </tr>
    <tr>
      <th>75144</th>
      <td>Dominic Barton</td>
      <td>Global Affairs Canada | Affaires mondiales Canada</td>
      <td>Ottawa and Washington</td>
      <td>37327.94</td>
    </tr>
    <tr>
      <th>67521</th>
      <td>Paul Terrien</td>
      <td>Global Affairs Canada | Affaires mondiales Canada</td>
      <td>Kazakhstan, UAE, Afghanistan, Vietman and Hong...</td>
      <td>37213.84</td>
    </tr>
    <tr>
      <th>67531</th>
      <td>Lawrence Cannon</td>
      <td>Global Affairs Canada | Affaires mondiales Canada</td>
      <td>Kazakhstan, UAE, Afghanistan, Vietnam and Hong...</td>
      <td>36944.79</td>
    </tr>
    <tr>
      <th>75459</th>
      <td>Bruce Christie</td>
      <td>Global Affairs Canada | Affaires mondiales Canada</td>
      <td>Singapore and Sydney, Australia</td>
      <td>33351.54</td>
    </tr>
    <tr>
      <th>92443</th>
      <td>Boivin, Steve</td>
      <td>National Defence | Défense nationale</td>
      <td>Canberra &amp; Sydney, Australia / Honolulu, Hawaii</td>
      <td>32539.97</td>
    </tr>
  </tbody>
</table>
</div>



This summary shows that John Murray has spent the most on a single trip, with a total of $51,393.34, compared to the others.


```python
# Count the top 10 most visited destinations
top_destinations = df["destination_en"].value_counts().head(10)

# Plot
plt.figure(figsize=(12,6))
sns.barplot(x=top_destinations.values, y=top_destinations.index, 
            palette=sns.light_palette("green", reverse=False, n_colors=len(top_destinations)), 
            hue=top_destinations.values)
plt.xlabel("Number of Trips")
plt.ylabel("Destination")
plt.title("Top 10 Most Visited Destinations")

plt.show()
```


    
![png](output_4_0.png)
    


Toronto appears as the most visited destination for government travel, followed closely by Ottawa. However, the dataset contains duplicate listings, such as variations in spelling or additional location details. This could slightly skew the rankings. The high number of visits to Toronto and Ottawa suggests that a large portion of government travel is domestic, likely for administrative meetings, policy discussions, and federal coordination. It would be valuable to compare these findings against international travel destinations to understand the scope of foreign engagements


```python
# Histogram of total expenses
plt.figure(figsize=(10,5))
sns.histplot(df["total"], bins=50, kde=True, color="royalblue")
plt.xlabel("Total Expense ($)")
plt.ylabel("Frequency")
plt.title("Distribution of Total Expenses")

plt.xticks(ticks=range(0, int(df["total"].max()) + 1000, 1000))
plt.xlim(-1000, 15000)

plt.show()
```


    
![png](output_6_0.png)
    


The distribution of total expenses shows that the majority of trips cost under `$1,000`, with a steep decline in frequency as costs rise. This suggests that most government trips are short and relatively inexpensive. However, a few trips exceed `$50,000` (have limited the graph to show a better visualization for the lower cost trips), indicating special cases of high expenditure. These could be long-term assignments, international diplomatic missions, or large delegation travels. The presence of extreme outliers could impact the overall budget analysis, and it may be necessary to investigate whether these costs align with standard travel policies.


```python
#Top 8 organizations based on total expenses
expense_columns = ['airfare', 'other_transport', 'lodging', 'meals', 'other_expenses']

grouped_expenses = df.groupby('title_en')[expense_columns].sum()

top_titles = grouped_expenses.sum(axis=1).sort_values(ascending=False).head(8).index
top_expenses = grouped_expenses.loc[top_titles]

ax = top_expenses.plot(kind='bar', stacked=True, figsize=(14, 8), colormap="Set2", edgecolor="black")

plt.title("Top 8 Total Expenses by Organization Title (Stacked)", fontweight="bold")
plt.xlabel("Organization Title")
plt.ylabel("Expense Amount ($)")

plt.xticks(rotation=30, ha="right", fontsize=12)
plt.yticks(fontsize=12)

ax.yaxis.set_major_formatter(mticker.FuncFormatter(lambda x, _: f"{int(x):,}"))

plt.legend(title="Expense Type", fontsize=12, title_fontsize=13, loc="upper right")

plt.grid(axis="y", linestyle="--", alpha=0.7)

plt.tight_layout()
plt.show()
```


    
![png](output_8_0.png)
    


The stacked bar chart displays the total expenses for the top eight government organization titles, broken down by expense type (airfare, lodging, transport, meals, and other expenses). The Press Secretary, Deputy Minister, and Chief of Staff have the highest total expenses, each exceeding $6 million, indicating frequent and possibly international travel. Airfare and lodging account for the majority of costs across all positions, highlighting that these roles require extensive travel.

The Minister and President roles also have substantial expenses but slightly lower compared to the top three, suggesting that while they travel often, their lodging or meal costs may be more controlled. Interestingly, Assistant Deputy Ministers and Associate Deputy Ministers show significantly lower expenses, indicating that their travel may be more localized or less frequent.

Anomalies could exist due to differences in trip duration, class of travel, or international vs. domestic flights. Further analysis into individual expense reports or justification documents would provide better insights into why some roles incur higher travel costs than others. Addressing potential cost inefficiencies, such as reviewing lodging choices or transport expenses, could lead to significant budget optimizations in government spending.
