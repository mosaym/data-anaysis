# data-anaysis_by using python _simple analyse for retrive inside

# By using python taking inside & convert to excel

import pandas as pd
import numpy as np

#checking data structure

df=pd.read_excel('EXIM DATA FY2021-22.xlsx',sheet_name='RAW DATA')
df.head()
df.columns

#data explore

df.groupby('EXPORTERNAME')['Total_Value_IN_FC'].sum().reset_index()
df.groupby(['EXPORTERNAME','CONSINEENAME','PRODUCTDESCRIPITION']).size()

#export data

sort_data=df.groupby(['EXPORTERNAME','CONSINEENAME','PRODUCTDESCRIPITION'])['Total_Value_IN_FC'].sum()
dx=pd.DataFrame(sort_data)

dx.to_excel('dx.xlsx',index=True)
