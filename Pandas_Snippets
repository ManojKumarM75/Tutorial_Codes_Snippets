# from array of dict, create a df
df_out = pd.DataFrame.from_dict(OutChannelList) 
print("DF- Out : ", len(df_out.index))

# pandas join two DataFrames
pd.set_option("display.max_columns", None)
pd.set_option("display.max_rows", None)
#pd.set_option("max_rows", None)

#print(len(df_out))
#print(df_out.to_string())
df_in = pd.DataFrame.from_dict(InChannelList)
df_in.info()
#print(df_in.to_string())
df_parta = df_in[["In_Key", "In_Slot", "In_Dest_Ip", "In_Dest_Port", "InChannelName", "In_isPresent", "ExtSource1_Key"]]
df_partb = df_in[["In_Key", "In_Slot", "In_Dest_Ip", "In_Dest_Port", "InChannelName", "In_isPresent", "ExtSource2_Key"]]
df_partb = df_partb.rename(columns = {'ExtSource2_Key':'ExtSource1_Key'}, inplace = True)

df_parta.info()
df_partb.info()


#print(pd.isnull(df_partb["ExtSource2_Key"]))
#print(df_partb.isnull().values.any())
#print(df_partb["ExtSource2_Key"])
df3=df_out.merge(df_parta, left_on='In_Key', right_on='ExtSource1_Key', how='inner')
df4=df_out.merge(df_partb, left_on='In_Key', right_on='ExtSource2_Key', how='inner')
print("DF- In : ", len(df_in.index))
print("DF- InA : ", len(df_parta.index))
print("DF- InB : ", len(df_partb.index))
print("DF- Out + InA : ", len(df3.index))
print("DF- Out + InB : ", len(df4.index))
df5 = pd.concat([df3, df4])
print("DF- 5 : ", len(df5.index))
df5.info()
exit()
df3=df_out.merge(df_in, left_on=['In_Key', 'In_Key'], right_on=['ExtSource1_Key', 'ExtSource2_Key'], how='inner')
#df3=df_out.join(df_in, lsuffix="_left", rsuffix="_right")
print("===============================")
print(df3.info())
#df4 = df3[["In_Slot","In_Dest_Ip", "In_Dest_Port", "InChannelName", "isPresent", "Out_Slot", "OutIp", "OutPort", "OutChannelName" ]]
#df4 = df3[["In_Slot", "In_Dest_Port", "InChannelName", "isPresent", "Out_Slot", "OutIp", "OutChannelName" ]]
#for row in df3:
#    print(row.)
#display(df4)
print(df3.to_string())
df3.to_csv("test.csv")
