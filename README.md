# EX-05-Feature-Generation
## AIM
To read the given data and perform Feature Generation process and save the data to a file.

## Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.

It includes two process:

Feature Encoding
Feature Scaling
## FEATURE ENCODING:
### 1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.

### 2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.

### 3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.

### 4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

## FEATURE SCALING:
### 1. Standard Scaler
It is also called Z-score normalization. It calculates the z-score of each value and replaces the value with the calculated Z-score. The features are then rescaled with x̄ =0 and σ=1

### 2. MinMaxScaler
It is also referred to as Normalization. The features are scaled between 0 and 1. Here, the mean value remains same as in Standardization, that is, 0.

### 3. Maximum absolute scaling
Maximum absolute scaling scales the data to its maximum value; that is, it divides every observation by the maximum value of the variable.The result of the preceding transformation is a distribution in which the values vary approximately within the range of -1 to 1.

### 4. RobustScaler
RobustScaler transforms the feature vector by subtracting the median and then dividing by the interquartile range (75% value — 25% value).

## ALGORITHM
### STEP 1
Read the given Data

### STEP 2
Clean the Data Set using Data Cleaning Process

### STEP 3
Apply Feature Generation techniques to all the feature of the data set

### STEP 4
Save the data to the file

# 1.FEATURE GENERATION FOR Data.csv
## CODE FOR FEATURE ENCODING AND FEATURE SCALING:
```
import pandas as pd
df=pd.read_csv("data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
temp=["Cold","Warm","Hot","Very Hot"]
enc=OrdinalEncoder(categories=[temp])
df["Ord_1"]=enc.fit_transform(df[["Ord_1"]])
df
education=["High School","Diploma","Bachelors","Masters","PhD"]
ed=OrdinalEncoder(categories=[education])
df["Ord_2"]=ed.fit_transform(df[["Ord_2"]])
df
pip install category_encoders
from category_encoders import BinaryEncoder
be=BinaryEncoder()
be.fit_transform(df["bin_1"])
df["bin_1"]=be.fit_transform(df[["bin_1"]])
df
be1=BinaryEncoder()
be1.fit_transform(df["bin_2"])
df["bin_2"]=be1.fit_transform(df[["bin_2"]])
df
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
ohe.fit_transform(df[["City"]])
from category_encoders import TargetEncoder
te=TargetEncoder()
te.fit_transform(X=df['Ord_1'],y=df["Target"])
le=LabelEncoder()
df["City"]=le.fit_transform(df[["City"]])
df

from sklearn.preprocessing import StandardScaler
sc=StandardScaler()
df1=pd.DataFrame(sc.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df1

from sklearn.preprocessing import MaxAbsScaler
mas=MaxAbsScaler()
df2=pd.DataFrame(mas.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df3=pd.DataFrame(mms.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import RobustScaler
rs=RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df4
```
# OUTPUT:
## Given DataFrame
![data1](https://user-images.githubusercontent.com/93427278/166728059-2bdba86d-9abb-4a6c-a12c-90bc6d436ae2.png)

## Feature encoding using Ordinal Encoder
![data2](https://user-images.githubusercontent.com/93427278/166728108-2831a415-36d5-4f1d-a1bb-25f381983cc5.png)
![data3](https://user-images.githubusercontent.com/93427278/166728173-343d68df-a199-4b7f-8cef-e3129caa9974.png)

## Feature encoding using Binary Encoder
![data4](https://user-images.githubusercontent.com/93427278/166728205-284d6f7a-2287-4850-aa6e-8e7a73c6d673.png)
![data5](https://user-images.githubusercontent.com/93427278/166728236-5b8c2397-0542-471e-9e41-6c96bc6a5bc8.png)
![data6](https://user-images.githubusercontent.com/93427278/166728262-64f9bbfd-cc16-4ddc-80f2-02641c89b5e8.png)
![data7](https://user-images.githubusercontent.com/93427278/166728364-711ea583-571e-4de4-a7a5-3063c575db65.png)

## Feature encoding using One Hot Encoder
![data8](https://user-images.githubusercontent.com/93427278/166728442-661f0bf7-a8e8-4cb4-a25b-acda2e021b15.png)

## Feature encoding using Target Encoder
![data9](https://user-images.githubusercontent.com/93427278/166728475-c75d0e77-7185-4178-abf4-a3823be2647c.png)

## Feature encoding using Label Encoder
![data10](https://user-images.githubusercontent.com/93427278/166728513-50c0bda5-db36-4ad5-ba8f-f3d9375e5bbe.png)

## Feature scaling using Standard Scaler
![data11](https://user-images.githubusercontent.com/93427278/166728541-400ff2bc-2c7b-4328-ac3d-68e1da4af6da.png)

## Feature scaling using MaxAbs Scaler
![data12](https://user-images.githubusercontent.com/93427278/166728573-5b9857fb-1563-43e5-a698-ff92598e509a.png)

## Feature scaling using MinMax Scaler
![data13](https://user-images.githubusercontent.com/93427278/166728610-d98d7b31-06a9-4be7-9603-cfaf1bb378d3.png)

## Feature scaling using Robust Scaler
![data14](https://user-images.githubusercontent.com/93427278/166728635-fb6eac58-da5a-4d8f-8f88-64abfa3696e6.png)

# 2.FEATURE GENERATION FOR Encoding.csv
## CODE FOR FEATURE ENCODING AND FEATURE SCALING:
```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
temp=["Cold","Warm","Hot"]
enc=OrdinalEncoder(categories=[temp])
df["ord_2"]=enc.fit_transform(df[["ord_2"]])
df
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df['bin_1']=be.fit_transform(df[['bin_1']])
df
be1=BinaryEncoder()
df['bin_2']=be1.fit_transform(df[['bin_2']])
df
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
ohe.fit_transform(df[["nom_0"]])
le=LabelEncoder()
df["nom_0"]=le.fit_transform(df[["nom_0"]])
df

from sklearn.preprocessing import StandardScaler
sc=StandardScaler()
df1=pd.DataFrame(sc.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df1

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df2=pd.DataFrame(mms.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler mas=MaxAbsScaler()
df3=pd.DataFrame(mas.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df3

from sklearn.preprocessing import RobustScaler
rs=RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df4
```
# OUTPUT:
## Given DataFrame
![enc1](https://user-images.githubusercontent.com/93427278/166729007-0ceab8b8-4f62-488f-a84c-81f6c684798e.png)

## Feature encoding using Ordinal Encoder
![enc2](https://user-images.githubusercontent.com/93427278/166729063-c40908a2-a634-4906-b244-3355148a876c.png)

## Feature encoding using Binary Encoder
![enc3](https://user-images.githubusercontent.com/93427278/166729091-fc413c9d-1c5e-43f5-a543-bbafba721ca2.png)
![enc4](https://user-images.githubusercontent.com/93427278/166729162-334ced7d-d2f6-44bc-9446-406396b98ec7.png)

## Feature encoding using One Hot Encoder
![enc5](https://user-images.githubusercontent.com/93427278/166729207-8d03c979-0023-4e78-9595-8ce77206bcb4.png)

## Feature encoding using Label Encoder
![ds ex05-01](https://user-images.githubusercontent.com/93427278/166867596-54d033ac-cd02-4c29-954c-7176732484cf.png)
![ds ex05-02](https://user-images.githubusercontent.com/93427278/166867603-52ef9b02-9f21-497a-b9ef-a137dfcdafe8.png)

## Feature scaling using Standard Scaler
![enc7](https://user-images.githubusercontent.com/93427278/166729355-c096d36e-4f6e-4582-9058-74b9f456c473.png)

## Feature scaling using MinMax Scaler
![enc8](https://user-images.githubusercontent.com/93427278/166729401-72c8c12b-f871-4a65-9ed7-d8f78b6e5383.png)

## Feature scaling using MaxAbs Scaler
![enc9](https://user-images.githubusercontent.com/93427278/166729449-3b1d9948-a61f-4ab9-a3b2-3c4444838a2f.png)

## Feature scaling using Robust Scaler
![enc10](https://user-images.githubusercontent.com/93427278/166729528-26ddceb7-5d74-4be9-8626-365570616da8.png)

# 3.FEATURE GENERATION FOR titanic_dataset.csv
## CODE FOR FEATURE ENCODING AND FEATURE SCALING:
```
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df
df.isnull().sum()
df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df
df.drop("Cabin",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Name",axis=1,inplace=True)
df.isnull().sum()
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
embark=["C","S","Q"]
emb=OrdinalEncoder(categories=[embark])
df["Embarked"]=emb.fit_transform(df[["Embarked"]])
df
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
df

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df1=pd.DataFrame(ss.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df1

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df2=pd.DataFrame(mms.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df2

from sklearn.preprocessing import MaxAbsScaler
mas=MaxAbsScaler()
df3=pd.DataFrame(mas.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df3

from sklearn.preprocessing import RobustScaler
rs = RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df4
```
# OUTPUT:
## Given DataFrame
![tit1](https://user-images.githubusercontent.com/93427278/166729907-864f67a2-292b-46b5-86b0-623fc95d4018.png)

## Resolving null value data
![tit2](https://user-images.githubusercontent.com/93427278/166729987-bf3f0ef2-7b33-45c6-9a28-4d2f81fa93f5.png)
![tit3](https://user-images.githubusercontent.com/93427278/166730122-66bbb495-5eb3-4acd-a88c-7440695fdb1e.png)

## Dropping unnecessary columns
![tit4](https://user-images.githubusercontent.com/93427278/166730193-45f7ac31-6721-4963-a927-b7316dd303be.png)

## Feature encoding using Ordinal Encoder
![tit5](https://user-images.githubusercontent.com/93427278/166730320-a6bd2ef5-c792-44f7-b228-0b2d2cf2378d.png)

## Feature encoding using Binary Encoder
![tit6](https://user-images.githubusercontent.com/93427278/166730455-633c31e1-eb74-41f1-97b2-2c84db36a55b.png)

## Feature scaling using Standard Scaler
![tit7](https://user-images.githubusercontent.com/93427278/166730587-ac41dd9c-0ad5-46e0-96d3-655f7ff448b9.png)

## Feature scaling using MinMax Scaler
![tit8](https://user-images.githubusercontent.com/93427278/166730692-10c6f980-76b4-4195-ae2e-b74a9b7b4dae.png)

## Feature scaling using MaxAbs Scaler
![tit9](https://user-images.githubusercontent.com/93427278/166730836-8994554a-cd85-42a5-9af1-7525d545aba4.png)

## Feature scaling using Robust Scaler
![tit10](https://user-images.githubusercontent.com/93427278/166730944-2cd8f869-adc5-45cd-9374-cf046cfecd9c.png)

## RESULT:
Feature Encoding process and Feature Scaling process is applied to the given data frame sucessfully.
