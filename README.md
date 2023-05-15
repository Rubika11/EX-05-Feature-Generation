# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE
DATA.CSV
```
import pandas as pd
df=pd.read_csv("data.csv")
df

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
from sklearn.preprocessing import OneHotEncoder

oe=OrdinalEncoder()
df1=df.copy()

df1["City"] = oe.fit_transform(df1[["City"]])
df1["bin_1"] = oe.fit_transform(df1[["bin_1"]])
df1["Ord_1"] = oe.fit_transform(df1[["Ord_1"]])
df1["Ord_2"] = oe.fit_transform(df1[["Ord_2"]])
df1["bin_2"] = oe.fit_transform(df1[["bin_2"]])

df2=df.copy()

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```
ENCODING DATASET
```
import pandas as pd
qf=pd.read_csv("encoding.csv")
qf

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
from sklearn.preprocessing import OneHotEncoder

oe=OrdinalEncoder()

qf1=qf.copy()


qf1["bin_1"] = oe.fit_transform(qf1[["bin_1"]])
qf1["nom_0"] = oe.fit_transform(qf1[["nom_0"]])
qf1["ord_2"] = oe.fit_transform(qf1[["ord_2"]])
qf1["bin_2"] = oe.fit_transform(qf1[["bin_2"]])

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
qf0=pd.DataFrame(sc.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf0   

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
qf2=pd.DataFrame(sc1.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
qf3=pd.DataFrame(sc2.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
qf4=pd.DataFrame(sc3.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf4
```
TITANIC_DATASET
```
import pandas as pd
rf=pd.read_csv("titanic.csv")
rf

#removing unwanted data
rf.drop("Name",axis=1,inplace=True)
rf.drop("Ticket",axis=1,inplace=True)
rf.drop("Cabin",axis=1,inplace=True)  

rf["Age"]=rf["Age"].fillna(rf["Age"].median())
rf["Embarked"]=rf["Embarked"].fillna(rf["Embarked"].mode()[0])

rf.isnull().sum()

rf1=rf.copy()

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
oe=OrdinalEncoder()

e1=OrdinalEncoder(categories=[embark])
rf1['Embarked'] = e1.fit_transform(rf[['Embarked']])
rf1['Sex'] = oe.fit_transform(rf[['Sex']])
rf1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
rf0=pd.DataFrame(sc.fit_transform(rf1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
rf0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
rf3=pd.DataFrame(sc1.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
rf4=pd.DataFrame(sc2.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
rf5=pd.DataFrame(sc3.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf5
```

# OUPUT
DATA CSV

![ds5 2](https://user-images.githubusercontent.com/118680410/234241617-d03ba20c-b8a2-42e2-98e3-2a4fd143d04b.png)
![ds5 1](https://user-images.githubusercontent.com/118680410/234241622-48be990d-6359-4e4e-ac54-0a95bd723cc3.png)
![ds5](https://user-images.githubusercontent.com/118680410/234241625-2a787605-9608-4438-884a-0c32cdd77f98.png)
![ds5 6](https://user-images.githubusercontent.com/118680410/234241627-6cef6da5-cea8-48c9-9291-ac071deb3957.png)
![ds5 3](https://user-images.githubusercontent.com/118680410/234241630-2cbe2a1e-b5ce-41e4-a120-f66a383c18ea.png)

ENCODING DATASET

![ds5 1 2](https://user-images.githubusercontent.com/118680410/234242989-068de031-9fba-49ff-8fca-2755258d5646.png)
![ds5 1 1](https://user-images.githubusercontent.com/118680410/234242991-b3ee0c3c-e4ed-4fec-938e-c8eb0b9c6de8.png)
![ds5 1 4](https://user-images.githubusercontent.com/118680410/234242993-84eaa12f-b5ba-4f35-b5a9-be52eb381956.png)
![ds5 1 3](https://user-images.githubusercontent.com/118680410/234242997-14dfb64d-f8e0-438e-8dfa-3d470781bd5d.png)

TITANIC_DATASET

![ds5 2 2](https://user-images.githubusercontent.com/118680410/234243197-108a9c8f-19ad-4fbb-aaee-3409e5529976.png)
![ds5 2 1](https://user-images.githubusercontent.com/118680410/234243204-1db95fc9-3149-4ed4-8e57-795a34e6f20e.png)
![ds5 2 3](https://user-images.githubusercontent.com/118680410/234243209-7c499d8c-6908-4b87-9a24-c8a2aa110b01.png)
![ds5 2 4](https://user-images.githubusercontent.com/118680410/234243275-225fbc09-c2e4-45a7-9cac-e4a460ce8f1d.png)

RESULT:
Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.
