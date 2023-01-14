## Data Clearing
```df.shape```

1. Extract columns: ```df = df[['', '', '']]```

2. Shows the first x columns: ```df.head()```

3. Group by columns: ```df.groupby(['', ''])```

4. Sort by: ```df.sort_values('', ascending=False)```

5. Filters: ```df.isin([COLUMNS])```

6. Join rows: ```'-'.join([ROWS])```

7. All rows/columns: ```axis=0```=>all the rows in each column; ```axis=1```=>all the columns in each row

8. Apply a function along an axis of the df: ```df.agg([''])```

9. Get the df that contains a specific column: ```df = df.loc[df[COLUMNS].notnull()```
<img width="400" alt="image" src="https://user-images.githubusercontent.com/114449631/211441567-435e8bd3-2475-43d6-b807-177925066d65.png">

10. Transpose the df: ```.T```

11. Basic properties: 
<img width="400" alt="image" src="https://user-images.githubusercontent.com/114449631/211650046-097d93ea-94e8-4f2a-9582-d8e7da443ea7.png">

12. Creating dataframe using series: 
<img width="400" alt="image" src="https://user-images.githubusercontent.com/114449631/211650426-42b56926-495e-4c8e-8cec-ed60847581bf.png">

13. df.loc[idx] selects the row indexed by the value idx,
df[col] selects the column labeled by the value col. Each selection results in a Pandas.Series object indexed by the columns/index of df respectively.

14.
|Method Name|Description|
|---|---|
|`head`|return the first `n` entries of a Series|
|`tail`|return the last `n` entries of a Series|
|`count`|Count the number of non-null entries of a Series|
|`nunique`|Returns number of unique values of a Series|

15. Removes duplicate rows :```drop_duplicates()```.

16. Select rows based on some conditions: salary[salary['Team'] == 'Los Angeles Lakers']

17. Series has at least one item greater than a value: 'a' in s

18. Does not contain a part of string: df[df['geo'].str.contains(",")==False]

19. Skip first entry in for loop in python：for car in cars[1:]:
20. 
