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

20. The maximum element in each column: schools.max()

21. The number of unique values in each column: schools.nunique()

22. Change the type of a column: schools['Enrollment'] = schools['Enrollment'].str.replace(',', '').astype(int)

23. To remove duplicates on specific column(s), use subset: df.drop_duplicates(subset=['brand'])

24. applies multiple Series methods to the columns of a DataFrame: 
df.agg([f1,...,fN]) returns a DataFrame obtained by applying each function to each column of df,
df.agg({col1:f1,...,colN:fN}) returns a Series obtained by applying each function to column specified by its corresponding key.

25. Multi-conditions selection: (currencies['continent'] == 'Asia') | (currencies['exchange'] < 1)

26. drop a column: df = df.drop('column_name', axis=1)

27. Rename Specific Columns: df = df.rename(columns={'oldName1': 'newName1', 'oldName2': 'newName2'})

28. Convert Dataframe column into an index: df = df.set_index('Name')

29. Filters columns by strings = grades_copy.filter(like='Lateness').filter(like = 'lab')

30. Multiple boolean conditions: ((scores['attempts']>1) & (scores['highest_score']<60.0)) 

31. Reassign row values based on conditions: scores.loc[scores['passed'] == True, ['pass']] = 'Yes'

32. Get the index: list(df.index.values)

33. Read csv file: scores_fp = os.path.join('data', 'scores.csv')
scores = pd.read_csv(scores_fp)

34. apply a function to dataframe: result_data.applymap(change)

35. get the number of unique values: df.nunique(axis=0)

36. get X largest number of elements that appeared in a column: df[columns].value_counts().nlargest(N)

37. arithmatics on series with different size but same index values: cleaned_copy = cleaned_copy.set_index('nation') => cleaned_copy['mean_score'] = cleaned_copy.groupby('nation')['score'].mean() => cleaned_copy['score'] = cleaned_copy['score'] - cleaned_copy['mean_score'] (lab03, q2)

38. create new columns by spliting existing columns: df_copy[['nation', 'national_rank_cleaned']] = df_copy.national_rank.str.split(',', expand=True)

39. check if it contains any null values: new_control['city'].notnull()

40. create data frame and assign column names: pd.DataFrame(columns = )

41. forcely convert a column into ints: pd.to_numeric(students['DSC 80 Final Grade'], errors='coerce')

42. Set value for an entire column: df.loc[:, 'max_speed'] = 30

43.  Merge nearly duplicate rows based on column value: df = df.groupby(['OwnerID', 'Name_owner'])['Name_pet'].apply(', '.join).reset_index()
-     where we want to get turn name_pet into a list of strings if ownerId's are the same

44.  convert a time like series to timeseries type: pd.to_datetime(sales['Date'])

45.  convert a timeseries object to some string kind representation: TS.dt.strftime('%B')

46.  change the column values by row index : sales_copy.loc[0, ['Total']] = np.NaN

47.  Time within an interval: df.between_time('16:00:00', '20:00:00')

48.  sort the values df.sort_values('Price').groupby('Name').last()

49.  create a datetime object: pd.to_datetime('2019-01-01')

50.  check if a value is NaN: ```child[1]!=child[1]```

51.  in-place change of series values: ```child.update(pd.Series(fill_values, index = [i]))```

52.  Series to dataframe: `ser.to_frame()`
53.  loads a JSON file from a file object: `json.load(f)`
54.   loads a JSON file from a string: `json.loads(f)`
55.   
