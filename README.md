# Exno:1
Data Cleaning Process
# NAME:A.DHARANI
# REF NO:25013947

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
            # Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```pythonimport pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df

```
![421953769-560c47ff-ca89-4c31-b6be-ef000bddbb72](https://github.com/user-attachments/assets/5b2820ea-25f0-4fbf-acff-836bc0f8a570)
```python
df.shape
```
![421954623-0c433834-9790-4dd7-916f-c723bbe25deb](https://github.com/user-attachments/assets/81deddac-bde1-41a9-9de6-ddc3bf604380)
```python
df.describe()
```
![421955212-5cab27f0-972e-4706-bda0-e1665d67184d](https://github.com/user-attachments/assets/6c5c6d1b-4021-47c2-94e1-0181a1dddee1)
```python
df.info()
```
![421955650-330fbd4b-4b55-46d2-9e3c-d3dd14611e77](https://github.com/user-attachments/assets/e65c155f-a4a4-4738-802e-215c34a5515b)
```python
df.head(5)
```
![421956003-59eb2db9-d8cd-4765-9504-be0ed12d8b56](https://github.com/user-attachments/assets/276b39cd-b137-4345-9893-499da54417a1)
```python
df.tail(2)
```
![421956281-04dbf369-665f-4119-9d49-a3c3bc3bd809](https://github.com/user-attachments/assets/658028bb-b6b0-4d13-afa1-5155f8110a6b)
```python
df.dropna(how='any').shape
```
![421956606-a077d1d0-b3d3-48da-8bc2-9e0556631770](https://github.com/user-attachments/assets/ce86b109-00b5-4d02-b87e-503f64a1aaf5)
```python
df.isnull().sum()
```
![421956858-eb446df1-d2b1-4b38-8a79-7343e2b2c930](https://github.com/user-attachments/assets/18e93c45-1979-4fdf-b573-4870eccbcafe)

```python
mn=df.TOTAL.mean()
df.TOTAL.fillna(mn,inplace=True)
df
```
![421957209-182c114a-5e8b-42ed-81f8-c5567b8fa769](https://github.com/user-attachments/assets/c88e80a4-481e-481f-9434-972b4aeb97ba)
```python
df.M1.dropna(inplace=True)
df
```
![421957436-ddad8115-ae82-4957-b46d-b806f5780408](https://github.com/user-attachments/assets/e499e9b9-bbd2-4178-82f4-bf6b2ae8fc5e)
```python
df.isna().sum()
```
![421957775-623a3810-df7e-42f2-8e11-320a3bd76124](https://github.com/user-attachments/assets/5031d8e8-5469-4583-b5e3-03259f8b9a22)
```python
df['M1'].fillna(method='ffill',inplace=True)
```
![421957999-b9e327d5-6569-4f0a-b041-de09090fb5b7](https://github.com/user-attachments/assets/f0bf1708-566f-46f4-9f0d-f89348aa90dd)

```python
df.duplicated()
```
![421958279-65a1e504-dbda-4fff-afa0-2bdd90be1321](https://github.com/user-attachments/assets/842fcc6c-e9d8-42c3-b3bc-d5b57a877494)
```python
df['DOB']
```
![421958514-634b89c5-f5d6-466a-a7b4-992c2f0714ef](https://github.com/user-attachments/assets/7de15d09-b336-4a2a-ba56-3e2e642d3a56)
```python
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![421958779-910da0e4-85b6-45cd-a1cb-48b1f525d148](https://github.com/user-attachments/assets/9a56eb3d-0886-45b3-88d0-5abb8717f159)
```python
import pandas as pd
import seaborn as sns
import numpy as np
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![421959048-93446204-963d-4f91-876a-eeb35cd9be70](https://github.com/user-attachments/assets/67cd225d-966f-41fa-ac9b-d963ca0c6298)
```python
sns.boxplot(data=af)
```
![421959340-952fff2b-ecc0-4dcf-b666-ac2296bffd7c](https://github.com/user-attachments/assets/dea0255b-5ef4-4b5d-9400-6ecb30af42a1)
```python
sns.scatterplot(data=af)
```
![421959508-258f4358-48d4-4217-a296-10dd7cbcac06](https://github.com/user-attachments/assets/7d62bf53-00c1-484c-90b7-d22daa028ab1)
```python
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![421959852-b9e1cbbb-0959-49d3-b1a3-9a4505beb782](https://github.com/user-attachments/assets/243c339c-8daf-436f-97ff-1bbe873ff1c7)
```python
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-q1
IQR
```
![421960180-937d8653-ce86-4c2a-9f25-915be2d65101](https://github.com/user-attachments/assets/df6b10e4-deeb-4c0a-9701-b482a8abefb4)
```python
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
```
![421960442-3dd079fe-316d-43da-bb68-47029cb6267f](https://github.com/user-attachments/assets/65f9c972-26f6-4c79-986a-9909c25dc66b)
```python
upper_bound
```
![421960679-c285184c-d142-4c59-b641-b8b738f1d856](https://github.com/user-attachments/assets/6842e957-ab84-4644-85c0-f3857f9b1457)
```python
outliers = [x for x in age if (x < lower_bound.iloc[0]) or (x > upper_bound.iloc[0])]
print("q1",q1)
print("q3",q3)
print("iqr",iqr)
print("lower bound",lower_bound)
print("upper bound",upper_bound)
print("outliers",outliers)
```
![421960949-9cacfb9b-9d20-4d59-bcf7-0c123115c7a3](https://github.com/user-attachments/assets/2d2c817a-63ae-47bc-9497-b76f1ceb8a8a)
```python
af=af[((af>=lower_bound)&(af<=upper_bound))]
```
![421961171-83aa02f6-1eef-450f-83f8-f764bb14ac59](https://github.com/user-attachments/assets/621778ae-ec17-4d1e-868a-2c690dda3d00)
```python
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![421961413-4f9585a5-422d-478d-8654-ebe5c58b880e](https://github.com/user-attachments/assets/b956ae3e-f810-4fd3-a4e9-213b7515e2ca)
```python
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
    print('Outlier in dataset is:',outlier)
```
![421961707-67511b46-8bde-4cfc-9133-b45ec8eb7d93](https://github.com/user-attachments/assets/2b95ed61-e36c-47bd-9990-125d455b6335)
```python
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}

df=pd.DataFrame(data)
df
```
![421962118-0b89160f-4f94-41b0-9303-99308683b98f](https://github.com/user-attachments/assets/15499fa1-3dde-4e62-98d9-8d45991b0f2a)
```python
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![421962406-8ab64742-3d5a-448b-aa6a-675485f233c0](https://github.com/user-attachments/assets/5a7fc8ea-b942-4e52-969d-8b1e40e085bf)
```python
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]


import numpy as np
out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out

op=d_o(val)
op
```
![421962803-b10e3ff9-2f75-46f3-91a2-f5038a2783de](https://github.com/user-attachments/assets/5f917e35-01f6-4792-a6ce-e9e0fb15c980)


# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method
