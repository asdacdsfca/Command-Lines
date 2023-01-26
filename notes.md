# Lectures to Review
6

1. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500324-a02a265d-b413-4f27-b0a3-acdd0278c14f.png">

2. unlike most pandas methods, assign returns a new DataFrame.

3. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500550-8fa2fb78-e620-48f0-906b-401ce37097ff.png">

4. DataFrames, like lists, arrays, and dictionaries, are mutable. As you learned in DSC 20, this means that they can be modified after being created. modified, even though we didn't reassign it!

5. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500643-eb87abc6-c5fe-4271-9e16-1e1c2acaa687.png">
<img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500656-f4749820-e9ab-4129-bb50-d624e28b1163.png">

6. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500730-39a6c059-77c9-46d5-8f3b-2ca0a42c2932.png">

7. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500743-e4ce10f4-105d-4182-a52b-38af697f5d40.png">

8. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500850-ba5c1a37-e025-41fa-a131-6cb665e5c992.png">

9. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500866-ace127b1-6bc0-4ef8-a32b-d67d74259e63.png">

10. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500948-beb0a95a-5d65-4884-8ccc-e6742c6dd91f.png">

11. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500963-76d96e15-f78a-4a20-a233-4832b22ac3e9.png">

12. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500992-b62e9a8b-d192-474b-964d-a3c1b836e358.png">

13. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212501042-2c6cfcbd-e6af-4454-aab1-07606a2c91e8.png">

14. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212501047-c035a516-f0ae-4317-a1f5-16a85e354977.png">

15. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212501072-2696b094-f07c-4af6-802a-e2b35dd6d6cd.png">
# 16. 
Applying Numpy functions to a Series (e.g. a column of a DataFrame) results in applying the function to the data in the underlying Numpy array.
ex. np.sum(ages) / ages.shape[0]
Pandas supplies these Numpy function as Series methods as well.
ex. ages.mean()

# The apply method
The apply method is both a Series and a DataFrame method for applying custom functions across data.
Notice that, when applied to a DataFrame, func should be a function that takes in a Series.

# The agg method
The agg method simultaneously applies multiple Series methods to the columns of a DataFrame.
ex. uswnt.agg(['mean', np.median, 'max'])
ex. uswnt.agg({'Player': ['min', 'max'], 'Age': ['mean', np.median, 'max']})

# Pandas
Never loop over the rows of a DataFrame (operations over columns are vectorized by Numpy array calculations).
Use built-in DataFrame methods on columns, over custom python functions, whenever possible (these functions are C-optimized Numpy methods).
Explicitly type the data if memory is an issue (more on that later!).

# Data Types
- A column’s data type determines which operations can be applied to it:
- Numpy arrays are by default of homogeneous data type.
- Pandas DataFrames are heterogeneous, column oriented tables. The columns are homogeneous, implying that column methods are fast.
- Pandas makes heavy use of the object data-type, which contains generic ‘object’ values that may be of mixed type. Performing operations on these columns is slow.
- ex: By default, Numpy coerces the integer to a string, resulting in an array of type <U1 (unicode string of length 1).
data = [['a', 1]] -> np.array(data) -> array([['a', '1']], dtype='<U1') -> np.array(data, dtype=np.object)
Pandas stores each column in its own array, each of a different type.
The dtype can be explicitly when defining the array.

# Representing Missing Data
<img width="600" alt="image" src="https://user-images.githubusercontent.com/114449631/212556189-776e4dff-f702-4cdf-b6fd-f5beb96f2637.png">
The following code intends to loop through the elements of the list, stating when a value is present or missing. Since it uses a == comparison to np.NaN, the code incorrectly states that every element is there!
Using the function pd.isnull returns the correct result
- python nan
The same python nan value verifies as occupying the same location in memory,
The two different python nan values occupy different locations in memory,
The two different np.NaN values occupy the same location in memory.
a, b, c, d = float('nan'), float('nan'), np.NaN, np.NaN
a is a, a is b, c is d

# 2.3 Copies and Views in Pandas
- An in-place reassignment of the upper-left value of the array homogeneous.values results in a changed DataFrame
- An in-place reassignment of the upper-left value of the array heterogeneous.values results in a unchanged DataFrame

# 2.3 Method Chaining
- Pandas usually returns copies
- can create problems when assigning variables to each sub-step (e.g. needlessly high memory usage)

# 3.1 Row selection
- Selecting explicit subsets of rows using loc: Given a dataframe df and a subset idx_list of the index df.index, the dataframe df.loc[idx_list] consists of the rows of df with index given by idx_list.

# 3.1 Column Selection
- Selecting explicit subsets of columns using []: Given a dataframe df and a subset cols of the columns df.columns, the dataframe df[cols] consists of the rows of df with columns given by the columns in cols.

# 3.1 Selecting rows using boolean indexes
- The subtable consisting of countries either in Asia or with an exchange rate less than 1 is obtained via:
asia_or_exch_less_1 = (currencies['continent'] == 'Asia') | (currencies['exchange'] < 1)
currencies.loc[asia_or_exch_less_1]

# 3.1 Selecting rows using functions
- def ends_in_o(df):
    '''returns a boolean array representing
    whether each row in the currency 
    column of `df` ends in  the letter o.'''
    return df['currency'].str.endswith('o')
currencies.loc[ends_in_o]

# 3.1 Selecting subtables using loc
- The loc selector allows simultaneous selection of rows and columns via matrix notation. That is, given a dataframe df, a list of indexes idx, and column labels cols, the expression df.loc[idx, cols] evaluates to the dataframe with rows corresponding to the index idx and columns corresponding to the columns in cols.
- The slicing operator : selects all rows and/or columns when passed into loc: currencies.loc[:, attributes]

# 3.2 Kinds of Data
- An attribute is quantitative if its values are numeric and standard mathematical operations (e.g. mean, sum, ratios) on those values make sense.
- An attribute is ordinal if its values have an ordering from smallest to greatest. Equivalently, there is a one-to-one correspondence between the values and a subset of the number-line, for which the order in the data is reflected in the ordering of the number-line.
- An attribute is nominal if the values are differentiated by only their label; they are neither quantitative nor ordinal.

# 3.3 Categorical empirical distributions
- The distribution of a categorical attribute is described by simply calculating the proportion of the whole made up by each value. Pandas provides a method called value_counts that calculates this quantity; the distribution is a series, indexed by the values of the attribute, with values given by each value’s proportion.
- ex.  The empirical distribution of the risk_category attribute in the inspections dataset is given by:
(
    inspections['risk_category']
    .value_counts(normalize=True)                    # empirical distribution
    .loc[['Low Risk', 'Moderate Risk', 'High Risk']] # sort distribution by order of the values
)

# 3.3 Cumulative Distribution Functions
- the distribution of the letter grades of students (pdf) describes the proportion of the class that received each letter grade,
- the cumulative distribution of the letter grades of students (cdf) describes the proportion of the class that received at most a given grade.
- def cdf_X(x):
    return (X < x).mean()
 The empirical cumulative distribution function of an attribute X at a value x is the proportion of values in X that are at most x.

# 3.4 Quantitative Empirical Distributions
 A probability density of an empirical distribution at a value x is the proportion of the observations per unit that occur near x. The appropriate value of ‘near’ corresponds to choosing a bin size for grouping data. The bin size should make sense when interpreting it in terms of the data generating process
 
 # 3.4 Computing quantitative distributions with np.histogram
- The array of bin edges is one element larger than the array of densities (and the number of bins).
<img width="600" alt="image" src="https://user-images.githubusercontent.com/114449631/212561832-b91c1bd2-c790-4537-9ecf-64d2abb63cb3.png">

- By default, the histogram uses 10 equally sized bins, spanning the range of the input data.
- Specifying a different number of bins (via an integer) results in equally sized bins.
- Non-equally sized bins are specified by passing a list of end-points.
- Passing density=False (the default) results in an array of counts, instead of densities.
- inspections['inspection_score'].plot(kind='hist', bins=10, density=True, title='histogram of inspection scores');
However this method has two disadvantages:
it works for plotting only, and doesn’t provide the user with the binned data itself, and
it slower and more memory intensive than np.histogram.
- Similarly, Pandas also provides a kernel density estimate, which is a smoothed histogram of the observed data. While very slow to plot, it avoids the need to choose an ‘appropriate’ bin size:
inspections['inspection_score'].plot(
    kind='kde', 
    title='kernel density estimate of the distribution of inspection scores'
);

# 5.1 Split: the groupby DataFrame method
- However, the groups property returns a dictionary keyed by group label, with the indices of df corresponding to each group label:
G.groups
- The G.get_group(label) method returns the DataFrame df.loc[df[key] == label]
- The components of split-apply-combine are as follows:
    Split the data into groups based on some criteria (often encoded in a column).
    Apply function(s) to each group independently.
    Combine the results into a data structure (e.g. a Series or DataFrame)
- [groupby also accepts a function to split data into groups](https://notes.dsc80.com/content/05/grouping.html)

# 5.1 Apply-Combine: GroupBy methods
- To calculate the routes with the most climbers on a given day, group the climbs by both date and route name:
(
    climbs
    .groupby(['Date', 'Route'])['Attempted']
    .sum()
    .sort_values(ascending=False)
    .reset_index()
)
- Remark: Grouping on multiple columns results in a multi-indexed Series/DataFrame; using reset_index on the output simplifies further processing.
- Notice that the Date column was dropped from the output; Pandas drops non-numeric columns when any of the aggregation methods requires numeric data.

# 5.1 Generic Apply-Combine: apply method
- [Process of filtering data frame](https://notes.dsc80.com/content/05/grouping.html#generic-apply-combine-apply-method)
- seems like groupby returns many data frames

# 5.2 Reshaping Data: Pivot Tables
- The pivot refers to reshaping a table from a long table of rows indexed by two characteristics, to a wide table with one characteristic per axis.
- Remark: The pivot_table is equivalent to pivot when the aggregation function is the identity function (aggfunc=lambda x:x).

# 5.2 Undoing a pivot
- Note that melt only undoes the reshaping operation of pivot – in general, the groupby aggregations cannot be inverted!
