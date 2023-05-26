# Data Structure in Pandas
* A data structure is a collection of data values and operations that can be applied to that data.
* It enables efficient storage, retrival and modification to the data.
* Two commonly used data structures used in pandas are-
	* Series
	* DataFrame
	
# Series
* A series is a one-dimensional array containing a sequence of vaules of any data type (int, float, list, string etc.) which by default have numeric data lables starting from zero.
* The data lable associated with a particular value is called its Index. We can also assign values of other data types as index.
* We can imagine a Pandas Series as a column in a spreadsheet. For example- 
```	
  Index	Value
  0		Arnab
  1		Samridhi
  2		Ramit
  3		Divyam
  4		Kritika
```

## Creation of series
There are different ways in which a series can be created in Pandas. To create or use a series, we first need to import the Pandas library.

### Creation of series from Scalar Values
* A series can be created using scalar values as shown in examples below:

Input-
```
>>> import pandas as pd                 #import pandas with alias pd
>>> series1 = pd.Series([10,20,30])     #create a series
>>> print(series1)                      #display the series
```

Output-
```
0    10
1    20
2    30
dtype: int64
```
* 0bserve that the output is shown in two columns -  the index is on the left and the data value is on the right.
* If we do not explicitly specify the an index for the data values while creating a series,  then by default the indexes range from 0 to N-1 where N is the number of data elements.
* We can also use user-defined lables to the index and use them to access elements of a series. For example-

Input-
```
>>> series2 = pd.Series([10,20,30], index = [3,1,2])
>>> print(series2)
```
Output-
```
3    10
1    20
2    30
dtype: int64
```
* We can also use letters as indexes. For example-

Input-
```
>>> series3 = pd.Series([10,20,30], index = ['a','b','c'])
>>> print(series3)
```
Output-
```
a    10
b    20
c    30
dtype: int64
```

### Creation of Series from NumPy Arrays-
* We can create a series from a one-dimensional (1-D) NumPy array, as shown below-

Input-
```
>>> import numpy as np              #importing NumPy with alias np
>>> import pandas as pd             #importing Pandas with alias pd
>>> array1 = np.array([1,2,3,4])
>>> series1 = pd.Series(array1)
>>> print(series1)
```
Output-
```
0    1
1    2
2    3
3    4
dtype: int32
```
* We can also use letters and strings as indexes. For example-

Input-
```
>>> series2 = pd.Series(array1, index = ['a','b','c','d'])
>>> print(series2)
```
Output-
```
a    1
b    2
c    3
d    4
dtype: int32
```
* When index labels are passed with the array, then the length of the index must be of the same size, otherwise it will result in a ValueError. Refer the example below for more clarity-

Input-
```
>>> series3 = pd.Series(array1, index = ['a','b','c','d','e'])
```
Output-
```
ValueError: Length of values (4) does not match length of index (5)
```

### Creation of Series from Dictonaries
* We know that a dictonaries have key-value pairs, and a value can be quickly determined if its key is known.
* Dictionary keys can be used to construct an index for a series, as shown in the example below-

Input-
```
>>> dict1 = {"India":"NewDelhi","UK":"London","Japan":"Tokyo"}
>>> series1 = pd.Series(dict1)
>>> print(series1)
```
Output-
```
India    NewDelhi
UK          London
Japan        Tokyo
dtype: object
```

## Accessing the elements of a Series
* There are two common ways for accessing the elements of a series-
	* Indexing
	* Slicing

### Indexing 
* Indexing in Series is similar to that for NumPy arrays, and is used to access the elements in a series.
* Indexes are of two types-
	* Positional index-
		* It takes an integer value that corresponds to its position in the series starting from 0.
	* Labelled index-
		* It just takes any user-defined label as index.
* Following example shows the usage of Positional Index for accessing a value from the Series-

Input-
```
>>> seriesNum = pd.Series([10,20,30])
>>> seriesNum[2]
```
Output-
```
30
```
* Here, the value 30 is displayed for the positional index 2.
* When labels are specified, we can use labels as indices while selecting values from a series, as shown below. Here, the value 3 is displayed for the labelled index Mar-

Input-
```
>>> seriesMnths = pd.Series([2,3,4], index =  ['Feb','Mar','Apr'])
>>> seriesMnths['Mar']
```
Output-
```
3
```
* In the following example, value NewDelhi is is displayed for the labelled index India-

Input-
```
>>> seriesCapCntry = pd.Series(['NewDelhi','WashingtonDC','London','Paris'], index = ['India','USA','UK','France'])
>>> seriesCapCntry['India']
```
Output-
```
'NewDelhi'
```
* We can also access an element of a list using the positional index-

Input-
```
>>> seriesCapCntry[2]
```
Output-
```
'London'
```
* More than one element of a series can be accessed using a list of positional integers or a list of index labels as shown below-

Input-
```



