# Hotel-Reviews

import numpy as np
import pandas as pd
import sklearn
import scipy

train_data = pd.read_csv("C:/Users/sudashan/Desktop/train_data.csv")
test_data = pd.read_csv("C:/Users/sudashan/Desktop/code/hotel_recc/test.csv")
train_data = train_data.head(1000)

train_data.drop(["date_time","site_name","user_id","hotel_market"],axis=1)
train_data.dropna(axis=0)

tsLen = len(train_data["date_time"])
train_data["Date"]=0
train_data["Time"]=0

#Takes the an item of the "date_time col and seperates the date & time, discarding the year
def getDate(item):
    date = (item[6:7],item[9:11])
    return date
def getTime(item):
    time = item[11:]
    return time
for i in range(tsLen):
    train_data["Date"][i]=getDate(train_data["date_time"][i])
    train_data["Time"][i]=getTime(train_data["date_time"][i])
