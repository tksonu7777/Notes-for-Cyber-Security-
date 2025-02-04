# 22CYBER33  
 ---
 ---
 

# Exercise: EDA :
## Exploratory Data Analysis (EDA) exercise,
## By exploring distributions and creating new variables, you can gain a deeper understanding of the dataset, which will inform later stages of data analysis

### examining user behaviour from New York Times data


### Task
- Create an age_group variable:
- Single-day analysis: For a single day's worth of data, you are to perform the following tasks

- Plotting distributions: 
- User segmentation:
- Extending analysis across days:







---
---


# Down load Data set
[click here to Download dataset](https://github.com/Notes4Cyber/College-note/blob/main/3rd%20year/5%20Sem/4.%20Introduction%20to%20Data%20Science/Assignment/Dataset/nyt1.csv)


## after downlaoded data set 
- ### I am using google colab or kaggle
- ## for colab
- ## connect google drive with colab
```py
from google.colab import drive
drive.mount('/content/drive')

```
## allow and continue 
## check the working directory
```
!ls '/content/drive'
```
## select he data set and add path to your directory 

 ```py

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


data1 = pd.read_csv('/content/drive/MyDrive/33Cyber33/22cyber33/ College /College-yeara-nots/3-year/5th sem/Data science /Assignment /nyt1.csv')


bins = [-float('inf'), 0, 18, 24, 34, 44, 54, 64, float('inf')]
labels = ['<0', '0-18', '19-24', '25-34', '35-44', '45-54', '55-64', '65+']
data1['agecat'] = pd.cut(data1['Age'], bins, labels=labels)


print(data1.describe())


def siterange(x):
    return len(x), x.min(), x.mean(), x.max()


age_summary = data1.groupby('agecat')['Age'].apply(siterange).reset_index()
print(age_summary)

 
summary = data1.groupby('agecat').agg({
    'Gender': 'sum',
    'Signed_In': 'sum',
    'Impressions': 'sum',
    'Clicks': 'sum'
}).reset_index()
print(summary)

 
plt.figure(figsize=(10, 6))
sns.histplot(data1, x='Impressions', hue='agecat', multiple='stack', binwidth=1)
plt.title('Histogram of Impressions by Age Category')
plt.show()

plt.figure(figsize=(10, 6))
sns.boxplot(data=data1, x='agecat', y='Impressions', palette='Set3')
plt.title('Boxplot of Impressions by Age Category')
plt.show()


data1['hasimps'] = pd.cut(data1['Impressions'], bins=[-float('inf'), 0, float('inf')], labels=['NoImps', 'Imps'])

data1['Clicks/Impressions'] = data1['Clicks'] / data1['Impressions']
 
clicks_summary = data1.groupby('hasimps')['Clicks'].apply(siterange).reset_index()
print(clicks_summary)

 
plt.figure(figsize=(10, 6))
sns.kdeplot(data=data1[data1['Impressions'] > 0], x='Clicks/Impressions', hue='agecat')
plt.title('Density Plot of Clicks/Impressions by Age Category')
plt.show()

plt.figure(figsize=(10, 6))
sns.kdeplot(data=data1[data1['Impressions'] > 0], x='Clicks/Impressions', hue='agecat')
plt.title('Density Plot of Clicks/Impressions by Age Category')
plt.show()


plt.figure(figsize=(10, 6))
sns.boxplot(data=data1[data1['Clicks'] > 0], x='agecat', y='Clicks', palette='Set3')
plt.title('Boxplot of Clicks by Age Category (Clicks > 0)')
plt.show()

plt.figure(figsize=(10, 6))
sns.kdeplot(data=data1[data1['Clicks'] > 0], x='Clicks', hue='agecat')
plt.title('Density Plot of Clicks by Age Category (Clicks > 0)')
plt.show()
 
data1['scode'] = 'NoImps'
data1.loc[data1['Impressions'] > 0, 'scode'] = 'Imps'
data1.loc[data1['Clicks'] > 0, 'scode'] = 'Clicks'

 
data1['scode'] = data1['scode'].astype('category')

 
print(data1.head())

 
def clen(x):
    return len(x)

 
etable = data1.groupby(['scode', 'Gender', 'agecat'])['Impressions'].apply(clen).reset_index()
print(etable)



```

## if you got any warning 
## add this 
```py
warnings.filterwarnings("ignore", category=FutureWarning)
warnings.filterwarnings("ignore", module="seaborn._oldcore")
```

# updated code 
```py

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings

 
warnings.filterwarnings("ignore", category=FutureWarning)
warnings.filterwarnings("ignore", module="seaborn._oldcore")

#   dataset
data1 = pd.read_csv('/kaggle/input/nyt1-csv/nyt1.csv')

 
data1['Age'] = data1['Age'].fillna(-1)

 
bins = [-float('inf'), 0, 18, 24, 34, 44, 54, 64, float('inf')]
labels = ['<0', '0-18', '19-24', '25-34', '35-44', '45-54', '55-64', '65+']
data1['agecat'] = pd.cut(data1['Age'], bins, labels=labels)

 
print(data1.describe())

 
def siterange(x):
    return len(x), x.min(), x.mean(), x.max()

 
age_summary = data1.groupby('agecat', observed=True)['Age'].apply(siterange).reset_index()
print(age_summary)

 
summary = data1.groupby('agecat', observed=True).agg({
    'Gender': 'sum',
    'Signed_In': 'sum',
    'Impressions': 'sum',
    'Clicks': 'sum'
}).reset_index()
print(summary)

 
plt.figure(figsize=(10, 6))
sns.histplot(data1, x='Impressions', hue='agecat', multiple='stack')
plt.title('Histogram of Impressions by Age Category')
plt.show()

 
plt.figure(figsize=(10, 6))
sns.boxplot(data=data1, x='agecat', y='Impressions', palette='Set3')
plt.title('Boxplot of Impressions by Age Category')
plt.show()

 
data1['hasimps'] = pd.cut(data1['Impressions'], bins=[-float('inf'), 0, float('inf')], labels=['NoImps', 'Imps'])

 
data1['Clicks/Impressions'] = data1['Clicks'] / data1['Impressions'].replace(0, 1)  # Avoid division by zero
data1['Clicks/Impressions'] = data1['Clicks/Impressions'].replace([np.inf, -np.inf], np.nan)  # Replace inf with NaN

 
clicks_summary = data1.groupby('hasimps', observed=True)['Clicks'].apply(siterange).reset_index()
print(clicks_summary)

 
plt.figure(figsize=(10, 6))
sns.kdeplot(data=data1[data1['Impressions'] > 0], x='Clicks/Impressions', hue='agecat')
plt.title('Density Plot of Clicks/Impressions by Age Category')
plt.show()

 
plt.figure(figsize=(10, 6))
sns.boxplot(data=data1[data1['Clicks'] > 0], x='agecat', y='Clicks', palette='Set3')
plt.title('Boxplot of Clicks by Age Category (Clicks > 0)')
plt.show()

 
data1['scode'] = 'NoImps'
data1.loc[data1['Impressions'] > 0, 'scode'] = 'Imps'
data1.loc[data1['Clicks'] > 0, 'scode'] = 'Clicks'

 
data1['scode'] = data1['scode'].astype('category')

 
print(data1.head())
 
def clen(x):
    return len(x)

 
etable = data1.groupby(['scode', 'Gender', 'agecat'], observed=True)['Impressions'].apply(clen).reset_index()
print(etable)

```




# Output
```
                 Age         Gender    Impressions         Clicks  \
count  458441.000000  458441.000000  458441.000000  458441.000000   
mean       29.482551       0.367037       5.007316       0.092594   
std        23.607034       0.481997       2.239349       0.309973   
min         0.000000       0.000000       0.000000       0.000000   
25%         0.000000       0.000000       3.000000       0.000000   
50%        31.000000       0.000000       5.000000       0.000000   
75%        48.000000       1.000000       6.000000       0.000000   
max       108.000000       1.000000      20.000000       4.000000   

           Signed_In  
count  458441.000000  
mean        0.700930  
std         0.457851  
min         0.000000  
25%         0.000000  
50%         1.000000  
75%         1.000000  
max         1.000000  
  agecat                                  Age
0     <0                  (137106, 0, 0.0, 0)
1   0-18   (19252, 7, 16.033503012674007, 18)
2  19-24  (35270, 19, 21.269038843209525, 24)
3  25-34  (58174, 25, 29.503352012926737, 34)
4  35-44   (70860, 35, 39.49467965001411, 44)
5  45-54   (64288, 45, 49.49258026381284, 54)
6  55-64  (44738, 55, 59.498189458625774, 64)
7    65+  (28753, 65, 72.98869683163495, 108)
  agecat  Gender  Signed_In  Impressions  Clicks
0     <0       0          0       685483   19480
1   0-18   12362      19252        96240    2523
2  19-24   18829      35270       176584    1709
3  25-34   30958      58174       290511    2937
4  35-44   37676      70860       355824    3662
5  45-54   34007      64288       322109    3232
6  55-64   23988      44738       224688    4556
7    65+   10445      28753       144120    4350
 
```
---
![image](https://github.com/user-attachments/assets/6854141a-fca5-471c-a531-b7e3edc3a2bf)
![image](https://github.com/user-attachments/assets/39b92456-f582-4299-9344-aeb41a081df9)
![image](https://github.com/user-attachments/assets/654a28ea-5006-4e9e-8feb-118de3751ad5)

![image](https://github.com/user-attachments/assets/97d5bfdb-10d3-4961-860d-019e34c499ea)

```
   Age  Gender  Impressions  Clicks  Signed_In agecat hasimps  \
0   36       0            3       0          1  35-44    Imps   
1   73       1            3       0          1    65+    Imps   
2   30       0            3       0          1  25-34    Imps   
3   49       1            3       0          1  45-54    Imps   
4   47       1           11       0          1  45-54    Imps   

   Clicks/Impressions scode  
0                 0.0  Imps  
1                 0.0  Imps  
2                 0.0  Imps  
3                 0.0  Imps  
4                 0.0  Imps  
     scode  Gender agecat  Impressions
0   Clicks       0     <0      17776.0
1   Clicks       0   0-18        846.0
2   Clicks       0  19-24        779.0
3   Clicks       0  25-34       1361.0
4   Clicks       0  35-44       1675.0
5   Clicks       0  45-54       1494.0
6   Clicks       0  55-64       2006.0
7   Clicks       0    65+       2598.0
8   Clicks       1     <0          NaN
9   Clicks       1   0-18       1525.0
10  Clicks       1  19-24        890.0
11  Clicks       1  25-34       1509.0
12  Clicks       1  35-44       1917.0
13  Clicks       1  45-54       1645.0
14  Clicks       1  55-64       2331.0
15  Clicks       1    65+       1486.0
16    Imps       0     <0     118401.0
17    Imps       0   0-18       6001.0
18    Imps       0  19-24      15538.0
19    Imps       0  25-34      25690.0
20    Imps       0  35-44      31290.0
21    Imps       0  45-54      28563.0
22    Imps       0  55-64      18626.0
23    Imps       0    65+      15585.0
24    Imps       1     <0          NaN
25    Imps       1   0-18      10754.0
26    Imps       1  19-24      17807.0
27    Imps       1  25-34      29241.0
28    Imps       1  35-44      35512.0
29    Imps       1  45-54      32143.0
30    Imps       1  55-64      21499.0
31    Imps       1    65+       8887.0
32  NoImps       0     <0        929.0
33  NoImps       0   0-18         43.0
34  NoImps       0  19-24        124.0
35  NoImps       0  25-34        165.0
36  NoImps       0  35-44        219.0
37  NoImps       0  45-54        224.0
38  NoImps       0  55-64        118.0
39  NoImps       0    65+        125.0
40  NoImps       1     <0          NaN
41  NoImps       1   0-18         83.0
42  NoImps       1  19-24        132.0
43  NoImps       1  25-34        208.0
44  NoImps       1  35-44        247.0
45  NoImps       1  45-54        219.0
46  NoImps       1  55-64        158.0
47  NoImps       1    65+         72.0

```








