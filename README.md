# ISSonVIS-Andrienko
Access for data in cloud for Andrienko's workshop during ISSonVIS 2021

## Excercise 1
(Jupyter notebook)[https://github.com/masopust/ISSonVIS-Andrienko/raw/main/SpaceTime-aggregation-v.2019.11.20.ipynb]
 - Block 4, line 2 - change data source to GitHub:
```python
events = pd.read_csv('https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/lightnings_13_30-17_30.csv', sep=',', decimal='.', header=0, index_col='id', parse_dates=['date time'], date_parser=dt_parse)
```

