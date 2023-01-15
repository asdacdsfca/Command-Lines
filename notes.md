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
A column’s data type determines which operations can be applied to it:
- Numpy arrays are by default of homogeneous data type.
- Pandas DataFrames are heterogeneous, column oriented tables. The columns are homogeneous, implying that column methods are fast.
- Pandas makes heavy use of the object data-type, which contains generic ‘object’ values that may be of mixed type. Performing operations on these columns is slow.

