# Tidy data set

About 80% of data analysis is often spent by cleaning messy data, structuring datasets to facilitate analysis.

We can say that a dataset is a collection of numbers or strings or both. If a value is number, it has quantitative character. If it is a string, it has qualitative character.

Tidy data sets are easy to manipulate, model and visualise, and have a specific structure. And therefore tidy data should fulfil [Codd's 3rd normal form](http://en.wikipedia.org/wiki/Boyce%E2%80%93Codd_normal_form).

* Each variable forms a column.
* Each observation forms a row.
* Each type of observational unit forms a table.

What is untidy data then? There are many ways data can be untidy. Wickham’s top five are as follows:

* Column names represent data values instead of variable names
* A single column contains data on multiple variables instead of a single variable
* Variables are contained in both rows and columns instead of just columns
* A single table contains more than one observational unit
Data about an observational unit is spread across multiple data sets

We might rather use one big data set, let's say a big table, than multiple connected smaller data sets, like in relational databases. It makes easier to perform analysis on one data set rather than on multilple datasets.

Anything else what does not fulfil the points above, we will call messy data.

Let's explore how to get tidy data set from raw and messy data.

## Raw and messy data

Raw data is the original and not modified data files and it is often difficult to use that raw data. Raw data can be for example videos, images, binary files, text files, unformatted Excel files with multiple worksheets, hand written data, JSON files, XML files and so on.

In order to check whether we are working with really raw data, we can check the following points:

* We ran NO software to modify the data
* We did NOT manipulated any numbers
* We did NOT remove any data
* We did NO summarizations

Analysis we run should include data cleaning to process raw data in order to prepare them for analysis.

## Cleaning data

Clean data is data that is ready for analysis. In order to clean data we might be merging, transforming, extracting, ordering or performing similar operations.

> All cleaning steps should be properly documented.

We might also want to order columns, so dimensions or fixed values are first and then we have measured values.

Common problems with messy data sets:

* Column names contains values
* Multiple values in one column
* Values are stored in both rows and columns
* Multiple document types are mixed in single document
* Single document type is stored in multiple types

> For some industries, there might be standarts for processing raw data.

### Melting dataset

When column names contains values we might need to melt the dataset.

For example, assume we have te following dataset.

| Income | < $10 | => $10  |
| -- | -- | -- |
| New York | 2500 | 5000 |
| San Francisco | 1000 | 2000 |

In order to melt it down, we should transform it, for example, to the following dataset structure.

| City | Income range | Population |
| -- | -- | -- |
| New York | < $10 | 2500 |
| New York | => $10 | 5000 |
| San Francisco | => $10 | 1000 |
| San Francisco | => $10 | 2000 |

See Reshaping chapter to learn how to melt the data.

## Tidy data

Tidy data is collection of four things:

1. Raw data
2. Tidy data set
3. Cook book describing each variable, for example a column in a table, and values in tidy data set. The cook book is  also sometimes called as metadata.
4. Exact steps, formulas and recepies we took to clean the raw data set.

Hints:

* Always include units in metadata.
* Include how you have collected the data
* Write down reproduction steps how to get tidy data from raw data.

> Recommended reading about [tidy data](http://www.stat.wvu.edu/~jharner/courses/stat623/docs/tidy-dataJSS.pdf).
