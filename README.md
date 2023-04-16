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

[1]
3s
import numpy as np
import pandas as pd
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
from sklearn.preprocessing import StandardScaler

[12]
0s
data = pd.read_csv('/content/Encoding Data.csv')
data

ORDINAL ENCODER

[15]
0s
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
[16]
0s
data['ord_2']=enc.fit_transform(data[["ord_2"]])
data

Label Encoder

[18]
0s
le=LabelEncoder()

data2=data.copy()

data2['nom_0']=le.fit_transform(data2['nom_0'])

data2

One Hot Encoder

[19]
0s
data = pd.read_csv('/content/titanic_dataset.csv')
data

[35]
0s
from sklearn.preprocessing import OneHotEncoder

ohe=OneHotEncoder(sparse_output=False)

df3=data.copy()

enc = pd.DataFrame(ohe.fit_transform(df3[['Cabin']]))

df3=pd.concat([df3,enc],axis=1)
pd.get_dummies(df3,columns=["Cabin"])

[37]
5s
pip install category_encoders
Looking in indexes: https://pypi.org/simple, https://us-python.pkg.dev/colab-wheels/public/simple/
Collecting category_encoders
  Downloading category_encoders-2.6.0-py2.py3-none-any.whl (81 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 81.2/81.2 kB 7.1 MB/s eta 0:00:00
Requirement already satisfied: pandas>=1.0.5 in /usr/local/lib/python3.9/dist-packages (from category_encoders) (1.5.3)
Requirement already satisfied: numpy>=1.14.0 in /usr/local/lib/python3.9/dist-packages (from category_encoders) (1.22.4)
Requirement already satisfied: scipy>=1.0.0 in /usr/local/lib/python3.9/dist-packages (from category_encoders) (1.10.1)
Requirement already satisfied: scikit-learn>=0.20.0 in /usr/local/lib/python3.9/dist-packages (from category_encoders) (1.2.2)
Requirement already satisfied: patsy>=0.5.1 in /usr/local/lib/python3.9/dist-packages (from category_encoders) (0.5.3)
Requirement already satisfied: statsmodels>=0.9.0 in /usr/local/lib/python3.9/dist-packages (from category_encoders) (0.13.5)
Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.9/dist-packages (from pandas>=1.0.5->category_encoders) (2022.7.1)
Requirement already satisfied: python-dateutil>=2.8.1 in /usr/local/lib/python3.9/dist-packages (from pandas>=1.0.5->category_encoders) (2.8.2)
Requirement already satisfied: six in /usr/local/lib/python3.9/dist-packages (from patsy>=0.5.1->category_encoders) (1.16.0)
Requirement already satisfied: threadpoolctl>=2.0.0 in /usr/local/lib/python3.9/dist-packages (from scikit-learn>=0.20.0->category_encoders) (3.1.0)
Requirement already satisfied: joblib>=1.1.1 in /usr/local/lib/python3.9/dist-packages (from scikit-learn>=0.20.0->category_encoders) (1.2.0)
Requirement already satisfied: packaging>=21.3 in /usr/local/lib/python3.9/dist-packages (from statsmodels>=0.9.0->category_encoders) (23.0)
Installing collected packages: category_encoders
Successfully installed category_encoders-2.6.0
Binary Encoder

[38]
1s
from category_encoders import BinaryEncoder
be = BinaryEncoder()
newdata=be.fit_transform(data['Sex'])
data=pd.concat([data,newdata],axis=1)
data2.copy()
data

[45]
0s
data = pd.read_csv('/content/data.csv')
data

[48]
0s
from category_encoders import TargetEncoder

te=TargetEncoder()

df4=data.copy()

new = te.fit_transform (X=df4["City"],y=df4["Target"])

df4=pd.concat([df4,new],axis=1)
df4

# RESULT
Thus we have performed Feature Generation process Successfully.
