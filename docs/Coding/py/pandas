

## basic examples  
```python 
import pandas as pd
mydataset = {
  'cars': ["BMW", "Volvo", "Ford"],
  'passings': [3, 7, 2]
}
myvar = pd.DataFrame(mydataset)
print(pd.__version__)  # see version
# shows nice table 
print(myvar)  
a = [1, 7, 2]
myvar = pd.Series(a)
myvar = pd.Series(a, index = ["x", "y", "z"])	# adding column title. 
calories = {"day1": 420, "day2": 380, "day3": 390}
myvar = pd.Series(calories)	# series can take dictionary too. 
# it shows data in column, index is added. 
print(myvar)

df = pd.read_csv('data.csv')	# load the csv to data frame. 
mdf = pd.read_json('data.json')  # json can be read similarly. 

df = pd.read_csv('data.csv')
print(df.tail())    # show last 5 items. 
print(df.tail(10))  # show last 10 items
print(df.head(n))	# show first few items
print(df.info())    # show info 
```

## cleaning data

```python 
import pandas as pd
df = pd.read_csv('data.csv')
new_df = df.dropna()		#droping empty data. 
df.dropna(inplace=True) # if the source need to be changed. 
df.fillna(130, inplace = True)	# this will fill data with 130
df["Calories"].fillna(130, inplace = True)  #Replace NULL values in the "Calories" columns with the number 130:
x = df["Calories"].mean()	#mean
x = df["Calories"].median()  #median
x = df["Calories"].mode()[0]  #mode

# date reformat.  
df['Date'] = pd.to_datetime(df['Date'])
print(df.to_string())
print(new_df.to_string())
```


## plotting data. 

Both matplotlib and pandas needed. 
```python 
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv('data.csv')
df.plot()
df.plot(kind = 'scatter', x = 'Duration', y = 'Calories')  # kind can be defined. 
df["Duration"].plot(kind = 'hist')	# kind histo 
plt.show()
```



## cheat sheet

function| purpose | example|
-|-|-|-
DataFrame()|create dictionary type data|pd.DataFrame(dict)|dict value should be a list with same length
Series()|create column data|pd.Series(listdata)| |
tail()|print last 5 data for large set|df.tail()|number can be set too

## Reference
[DataFrame](https://www.w3schools.com/python/pandas/pandas_ref_dataframe.asp)  
