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
```
import pandas as pd
df = pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![img-1](https://github.com/user-attachments/assets/1f571561-7a91-4f27-9dc1-c7dae822c477)
```
df.info()
```
![img-2](https://github.com/user-attachments/assets/9bfa3146-2682-4421-8f59-de79de1bc7e1)
```
df.describe()
```
![img-3](https://github.com/user-attachments/assets/1fa3ed89-69bb-498c-aa90-62a82cca57a2)
```
df.shape
```
![img-4](https://github.com/user-attachments/assets/319fcf9a-6167-472b-a94e-e55a241ca104)
```
df.head(10)
```
![img-5](https://github.com/user-attachments/assets/dabc22a9-02d1-4f39-ab42-03936b34ff30)
```
df.tail(10)
```
![img-6](https://github.com/user-attachments/assets/13da6168-713e-4134-aeac-6de075395436)
```
df.isna().sum()
```
![img-7](https://github.com/user-attachments/assets/6bae0850-85df-4ec0-af42-7dddf9037a22)
```
df.dropna(how='any').shape
```

![img-8](https://github.com/user-attachments/assets/676708a1-409a-42af-8fca-d859a6ca6e0a)

```
df.shape
```

![img-9](https://github.com/user-attachments/assets/50a65685-62c9-4d19-b21d-5cd53e7d618c)

```
x = df.dropna(how='any')
x
```

![img-10](https://github.com/user-attachments/assets/b096bd65-f15c-4956-a251-e92833b43e97)

```
mn = df.TOTAL.mean()
mn
```

![img-11](https://github.com/user-attachments/assets/e0272e4f-609f-49d7-896a-f6e6cf232399)

```
df.TOTAL.fillna(mn,inplace=True)
df
```

![img-12](https://github.com/user-attachments/assets/2cc05f59-2d0d-4ed0-b45c-ca3a37803ce5)

```
df.isnull().sum()
```

![img-13](https://github.com/user-attachments/assets/6684e0c2-64a2-4688-9eb6-f76225f051aa)

```
df.M1.fillna(method='ffill',inplace=True)
df
```

![img-14](https://github.com/user-attachments/assets/38ab8ade-bc69-4e76-a730-fefdc1090569)

```
df.isnull().sum()
```

![img-15](https://github.com/user-attachments/assets/b33eda65-a833-47de-90ac-80b1030bd79b)

```
df.M2.fillna(method='ffill',inplace=True)
df
```

![img-16](https://github.com/user-attachments/assets/6eb69483-e28a-4d6d-9e52-30de38a9fc2c)

```
df.isna().sum()
```

![img-17](https://github.com/user-attachments/assets/a0d9665d-8196-49cb-a19a-8efa074dd60f)

```
df.M3.fillna(method='ffill',inplace=True)
df
```

![img-18](https://github.com/user-attachments/assets/23f3d1b0-61a1-4688-9050-23f93e253551)

```
df.isnull().sum()
```

![img-19](https://github.com/user-attachments/assets/63dd2228-853d-425a-9ba5-0b8d43f4f240)

```
df.duplicated()
```

![img-20](https://github.com/user-attachments/assets/c1ce24ca-b931-4149-a535-3e3a92d187e6)

```
df.drop_duplicates(inplace=True)
df
```

![img-21](https://github.com/user-attachments/assets/60c98aea-45d9-4c23-813b-6c8301af5d7e)

```
df.duplicated()
```

![img-22](https://github.com/user-attachments/assets/c1c946a7-f89e-42c3-8094-385a827dea6b)

```
df['DOB']
```

![img-23](https://github.com/user-attachments/assets/a2316e5c-b64c-4c33-82b2-1122d9ff9262)

```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```

![img-24](https://github.com/user-attachments/assets/3cb0ea72-4b66-4ade-8b2d-651eb99a13ce)

```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```

![img-25](https://github.com/user-attachments/assets/98b5d4b6-fb17-4022-a140-d5c1dac85d2b)

```
import pandas as pd
import numpy as np
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```

![img-26](https://github.com/user-attachments/assets/32a780b0-4ccb-426b-b98f-b32d9b201517)

```
sns.boxplot(data=af)
```

![img-27](https://github.com/user-attachments/assets/2215e107-c607-40c9-9d31-1bb1f5148331)

```
sns.scatterplot(data=af)
```

![img-28](https://github.com/user-attachments/assets/897ab165-bea1-479d-804c-cbdf5043907b)

```
q1 = df.quantile(0.25)
q2 = df.quantile(0.50)
q3 = df.quantile(0.75)
iqr = q3-q1
iqr
```

![img-29](https://github.com/user-attachments/assets/49410b59-0749-4867-ab84-c7e7a6baec0f)

```
Q1 = np.percentile(df,25)
Q3 = np.percentile(df,75)
IQR = Q3-Q1
IQR
```

![img-30](https://github.com/user-attachments/assets/d4dd4dce-54ab-4acc-b293-807b18381e4e)

```
lower_bound = Q1 - 1.5*IQR
upper_bound = Q3 + 1.5*IQR
lower_bound
```

![img-31](https://github.com/user-attachments/assets/b50aaea9-b7eb-451e-ab2e-87eb110fc5bf)

```
upperbound
```
![img-32](https://github.com/user-attachments/assets/0a5a2c3a-3f1c-4af8-be23-2c4bf9b12a97)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```

![img-33](https://github.com/user-attachments/assets/fcf2242d-8f67-4297-95fb-dd14ac365b40)

```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![img-34](https://github.com/user-attachments/assets/a7d119b9-1b3b-4503-bf67-162ece3bc07a)

```
af=af.dropna()
af
```
![img-35](https://github.com/user-attachments/assets/a089def3-55ec-4d5d-bf98-8ced7a77b360)

```
sns.boxplot(data = af)
```

![img-36](https://github.com/user-attachments/assets/46f8715c-1722-4d85-a019-0cf1921b3e52)

```
sns.scatterplot(data=af)
```

![img-37](https://github.com/user-attachments/assets/28faacab-8e5c-4560-899c-4c9db3829771)

```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```

![img-38](https://github.com/user-attachments/assets/f1aed340-ece1-4322-84a6-24ff1dff50e6)

```
threshold=3
outlier=[]
for i in data:
  z = (i-mean)/std
  if(z>threshold):
    outlier.append(i)
print('outlier in dataset is',outlier)
```

![img-39](https://github.com/user-attachments/assets/14c08e7b-5b9f-45a6-9ef0-f6f5ebe66eb5)

```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df1=pd.DataFrame(data)
df1
```

![img-40](https://github.com/user-attachments/assets/88c9a1a3-23e2-4f38-9938-cad682f408d9)

```
z=np.abs(stats.zscore(df1))
print(df1[z['weight']>3])
```

![img-41](https://github.com/user-attachments/assets/217ff489-a1b6-493b-9628-71438e1b7777)

# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score methods
