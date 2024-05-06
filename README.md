# EXNO2DS
# AIM:
To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
### Exploratory data analysis:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv("/content/titanic_dataset.csv")
dt
```
![image](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/57272d58-ca70-4ce9-83a3-87ab4019a3b7)


```
dt.info()
```
![image](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/6898b3cf-3a41-4b2d-9c44-533395884d7e)

```
dt.shape
```
![311099865-a0eef082-ae2d-4d5c-ad46-419a4daf7e98](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/db824ca2-9f32-4b32-8897-eea2f692f7dc)
```
dt.set_index("PassengerId",inplace=True)
dt.describe()
```
![311099883-c8b82f77-4b64-41f4-b8c6-6da80df4791b](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/5fc4490c-e71a-4984-af1e-08540d539462)

### Categorical data analysis:
```
dt.nunique()
```
![311099897-24404bf7-7cbe-4dfe-934e-4df366660737](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/f2d58808-a860-401a-987b-990f2da4da29)
```
dt["Pclass"].value_counts()
```
![image](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/6e9b33c4-0800-4d8b-8428-906df28550d3)

### Univariate analysis:
```
sns.countplot(data=dt,x="Cabin")
```

![image](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/f9cbb8d7-0a9d-4f08-83d1-72dd22390e1b)

```
dt.Pclass.unique()
```
![311100655-d506691d-69cd-4ec5-be17-d1e34caa37cc](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/e09d9f9f-67ef-40cc-893a-21ae612bed91)

```
dt.rename(columns = {'Sex':'Gender'},inplace=True)
dt
```
![311100681-af221019-adaa-4f5f-85a6-3f4b13d0cb33](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/a4565b9c-fab8-4843-b870-38686e37157e)

### Bivariate analysis:
```
sns.catplot(x="Parch",col="Pclass",kind="count",data=dt,height=5,aspect=.7)
```

![image](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/f69f775e-bb63-4f99-a58c-561af181abdd)
```
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")
```
![311100762-cac9226f-2cb4-4693-99ab-aa262cd28e3a](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/f3352ce5-516a-4431-b7ae-51e90caee787)

```
dt.boxplot(column="Age",by="Survived")
```
![311100774-17ab0861-c128-47e7-a313-116bedd8e100](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/8212e3d7-3564-4b73-909f-010654945a16)

```
sns.scatterplot(x=dt["Age"],y=dt["SibSp"])
```

![image](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/52ecd60c-63aa-4cbb-ac67-d83f168f6992)

```
sns.jointplot(x="Age",y="Fare",data=dt)
```
![311100804-290d6166-e4f3-471b-8582-72600004084f](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/6ca0ee23-5f26-45b1-8923-a4f693b025d2)

### Multivariate analysis:
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```
![311100829-cfad821e-1d27-4c6d-96da-a43c261076c6](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/6de78ee3-38f4-4169-a6e2-fa05b8404891)
```
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![311100863-633922ee-abf2-400f-bd54-1e6d0533467e](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/41251fb2-4f65-4796-ac6c-0f1a442ccab1)

### Co-relation:
```
corr = dt.corr()
sns.heatmap(corr,annot=False)
```

![image](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/51d2f061-9eb4-453a-9472-f375f1d81649)

```
sns.pairplot(dt)
```
![311100952-fff650c4-8ab7-4bbd-b4d9-043659f1a7fe](https://github.com/Kowsalyasathya/EXNO2DS/assets/118671457/a2cd8a57-c7d7-4ee4-82c6-a4ab27f32549)
# RESULT
Thus the Exploratory Data Analysis process is performed successfully on the given data using python code.
