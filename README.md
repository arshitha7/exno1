# Exno:1
Data Cleaning Process

## AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

## Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

## Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

## Coding and Output
###                                            Data Cleaning
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv");
df
```
![image](https://github.com/user-attachments/assets/d7c768b7-ede3-411b-8936-fd3b1b8f4a79)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/2b11b34a-e389-4a2b-a3e3-5dc23d3c5235)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/11ee6327-859b-4436-99f3-70fb560bd0fd)
```
 df.dropna()
```
![image](https://github.com/user-attachments/assets/cef4fae8-f52a-4401-941f-3a3e35bf7d99)
```
 df.fillna(0)
```
![image](https://github.com/user-attachments/assets/09e5dd18-e961-4531-b4ec-3fe2f4aa097d)
```
 df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/0a783798-3e3c-4add-bfa4-1381ad8bd17c)
```
 df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/c859dde4-0251-4d02-a525-f6657dcd5070)
```
 df_dropped = df.dropna()
 df_dropped
```
![image](https://github.com/user-attachments/assets/d497537e-7367-4e95-842a-4c8f677ba640)
```
 df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/e9651445-d90c-4539-8437-20cf82ffa218)
###  IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/6603b793-624b-4d55-a33b-e9c294ad666c)
```
 ir.describe()
```
![image](https://github.com/user-attachments/assets/fc397da7-d956-4049-b6a5-0c1080d5fd3f)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/05574c69-ace2-427c-8794-4c32ee29483e)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/69305f0d-6a19-4979-ba6a-3f48b21e0f83)
```
 rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
 rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/165f647f-12c0-46e9-add1-b24a9c0f33b4)
```
 delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
 delid
```
![image](https://github.com/user-attachments/assets/541b8443-603b-4ee2-8eec-650c0ca6f577)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/1c96f345-8483-48a9-b38c-9900f744b7fe)
###  Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/5b624f5f-ed24-41d4-8577-6bb53cf0eba6)
```
 df = pd.read_csv("heights.csv")
 q1 = df['height'].quantile(0.25)
 q2 = df['height'].quantile(0.5)
 q3 = df['height'].quantile(0.75)
 iqr = q3-q1
 iqr
```
![image](https://github.com/user-attachments/assets/c2e7d821-fbe3-4d95-be24-23dae86c315a)
```
 low = q1- 1.5*iqr
 low
```
![image](https://github.com/user-attachments/assets/ebeb6ebe-ebac-452f-869f-8738ef847854)
```
 high = q3 + 1.5*iqr
 high
```
![image](https://github.com/user-attachments/assets/422d317b-b059-4b2d-b70b-a687670523b2)
```
 df1 = df[((df['height'] >=low)& (df['height'] <=high))]
 df1
```
![image](https://github.com/user-attachments/assets/33ed49cb-6424-4dfb-8167-41a3ffa15ce5)
```
 z = np.abs(stats.zscore(df['height']))
 z
```
![image](https://github.com/user-attachments/assets/3002191f-7616-4470-b849-37aaff00ca71)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/41b01e90-1760-4726-ba29-5b6c014e140d)





# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
