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


## Coding:
Developed by: Anbu Vinotha.S Registration NUmber: 212223230015
## Data Cleaning:
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/d3d690eb-6b3f-474a-b26b-962e51c43ee4)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/4657afb0-8fd5-4595-aa03-3a7b539e9d95)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/f645628e-95e5-4049-b198-d61ea549d6a3)
```
df.dropna()

```
![image](https://github.com/user-attachments/assets/f2530325-38d1-4cb4-a027-e46cc54d3e0b)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/976e827e-0ae5-4294-993c-3437ae49aa7f)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/9ac154ff-de55-4894-b5a7-96f151a36daf)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/29b4263d-071a-431f-a908-031a276f57b1)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/9924299f-9f01-439f-8d25-9c4382de438a)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/f90bfd4f-3255-493c-9365-f692526fdd9b)
## IQR (Inter Quartile Range):
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/ff7e2838-b990-44d5-8f5d-0e8ca4bb3863)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/7876dcfa-99e9-4528-aa81-95f602ebae82)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/e47c6ee2-50c0-4444-9a8c-622439bfc3fa)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/4293484f-4163-4fab-a39e-ddf2acb15c70)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/74661ca7-a789-47c4-8274-115a0dc7805d)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/c4498bbc-1ee5-49f0-b1ac-e3020c3190ea)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/aff43c73-0dba-4384-b1f1-1a66906f2451)

## Z Score:
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/53aef7d4-0bb1-4299-ae6b-53a24f07788a)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/f49a1ba6-7e3c-4ae0-a3ac-2fdbf8a5f66d)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/48356e8d-965e-4cd5-8435-513d6ddff326)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/5904ae49-d822-4913-90ec-0384a1bba5a8)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/df30773f-e186-46c8-9557-f1d7b32c5915)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/f53a084c-9c41-4635-b298-433f5bffc19c)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/79f298d9-3bba-4017-a1c5-7be1b1693a5c)



## Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.


























# Result
          <<include your Result here>>
