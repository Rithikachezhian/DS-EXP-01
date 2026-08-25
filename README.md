# DS-EXP-01

Data Cleaning Process

AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

Coding and Output:
import pandas as pd  
df=pd.read_csv("/content/SAMPLEIDS.csv") 
df

<img width="1297" height="747" alt="image" src="https://github.com/user-attachments/assets/9ab708f1-6b66-413c-8e8e-359a627aa6f9" />

df.head()
<img width="972" height="283" alt="image" src="https://github.com/user-attachments/assets/c531ea7d-8d73-43f1-8f30-c4a17c5c2599" />

df.tail()
<img width="1002" height="242" alt="image" src="https://github.com/user-attachments/assets/3e30ff7e-e8df-4aaf-b23e-2019009764ba" />

df.info()
<img width="810" height="373" alt="image" src="https://github.com/user-attachments/assets/50faf738-4d8d-4c99-ac35-4157d3ed71f5" />

df.describe()
<img width="1111" height="308" alt="image" src="https://github.com/user-attachments/assets/374c5649-3c5f-4bf9-852a-4c09747c923a" />

df.isnull().sum()
<img width="871" height="465" alt="image" src="https://github.com/user-attachments/assets/4fa01d41-8b2c-4d12-9af6-0143885e252f" />

df.isnull().sum()
<img width="1068" height="451" alt="image" src="https://github.com/user-attachments/assets/47b31419-2945-4648-84ff-c52befc2d55b" />

df.isnull().any()
<img width="1241" height="465" alt="image" src="https://github.com/user-attachments/assets/6de4d54d-9211-4f71-8f1c-0bb3b85c692c" />

df.dropna()
<img width="1232" height="468" alt="image" src="https://github.com/user-attachments/assets/5bd21300-8942-4135-a73a-d65cf8d582d1" />

df.fillna(0)
<img width="1215" height="692" alt="image" src="https://github.com/user-attachments/assets/8a54ab2c-1667-4513-8c66-aec829ca4cd7" />

df.fillna(method='ffill')
<img width="1436" height="716" alt="image" src="https://github.com/user-attachments/assets/aa7c121b-e98f-43b9-9da7-4e02f6aa59aa" />

df.fillna({'GENDER':'MALE','NAME':'SRI'})
<img width="1351" height="697" alt="image" src="https://github.com/user-attachments/assets/c6879c69-e319-4939-8f48-c15c72f7f054" />

ir=pd.read_csv("/content/iris.csv") 
ir
<img width="1475" height="482" alt="image" src="https://github.com/user-attachments/assets/b24ea2e8-5ad0-4ef2-84c2-5ae9d937db0d" />

ir.describe()
<img width="1265" height="322" alt="image" src="https://github.com/user-attachments/assets/0851b388-4282-4c96-9f6b-ab7c25766f46" />

import seaborn as sns 
sns.boxplot(x='sepal_width',data=ir)
<img width="1077" height="486" alt="image" src="https://github.com/user-attachments/assets/ef14596f-6aae-4a59-91ac-5cc95d77061f" />


Q1=ir.sepal_width.quantile(0.25) 
Q3=ir.sepal_width.quantile(0.75) 
(IQR)=Q3-Q1 
print(IQR)
<img width="1200" height="120" alt="image" src="https://github.com/user-attachments/assets/248fe992-72bb-479e-bc95-d2d2044ff4c6" />


ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))] 
ran['sepal_width']
<img width="1308" height="248" alt="image" src="https://github.com/user-attachments/assets/c6e1b8be-680e-4468-bfac-979f5dc067d4" />

ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))] 
ran['sepal_width']
<img width="1455" height="487" alt="image" src="https://github.com/user-attachments/assets/f296495d-9dd4-4e3f-964d-bb3f49197761" />

sns.boxplot(x='sepal_width',data=ran)
<img width="1187" height="472" alt="image" src="https://github.com/user-attachments/assets/f02c5471-b762-405b-b3d3-24763aea10b9" />

import numpy as np 
import scipy.stats as stats

z=np.abs(stats.zscore(ir['petal_length'])) 
z
<img width="1510" height="561" alt="image" src="https://github.com/user-attachments/assets/956a8b20-6dc3-4e84-80a2-9b3123cdbc7a" />

ir1=ir[z<3] 
ir1
<img width="1156" height="482" alt="image" src="https://github.com/user-attachments/assets/90bc2d61-87d7-4d36-bc4d-0180f579fc1a" />


Result
      Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
