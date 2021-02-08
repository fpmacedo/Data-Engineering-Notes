# Primary Key

- Must be unique

- The PRIMARY KEY is made up of either just the PARTITION KEY or may also include additional CLUSTERING COLUMNS

- A Simple PRIMARY KEY is just one column that is also the PARTITION KEY. A Composite PRIMARY KEY is made up of more than one column and will assist in creating a unique value and in your retrieval queries

- The PARTITION KEY will determine the distribution of data across the system

Here is the [DataStax](https://docs.datastax.com/en/archived/cql/3.3/cql/cql_using/useSimplePrimaryKeyConcept.html#useSimplePrimaryKeyConcept) documentation on Primary Keys.

Obs.: If two rows have the same primary key the data will be overwritten.

## EXAMPLE: 
[Lesson 3 Exercise 2 Primary Key-ANSWER KEY](./notebooks/ANSWER_KEY.ipynb)


## Clustering Columns

- The clustering column will sort the data in sorted ascending order, e.g., alphabetical order. Note: this is a mistake in the video, which says descending order.

- More than one clustering column can be added (or none!)

- From there the clustering columns will sort in order of how they were added to the primary key

![](images/clustering.png)
### Commonly Asked Questions:

#### How many clustering columns can we add?

You can use as many clustering columns as you would like. You cannot use the clustering columns out of order in the SELECT statement. You may choose to omit using a clustering column in your SELECT statement. That's OK. Just remember to use them in order when you are using the SELECT statement.

Additional Resources:

Here is the [DataStax](https://docs.datastax.com/en/archived/cql/3.3/cql/cql_using/useCompoundPrimaryKeyConcept.html) documentation on Composite Partition Keys.

This [Stackoverflow](https://stackoverflow.com/questions/24949676/difference-between-partition-key-composite-key-and-clustering-key-in-cassandra) page provides a nice description of the difference between Partition Keys and Clustering Keys.