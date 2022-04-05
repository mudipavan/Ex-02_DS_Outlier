# Ex-02_DS_Outlier
# AIM
To detect and remove the outliers in the given data set and save the final data.
# EXPLANATION
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.
# ALGORITHM
# Step 1
Import the required packages(pandas,numpy,scipy)
# Step 2
Read the given csv file
# Step 3
Convert the file into a dataframe and get information of the data.
# Step 4
Remove the non numerical data columns using drop() method.
# Step 5
Detect the outliers in the data set using z scores method.
# Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
# Step 7
Check if the outliersare removed from data set using graphical methods.
# Step 8
Save the final data set into the file.
# PROGRAM
```
Developed by: Pavan.Mudi
Register number:212221230067


import pandas as pd
df=pd.read_csv('weight.csv')
df

#removing non numerical columns
df=df.drop("Gender",axis=1)
print('After removing Non numeric columns:')
df

#graph to display outliers
df.boxplot()

#calculating z scores to detect outliers
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
print(z)

#removing outliers from weight
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1

#checking if outliers are removed through graph
df1.boxplot()

#removing outliers from height
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df_new

#checking if outliers are removed through graph
df_new.boxplot()

#final dataset
df_new

#saving data file
df.to_csv('weight.csv', index=False)
```
# OUTPUT
# Initial data set
![image](https://user-images.githubusercontent.com/94828517/161674302-2d963613-d9a7-4332-973d-a3ff52f56539.png)
 
# Data set after removing non numerical sets
![image](https://user-images.githubusercontent.com/94828517/161674360-11eebf85-d0e7-41a8-b36b-30ebe093628f.png)

# Graph displaying initial dataset with outliers
![image](https://user-images.githubusercontent.com/94828517/161674399-14d82419-9bba-4bdd-8a82-cd8e46ccc514.png)
 
# Z scores to detect outliers
![image](https://user-images.githubusercontent.com/94828517/161674445-2547550f-8930-4bf9-84f5-362e8c154573.png)
 
# Data set after removing outliers in weight using z scores and list manupilation
![image](https://user-images.githubusercontent.com/94828517/161674466-15d72200-79af-43f2-a635-db74b7f71d20.png)
 
# Graph after removing outliers in weight
 ![image](https://user-images.githubusercontent.com/94828517/161674581-ed66c739-682e-4068-813c-dce837bba171.png)

# Data set after removing outliers in height using Interquartile Range(IQR)
![image](https://user-images.githubusercontent.com/94828517/161674606-aa15bc89-44a2-4ddf-8bc5-3ac565bb0dee.png)
 
# Final graph after removing all outliers
 ![image](https://user-images.githubusercontent.com/94828517/161674628-bdaf6082-2412-4f21-92ea-fad987298e8c.png)

# Final data set
 ![image](https://user-images.githubusercontent.com/94828517/161674640-c2327ce1-b393-4827-96d7-0fa0b0d8aa11.png)

# RESULT
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.

