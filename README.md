## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.

STEP 2:Clean the Data Set using Data Cleaning Process.

STEP 3:Apply Feature Encoding for the feature in the data set.

STEP 4:Apply Feature Transformation for the feature in the data set.

STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
Developed By:LOKESH N
Reg no:212222100023
```
    
     import pandas as pd
     df=pd.read_csv("/content/Encoding Data.csv")
     df
    
  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/119155e5-f70f-4e98-bc72-cc93c564f510)


    
    from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
    pm=['Hot','Warm','Cold']
    e1=OrdinalEncoder(categories=[pm])
    e1.fit_transform(df[["ord_2"]])
    

  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/d395d839-8db0-4300-8f13-d3115c36f63b)




    
    df['bo2']=e1.fit_transform(df[["ord_2"]])
    df
    

 ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/b608afce-9571-45cd-be0b-feb2bb49300a)


    
    df['bo2']=e1.fit_transform(df[["ord_2"]])
    df
    
  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/55d2e943-f547-46e8-b213-c25f8430e99b)

    
    le=LabelEncoder()
    dfc=df.copy()
    dfc['ord_2']=le.fit_transform(dfc['ord_2'])
    dfc
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/11350557-e6ba-4a49-a32d-7f3bf602fef2)

  

    
    from sklearn.preprocessing import OneHotEncoder
    ohe=OneHotEncoder(sparse=False)
    df2=df.copy()
    enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
    df2=pd.concat([df2,enc],axis=1)
    df2
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/fc211cf7-32b1-4e7b-ae66-549836158b3d)

 
    
    pd.get_dummies(df2,columns=["nom_0"])
    

  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/f19cfc9c-9f8d-4343-b3fd-0f9666932309)


    
    pip install --upgrade category_encoders
    

 ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/51428424-4f3e-4476-8a79-61c49ccaa8ea)

    
    from category_encoders import BinaryEncoder
    df=pd.read_csv("/content/data.csv")
    be=BinaryEncoder()
    nd=be.fit_transform(df['Ord_2'])
    fb=pd.concat([df,nd],axis=1)
    dfb1=df.copy()
    dfb
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/71cf9298-786c-48c2-b35f-f3f49785e6a4)

 
    
    from category_encoders import TargetEncoder
    te=TargetEncoder()
    cc=df.copy()
    new=te.fit_transform(X=cc["City"],y=cc["Target"])
    cc=pd.concat([cc,new],axis=1)
    cc
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/2e1c3c7e-282b-4377-ac4e-c42d7f2541f6)

  

    
    import pandas as pd
    from scipy import stats
    import numpy as np
    df=pd.read_csv("/content/Data_to_Transform.csv")
    df
    

  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/82b64ce1-3888-4fb3-84e8-c47358de7c2b)


    
    df.skew()
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/c41f6b92-3c0a-40ae-bb08-feb3522ff479)

 
    
    np.log(df["Highly Positive Skew"])
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/042f516e-40c8-40a0-bd79-1ae8622c6932)

 

    
    np.reciprocal(df["Moderate Positive Skew"])
    

  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/5c810df2-2d1d-4475-bdd3-70edeac28dd2)

    
    np.sqrt(df["Highly Positive Skew"])
    

  
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/01b9e84c-6859-4dc8-8cee-d7fabb87fb1e)

    
    np.square(df["Highly Positive Skew"])
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/bdb1947a-52ca-4dea-bbe2-e0c70526a2c1)

  

    
   df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
   
   df
  
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/2941af49-ae45-4ee9-a61e-223f432f78cb)

 

    
    df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
    df.skew()
    
 ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/64a8c7bd-2699-49ab-bc4e-86dbe131a1ae)

    
    df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
    df.skew()
    ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/9f89a45c-8e53-4153-b23f-5a7e169622e2)

  
    
   import matplotlib.pyplot as plt
   import seaborn as sns
   import statsmodels.api as sm
   import scipy.stats as stats

   sm.qqplot(df["Moderate Negative Skew"],line='45')

   plt.show()
    

  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/29aad840-8e44-4afb-b5b4-da964cc45adf)

    
    sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
    

  ![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/a8a822e4-d7de-4da8-a6f4-f6ca76217e83)

    
    from sklearn.preprocessing import QuantileTransformer
    qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

    df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

    sm.qqplot(df["Moderate Negative Skew"],line='45')
    plt.show()
    
    
![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/0c4668a3-e966-4c8c-a58f-ac7bcea5e93c)

 

    df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
    sm.qqplot(df['Highly Negative Skew'], line='45')
    plt.show()

![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/e1d6705b-6349-4731-91bc-6974e757ef97)

    sm.qqplot(df['Highly Negative Skew_1'], line='45')
    plt.show()

    

![image](https://github.com/lokeshnarayanan/EXNO-3-DS/assets/119393019/dd66a5ce-43c7-410b-9c02-eb08c35d28ea)

  # RESULT:
        Hence performing Feature Encoding and Transformation process is Successful.
        
