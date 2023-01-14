1. <img width="500" alt="image" src="https://user-images.githubusercontent.com/114449631/212500324-a02a265d-b413-4f27-b0a3-acdd0278c14f.png">
2. unlike most pandas methods, assign returns a new DataFrame.

#Adding and modifying columns, in-place
You can assign a new column to a DataFrame in-place using [].
This works like dictionary assignment.
This modifies the underlying DataFrame, unlike assign, which returns a new DataFrame.
This is the more "common" way of adding/modifying columns.
⚠️ Warning: Exercise caution when using this approach, since this approach changes the values of existing variables.

#Mutability
DataFrames, like lists, arrays, and dictionaries, are mutable. As you learned in DSC 20, this means that they can be modified after being created.

Not only does this explain the behavior on the previous slide, but it also explains the following:
