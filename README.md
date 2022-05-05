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

# OUPUT

## Given DataFrame
![ex5 1](https://user-images.githubusercontent.com/93427923/166866921-11d3cb0b-069e-475d-9dc2-9492dd1c7d29.png)

## Feature encoding using Ordinal Encoder
![ex5 2](https://user-images.githubusercontent.com/93427923/166866958-64542bf3-4b0b-4e48-868f-830642e5e4a7.png)

## Feature encoding using Binary Encoder
![ex5 3](https://user-images.githubusercontent.com/93427923/166866998-9172f7f9-b98f-4fdc-870c-28256e3775de.png)
![ex5 4](https://user-images.githubusercontent.com/93427923/166867012-f4a288da-4b5f-4bbe-b7ff-ff1144c3d1f2.png)

## Feature encoding using One Hot Encoder
![ex5 5](https://user-images.githubusercontent.com/93427923/166867051-7fde4212-a225-497e-a410-f3d18986f848.png)

## Feature encoding using Target Encoder
![ex5 6](https://user-images.githubusercontent.com/93427923/166867162-4169133e-3182-409c-9f22-571dd7493049.png)

## Feature encoding using Label Encoder
![ex5 7](https://user-images.githubusercontent.com/93427923/166867193-1a71f812-8f68-4d3e-9a26-52ca31e12839.png)

## Feature scaling using Standard Scaler
![ex5 8](https://user-images.githubusercontent.com/93427923/166867239-0effcf9b-0aef-4b77-b990-a29f2489ed5f.png)

## Feature scaling using MaxAbs Scaler
![ex5 9](https://user-images.githubusercontent.com/93427923/166867269-f4b375e2-a0e9-423a-877d-7dd59f783376.png)

### Feature scaling using MinMax Scaler
![ex5 10](https://user-images.githubusercontent.com/93427923/166867297-b6815cc9-272e-4846-a3f8-a8f475a08c2b.png)

## Feature scaling using Robust Scaler
![ex5 11](https://user-images.githubusercontent.com/93427923/166867328-047b2a8a-a856-482f-b8c0-b867d2f382bf.png)

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
![e5 1](https://user-images.githubusercontent.com/93427923/166868334-4d635547-d30a-432c-9d22-f3c2517f254f.png)

## Feature encoding using Ordinal Encoder
![e5 2](https://user-images.githubusercontent.com/93427923/166868938-4ac7fcae-2c03-4699-927a-786efc705d4d.png)

## Feature encoding using Binary Encoder
![e5 3](https://user-images.githubusercontent.com/93427923/166868990-51bc797e-7e23-4434-9aa7-25d044855d00.png)

## Feature encoding using One Hot Encoder
![e5 4](https://user-images.githubusercontent.com/93427923/166869028-a394bb4f-d7d4-45aa-9a31-78913d977a10.png)

## Feature encoding using Label Encoder
![e5 5](https://user-images.githubusercontent.com/93427923/166869077-7f669d6f-c92f-4e2c-a082-de3fbf749b79.png)

## Feature scaling using Standard Scaler
![e5 6](https://user-images.githubusercontent.com/93427923/166869114-b6ae6f3e-ea74-4a5f-ba33-0dd25facccd8.png)

## Feature scaling using MinMax Scaler
![e5 7](https://user-images.githubusercontent.com/93427923/166869146-7227630a-d7f7-4319-820b-d7ba402a11f8.png)

## Feature scaling using MaxAbs Scaler
![e5 8](https://user-images.githubusercontent.com/93427923/166869173-d1be1bde-b512-4f20-8848-39d0395e3ef3.png)

## Feature scaling using Robust Scaler
![e5 9](https://user-images.githubusercontent.com/93427923/166869201-26e06f21-1f96-4527-972c-7d3abe838610.png)

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
![5 1](https://user-images.githubusercontent.com/93427923/166869690-178bb7f5-e94d-49ec-9d22-b4ea12db1f8b.png)

## Resolving null value data
![5 2](https://user-images.githubusercontent.com/93427923/166869727-d29cf218-d4b7-42e4-88c7-a377684c3936.png)

## Dropping unnecessary columns
![5 3](https://user-images.githubusercontent.com/93427923/166869773-d781f23b-6854-4562-8eff-97567f1f8e25.png)

## Feature encoding using Ordinal Encoder
![5 4](https://user-images.githubusercontent.com/93427923/166870066-6c10baca-1b05-4cc2-a5f7-b57647af8365.png)

## Feature encoding using Binary Encoder
![5 5](https://user-images.githubusercontent.com/93427923/166870083-cc9b9631-ee56-4237-b8ba-92c9837069a8.png)

## Feature scaling using Standard Scaler
![5 6](https://user-images.githubusercontent.com/93427923/166870097-0da7bafd-fe79-4fa4-bddf-71660b59196d.png)

## Feature scaling using MinMax Scaler
![5 7](https://user-images.githubusercontent.com/93427923/166870113-cdf11e4f-1223-42ea-9aea-074894826f1d.png)

## Feature scaling using MaxAbs Scaler
![5 8](https://user-images.githubusercontent.com/93427923/166870121-51724f1a-f575-4d4c-be0a-661631762175.png)

## Feature scaling using Robust Scaler
![5 9](https://user-images.githubusercontent.com/93427923/166870135-8fb7b5a2-7370-429e-bfeb-70a4da64b9a5.png)

# RESULT:
Feature Encoding process and Feature Scaling process is applied to the given data frame sucessfully.








