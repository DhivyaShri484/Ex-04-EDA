# Ex-04-EDA

# AIM
To perform EDA on the given data set.

# Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM
# STEP 1
Import the required packages(pandas,numpy,seaborn).
# STEP 2
Read and Load the Dataset.
# STEP 3
Remove the null values from the data and remove the outliers.
# STEP 4
Remove the non numerical data columns using drop() method.
# STEP 5:
returns object containing counts of unique values using (value_counts()).
# STEP 6:
Plot the counts in the form of Histogram or Bar Graph.
# STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).
# STEP 8:
Save the final data set into the file.

# CODE
```
Program 
Developed by: Dhivya Shri.B
Register no:212221230009

import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("supermarket.csv")
df

#cleaning dataset
#checking for null values
df.isnull().sum()

#data is cleaned, proceed to remove outliers
#checking for outliers
df.boxplot()

#removing outliers
cols = ['Unit price','Quantity','Tax 5%','Total','cogs','gross margin percentage','gross income','Rating']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df
df.boxplot()

#outliers removed
# performing data analysis
# performing data analysis
#statistical analysis for single data group
df['Branch'].value_counts()
df['City'].value_counts()
df['Customer type'].value_counts()
df['Gender'].value_counts()
df['Product line'].value_counts()
df['Quantity'].value_counts()
df['Payment'].value_counts()

#statistical analysis for two data groups
pd.crosstab(df["Customer type"],df["Branch"])
pd.crosstab(df["Customer type"],df["City"])
pd.crosstab(df["Customer type"],df["Gender"])
pd.crosstab(df["Customer type"],df["Payment"])
pd.crosstab(df["Product line"],df["Quantity"])

#statistical analysis for multiple data groups
#analysing pairwise correlation of columns in dataset
df.corr()

#graphical analysis of categorical data--univariate
sns.countplot(x="Branch",data=df)
sns.countplot(x="City",data=df)
sns.countplot(x="Customer type",data=df)
sns.countplot(x="Payment",data=df)
sns.countplot(x="Gender",data=df)
sns.countplot(y="Product line",data=df)
sns.countplot(x="Quantity",data=df)

#graphical analysis of non-categorical data or data with multiple categories--univariate
sns.displot(df["Unit price"])
sns.displot(df["Tax 5%"])
sns.displot(df["cogs"])
sns.displot(df["gross income"])

#graphical analysis of categorical data--bivariate
sns.countplot(x="City",hue="Customer type",data=df)
sns.countplot(x="Branch",hue="Customer type",data=df)
sns.countplot(x="Gender",hue="Customer type",data=df)
sns.countplot(x="Payment",hue="Customer type",data=df)
sns.countplot(y="Product line",hue="Quantity",data=df)

#graphical analysis of non-categorical data or data with multiple categories--bivariate
sns.displot(df[df["City"]=='Yangon']["cogs"])
sns.displot(df[df["City"]=='Mandalay']["cogs"])
sns.displot(df[df["City"]=='Naypyitaw']["cogs"])

sns.displot(df[df["Product line"]=='Health and beauty']["Gender"])
sns.displot(df[df["Product line"]=='Electronic accessories']["Gender"])
sns.displot(df[df["Product line"]=='Home and lifestyle']["Gender"])
sns.displot(df[df["Product line"]=='Sports and travel']["Gender"])
sns.displot(df[df["Product line"]=='Food and beverages']["Gender"])
sns.displot(df[df["Product line"]=='Fashion accessories']["Gender"])

sns.displot(df[df["Gender"]=='Male']["gross income"])
sns.displot(df[df["Gender"]=='Female']["gross income"])

#Graphical representation of data--multivariate 
df.drop('gross margin percentage',axis=1,inplace=True)
sns.heatmap(df.corr(),annot=True)
```

# OUPUT
# Original Data
![image](https://user-images.githubusercontent.com/94505585/164959885-669c4ee6-48df-4961-8cfd-04f56b72f55f.png)

# Data Cleaning Process
![image](https://user-images.githubusercontent.com/94505585/164959900-6afe1e8d-a307-48b1-ab63-fc0cd545b071.png)

# Removing Outliers Process
![image](https://user-images.githubusercontent.com/94505585/164959920-f181034e-85fd-4d16-a755-f90677c1259a.png)
![image](https://user-images.githubusercontent.com/94505585/164959926-e5841326-ff84-4a5d-b98a-32ba83784aca.png)
![image](https://user-images.githubusercontent.com/94505585/164959945-368298ec-c81a-4cc7-930a-c2dbc9e46ddd.png)

# Performing Data analysis
# Statistical Analysis for Single data group
![image](https://user-images.githubusercontent.com/94505585/164960047-a161ac3e-8ef0-48e9-b8c2-19adc17f754d.png) ![image](https://user-images.githubusercontent.com/94505585/164960059-f892b925-5960-45b8-bdef-84cadfd75a7a.png) ![image](https://user-images.githubusercontent.com/94505585/164960070-ba8b4015-11ab-4dd1-85d2-b37244503525.png) ![image](https://user-images.githubusercontent.com/94505585/164960079-4f8328b5-cb38-44c8-a288-1668511b2746.png) ![image](https://user-images.githubusercontent.com/94505585/164960092-fcc0fa73-0fe9-411a-910f-98c0bb91e633.png) ![image](https://user-images.githubusercontent.com/94505585/164960100-b736bba2-d6b7-4eea-9210-f148c8c04bb7.png) ![image](https://user-images.githubusercontent.com/94505585/164960109-1ff5f019-ffb9-408a-9391-72fa9d067181.png)

# Statistical analysis for two data groups
![image](https://user-images.githubusercontent.com/94505585/164960138-6f5106c0-5122-4142-bdab-ac48f3bebe3d.png) ![image](https://user-images.githubusercontent.com/94505585/164960143-a345f6f4-4578-4431-aa0d-95a3a6284ad8.png)
![image](https://user-images.githubusercontent.com/94505585/164960152-bba56851-75ff-470e-a9fc-a439fcd25f59.png) ![image](https://user-images.githubusercontent.com/94505585/164960161-fe8e03ba-a217-4eab-85df-17789092455c.png)
![image](https://user-images.githubusercontent.com/94505585/164960167-0e07f4dc-dceb-4792-ac40-f75d71601f2c.png)

# Pairwise correlation of columns in dataset
![image](https://user-images.githubusercontent.com/94505585/164960178-2ad031bb-0536-49f1-8ba1-1bd7544b3797.png)

# Graphical analysis of categorical data--univariate
![image](https://user-images.githubusercontent.com/94505585/164960192-fc55e0e7-5a12-47a5-a559-a4cc3a351b40.png) ![image](https://user-images.githubusercontent.com/94505585/164960198-bdee4ea6-0c7b-4df2-a7a1-75355bdf2e1c.png)
![image](https://user-images.githubusercontent.com/94505585/164960203-eaff91e0-b114-48d1-b988-183238546e08.png) ![image](https://user-images.githubusercontent.com/94505585/164960207-52cd66d6-8e6e-4456-9e65-f32b9e9c0330.png)
![image](https://user-images.githubusercontent.com/94505585/164960218-9e5cc170-a590-43ad-8d0b-c9b8985a5e11.png)
![image](https://user-images.githubusercontent.com/94505585/164960221-7246bfe7-7c8f-473e-9981-5618ade0a44e.png) ![image](https://user-images.githubusercontent.com/94505585/164960224-8394e89b-db33-4b15-8cff-fb0dfcd2c942.png)

# Graphical analysis of non-categorical data or data with multiple categories--univariate
![image](https://user-images.githubusercontent.com/94505585/164960234-9219f026-918a-418f-8b23-9eff7c103d42.png) ![image](https://user-images.githubusercontent.com/94505585/164960241-8ebc8e04-2dcb-4149-87af-91066bc1bb09.png)
![image](https://user-images.githubusercontent.com/94505585/164960253-c2b66266-380f-4689-b497-02f47d7f057e.png) ![image](https://user-images.githubusercontent.com/94505585/164960259-1d3b3b7d-b590-40df-8ac2-f92536abf49c.png)

# Graphical analysis of categorical data--bivariate
![image](https://user-images.githubusercontent.com/94505585/164960286-68779450-52d2-4763-8761-0bc6fdb45c62.png) ![image](https://user-images.githubusercontent.com/94505585/164960290-4f71e00b-796d-4109-b1d7-ca161a6fba46.png)
![image](https://user-images.githubusercontent.com/94505585/164960296-8074bd4f-27c3-4640-b9c5-d89890e3e612.png) ![image](https://user-images.githubusercontent.com/94505585/164960309-97c62f46-5695-429d-9f19-ba84a5297cb5.png)
![image](https://user-images.githubusercontent.com/94505585/164960320-542b5809-f2c7-4019-90a9-5b1a5c427bc9.png)

# Graphical analysis of non-categorical data or data with multiple categories--bivariate
![image](https://user-images.githubusercontent.com/94505585/164960340-b5fa9898-5a7f-4535-9c3e-5d443cb3f59b.png)
![image](https://user-images.githubusercontent.com/94505585/164960347-a12fbb43-2724-445f-83d6-2a9030ba6721.png)

![image](https://user-images.githubusercontent.com/94505585/164960351-e4a1f671-b6f8-4880-b9da-01b35f929d9d.png)
![image](https://user-images.githubusercontent.com/94505585/164960357-bcbc80ce-e206-43d2-8668-17d5d4898779.png)
![image](https://user-images.githubusercontent.com/94505585/164960361-ea9168c6-ef3d-44b2-ae3c-d3bd86947729.png)
![image](https://user-images.githubusercontent.com/94505585/164960364-2106f7d4-14de-4a2d-a2ef-75ac04e38a82.png)
![image](https://user-images.githubusercontent.com/94505585/164960372-35563f46-0021-402d-9b38-a0cd0b48243a.png)
![image](https://user-images.githubusercontent.com/94505585/164960376-4f7275ec-986b-4c41-a111-8d386c2dc739.png)

# Graphical representation of data--multivariate
![image](https://user-images.githubusercontent.com/94505585/164960390-bae650c6-e702-4fe8-b0c1-3c8af67a0511.png)

# RESULT
The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.












 



 






 

















