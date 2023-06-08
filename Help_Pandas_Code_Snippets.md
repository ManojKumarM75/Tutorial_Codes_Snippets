### Create a df from array of dict, 
df_out = pd.DataFrame.from_dict(OutChannelList) 

### len of df
print("DF- Out : ", len(df_out.index))

### show full cols, rows
pd.set_option("display.max_columns", None)

pd.set_option("display.max_rows", None)

### display whole df
#print(df_out.to_string())

### display structure
df_in.info()

### cut the df into many
df_parta = df_in[["In_Key", "In_Slot", "In_Dest_Ip", "In_Dest_Port", "InChannelName", "In_isPresent", "ExtSource1_Key"]]

df_partb = df_in[["In_Key", "In_Slot", "In_Dest_Ip", "In_Dest_Port", "InChannelName", "In_isPresent", "ExtSource2_Key"]]

### rename cols of df
df_partb = df_partb.rename(columns = {'ExtSource2_Key':'ExtSource1_Key'}, inplace = True)

### check for null
print(pd.isnull(df_partb["ExtSource2_Key"]))

print(df_partb.isnull().values.any())

### display only one col
print(df_partb["ExtSource2_Key"])

###  join two DataFrames (relate on key or keys (use array on both sides))
df3=df_out.merge(df_parta, left_on='In_Key', right_on='ExtSource1_Key', how='inner')
#not tested:  df3=df_out.merge(df_in, left_on=['In_Key', 'In_Key1'], right_on=['ExtSource1_Key', 'ExtSource2_Key'], how='inner')

### concat dfs
df5 = pd.concat([df3, df4])

### df to CSV
df3.to_csv("test.csv")


