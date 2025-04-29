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

df=pd.read_csv("/content/SAMPLEIDS (1).csv")

df
```
![Screenshot 2025-04-15 103834](https://github.com/user-attachments/assets/028a6a70-e81f-4387-8437-c5072f881ba1)
```
df.isnull()
```
![Screenshot 2025-04-15 104035](https://github.com/user-attachments/assets/bff42a56-3bfe-4af2-a89e-473e24e14494)
```
df.notnull()
```
![Screenshot 2025-04-15 110705](https://github.com/user-attachments/assets/67cd3730-912d-484e-a0c0-e8935d8620c8)
```
df.dropna(axis=1)
```
![Screenshot 2025-04-15 110828](https://github.com/user-attachments/assets/03b02f97-3efc-4f9a-b795-de92d1127317)
```
df.dropna(axis=0)
```
![Screenshot 2025-04-15 111100](https://github.com/user-attachments/assets/ad214fc6-145e-45d3-8d1e-e0e0a81d568c)
```
dfs=df[df['TOTAL']>270]

dfs
```
![Screenshot 2025-04-15 111206](https://github.com/user-attachments/assets/909df338-a594-416f-9ba9-4a938a603a21)
```
dfs=df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]

dfs
```
![Screenshot 2025-04-15 111506](https://github.com/user-attachments/assets/a6262928-cd15-4b65-8fd0-87687431cfdb)
```

df.iloc[:4]
```
![Screenshot 2025-04-15 111630](https://github.com/user-attachments/assets/eb6a1a92-75f0-42b8-a3dd-409dede9e95e)
```
df.iloc[0:4, 1:4]
``
![Screenshot 2025-04-15 111721](https://github.com/user-attachments/assets/0e9e8cc1-269e-4553-a29d-0570d6c7f591)
```
df.iloc[[1,3,5],[1,3]]

df
``
![Screenshot 2025-04-15 112051](https://github.com/user-attachments/assets/7b9e71d8-6f19-4140-af0e-cd01adda79e7)
```
dff=df.fillna(0)
dff
```
![Screenshot 2025-04-15 112149](https://github.com/user-attachments/assets/14a4a7e1-4770-461f-bc67-3691d4cac014)
```
df['TOTAL'].fillna(value=df['TOTAL'].mean())

dff
```
![Screenshot 2025-04-15 112347](https://github.com/user-attachments/assets/469ada82-8f13-430c-838b-cc2b9f60510e)
```
df.fillna(method='ffill')
```
![Screenshot 2025-04-15 112432](https://github.com/user-attachments/assets/59e07a48-5e5f-477d-a1a3-2a35e37c37a6)
```
df.fillna(method='bfill')
```
![Screenshot 2025-04-15 113431](https://github.com/user-attachments/assets/cc413bd0-d650-4548-b0ec-aeb5e6f08a28)
```
df['TOTAL'].fillna(value=df['TOTAL'].mean(), inplace=True)

df
```
![Screenshot 2025-04-15 113605](https://github.com/user-attachments/assets/59de4585-2818-49e4-a3c2-5cccf6eaf653)
```
import pandas as pd
import seaborn as sns
import numpy as np

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
 af=pd.DataFrame(age)
 af
```
![Screenshot 2025-04-15 113947](https://github.com/user-attachments/assets/bf1bc24f-e0d7-479d-a565-ca85f0710c49)
```
sns.boxplot(data=af)
```
![Screenshot 2025-04-15 114346](https://github.com/user-attachments/assets/fa6fbc2a-59d5-4b73-a30d-4282a0a3c876)
```
sns.scatterplot(data=af)
```
![Screenshot 2025-04-15 114632](https://github.com/user-attachments/assets/29c61805-ab9d-4bca-b436-db371302ab07)
```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2025-04-15 114739](https://github.com/user-attachments/assets/c25b22b1-fa99-4017-b6b5-fc048f5d9454)
```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
![Screenshot 2025-04-15 115042](https://github.com/user-attachments/assets/670ba0a7-e016-4240-9dcd-cb87e778682f)
```
lower_bound=Q1-1.5*IQR
upper_bound= Q3+1.5*IQR

lower_bound
```
![Screenshot 2025-04-15 132354](https://github.com/user-attachments/assets/a7c9e7d0-46fc-4424-89e3-0372923397a2)
```
upper_bound
```
![Screenshot 2025-04-15 132412](https://github.com/user-attachments/assets/7ac5a815-87e8-4408-a23a-25d3be598957)
```
outliers=[x for x in age if x < lower_bound or x > upper_bound]

print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower bound:", lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```
![Screenshot 2025-04-15 140636](https://github.com/user-attachments/assets/bf031e61-d815-4d94-8b8f-fb28bb3ca078)
```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![Screenshot 2025-04-15 140705](https://github.com/user-attachments/assets/89308a89-db6b-4dae-881e-b09764be3332)
```
af.dropna()
```
![Screenshot 2025-04-15 140747](https://github.com/user-attachments/assets/a289c4df-ecc4-4a71-9fc7-e955173cd099)

```
sns.boxplot(data=af)
```
![Screenshot 2025-04-15 140815](https://github.com/user-attachments/assets/31cd0d59-6306-4e14-98ca-7f63f5fd2fc0)
```
sns.scatterplot(data=af)
```
![Screenshot 2025-04-15 140913](https://github.com/user-attachments/assets/380ca24b-5f65-490e-a7d2-3091a3e30342)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of dataset is',mean)
print('std.deviation is',std)
```
![Screenshot 2025-04-15 140938](https://github.com/user-attachments/assets/93ad4964-6b1a-4b4f-a8de-beec14c03205)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![Screenshot 2025-04-15 141003](https://github.com/user-attachments/assets/a27b37dc-cc15-410a-b6a7-a44dc6818683)
```
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,258]}

import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,258]}
df=pd.DataFrame(data)
df
```
![Screenshot 2025-04-15 141341](https://github.com/user-attachments/assets/cc917e51-9292-4a19-8a4a-ead29184485c)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/user-attachments/assets/24a3b6ec-d597-4d80-bd99-8ae74618b743)

```
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,258]

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
![Screenshot 2025-04-15 143016](https://github.com/user-attachments/assets/ec41ad5d-3a5f-4301-80b1-ddf8b38a7662)

# Result
          Thus we have cleaned the data and removed the outliers by detection using IQR and Z
score
 
