import numpy as np
import pandas as pd
file  = open('sample.txt','r')
lines = file.readlines()
count = 0
column_sizes = np.array([11,11,8,35,31,1,35,8,70,1,9,1,1,1,10,10,1,7,15,35,35,35,35,35,35,35,35,35,35,35,35,35,35,35,2,7,2,5,4,2,1,1,20,3,7,11,3,7,11,1,100,3,20,20,10,1,1,1,1,1,1,1,1,1,1,1,1,20,1,11,11,1,1,1,1,1,1,1,1,1,1,1,1,1,216])
df = pd.DataFrame()
row_arr =[]
for line in lines:
    start_pos = 0
    end_pos = 0
    column_arr=[]
    for size in column_sizes:
        start_pos = end_pos
        end_pos = start_pos + int(size)
        column_arr.append(line[start_pos : end_pos])
    row_arr.append(column_arr)
df = pd.DataFrame(row_arr)
df.to_csv('sample.csv')
   #df = df.append(dict(zip(df.columns, row_arr)), ignore_index=True)
print(df)
