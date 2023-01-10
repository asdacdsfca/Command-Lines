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
<img width="795" alt="image" src="https://user-images.githubusercontent.com/114449631/211441000-9349e625-2ef0-4e4c-995a-8248491402e8.png">


10. 
