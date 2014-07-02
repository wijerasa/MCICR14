---
title: "Introduction To R"
author: "Saranga Wijeratne"
highlighter: highlight.js
output: word_document
job: Systems Developer
knit: slidify::knit2slides
mode: selfcontained
hitheme: tomorrow
subtitle: null
framework: io2012
widgets: []
github:
        user: wijerasa
        repo: MCICR14
---

## Topics

1. Primitive Data types in R
2. Primary Data Structures in R
   - Vectors
   - List
   - Dataframes
 
3. Missing Data
4. Importing and Exporting Data

--- .class #0

## Useful R commands

### help and search
- ? - Help.  __Usage: ?c__
- ?? - Search. __Usage: ??c__

### Checking for types
- _str_, _mode_ provide info on type
- is.XXX
  - _XXX_: integer,numeric, logical,character
  
### Casting between types    
- as.XXX casts to specific type

--- .class #0.1

## Useful R commands

### Examing Objects
- y
- head(y)
- summary(y)
- str(y)
- dim(y)


--- .class #1 

## 1. Primitive Data types in R

- integer
- numeric
- text/string
- complex numbers
- logical values

--- .class #2

## 2. Primary Data Structures in R ##


- 2.1. Vectors - _Vectors are a collection of data of the same type._ 
- 2.2. Lists-    _Lists are a collection of R objects._
- 2.3. Data Frames- _Tabular data sets in R are stored as dataframes._

Dimension | Homogeneous | Heterogeneous
--------- | ----------- | -------------
1d        | Vector      | List
2d        | Matrix      | Data frame
nd        | Array


--- .class #3

## 2.1 Vectors ##

#### __Vectors are a collection of data of the same type.__ 

The data can be integers, floats (decimal numbers), complex numbers, text/strings, or logical values.

### Creating a Vector


- __c():__ Function combines the data into a Vector

 - Ex 1: 

   
   ```r
     doublevector<-c(11,12.4,56,100)        
   ```
  - Ex 2:

   
   ```r
     isthisavector<-c(12,"weirdo",23.4)                 
   ```

<style>
strong {
  font-weight: bold;
  font-style: italic;
}
em {
  font-style: italic;
}
</style>


--- .class #4

## 2.1  Vectors Cont... ##


### Creating a Vector ###

- __seq(from, to, by)__
 - Ex 1: 
 
 ```r
 intvector<-seq(from=1, to=100, by=2)
 ```
 #### OUTPUT:
 
 ```r
 intvector
 ```
 
 ```
 ##  [1]  1  3  5  7  9 11 13 15 17 19 21 23 25 27 29 31 33 35 37 39 41 43 45
 ## [24] 47 49 51 53 55 57 59 61 63 65 67 69 71 73 75 77 79 81 83 85 87 89 91
 ## [47] 93 95 97 99
 ```

<style>
strong {
  font-weight: bold;
  font-style: italic;
}
em {
  font-style: italic;
}
</style>


--- .class #5

## 2.1  Vectors Cont... ##


### Creating a Vector ###
 
 - Ex 2:
 
 ```r
 intvector<-1:40 
 ```
 OUTPUT:
 
 ```r
 intvector
 ```
 
 ```
 ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
 ## [24] 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40
 ```

--- .class #5

## 2.1  Vectors Cont... ##


### Address  values in a Vector ###

- __[]__ -use brackets. Ex:  _myVector[index]_
  - Ex 1:
  
  ```r
  myVector<-1:10
  
  first_item<-myVector[1]                         
  ```
 #### OUTPUT:
 
 ```r
  first_item
 ```
 
 ```
 ## [1] 1
 ```
**Note: Vectors in R are one-based** 
*i.e start at 1*

--- .class #6

## 2.1  Vectors Cont... ##


### Address  values in a Vector Cont... ###


  - Ex 2:
  
  ```r
  first_five_items<-myVector[1:5]    
  ```
  
  #### OUTPUT:
  
  ```r
  first_five_items
  ```
  
  ```
  ## [1] 1 2 3 4 5
  ```

--- .class #7

## 2.1  Vectors  ##


#### Question 


- From the R command line, creat a vector of 10 numbers.
- Append 4 __NA__ values. Hint: use __c()__ function to combine __NA__ vector with the number vector
- Use __is.na()__ function to identify __NA__ values in the above Vector
- Identify the type of data structure  generated in previous question (using __is.logical()__)

--- .class #7

## 2.2  Lists ##

#### __Lists are a collection of R objects.__ 

Unlike vectors, lists can consist any R objects i.e Vectors, Strings, integers.
Objects do not need to be in the same type.

### Creating a List ###

- __list():__ Function combines the data into a list
 - Ex 1: 

   
   ```r
     myAwesomeList<-list( 11,               #integer
                          12.4,             #double
                          c("Rep1","Rep2"), #character Vector
                          "RNA-Seq"         #String
                         )               
   ```

--- .class #8

## 2.2  Lists Cont... ##


### Creating a List Cont... ###
#### OUTPUT:

   
   ```r
     myAwesomeList              
   ```
   
   ```
   ## [[1]]
   ## [1] 11
   ## 
   ## [[2]]
   ## [1] 12.4
   ## 
   ## [[3]]
   ## [1] "Rep1" "Rep2"
   ## 
   ## [[4]]
   ## [1] "RNA-Seq"
   ```

--- .class #9

## 2.2 Lists Cont... ##


### Creating a List Cont... ###


  - Ex 2:
  
  ```r
  myAwesomeList2<-list(
                      countData=(
                                  list(c(12,13,45,155),c(1,3,5,130),c(12,13,45,155))
                                ),
                                
                      headers=c("R1","R2","C1","C2")
                    )    
  ```

--- .class #10

## 2.2 Lists Cont... ##


### Creating a List Cont... ###
#### OUTPUT:

   
   ```r
     myAwesomeList2              
   ```
   
   ```
   ## $countData
   ## $countData[[1]]
   ## [1]  12  13  45 155
   ## 
   ## $countData[[2]]
   ## [1]   1   3   5 130
   ## 
   ## $countData[[3]]
   ## [1]  12  13  45 155
   ## 
   ## 
   ## $headers
   ## [1] "R1" "R2" "C1" "C2"
   ```

--- .class #11

## 2.2 Lists Cont... ##


### Address  values in a List ###


  - __[]__ -use brackets
   - Ex 1: Get the first element of the list
  
  ```r
  myAwesomeList[1]                         
  ```
  
  ```
  ## [[1]]
  ## [1] 11
  ```
- Ex 2: Get the first element of the first element
  
  ```r
  myAwesomeList[[1]] 
  ```
  
  ```
  ## [1] 11
  ```
  

--- .class #12


## 2.2 Lists Cont... ##


### Address  values in a List Cont... ###


  - __Use object's name__
   - Ex 2: Get the object names from the list
  
  ```r
  names(myAwesomeList2)                        
  ```
  
  ```
  ## [1] "countData" "headers"
  ```
#### OUTPUT:
 
 ```r
  myAwesomeList2$headers
 ```
 
 ```
 ## [1] "R1" "R2" "C1" "C2"
 ```

--- .class #13

## 2.2 Lists  ##


#### Question 


- Create a list of 3 objects.
- Address the objects in the list by bracket notation and the name
- use as.vector function on the list and convert the list to vectors

--- .class #14
## 2.3 Dataframes ##

#### __Tabular data sets in R are stored as dataframes.__ 

The list of vectors can think as a Dataframe. 

### Creating a Dataframes ###

- __data.frame()__ 
 - Ex 1: 

   
   ```r
     myDataFrame<-data.frame( 
                              col1=c(11,12.4,56,100), #first column
                              col2=c(23,3,1,5)        #second column
                            )                    
   ```

--- .class #15

## 2.3  Dataframes Cont... ##
#### OUTPUT:

   
   ```r
     myDataFrame                
   ```
   
   ```
   ##    col1 col2
   ## 1  11.0   23
   ## 2  12.4    3
   ## 3  56.0    1
   ## 4 100.0    5
   ```


--- .class #16

## 2.3  Dataframes Cont... ##

### Creating a Dataframe ###

- __read.table()__ 

  **Download this file: "https://osu.box.com/countData"**
 - Ex 2: 

   
   ```r
     countTable<-read.table(
                  
                  file="~/Box Sync/File_Sharing/CountTable/CountTable.txt",
                  sep="\t"
                  
                  )     
   ```


--- .class #17

## 2.3  Dataframes Cont... ##
#### OUTPUT:


```r
     head(n=3,countTable)                                             
```

```
##             untreated1 untreated2 untreated3 untreated4 treated1 treated2
## FBgn0000003          0          0          0          0        0        0
## FBgn0000008         92        161         76         70      140       88
## FBgn0000014          5          1          0          0        4        0
##             treated3
## FBgn0000003        1
## FBgn0000008       70
## FBgn0000014        0
```


--- .class #18

## 2.3  Dataframes Cont... ##

### Address  values in a Dataframe... ###


  - Ex 1: __Using column names__
  
  ```r
  first_column<-myDataFrame$col1    
  ```
  
####  OUTPUT:
  
  ```r
  first_column
  ```
  
  ```
  ## [1]  11.0  12.4  56.0 100.0
  ```


--- .class #19

## 2.3  Dataframes Cont... ##


### Address  values in a Dataframe Cont... ###

  - Ex 2:[] -__Using brackets. Ex: myDataFrame[rownumber,columnnumber]__
  
  ```r
  second_column<-myDataFrame[,2]   
  ```
  
####  OUTPUT:
  
  ```r
  second_column
  ```
  
  ```
  ## [1] 23  3  1  5
  ```


--- .class #20

## 2.3  Dataframes Cont..  ##


#### Question 


- Create following dataframe


```
##   n  s     b
## 1 2 aa  TRUE
## 2 3 bb FALSE
## 3 5 cc  TRUE
```
- verify your dataframe using __is.dataframe()__
- check number of data rows using __nrows()__
- check number of columns using __ncol()__
- check the dimensions using __dim()__
- check headers using __colname()__



--- .class #21

## 3  Missing Data ##


- NA - _not available._ 
- Inf, -Inf, NaN-    _Postive Infinite, Negative Infinite, Not A Number (impossible values, dividing by Zero)._

--- 

### How to check ###

- __is.finite(),is.nan(), is.na(), complete.cases()__ - Use these functions to check above special values

#### Example ####


```r
vector_missing_values<-c(1,2,3,NA,NaN,Inf,-Inf)
is.na(vector_missing_values)
```

```
## [1] FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
```

```r
is.finite(vector_missing_values)
```

```
## [1]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE
```

```r
is.infinite(vector_missing_values)
```

```
## [1] FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE
```



--- .class #22

## 3  Missing Data Cont.. ##

#### Example ####


```r
complete.cases(vector_missing_values)
```

```
## [1]  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE
```



--- .class #23

## 3 Missing Data Cont.. ##

### Ways to Exclude Missing Values ###

- na.fail() : _Stop if any missing values are encountered_
- na.omit(): _Drop out any rows with missing values anywhere in them and forgets them forever._
- na.exclude(): _Drop out rows with missing values, but keeps track of where they were (so that when you make predictions, for example, you end up with a vector whose length is that of the original response.)_
- na.pass(): _Take no action._
- Many functions have parameter na.rm



--- .class #24

## 4 Importing and Exporting Data ##

### Data formats###

- Tabular Flat Files

Data store in a table, consisting of columns and rows. These include spreadsheets and delimited text files.

#### Examples 
Excel spreadsheets (.xls or .xlsx), Comma separated variables (.csv) and tab- delimited text files (usually .txt or .dat)

- Relational databases

A collection of tables, each having one column identified as a key variable. Tables are related to each other through these keys.

#### Examples 
Microsoft Access, database software such as MySQL and Oracle.



--- .class #25

## 4 Importing and Exporting Data ##

### Tabular Flat Files###

- Text files

  Data stored as plain text is the simplest and preferred format. Rows are given stored on a line and columns are separated by a delimiter. Common delimiters include: commas (.csv), tabs, semicolons, and ampersands (.txt or .dat).
In this seminar we will show how to import a text file into R.

- Excel spreadsheets

  Microsoft Excel default file format is either a binary (.xls) format or xml (.xlsx) format. This is necessary to support the formatting and formula functionality of Excel.

  R does not currently support the direct import of Excel files. Instead, data in an Excel spreadsheet can be saved as a comma delimited text file, by selecting the option under the “File->Save As” menu.



--- .class #26

## 4 Importing and Exporting Data ##

### Importing Tabular Flat Files###

Function |  header |  sep |	quote |	dec |	fill |	comment.char
-------- | ------- | ---- | ----- | --- | ---- | -------------
read.table |  FALSE |	 |	\” or \’ |	.	| !blank.lines.skip	| #
read.csv |	TRUE |	, |	\” |	. |	TRUE	 
read.csv2 |	TRUE |	; |	\” |	, |	TRUE	 
read.delim |	TRUE |	\t |	\” |	.	| TRUE	 
read.delim2 |	TRUE |	\t |	\” |	, |	TRUE	 

---


#### Examples ####

```r
countTable<-read.table(
            file="~/Box Sync/File_Sharing/CountTable/CountTable.txt", 
            sep="\t"
            )
```


```r
head(countTable, 5)
```

```
##             untreated1 untreated2 untreated3 untreated4 treated1 treated2
## FBgn0000003          0          0          0          0        0        0
## FBgn0000008         92        161         76         70      140       88
## FBgn0000014          5          1          0          0        4        0
## FBgn0000015          0          2          1          2        1        0
## FBgn0000017       4664       8714       3564       3150     6205     3072
##             treated3
## FBgn0000003        1
## FBgn0000008       70
## FBgn0000014        0
## FBgn0000015        0
## FBgn0000017     3334
```


--- .class #27

## 4 Importing and Exporting Data ##

### Importing Tabular Flat Files cont..###

- _read.table(file, header, sep, ...)_
  - Imports any delimited text file into R.
  - _"file"_ is a string _i.e_ path to the file on your hard drive, or URL path
  - _"header"_ can be either "TRUE" or "FALSE", and tells you the first line of the text is coulumn names(variables)
  - _"sep"_ describes delimiter used in the text file.

- _read.csv(file, header, ...)_
- _scan(file, what, n, sep, ...)_



--- .class #28

## 4 Importing and Exporting Data ##

### Exporting Data###

- _write.table(dataset, file="name.txt", sep="\t")_
- _write.csv(dataset, file="name.csv")_

#### __By default, the write.csv and write.table functions create an extra column in the file containing the observation numbers. To prevent this, set the row.names argument to F.__

- _write.table(dataset, "filename.txt, row.names=F)_

- _write.csv(dataset, "filename.csv, row.names=F)_


--- .class #29

## Questions?

--- .class #30



