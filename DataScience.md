# DataScience

## [<u>NumPy</u>](https://numpy.org/doc/stable/index.html)
### Arrays
```python
import numpy as np

a = np.array([1, 2, 3])   # Create a rank 1 array
print(type(a))            # Prints "<class 'numpy.ndarray'>"
print(a.shape)            # Prints "(3,)"
print(a[0], a[1], a[2])   # Prints "1 2 3"
a[0] = 5                  # Change an element of the array
print(a)                  # Prints "[5, 2, 3]"

b = np.array([[1,2,3],[4,5,6]])    # Create a rank 2 array
print(b.shape)                     # Prints "(2, 3)"
print(b[0, 0], b[0, 1], b[1, 0])   # Prints "1 2 4"
```

### Create array
```python
import numpy as np

a = np.zeros((2,2))   # Create an array of all zeros
print(a)              # Prints "[[ 0.  0.]
                      #          [ 0.  0.]]"

b = np.ones((1,2))    # Create an array of all ones
print(b)              # Prints "[[ 1.  1.]]"

c = np.full((2,2), 7)  # Create a constant array
print(c)               # Prints "[[ 7.  7.]
                       #          [ 7.  7.]]"

d = np.eye(2)         # Create a 2x2 identity matrix
print(d)              # Prints "[[ 1.  0.]
                      #          [ 0.  1.]]"

e = np.random.random((2,2))  # Create an array filled with random values
print(e)                     # Might print "[[ 0.91940167  0.08143941]
                             #               [ 0.68744134  0.87236687]]"
```

### Array indexing
```python
import numpy as np

# Create rank 2 array with shape (3, 4)
# [[ 1  2  3  4]
#  [ 5  6  7  8]
#  [ 9 10 11 12]]
a = np.array([[1,2,3,4], [5,6,7,8], [9,10,11,12]])

# Use slicing to pull out the subarray consisting of the first 2 rows
# and columns 1 and 2; b is the following array of shape (2, 2):
# [[2 3]
#  [6 7]]
b = a[:2, 1:3]

# A slice of an array is a view into the same data, so modifying it
# will modify the original array.
print(a[0, 1])   # Prints "2"
b[0, 0] = 77     # b[0, 0] is the same piece of data as a[0, 1]
print(a[0, 1])   # Prints "77"
```

### Boolean array indexing
```python
import numpy as np

a = np.array([[1,2], [3, 4], [5, 6]])

bool_idx = (a > 2)   # Find the elements that are bigger than 2;
                     # this returns a numpy array of Booleans of the same
                     # shape as a, where each slot of bool_idx tells
                     # whether that element of a is > 2.

print(bool_idx)      # Prints "[[False False]
                     #          [ True  True]
                     #          [ True  True]]"

# We use boolean array indexing to construct a rank 1 array
# consisting of the elements of a corresponding to the True values
# of bool_idx
print(a[bool_idx])  # Prints "[3 4 5 6]"

# We can do all of the above in a single concise statement:
print(a[a > 2])     # Prints "[3 4 5 6]"
```

### Datatypes
```python 
import numpy as np

x = np.array([1, 2])   # Let numpy choose the datatype
print(x.dtype)         # Prints "int64"

x = np.array([1.0, 2.0])   # Let numpy choose the datatype
print(x.dtype)             # Prints "float64"

x = np.array([1, 2], dtype=np.int64)   # Force a particular datatype
print(x.dtype)                         # Prints "int64"
```

### Array math
```python
import numpy as np

x = np.array([[1,2],[3,4]], dtype=np.float64)
y = np.array([[5,6],[7,8]], dtype=np.float64)

# Elementwise sum; both produce the array
# [[ 6.0  8.0]
#  [10.0 12.0]]
print(x + y)
print(np.add(x, y))

# Elementwise difference; both produce the array
# [[-4.0 -4.0]
#  [-4.0 -4.0]]
print(x - y)
print(np.subtract(x, y))

# Elementwise product; both produce the array
# [[ 5.0 12.0]
#  [21.0 32.0]]
print(x * y)
print(np.multiply(x, y))

# Elementwise division; both produce the array
# [[ 0.2         0.33333333]
#  [ 0.42857143  0.5       ]]
print(x / y)
print(np.divide(x, y))

# Elementwise square root; produces the array
# [[ 1.          1.41421356]
#  [ 1.73205081  2.        ]]
print(np.sqrt(x))

x = np.array([[1,2],[3,4]])
y = np.array([[5,6],[7,8]])

v = np.array([9,10])
w = np.array([11, 12])

# Inner product of vectors; both produce 219
print(v.dot(w))
print(np.dot(v, w))

# Matrix / vector product; both produce the rank 1 array [29 67]
print(x.dot(v))
print(np.dot(x, v))

# Matrix / matrix product; both produce the rank 2 array
# [[19 22]
#  [43 50]]
print(x.dot(y))
print(np.dot(x, y))

x = np.array([[1,2],[3,4]])

print(np.sum(x))  # Compute sum of all elements; prints "10"
print(np.sum(x, axis=0))  # Compute sum of each column; prints "[4 6]"
print(np.sum(x, axis=1))  # Compute sum of each row; prints "[3 7]"

# Transpose
import numpy as np

x = np.array([[1,2], [3,4]])
print(x)    # Prints "[[1 2]
            #          [3 4]]"
print(x.T)  # Prints "[[1 3]
            #          [2 4]]"

# Note that taking the transpose of a rank 1 array does nothing:
v = np.array([1,2,3])
print(v)    # Prints "[1 2 3]"
print(v.T)  # Prints "[1 2 3]"
```

![numpy_merkblatt.jpg](.\numpy_merkblatt.jpg)

## [<u>Pandas</u>](https://pandas.pydata.org/docs/)

### <u>Series</u>
```python
import numpy as np
import pandas as pd

labels = ["a", "b", "c"]
liste = [10, 20, 30]
arr = np.array(liste)
d = {"a": 10, "b": 20, "c":30}

# create Series from list
pd.Series(data=liste)

# create Series from list with index
pd.Series(data=liste,index=labels)

# create Series from numpy array with index
pd.Series(arr, labels)

# pandas recognise keys of dict automaticly 
# and makes them to index
pd.Series(d)
```

```python
ser1 = pd.Series([1,2,3,4], index=["USA", "Deutschland", "Russland", "Japan"])
ser2 = pd.Series([5,6,7,8], index=["USA", "Deutschland", "Italien", "Japan"])
ser1 + ser2

# result
Deutschland     8.0
Italien         NaN
Japan          12.0
Russland        NaN
USA             6.0
dtype: float64
```
### <u>Data Frames</u>
```python
import numpy as np
import pandas as pd

from numpy.random import randn

#
np.random.seed(101)

# create DataFrame, matrix with random numbers 5-rows (index) 4-columns
# index tells the 'names' of rows column tells 'names' of columns
df = pd.DataFrame(randn(5,4), index='A B C D E'.split(), columns='W X Y Z'.split())

# returns column 'W'
df["W"]

# returns columns 'W' and 'Z', it has to be a list of indixes
df[["W","Z"]] 

# returns column 'W' (SQL syntax)
df.W

# crate a new column
df["F"] = df["W"] + df["Y"]

# drop create new DataFrame without column 'F', parameter axis tells what has to be delete
# axis=0 -> drop row (default value)
# axis=1 -> drop column
df.drop('F', axis=1)

# don't create a new DataFrame, but drop from this DataFrame
df.drop('F', axis=1, inplace=True)

# returns a row 'A', access the row by name
df.loc['A']

# returns a row with index 2, access the row by index
df.iloc[2]

# returns value of coordinate, is also posible with coordinates with iloc[1,2]
df.loc['B', 'Y']

# returns a subset, by changing of values in subset effects to df
df.loc[['A','B'], ['W', 'Y']]

# conditions
df>0

df[df>0]

df['W']>0

# returns all rows from DataFrame, where value of 'W'-row is <0 
df[df['W']>0]

# returns all rows from 'Y', where value of 'W'-row is <0 
df[df['W']>0]['Y']

# returns all rows from 'Y' and 'X', where value of 'W'-row is <0 
df[df['W']>0][['Y', 'X']]

# set index to 0, 1, ....
df.reset_index()

# create new index List and set it to the DataFrame
index_staaten = 'BY BW HH BB NW'.split()
df['Staaten'] = index_staaten
df.set_index('Staaten', inplace=True)

# returns name of Index
df.index.name
```
### <u>Data Frames</u>

```python
import numpy as np
import pandas as pd

# create DataFrame
df = pd.DataFrame({'A':[1,2,np.nan], 'B':[5,np.nan,np.nan], 'C':[1,2,3]})

# Elimination process
# returns only rows without nan-values, if axis=0 (default values) returns columns
df.dropna(axis=1)

# Threshold (Schwelle)
# returns rows with number of nan-values lessthen 2
df.dropna(thresh=2)

# Inputation
# returns DataFrame and fill nan-values with value (=0)
df.fillna(value=0)

# returns column 'A' and fill nan-values with mean of column 'A'
df['A'].fillna(value=df['A'].mean())
```

### <u>GroupBy</u>
```python
import pandas as pd
data = {'Firma':['GOOG', 'GOOG','MSFT', 'MSFT', 'FB', 'FB'],
        'Person':['Sam','Charlie', 'Amy', 'Vanessa', 'Carl', 'Sarah'],
        'Sales':[200,120,340,124,243,350]
}

df = pd.DataFrame(data)

# create groupby-object
by_firma = df.groupby('Firma')

by_firma.mean() # calculate a mean value
by_firma.std() # calculate a std value
by_firma.min() # calculate a min value
by_firma.max()['Sales'] # calculate a max value for sales column
by_firma.count() # calculate a count value
by_firma.describe() # calculate a statistic values of the data frame
by_firma.describe().transpose() # transpose the matrix with statsitsc values
by_firma.describe().transpose()['GOOG'] # calculate a statistic values only for column 'GOOG'
```

### <u>Merging, Joining and Concatenating</u>
```python
import pandas as pd

df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                        'B': ['B0', 'B1', 'B2', 'B3'],
                        'C': ['C0', 'C1', 'C2', 'C3'],
                        'D': ['D0', 'D1', 'D2', 'D3']},
                        index=[0, 1, 2, 3])

df2 = pd.DataFrame({'A': ['A4', 'A5', 'A6', 'A7'],
                        'B': ['B4', 'B5', 'B6', 'B7'],
                        'C': ['C4', 'C5', 'C6', 'C7'],
                        'D': ['D4', 'D5', 'D6', 'D7']},
                         index=[4, 5, 6, 7]) 

df3 = pd.DataFrame({'A': ['A8', 'A9', 'A10', 'A11'],
                        'B': ['B8', 'B9', 'B10', 'B11'],
                        'C': ['C8', 'C9', 'C10', 'C11'],
                        'D': ['D8', 'D9', 'D10', 'D11']},
                        index=[8, 9, 10, 11])

# Concat
# Concatanate by columns
pd.concat([df1, df2, df3])

# Concatanate by rows
pd.concat([df1, df2, df3], axis=1)

# Merge
links = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                     'A': ['A0', 'A1', 'A2', 'A3'],
                     'B': ['B0', 'B1', 'B2', 'B3']})
   
rechts = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                          'C': ['C0', 'C1', 'C2', 'C3'],
                          'D': ['D0', 'D1', 'D2', 'D3']})    

# merge dfs, how=[inner, outer, right, left] on=[name of column]
pd.merge(rechts, links, how='inner', on='key')

links = pd.DataFrame({'key1': ['K0', 'K0', 'K1', 'K2'],
                     'key2': ['K0', 'K1', 'K0', 'K1'],
                        'A': ['A0', 'A1', 'A2', 'A3'],
                        'B': ['B0', 'B1', 'B2', 'B3']})
    
rechts = pd.DataFrame({'key1': ['K0', 'K1', 'K1', 'K2'],
                               'key2': ['K0', 'K0', 'K0', 'K0'],
                                  'C': ['C0', 'C1', 'C2', 'C3'],
                                  'D': ['D0', 'D1', 'D2', 'D3']})

# merge dfs, how=[inner, outer, right, left] on=[name of columns]
pd.merge(links, rechts, how='left', on=['key1', 'key2'])

# Join
links = pd.DataFrame({'A': ['A0', 'A1', 'A2'],
                     'B': ['B0', 'B1', 'B2']},
                      index=['K0', 'K1', 'K2']) 

rechts = pd.DataFrame({'C': ['C0', 'C2', 'C3'],
                    'D': ['D0', 'D2', 'D3']},
                      index=['K0', 'K2', 'K3'])

# join dfs, how=[inner, outer, right, left]
links.join(rechts, how='outer')
```

## <u>Operations</u>
```python
import pandas as pd

df = pd.DataFrame({'spa1':[1,2,3,4],
                   'spa2':[444,555,666,444],
                   'spa3':['abc','def','ghi','xyz']})

df.head() # returns x first rows of DataFrame
df.loc[2].unique() # returns unique values of row with index 2
df['spa2'].unique() # returns unique values of column with name spa2
df['spa1'].nunique() # returns number of unique values
df['spa2'].value_counts() # returns number of values
df['spa1'].apply(function name) # applies the function to all values
df['spa2'].apply(lambda x: x*3) # applies lambda is posible
df.drop('spa1', axis=1) # delete row or col not permanently
del df['spa1'] # Delete row or column from DataFrame permanently
df.columns # show all columns names
df.index
df.sort_values(by='spa2', inplace=True) # sorts DF by spa2

data = {'A':['foo','foo','foo','bar','bar','bar'],
        'B':['one','one','two','two','one','one'],
        'C':['x','y','x','y','x','y'],
        'D':[1,3,2,5,4,1]
}

df = pd.DataFrame(data)

# pivote table
df.pivot_table(values='D', index=['A','B'],columns='C')
```

# <u>CSV, Excel and SQL</u>
```python
import numpy as np
import pandas as pd

df = pd.read_csv(<file path>)
df.to_csv(<file name>)

df = pd.read_excel(<path>, sheetname=<sheetname>)
df.to_excel(<path>, sheetname=<name>)

# es werden alle Tabellen auf der Seit geparst
# und als liste in df_html gespeichern
df_html = pd.read_html(<link>)

from sqlalchemy import create_engine

engine = create_engine('sqlite:///:memory:')
df.to_sql('Daten', engine)
sql_df = pd.read_sql('Daten', con=engine)
```

![Pandas_merkblatt_01](.\Pandas_Merkblatt_01.png)
![Pandas_merkblatt_01](.\Pandas_Merkblatt_02.png)