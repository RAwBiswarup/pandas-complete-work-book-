# pandas-complete-work-book-
import pandas as pd
import numpy as np

sub=pd.read_csv("simple employee data_csv.csv")

sub

sub.info()

sub.describe()

sub.isnull()

sub.isnull().sum()

sub["empid"].duplicated()

sub.drop_duplicates("empid",inplace=True)

sub

sub.dropna()

sub

sub["salary"].mean()

sub["salary"].replace(np.nan,28375.0,inplace=True)

sub

sub["name"].fillna(method="bfill",inplace=True)

sub

sub["last name"].fillna(method="bfill",inplace=True)

sub

sub["gender"].fillna(method="bfill",inplace=True)

sub

sub["joining mont"].fillna(method="ffill",inplace=True)

sub


sub["bonus amount"]=(sub["salary"]/100)*sub["bonus"]

sub

sub.loc[(sub["bonus"]==0),"bonus statuse"]="do not recive bonus"
sub.loc[(sub["bonus"]>0),"bonus statuse"]="recive bonus"

sub

sub["full name"]=sub["name"]+" "+sub["last name"]

sub

def extract (values):
    return values[:3]
sub["joining mont in sort"]=sub["joining mont"].map(extract)

sub

sub.groupby(["empid","gender"]).agg({"salary":"sum","bonus amount":"min"})

sub

# sub["salary"][0]=500

sub.drop("salary",axis=1)

sub

sub.drop(0)

sub.loc[[(0),(1)]]

sub1=sub[["empid","name","salary"]]

sub2=sub[["empid","bonus","bonus amount"]]

sub1

sub2

sub3=pd.merge(sub1,sub2,on="empid")

sub3


sub4=sub3.loc[[(0),(1),(2)]]

sub4

sub5=sub3.loc[[(3),(4),(5)]]

sub5

sub6=pd.concat([sub4,sub5])

sub6

dt={"emid":["e01","e02","e03","e04","e05"],"Name":["ram","sham","laxman","arjun","sudama"],"age":[21,20,23,25,20]}
dt1={"emid":["e01","e07","e03","e08","e05"],"sal":[50000,45000,40000,35000,100000]}

dtf1=pd.DataFrame(dt)
dtf2=pd.DataFrame(dt1)

dtf3=pd.merge(dtf1,dtf2,on="emid",how="right")
dtf4=pd.merge(dtf1,dtf2,on="emid",how="left")

dtf3

dtf4

# to compare dataframe :
item1={"fruit":["mango","banana","orange","apple","papaya"],"price":[150,50,120,250,25],"quantity":[9,7,20,22,2]}
item2={"fruit":["mango","banana","orange","apple","papaya"],"price":[180,50,150,220,25],"quantity":[8,7,18,25,2]}

item3=pd.DataFrame(item1)
item4=pd.DataFrame(item2)

com=item3.compare(item4)

com

com=item3.compare(item4,align_axis=0)

com

comeq=item3.compare(item4,keep_equal=True)

comeq

comeqf=item3.compare(item4,keep_equal=False)

comeqf

comsh=item3.compare(item4,keep_shape=True)

comsh

comshf=item3.compare(item4,keep_shape=False)

comshf

# Pivot tabular data :


dfp={"keys":["key1","key2","key1","key2"],"name":["ram","sham","laxman","bharat"],
     "house":["red","green","yellow","pink"],"greads":["2nd","1st","3rd","4th"]}

dpt=pd.DataFrame(dfp)

dpt

dpvt=dpt.pivot(index="keys",columns="name",values=["house","greads"]).fillna(0)

dpvt

# Melting data Frame :

dfp={"keys":["key1","key2","key1","key2"],"name":["ram","sham","laxman","bharat"],
     "house":["red","green","yellow","pink"],"greads":["2nd","1st","3rd","4th"]}

dm=pd.DataFrame(dfp)

dm

dtmlt=pd.melt(dm,id_vars=["name"],value_vars=["house"])

dtmlt

datamlt=pd.melt(dm,id_vars=["name"],value_vars=["house","greads"])

datamlt

