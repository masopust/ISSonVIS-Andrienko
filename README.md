# ISSonVIS-Andrienko
Access for data in cloud for Andrienko's workshop during ISSonVIS 2021

# For running in Google Colab load these Jupyter notebooks and make some minor changes in the code
## Excercise 1
[Jupyter notebook](https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/SpaceTime-aggregation-v.2019.11.20.ipynb)
 - Block 4 - change data source to GitHub:
```python
np.random.seed(123)
events = pd.read_csv('https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/lightnings_13_30-17_30.csv', sep=',', decimal='.', header=0, index_col='id', parse_dates=['date time'], date_parser=dt_parse)
events.describe()
```

## Excercise 2
[Jupyter notebook for DB clustering](https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/DBClustering.ipynb)
 - Block 4 - change data source to GitHub:
```python
#events = pd.read_csv('https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/cherryblossom_2012-2017.csv', sep=',', decimal='.', 
                      #header=0, index_col='PhotoID', parse_dates=['DateTaken'], date_parser=dt_parse)
#events = pd.read_csv('https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/cherryblossom_USA_filtered.csv', sep=',', decimal='.', 
                      #header=0, index_col='PhotoID', parse_dates=['DateTaken'], date_parser=dt_parse)
events = pd.read_csv('https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/cherryblossom_2012-2014.csv', sep=',', decimal='.', 
                     header=0, index_col='PhotoID', parse_dates=['DateTaken'], date_parser=dt_parse)
events.describe()
```
[Jupyter notebook for PB clustering](https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/PBClustering.ipynb)
 - Block 1 - install chart_studio and import chart_studio.plotly instead of plotly.plotly:
```python
# Importing Libraries
import os

import numpy as np
import pandas as pd
import matplotlib
import matplotlib.pyplot as plt
%matplotlib inline
matplotlib.rcParams['figure.figsize'] = (9.0, 3.0)

#import seaborn as sns
!pip install chart_studio
import chart_studio.plotly  as py
import plotly.graph_objs as go
import cufflinks
#pd.options.display.max_columns = 30
#from IPython.core.interactiveshell import InteractiveShell
import plotly.figure_factory as ff
#InteractiveShell.ast_node_interactivity = 'all'
#from plotly.offline import iplot
cufflinks.go_offline()
cufflinks.set_config_file(world_readable=True, theme='pearl')

from sklearn.manifold import MDS
from sklearn.preprocessing import MinMaxScaler
from sklearn.cluster import KMeans

np.random.seed(123)

```
- Block 3 - change data source to GitHub:
```python
# Loading csv file into Pandas DataFrame
wd = pd.read_csv('https://raw.githubusercontent.com/masopust/ISSonVIS-Andrienko/main/weekly_counts_by_regions.csv')
wd.head(5)
```
- Block 9 - Use fig.show(renderer="colab") instead of iplot:
```python
for i in range(len(counts_columns)):
    boxes=[]
    for j in range(len(centroids)):
        box = go.Box(
            y=wd.loc[wd[clust_id_col_name] == j][counts_columns[i]],
            name = j,
            marker = dict(
                color = cluster_colors[j],
            )
        )
        boxes.append(box)


    layout = go.Layout(
        title = "Statistics of counts by the clusters for region "+counts_columns[i]
    )
    
    fig = go.Figure(data=boxes,layout=layout)
    fig.show(renderer="colab")
```
