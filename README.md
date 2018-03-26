
Description
========================================================
As a light data **processing** and **analysis** library，**DaPy** is
committed to saving data scientists the time of analyzing
datasets and improving the efficiency of research.
We hope that DaPy can help data scientists process or 
analysis their datasets more *quickly* and *easily*.  

In terms of **data loading**, DaPy's data structure 
is so clear and concise that data scientists could "feel" data;
functions are feature-rich and efficient, saving data
scientists the processing time for complex data. In terms
of **descriptive statistics**, DaPy has provided comprehensive
calculation formulas that can help data scientists quickly
understand data characteristics.  

In the future, DaPy will add more data cleansing and
***inferential statistics functions***; implement more formulas
used in ***mathematical modeling***; and even
include some simple ***machine learning models*** (multilayer
perceptrons, support vector machines, etc.). DaPy is
continuously improving according to the data analysis process.  

If you think DaPy is interesting or helpful,
don't forget to share DaPy with your frineds! If you have 
any suggestions, please tell us with "Issues". Besides, 
*giving us a 'Star'* will be the best way to encourage us!  

Installation
========================================================
The Latest version 1.3.1 had been upload to PyPi.
```
pip install DaPy
```

Characteristic
========================================================
We have tested the performance of DaPy in loading file.
It was an amazing result that DaPy has the `fastest speed` with `less memory`.
Despite this, because DaPy is not yet able to support matrix operations, it has a long way to go to achieve Numpy's and Pandas' achievements in scientific computing. The testing code has been uploaded already.
<table>
<tr>
	<td>Date: 2018-3-12</td>
	<td>Testing Information</td>
	</tr>
<tr>
	<td>CPU</td>
	<td>Intel Core i7-6560U</td>
	</tr>
<tr>
	<td>Hard Disk</td>
	<td>NVMe THNSN5256GPU7 NV</td>
	</tr>
<tr>
	<td>File Size</td>
	<td>96MB</td>
	</tr>
<tr>
	<td>Platform</td>
	<td>Win10</td>
	</tr>
<tr>
	<td>Lancher</td>
	<td>Python2.7-64Bit</td>
	</tr>
</table>
<table>
<tr>
	<td>Result of Testing</td>
</tr>
<tr>
	<td></td>
	<td>DaPy</td>
	<td>Pandas</td>
	<td>Numpy</td> 
</tr>
<tr>
	<td>Loading Time</td>
	<td>17.77s</td>
	<td>4.55s</td>
	<td>62.23s</td>
</tr>
<tr>
	<td>Traverse Time</td>
	<td>0.5s</td>
	<td>316.5s</td>
	<td>0.1s</td>
</tr>
<tr>
	<td>Total Spent</td>
	<td>18.2s</td>
	<td>321.1s</td>
	<td>62.3</td>
	</tr>
<tr>
	<td>Memory Size</td>
	<td>14MB</td>
	<td>174MB</td>
	<td>69MB</td>
	</tr>
</table>

Examples
========================================================

```Python
<Example 1>
>>> import DaPy as dp
>>> data = dp.DataSet('ExamplesDB.csv')
>>> data.readframe()
>>> data.data
[Data(A_col=3, B_col=2, C_col=1, D_col=4),
 Data(A_col=4, B_col=3, C_col=2, D_col=2), 
 Data(A_col=1, B_col=3, C_col=4, D_col=2), 
 Data(A_col=3, B_col=3, C_col=1, D_col=2), 
 Data(A_col=4, B_col=5, C_col=4, D_col=3),
 Data(A_col=2, B_col=1, C_col=1, D_col=5),
 Data(A_col=6, B_col=4, C_col=3, D_col=2),
 Data(A_col=4, B_col=7, C_col=8, D_col=3),
 Data(A_col=1, B_col=9, C_col=8, D_col=3),
 Data(A_col=3, B_col=2, C_col=6, D_col=5),
 Data(A_col=2, B_col=9, C_col=1, D_col=5),
 Data(A_col=3, B_col=4, C_col=1, D_col=6)]
>>> data[0].B_col # Data in the second column of the first record
2
>>> data[-1].C_col # Data in the third column of the last record
1
>>>
```

In Example 1, you have loaded a data set as a frame 
from your data profile. Easily, right? Anyway, there is 
another way to load data by column as series. Here is 
the example.

```Python
<Example 2>
>>> data.readcol()
>>> data.titles
['A_col', 'B_col', 'C_col', 'D_col']
>>> for title in data.titles:
	print title, data[title]
	
A_col [3, 4, 1, 3, 4, 2, 6, 4, 1, 3, 2, 3]
B_col [2, 3, 3, 3, 5, 1, 4, 7, 9, 2, 9, 4]
C_col [1, 2, 4, 1, 4, 1, 3, 8, 8, 6, 1, 1]
D_col [4, 2, 2, 2, 3, 5, 2, 3, 3, 5, 5, 6]
>>>
```

Example 1 and Example 2  have showed two ways to load data.
But a simpler data structure is always neccessary. We offer
the third way to load data in bellowed.

```Python
<Example 3>
>>> data.readtable()
>>> data.data
[[3, 2, 1, 4], 
 [4, 3, 2, 2], 
 [1, 3, 4, 2], 
 [3, 3, 1, 2], 
 [4, 5, 4, 3], 
 [2, 1, 1, 5], 
 [6, 4, 3, 2], 
 [4, 7, 8, 3], 
 [1, 9, 8, 3], 
 [3, 2, 6, 5], 
 [2, 9, 1, 5], 
 [3, 4, 1, 6]]
>>>
```
Afther we load the data in menmory, we would like to 
characterize the data set and try to describe it. See the 
example as follow.

```Python
<Example 4>
>>> data.readcol()
>>> len(data) # How much records does dataset include
12
>>> str(data) # The name of dataset
'Data'
>>> dp.CountDistribution(data['A_col'])
[0.16666666666666666, 0.16666666666666666, 0.0, 0.3333333333333333, 0.0, 0.25, 0.0, 0.0, 0.0, 0.08333333333333333]
>>> dp.CountFrequency(data['A_col'],2)
0.16666666666666666
>>> dp.Statistic(data['A_col'])
STAT(Mean=3.0, Std=1.4142135623730951, CV=0.47140452079103173, Min=1, Max=6, Range=5)
>>> dp.CountQuantiles(data['A_col'])
[1, 1, 2, 3, 4, 6]
>>> dp.cov(data['A_col'], data['B_col'])
-0.5833333333333339
>>>
```

Finally, we also support the user opearts the dataset with
'-' or '+'. It will help you change the data size.


```Python
<Example 5>
>>> data.readtable()
>>> data - 2
>>> len(data)
10
>>> data.data
[[3, 2, 1, 4], 
 [4, 3, 2, 2], 
 [1, 3, 4, 2], 
 [3, 3, 1, 2], 
 [4, 5, 4, 3], 
 [2, 1, 1, 5], 
 [6, 4, 3, 2], 
 [4, 7, 8, 3], 
 [1, 9, 8, 3], 
 [3, 2, 6, 5], 
 [2, 9, 1, 5], 
 [3, 4, 1, 6]]
>>>
```
Data Structure
========================================================
Since the very beginning, we have designed DaPy to Python's native data structure as much as possible, so that it is easier for users to adapt to our library. At the same time, we believe that the original data structure of Python will definitely perform better than our own. The results of the experiment also prove this idea.
- Type of Value
	- [float] 
		If the symbol of '.' is inside of the value, Datapy will try to transfrom the value into 'float' at first, while you load a new dataset from file. The type of float are descided by Python.
	- [integer]
		If the value contains digit number only, Datapy will transfrom it in to 'int'.
	- [Bool]
		If the value is similar as blanket, 'None', 'NA', 'N/A' and '?', Datapy will transfrom the value into None or anything else you set as missing value.
	- [string] 
		If the value doesn't meet any condition, it will be transfrom into 'string'. 

- Type of DataSet
	- [frame] It is a list with amount of named-tuples inside. You can easily get the records you want with this data structure. And it is write-protected by "tuples", and you can be more at ease with your data. Therefore, we recommend that you use this data structure when you only need to traverse the data without changing it.
	- [table] It is a list with amount of lists inside. This is a simple data structure for you. While you use this structure, you always expect to process the source data set.
	- [series] It is a diction while the column name are 'Key' and datas are included in a list as 'Value'. When you need to analyze a variable in the dataset and not all the variables in each record, you can easily extract one column in this structure.


Instructions for use
========================================================
```Python
DaPy.DataSet(addr='data.csv', title=True, split='AUTO',db=None, name='Data', firstline=1, miss_value=None)
```
This class is the core function for processing data, which supports user to pretreatment the database.
distribution of the data.
* [addr] Your database path and name;
* [title] "True" means your database includes title in some line. To the contrary, "False" means the there is no title on it.
* [split] This variable means the separator of the database in every line. 'AUTO' will ask system find the best match separator to split the file. The system will set separator as ',' if the file type is '.cvs' and set separator as ' ' if the file type is '.txt', while will set separator as '\t' if the file type is '.xls'.
* [db] You could set a canned database.
* [name] Your database name.
* [firstline] Your data starts from "firstline".
* [miss_value] The missing value in your data will be replace into the simble of this variable.
```Python
DataSet.readframe(col=all)
```
This function will help you load data from a file as a DataFrame, which implements with some named-tuple in a list. You could pickout the  data with line number and columen name.
- [col] Giving a iterable variable which contains the column number you would like to choose.

```Python
DataSet.readtable(col=all)
```
This function will help you load data from a file as a DataFrame, which implements with lists only. So it will not be allowed in pick out data with the column name.
- [col] Giving a iterable variable which contains the column number you would like to choose.

```Python
DataSet.readcol(col=all)
```
This function supports user to load data by column which has the data structure as a diction and the keyword is column and the series is value. Additonly, you could pick series of  data in one column.
- [col] Giving a iterable variable which contains the column number you would like to choose.
```Python
DataSet.tocsv(addr)
```
This function will help you to save the dataset as a 'csv' file.
- [addr] Expects a string type value of file address.
```Python
DataSet.data
```
- Return the data you just loaded before.

```Python
DataSet.titles
```
- Return the title of this data set.

```Python
str(DataSet.data)
```
- Return the name of this dataset.

```Python
len(DataSet.data)
```
- Return the number of records.
```Python
DaPy.cor(data_1, data_2)
```
This function will help you calculate the correlation of two series data.
```Python
DaPy.cov(data_1, data_2)
```
This function will help you calculate the covariance of two series data.
```Python
DaPy.CountFrequency(data, cut=0.5)
```
This function is used in counting the distribution of a data series. 
- [cut] means the cut point you want.If you would like to calculate the proportion of series, you can get help from this function.
- [data] expects a iterble item, such as tuple() or list(). Unnecessary variable "cut" expects a number. It will return a float means the proportion of data which is larger than "cut".

```Python
DaPy.CountQuantiles(data, shapes=[0.05,0.1,0.25,0.5,0.75,0.9,0.95])
```
This function could help you find the Quantiles of the data.
- [shapes] Expects a iterble item which includes some decimals.
- Return the value of each quantile.
```Python
DaPy.CountDistribution(data, breaks=10)
```
This function could help you statistic the distribution of the data.
- [breaks] Expects a integer which means how many groups you would like to partition.
- Return a list that includes the frequency of each partition.
```Python
DaPy.Statistic(data)
```
- Return the basic statistics of the data set as NamedTuple.
- The tuple includes 'Mean','Std','CV','Min','Max' and 'Range'.

License
========================================================
Copyright (C) 2018 Xuansheng Wu
<br>
This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.</br>
<br>
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.</br>
<br>
You should have received a copy of the GNU General Public License
along with this program.  If not, see https:\\www.gnu.org\licenses.# datapy
A light Python library for data processing and analysing.</br>
