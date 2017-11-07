import pandas as pd
import numpy as np

# read and import excel files
his_data = pd.read_excel('C:\\Users\\Administrator\\Volvo\\Up_to_1102\\Historical_Data_1102.xlsx', index_col='Prospect id')
data_1103_m = pd.read_excel('C:\\Users\\Administrator\\Volvo\\Up_to_1102\\LeadApp_1103_morning.xlsx',  index_col ='Prospect id')

# concatenate two datasets
all_data = pd.concat([his_data, data_1103_m], ignore_index = False)
# change the actual column name a bit to avoid info leakage
all_data_clean = all_data.drop_duplicates(['*手机 ']) 

# pick up all the phone numbers (which represent people) that are unique in the merged dataset
data_1103_m_clean = data_1103_m.merge(all_data_clean, how = 'inner')

# save as excel file
writer = pd.ExcelWriter('pandas_simple.xlsx', engine='xlsxwriter')
data_1103_m_clean.to_excel(writer, sheet_name='Sheet1')
writer.save()
