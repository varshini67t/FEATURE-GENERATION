# FEATURE-GENERATION
# EX-05-Feature-Generation
# AIM

To read the given data and perform Feature Generation process and save the data to a file.

# ALGORITHM

STEP 1 Read the given Data

STEP 2 Clean the Data Set using Data Cleaning Process

STEP 3 Apply Feature Generation techniques to all the feature of the data set

STEP 4 Save the data to the file

# CODE
import numpy as np
import pandas as pd
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
from sklearn.preprocessing import StandardScaler

data = pd.read_csv('/content/Encoding Data.csv')
data

ORDINAL ENCODER

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder

Climate = ['Cold','Warm', 'Hot']

enc=OrdinalEncoder(categories=[Climate])

enc.fit_transform(data[["ord_2"]])


array([[2.],
       [1.],
       [0.],
       [1.],
       [0.],
       [2.],
       [0.],
       [0.],
       [1.],
       [2.]])

data['ord_2']=enc.fit_transform(data[["ord_2"]])
data

Label Encoder

le=LabelEncoder()

data2=data.copy()

data2['nom_0']=le.fit_transform(data2['nom_0'])

data2

One Hot Encoder

data = pd.read_csv('/content/titanic_dataset.csv')
data

from sklearn.preprocessing import OneHotEncoder

ohe=OneHotEncoder(sparse_output=False)

df3=data.copy()

enc = pd.DataFrame(ohe.fit_transform(df3[['Cabin']]))

df3=pd.concat([df3,enc],axis=1)
pd.get_dummies(df3,columns=["Cabin"])

pip install category_encoders

Binary Encoder

from category_encoders import BinaryEncoder
be = BinaryEncoder()
newdata=be.fit_transform(data['Sex'])
data=pd.concat([data,newdata],axis=1)
data2.copy()
data

data = pd.read_csv('/content/data.csv')
data

from category_encoders import TargetEncoder

te=TargetEncoder()

df4=data.copy()

new = te.fit_transform (X=df4["City"],y=df4["Target"])

df4=pd.concat([df4,new],axis=1)
df4
# OUTPUT
![image](https://user-images.githubusercontent.com/107982953/235742650-b2ccb142-06ca-4a42-bcd7-3301850a76d2.png)
![image](https://user-images.githubusercontent.com/107982953/235742756-a61e0cb2-a197-4fcb-8b38-86cc36c2dbfb.png)
![image](https://user-images.githubusercontent.com/107982953/235742816-34e63879-6720-4ce4-829a-d0d64d0898c3.png)
![image](https://user-images.githubusercontent.com/107982953/235742879-cdd70523-dedf-4e61-922c-247dbfb3fa15.png)
![image](https://user-images.githubusercontent.com/107982953/235742965-0e519269-dce0-4b05-a9c6-a9f6cbe9475f.png)
![image](https://user-images.githubusercontent.com/107982953/235743108-3d4202aa-a365-4cbb-abb1-770b9e97953c.png)
![image](https://user-images.githubusercontent.com/107982953/235743180-5777fb87-20fa-4ab0-8ef8-15f0d73778b2.png)
![image](https://user-images.githubusercontent.com/107982953/235743247-898863b2-a228-47d4-8954-fc8def3b6389.png)
![image](https://user-images.githubusercontent.com/107982953/235743314-0b069143-20b4-4475-b1cf-2eca7d1e1726.png)

# RESULT
Thus we have performed Feature Generation process Successfully.
