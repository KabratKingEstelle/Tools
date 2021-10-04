pandas

NAN

df\[pd.isnull(df).any(axis=1)\].head()

df = df.dropna()

Drop

df = df.dropna()

df = df.drop(\['name','cabin','ticket'\],axis=1)

Map

df\['sex'\].value_counts() female male

df\['sex'\] = df\['sex'\].map({'female':0,'male':}).astype(int)

df\['embarked'\] = df\['embarked'\].dropna().map( {'S':0, 'C':1, 'Q':2} ).astype(int)