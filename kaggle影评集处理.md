```python
import numpy as np
import matplotlib.pyplot as plt
from pyecharts.charts import Bar,Grid,Line,Pie
import pyecharts.options as opts
from pyecharts.globals import ThemeType
import pandas as pd
movies = pd.read_csv('movietweetings/movies.dat', delimiter = '::',
                        engine = 'python', header = None, names = ['Movie ID', 'Movie Title', 'Genre'], encoding = 'utf-8')
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Movie ID</th>
      <th>Movie Title</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8</td>
      <td>Edison Kinetoscopic Record of a Sneeze (1894)</td>
      <td>Documentary|Short</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>La sortie des usines Lumière (1895)</td>
      <td>Documentary|Short</td>
    </tr>
    <tr>
      <th>2</th>
      <td>12</td>
      <td>The Arrival of a Train (1896)</td>
      <td>Documentary|Short</td>
    </tr>
    <tr>
      <th>3</th>
      <td>25</td>
      <td>The Oxford and Cambridge University Boat Race ...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>91</td>
      <td>Le manoir du diable (1896)</td>
      <td>Short|Horror</td>
    </tr>
  </tbody>
</table>
</div>



# 解决找不到已安装的模块


```python
import pip
def install(package):
   pip.main(['install', package])
install('pyecharts') 
```

    WARNING: pip is being invoked by an old script wrapper. This will fail in a future version of pip.
    Please see https://github.com/pypa/pip/issues/5599 for advice on fixing the underlying issue.
    To avoid this problem you can invoke Python with '-m pip' instead of running pip directly.
    

    Collecting pyecharts
      Using cached pyecharts-1.8.1-py3-none-any.whl (134 kB)
    Requirement already satisfied: jinja2 in c:\users\xiefe\anaconda3\lib\site-packages (from pyecharts) (2.11.1)
    Collecting prettytable
      Using cached prettytable-0.7.2.tar.bz2 (21 kB)
    Collecting simplejson
      Downloading simplejson-3.17.0-cp37-cp37m-win_amd64.whl (73 kB)
    Requirement already satisfied: MarkupSafe>=0.23 in c:\users\xiefe\anaconda3\lib\site-packages (from jinja2->pyecharts) (1.1.1)
    Building wheels for collected packages: prettytable
      Building wheel for prettytable (setup.py): started
      Building wheel for prettytable (setup.py): finished with status 'done'
      Created wheel for prettytable: filename=prettytable-0.7.2-py3-none-any.whl size=13704 sha256=29aaac7b392eec5f78dfb7fc2348a69a0f1925b71076c1069a97bfc2b3943d07
      Stored in directory: c:\users\xiefe\appdata\local\pip\cache\wheels\8c\76\0b\eb9eb3da7e2335e3577e3f96a0ae9f74f206e26457bd1a2bc8
    Successfully built prettytable
    Installing collected packages: prettytable, simplejson, pyecharts
    Successfully installed prettytable-0.7.2 pyecharts-1.8.1 simplejson-3.17.0
    


```python
users = pd.read_csv('movietweetings/users.dat', delimiter = '::',
                    engine = 'python', header = None, names = ['User ID', 'Twitter ID'], encoding = 'utf-8')
users.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>User ID</th>
      <th>Twitter ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>397291295</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>40501255</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>417333257</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>138805259</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2452094989</td>
    </tr>
  </tbody>
</table>
</div>




```python
ratings = pd.read_csv('movietweetings/ratings.dat', delimiter = '::',
                     engine = 'python', header = None, names = ['User ID', 'Movie ID', 'Rating', 'Rating Timestamp'], encoding = 'utf-8')
ratings.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>User ID</th>
      <th>Movie ID</th>
      <th>Rating</th>
      <th>Rating Timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>111161</td>
      <td>10</td>
      <td>1373234211</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>117060</td>
      <td>7</td>
      <td>1373415231</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>120755</td>
      <td>6</td>
      <td>1373424360</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>317919</td>
      <td>6</td>
      <td>1373495763</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>454876</td>
      <td>10</td>
      <td>1373621125</td>
    </tr>
  </tbody>
</table>
</div>



# read_csv使用说明
* 第一个参数表示文件的相对路径
* 第二个关键字参数：delimiter=’：：’表示文件分隔符使用：：
* 后面几个关键字参数分别代表使用的引擎，文件没有表头，所以header为None
* 导入后DataFrame的列名，使用names关键字设置，这个参数要记住，比较有用

# 数据预览
* info 统计出数据的每一列类型，是否为null和个数
* describe 描述出数据每一列的统计学信息，包括常见的平均值、方差、中位数、分位数


```python
movies.info()
# 只有Genre列存在空值，因为 34159<34437
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 34437 entries, 0 to 34436
    Data columns (total 3 columns):
     #   Column       Non-Null Count  Dtype 
    ---  ------       --------------  ----- 
     0   Movie ID     34437 non-null  int64 
     1   Movie Title  34437 non-null  object
     2   Genre        34159 non-null  object
    dtypes: int64(1), object(2)
    memory usage: 807.2+ KB
    


```python
users.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 60283 entries, 0 to 60282
    Data columns (total 2 columns):
     #   Column      Non-Null Count  Dtype
    ---  ------      --------------  -----
     0   User ID     60283 non-null  int64
     1   Twitter ID  60283 non-null  int64
    dtypes: int64(2)
    memory usage: 942.0 KB
    


```python
ratings.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 814505 entries, 0 to 814504
    Data columns (total 4 columns):
     #   Column            Non-Null Count   Dtype
    ---  ------            --------------   -----
     0   User ID           814505 non-null  int64
     1   Movie ID          814505 non-null  int64
     2   Rating            814505 non-null  int64
     3   Rating Timestamp  814505 non-null  int64
    dtypes: int64(4)
    memory usage: 24.9 MB
    


```python
ratings.describe()
# 平均分为7.304461   方差为1.855768
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>User ID</th>
      <th>Movie ID</th>
      <th>Rating</th>
      <th>Rating Timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>814505.000000</td>
      <td>8.145050e+05</td>
      <td>814505.000000</td>
      <td>8.145050e+05</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>30131.011142</td>
      <td>2.011445e+06</td>
      <td>7.304461</td>
      <td>1.447851e+09</td>
    </tr>
    <tr>
      <th>std</th>
      <td>17222.165032</td>
      <td>1.736959e+06</td>
      <td>1.855768</td>
      <td>6.015519e+07</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>8.000000e+00</td>
      <td>0.000000</td>
      <td>1.362062e+09</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>15403.000000</td>
      <td>7.654430e+05</td>
      <td>6.000000</td>
      <td>1.393032e+09</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>30148.000000</td>
      <td>1.675192e+06</td>
      <td>7.000000</td>
      <td>1.438288e+09</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>44890.000000</td>
      <td>2.660888e+06</td>
      <td>9.000000</td>
      <td>1.495925e+09</td>
    </tr>
    <tr>
      <th>max</th>
      <td>60283.000000</td>
      <td>1.106613e+07</td>
      <td>10.000000</td>
      <td>1.573171e+09</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize = [10, 8])
plt.subplot(221)
plt.hist(x = ratings['Rating'], color = ['orange'])
plt.subplot(222)
plt.boxplot(x = ratings['Rating'], showmeans = True, meanline = True)
plt.grid()
plt.show()
# 25%的电影得分在0-6分，6-7分的电影又有25%，7-9分的电影又有25%，9分以上的电影占有25%
```


![png](output_11_0.png)


# 补全空值


```python
movies[movies['Genre'].isnull()].head()
# 只有movies.dat文件的Genre列有空值，打印前5行空值
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Movie ID</th>
      <th>Movie Title</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>25</td>
      <td>The Oxford and Cambridge University Boat Race ...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>443</td>
      <td>Hiawatha, the Messiah of the Ojibway (1903)</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>5530</td>
      <td>L'héroïsme de Paddy (1915)</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50</th>
      <td>9340</td>
      <td>The Man Who Woke Up (1918)</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>79</th>
      <td>12844</td>
      <td>White and Unmarried (1921)</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['Genre'].value_counts()
# 使用value_counts()方法统计此列的取值种类数，可以根据|解析字符串，然后统计每个子串出现次数。
```




    Drama                                3463
    Comedy                               1999
    Documentary                          1377
    Comedy|Drama                         1328
    Drama|Romance                        1160
                                         ... 
    Musical|Drama|Comedy                    1
    Musical|Drama|Family                    1
    Documentary|Adventure|Family|News       1
    Drama|Mystery|Short                     1
    Family|Music|Romance                    1
    Name: Genre, Length: 2693, dtype: int64




```python
movies['Genre'].isnull().sum()/len(movies['Genre'])  # 打印空值比例
movies['Genre'].fillna('other', inplace = True)  # 填充Genre列的空值，填充为other类型
```

# 特征工程


```python
genres = movies['Genre'].str.split('|').to_numpy()
# 根据分隔符|解析此列，并将此列转换为Numpy对象
```


```python
# 使用defaultdict 统计出电影种类和对应的电影数
from collections import defaultdict
counter = defaultdict(int)
for genre in genres:
    for e in genre:
        counter[e] +=1
counter
```




    defaultdict(int,
                {'Documentary': 3224,
                 'Short': 1391,
                 'other': 278,
                 'Horror': 4288,
                 'Comedy': 10741,
                 'Action': 5175,
                 'Adventure': 3116,
                 'Fantasy': 2179,
                 'Sci-Fi': 2368,
                 'Crime': 4723,
                 'Western': 497,
                 'Drama': 17589,
                 'Romance': 5987,
                 'History': 1329,
                 'Family': 1895,
                 'War': 1211,
                 'Sport': 857,
                 'Biography': 1765,
                 'Mystery': 2649,
                 'Thriller': 7307,
                 'Animation': 1204,
                 'Music': 1183,
                 'Musical': 822,
                 'Film-Noir': 266,
                 'Adult': 10,
                 'Talk-Show': 3,
                 'News': 110,
                 'Reality-TV': 8,
                 'Game-Show': 1})




```python
# 对上面的字典按种类数排序
counter_sorted = sorted(counter.items(), key = lambda x: x[1])
counter_sorted
```




    [('Game-Show', 1),
     ('Talk-Show', 3),
     ('Reality-TV', 8),
     ('Adult', 10),
     ('News', 110),
     ('Film-Noir', 266),
     ('other', 278),
     ('Western', 497),
     ('Musical', 822),
     ('Sport', 857),
     ('Music', 1183),
     ('Animation', 1204),
     ('War', 1211),
     ('History', 1329),
     ('Short', 1391),
     ('Biography', 1765),
     ('Family', 1895),
     ('Fantasy', 2179),
     ('Sci-Fi', 2368),
     ('Mystery', 2649),
     ('Adventure', 3116),
     ('Documentary', 3224),
     ('Horror', 4288),
     ('Crime', 4723),
     ('Action', 5175),
     ('Romance', 5987),
     ('Thriller', 7307),
     ('Comedy', 10741),
     ('Drama', 17589)]




```python
# 只取电影种类数最多的前10进行分析
top10 = counter_sorted[-10:]
top10
```




    [('Mystery', 2649),
     ('Adventure', 3116),
     ('Documentary', 3224),
     ('Horror', 4288),
     ('Crime', 4723),
     ('Action', 5175),
     ('Romance', 5987),
     ('Thriller', 7307),
     ('Comedy', 10741),
     ('Drama', 17589)]




```python
# 开始绘制前10最多种类的柱状图，使用pyecharts绘制
x = [x for x, y in top10]
y = [y for x ,y in top10]
x,y
bar = (
    Bar(init_opts = opts.InitOpts(height= '1200px')).add_xaxis(x).add_yaxis('电影种类名', y, category_gap='50%').reversal_axis()
    .set_global_opts(title_opts=opts.TitleOpts(title="电影种类及影片数"), toolbox_opts=opts.ToolboxOpts())
)
grid = (
    Grid(init_opts=opts.InitOpts(theme=ThemeType.LIGHT)).add(bar, grid_opts=opts.GridOpts(pos_left="30%"))
)
grid.render_notebook()
```

    C:\Users\xiefe\anaconda3\lib\site-packages\pyecharts\charts\chart.py:14: PendingDeprecationWarning: pyecharts 所有图表类型将在 v1.9.0 版本开始强制使用 ChartItem 进行数据项配置 :)
      super().__init__(init_opts=init_opts)
    C:\Users\xiefe\anaconda3\lib\site-packages\pyecharts\charts\composite_charts\grid.py:17: PendingDeprecationWarning: pyecharts 所有图表类型将在 v1.9.0 版本开始强制使用 ChartItem 进行数据项配置 :)
      super().__init__(init_opts=init_opts)
    





<script>
    require.config({
        paths: {
            'echarts':'https://assets.pyecharts.org/assets/echarts.min'
        }
    });
</script>

        <div id="1e48ea2665d24c13afeb225c15074f01" style="width:900px; height:500px;"></div>

<script>
        require(['echarts'], function(echarts) {
                var chart_1e48ea2665d24c13afeb225c15074f01 = echarts.init(
                    document.getElementById('1e48ea2665d24c13afeb225c15074f01'), 'light', {renderer: 'canvas'});
                var option_1e48ea2665d24c13afeb225c15074f01 = {
    "animation": true,
    "animationThreshold": 2000,
    "animationDuration": 1000,
    "animationEasing": "cubicOut",
    "animationDelay": 0,
    "animationDurationUpdate": 300,
    "animationEasingUpdate": "cubicOut",
    "animationDelayUpdate": 0,
    "color": [],
    "series": [
        {
            "type": "bar",
            "name": "\u7535\u5f71\u79cd\u7c7b\u540d",
            "xAxisIndex": 0,
            "yAxisIndex": 0,
            "legendHoverLink": true,
            "data": [
                2649,
                3116,
                3224,
                4288,
                4723,
                5175,
                5987,
                7307,
                10741,
                17589
            ],
            "showBackground": false,
            "barMinHeight": 0,
            "barCategoryGap": "50%",
            "barGap": "30%",
            "large": false,
            "largeThreshold": 400,
            "seriesLayoutBy": "column",
            "datasetIndex": 0,
            "clip": true,
            "zlevel": 0,
            "z": 2,
            "label": {
                "show": true,
                "position": "top",
                "margin": 8
            }
        }
    ],
    "legend": [
        {
            "data": [
                "\u7535\u5f71\u79cd\u7c7b\u540d"
            ],
            "selected": {
                "\u7535\u5f71\u79cd\u7c7b\u540d": true
            },
            "show": true,
            "padding": 5,
            "itemGap": 10,
            "itemWidth": 25,
            "itemHeight": 14
        }
    ],
    "tooltip": {
        "show": true,
        "trigger": "item",
        "triggerOn": "mousemove|click",
        "axisPointer": {
            "type": "line"
        },
        "showContent": true,
        "alwaysShowContent": false,
        "showDelay": 0,
        "hideDelay": 100,
        "textStyle": {
            "fontSize": 14
        },
        "borderWidth": 0,
        "padding": 5
    },
    "xAxis": [
        {
            "show": true,
            "scale": false,
            "nameLocation": "end",
            "nameGap": 15,
            "gridIndex": 0,
            "inverse": false,
            "offset": 0,
            "splitNumber": 5,
            "minInterval": 0,
            "splitLine": {
                "show": false,
                "lineStyle": {
                    "show": true,
                    "width": 1,
                    "opacity": 1,
                    "curveness": 0,
                    "type": "solid"
                }
            }
        }
    ],
    "yAxis": [
        {
            "show": true,
            "scale": false,
            "nameLocation": "end",
            "nameGap": 15,
            "gridIndex": 0,
            "inverse": false,
            "offset": 0,
            "splitNumber": 5,
            "minInterval": 0,
            "splitLine": {
                "show": false,
                "lineStyle": {
                    "show": true,
                    "width": 1,
                    "opacity": 1,
                    "curveness": 0,
                    "type": "solid"
                }
            },
            "data": [
                "Mystery",
                "Adventure",
                "Documentary",
                "Horror",
                "Crime",
                "Action",
                "Romance",
                "Thriller",
                "Comedy",
                "Drama"
            ]
        }
    ],
    "title": [
        {
            "text": "\u7535\u5f71\u79cd\u7c7b\u53ca\u5f71\u7247\u6570",
            "padding": 5,
            "itemGap": 10
        }
    ],
    "toolbox": {
        "show": true,
        "orient": "horizontal",
        "itemSize": 15,
        "itemGap": 10,
        "left": "80%",
        "feature": {
            "saveAsImage": {
                "type": "png",
                "backgroundColor": "auto",
                "connectedBackgroundColor": "#fff",
                "show": true,
                "title": "\u4fdd\u5b58\u4e3a\u56fe\u7247",
                "pixelRatio": 1
            },
            "restore": {
                "show": true,
                "title": "\u8fd8\u539f"
            },
            "dataView": {
                "show": true,
                "title": "\u6570\u636e\u89c6\u56fe",
                "readOnly": false,
                "lang": [
                    "\u6570\u636e\u89c6\u56fe",
                    "\u5173\u95ed",
                    "\u5237\u65b0"
                ],
                "backgroundColor": "#fff",
                "textareaColor": "#fff",
                "textareaBorderColor": "#333",
                "textColor": "#000",
                "buttonColor": "#c23531",
                "buttonTextColor": "#fff"
            },
            "dataZoom": {
                "show": true,
                "title": {
                    "zoom": "\u533a\u57df\u7f29\u653e",
                    "back": "\u533a\u57df\u7f29\u653e\u8fd8\u539f"
                },
                "icon": {},
                "xAxisIndex": false,
                "yAxisIndex": false,
                "filterMode": "filter"
            },
            "magicType": {
                "show": true,
                "type": [
                    "line",
                    "bar",
                    "stack",
                    "tiled"
                ],
                "title": {
                    "line": "\u5207\u6362\u4e3a\u6298\u7ebf\u56fe",
                    "bar": "\u5207\u6362\u4e3a\u67f1\u72b6\u56fe",
                    "stack": "\u5207\u6362\u4e3a\u5806\u53e0",
                    "tiled": "\u5207\u6362\u4e3a\u5e73\u94fa"
                },
                "icon": {}
            },
            "brush": {
                "icon": {},
                "title": {
                    "rect": "\u77e9\u5f62\u9009\u62e9",
                    "polygon": "\u5708\u9009",
                    "lineX": "\u6a2a\u5411\u9009\u62e9",
                    "lineY": "\u7eb5\u5411\u9009\u62e9",
                    "keep": "\u4fdd\u6301\u9009\u62e9",
                    "clear": "\u6e05\u9664\u9009\u62e9"
                }
            }
        }
    },
    "grid": [
        {
            "show": false,
            "zlevel": 0,
            "z": 2,
            "left": "30%",
            "containLabel": false,
            "backgroundColor": "transparent",
            "borderColor": "#ccc",
            "borderWidth": 1
        }
    ]
};
                chart_1e48ea2665d24c13afeb225c15074f01.setOption(option_1e48ea2665d24c13afeb225c15074f01);
        });
    </script>





```python
# 进一步观察这些种类所占比重，想到饼状图，使用pyecharts绘制
c = (
    Pie()
    .add(
        "",
        [list(z) for z in top10 ],
        radius=["40%", "55%"],
        label_opts=opts.LabelOpts(
            position="outside",
            formatter="{a|{a}}{abg|}\n{hr|}\n {b|{b}: }{c}  {per|{d}%}  ",
            background_color="#eee",
            border_color="#aaa",
            border_width=1,
            border_radius=4,
            rich={
                "a": {"color": "#999", "lineHeight": 22, "align": "center"},
                "abg": {
                    "backgroundColor": "#e3e3e3",
                    "width": "100%",
                    "align": "right",
                    "height": 22,
                    "borderRadius": [4, 4, 0, 0],
                },
                "hr": {
                    "borderColor": "#aaa",
                    "width": "100%",
                    "borderWidth": 0.5,
                    "height": 0,
                },
                "b": {"fontSize": 16, "lineHeight": 33},
                "per": {
                    "color": "#eee",
                    "backgroundColor": "#334455",
                    "padding": [2, 4],
                    "borderRadius": 2,
                },
            },
        ),
    )
)

c.render_notebook()
```

    C:\Users\xiefe\anaconda3\lib\site-packages\pyecharts\charts\chart.py:14: PendingDeprecationWarning: pyecharts 所有图表类型将在 v1.9.0 版本开始强制使用 ChartItem 进行数据项配置 :)
      super().__init__(init_opts=init_opts)
    





<script>
    require.config({
        paths: {
            'echarts':'https://assets.pyecharts.org/assets/echarts.min'
        }
    });
</script>

        <div id="4dbeec64c57f42c98bd13216739e33e3" style="width:900px; height:500px;"></div>

<script>
        require(['echarts'], function(echarts) {
                var chart_4dbeec64c57f42c98bd13216739e33e3 = echarts.init(
                    document.getElementById('4dbeec64c57f42c98bd13216739e33e3'), 'white', {renderer: 'canvas'});
                var option_4dbeec64c57f42c98bd13216739e33e3 = {
    "animation": true,
    "animationThreshold": 2000,
    "animationDuration": 1000,
    "animationEasing": "cubicOut",
    "animationDelay": 0,
    "animationDurationUpdate": 300,
    "animationEasingUpdate": "cubicOut",
    "animationDelayUpdate": 0,
    "color": [
        "#c23531",
        "#2f4554",
        "#61a0a8",
        "#d48265",
        "#749f83",
        "#ca8622",
        "#bda29a",
        "#6e7074",
        "#546570",
        "#c4ccd3",
        "#f05b72",
        "#ef5b9c",
        "#f47920",
        "#905a3d",
        "#fab27b",
        "#2a5caa",
        "#444693",
        "#726930",
        "#b2d235",
        "#6d8346",
        "#ac6767",
        "#1d953f",
        "#6950a1",
        "#918597"
    ],
    "series": [
        {
            "type": "pie",
            "clockwise": true,
            "data": [
                {
                    "name": "Mystery",
                    "value": 2649
                },
                {
                    "name": "Adventure",
                    "value": 3116
                },
                {
                    "name": "Documentary",
                    "value": 3224
                },
                {
                    "name": "Horror",
                    "value": 4288
                },
                {
                    "name": "Crime",
                    "value": 4723
                },
                {
                    "name": "Action",
                    "value": 5175
                },
                {
                    "name": "Romance",
                    "value": 5987
                },
                {
                    "name": "Thriller",
                    "value": 7307
                },
                {
                    "name": "Comedy",
                    "value": 10741
                },
                {
                    "name": "Drama",
                    "value": 17589
                }
            ],
            "radius": [
                "40%",
                "55%"
            ],
            "center": [
                "50%",
                "50%"
            ],
            "label": {
                "show": true,
                "position": "outside",
                "margin": 8,
                "formatter": "{a|{a}}{abg|}\n{hr|}\n {b|{b}: }{c}  {per|{d}%}  ",
                "backgroundColor": "#eee",
                "borderColor": "#aaa",
                "borderWidth": 1,
                "borderRadius": 4,
                "rich": {
                    "a": {
                        "color": "#999",
                        "lineHeight": 22,
                        "align": "center"
                    },
                    "abg": {
                        "backgroundColor": "#e3e3e3",
                        "width": "100%",
                        "align": "right",
                        "height": 22,
                        "borderRadius": [
                            4,
                            4,
                            0,
                            0
                        ]
                    },
                    "hr": {
                        "borderColor": "#aaa",
                        "width": "100%",
                        "borderWidth": 0.5,
                        "height": 0
                    },
                    "b": {
                        "fontSize": 16,
                        "lineHeight": 33
                    },
                    "per": {
                        "color": "#eee",
                        "backgroundColor": "#334455",
                        "padding": [
                            2,
                            4
                        ],
                        "borderRadius": 2
                    }
                }
            }
        }
    ],
    "legend": [
        {
            "data": [
                "Mystery",
                "Adventure",
                "Documentary",
                "Horror",
                "Crime",
                "Action",
                "Romance",
                "Thriller",
                "Comedy",
                "Drama"
            ],
            "selected": {}
        }
    ],
    "tooltip": {
        "show": true,
        "trigger": "item",
        "triggerOn": "mousemove|click",
        "axisPointer": {
            "type": "line"
        },
        "showContent": true,
        "alwaysShowContent": false,
        "showDelay": 0,
        "hideDelay": 100,
        "textStyle": {
            "fontSize": 14
        },
        "borderWidth": 0,
        "padding": 5
    }
};
                chart_4dbeec64c57f42c98bd13216739e33e3.setOption(option_4dbeec64c57f42c98bd13216739e33e3);
        });
    </script>





```python
top10_genre = [x for x, y in top10]
pat = '|'.join(top10_genre)
mask1 = movies['Genre'].str.contains(pat)
mask1
# 符号|在正则表达式中表示或，使用|连接top10_genre得到一个正则字符串pat，使用contain方法判断Genre列的取值（每个单元格值是个list）是否匹配pat，得到掩码mask1
```




    0        True
    1        True
    2        True
    3         NaN
    4        True
             ... 
    34432    True
    34433    True
    34434    True
    34435    True
    34436    True
    Name: Genre, Length: 34437, dtype: object




```python
# 将掩码应用到movies
movies1 = movies[mask1]
movies1
# error 布尔类型
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-38-4f4f39e2cc6f> in <module>
          1 # 将掩码应用到movies
    ----> 2 movies1 = movies[mask1]
          3 movies1
    

    ~\anaconda3\lib\site-packages\pandas\core\frame.py in __getitem__(self, key)
       2788 
       2789         # Do we have a (boolean) 1d indexer?
    -> 2790         if com.is_bool_indexer(key):
       2791             return self._getitem_bool_array(key)
       2792 
    

    ~\anaconda3\lib\site-packages\pandas\core\common.py in is_bool_indexer(key)
        134             if not lib.is_bool_array(key):
        135                 if isna(key).any():
    --> 136                     raise ValueError(na_msg)
        137                 return False
        138             return True
    

    ValueError: cannot mask with array containing NA / NaN values



```python
# 根据movieID列去重，并且重置索引列
movies2 = movies.drop_duplicates(['Movie ID']).reset_index()
movies2
# 观察到Movie Title列，括号里的数字表示电影的出场日期，把它提取到单独一列里
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Movie ID</th>
      <th>Movie Title</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>8</td>
      <td>Edison Kinetoscopic Record of a Sneeze (1894)</td>
      <td>Documentary|Short</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>10</td>
      <td>La sortie des usines Lumière (1895)</td>
      <td>Documentary|Short</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>12</td>
      <td>The Arrival of a Train (1896)</td>
      <td>Documentary|Short</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>25</td>
      <td>The Oxford and Cambridge University Boat Race ...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>91</td>
      <td>Le manoir du diable (1896)</td>
      <td>Short|Horror</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>34430</th>
      <td>34432</td>
      <td>10977680</td>
      <td>Deon Cole: Cole Hearted (2019)</td>
      <td>Comedy</td>
    </tr>
    <tr>
      <th>34431</th>
      <td>34433</td>
      <td>10987544</td>
      <td>The Forest of Love (2019)</td>
      <td>Crime</td>
    </tr>
    <tr>
      <th>34432</th>
      <td>34434</td>
      <td>11033952</td>
      <td>Square One (2019)</td>
      <td>Documentary</td>
    </tr>
    <tr>
      <th>34433</th>
      <td>34435</td>
      <td>11064486</td>
      <td>Puppy (2019)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>34434</th>
      <td>34436</td>
      <td>11066130</td>
      <td>Upstarts (2019)</td>
      <td>Drama</td>
    </tr>
  </tbody>
</table>
<p>34435 rows × 4 columns</p>
</div>




```python
# 使用根据特定自负的分列方法partition
parts = movies2['Movie Title'].str.partition('(')
parts
# 最后一列是我们想要的，还需要剔除多余的右括号字符
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Edison Kinetoscopic Record of a Sneeze</td>
      <td>(</td>
      <td>1894)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>La sortie des usines Lumière</td>
      <td>(</td>
      <td>1895)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>The Arrival of a Train</td>
      <td>(</td>
      <td>1896)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Oxford and Cambridge University Boat Race</td>
      <td>(</td>
      <td>1895)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Le manoir du diable</td>
      <td>(</td>
      <td>1896)</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>34430</th>
      <td>Deon Cole: Cole Hearted</td>
      <td>(</td>
      <td>2019)</td>
    </tr>
    <tr>
      <th>34431</th>
      <td>The Forest of Love</td>
      <td>(</td>
      <td>2019)</td>
    </tr>
    <tr>
      <th>34432</th>
      <td>Square One</td>
      <td>(</td>
      <td>2019)</td>
    </tr>
    <tr>
      <th>34433</th>
      <td>Puppy</td>
      <td>(</td>
      <td>2019)</td>
    </tr>
    <tr>
      <th>34434</th>
      <td>Upstarts</td>
      <td>(</td>
      <td>2019)</td>
    </tr>
  </tbody>
</table>
<p>34435 rows × 3 columns</p>
</div>




```python
myear = parts[2].str.replace(')', '')
myear
# 注意此列的类型还不是int类型
```




    0        1894
    1        1895
    2        1896
    3        1895
    4        1896
             ... 
    34430    2019
    34431    2019
    34432    2019
    34433    2019
    34434    2019
    Name: 2, Length: 34435, dtype: object




```python
myear.apply(type)
```




    0        <class 'str'>
    1        <class 'str'>
    2        <class 'str'>
    3        <class 'str'>
    4        <class 'str'>
                 ...      
    34430    <class 'str'>
    34431    <class 'str'>
    34432    <class 'str'>
    34433    <class 'str'>
    34434    <class 'str'>
    Name: 2, Length: 34435, dtype: object




```python
# 使用astype方法转化为int型
myear = myear.astype(int)
myear
```




    0        1894
    1        1895
    2        1896
    3        1895
    4        1896
             ... 
    34430    2019
    34431    2019
    34432    2019
    34433    2019
    34434    2019
    Name: 2, Length: 34435, dtype: int32




```python
# 最后赋值给新建的列year上
movies2.loc[:,'year'] = myear
movies2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Movie ID</th>
      <th>Movie Title</th>
      <th>Genre</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>8</td>
      <td>Edison Kinetoscopic Record of a Sneeze (1894)</td>
      <td>Documentary|Short</td>
      <td>1894</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>10</td>
      <td>La sortie des usines Lumière (1895)</td>
      <td>Documentary|Short</td>
      <td>1895</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>12</td>
      <td>The Arrival of a Train (1896)</td>
      <td>Documentary|Short</td>
      <td>1896</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>25</td>
      <td>The Oxford and Cambridge University Boat Race ...</td>
      <td>NaN</td>
      <td>1895</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>91</td>
      <td>Le manoir du diable (1896)</td>
      <td>Short|Horror</td>
      <td>1896</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>34430</th>
      <td>34432</td>
      <td>10977680</td>
      <td>Deon Cole: Cole Hearted (2019)</td>
      <td>Comedy</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>34431</th>
      <td>34433</td>
      <td>10987544</td>
      <td>The Forest of Love (2019)</td>
      <td>Crime</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>34432</th>
      <td>34434</td>
      <td>11033952</td>
      <td>Square One (2019)</td>
      <td>Documentary</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>34433</th>
      <td>34435</td>
      <td>11064486</td>
      <td>Puppy (2019)</td>
      <td>Drama</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>34434</th>
      <td>34436</td>
      <td>11066130</td>
      <td>Upstarts (2019)</td>
      <td>Drama</td>
      <td>2019</td>
    </tr>
  </tbody>
</table>
<p>34435 rows × 5 columns</p>
</div>




```python
movies2.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 34435 entries, 0 to 34434
    Data columns (total 5 columns):
     #   Column       Non-Null Count  Dtype 
    ---  ------       --------------  ----- 
     0   index        34435 non-null  int64 
     1   Movie ID     34435 non-null  int64 
     2   Movie Title  34435 non-null  object
     3   Genre        34157 non-null  object
     4   year         34435 non-null  int32 
    dtypes: int32(1), int64(2), object(2)
    memory usage: 1.2+ MB
    

### 至此得到的movies2就是清洗过后的DataFrame
* users两列都是ID，并且无空值，不用清洗
* ratings有一个时间戳，是用偏移值表示，使用起来不方便，想办法转化构造出车、月、日三列


```python
# pandas方法to_datatime能够按列转化时间戳为datatime对象，省去for循环
rating_dt = pd.to_datetime(ratings['Rating Timestamp'], unit = 's')
rating_dt
# 参数unit默认为ns，此列时间戳单位为s，所以要重新设置
```




    0        2013-07-07 21:56:51
    1        2013-07-10 00:13:51
    2        2013-07-10 02:46:00
    3        2013-07-10 22:36:03
    4        2013-07-12 09:25:25
                     ...        
    814500   2019-09-07 00:34:16
    814501   2019-09-21 00:35:44
    814502   2013-06-23 07:34:11
    814503   2013-07-08 12:42:49
    814504   2013-07-14 03:29:20
    Name: Rating Timestamp, Length: 814505, dtype: datetime64[ns]




```python
# 同时基于datatime构造几列：year，month， day
ratings.loc[:,'rating_dt'] = rating_dt.dt.date
ratings.loc[:, 'year'] = rating_dt.dt.year
ratings.loc[:, 'month'] = rating_dt.dt.month
ratings.loc[:, 'day'] = rating_dt.dt.day
ratings
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>User ID</th>
      <th>Movie ID</th>
      <th>Rating</th>
      <th>Rating Timestamp</th>
      <th>rating_dt</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>111161</td>
      <td>10</td>
      <td>1373234211</td>
      <td>2013-07-07</td>
      <td>2013</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>117060</td>
      <td>7</td>
      <td>1373415231</td>
      <td>2013-07-10</td>
      <td>2013</td>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>120755</td>
      <td>6</td>
      <td>1373424360</td>
      <td>2013-07-10</td>
      <td>2013</td>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>317919</td>
      <td>6</td>
      <td>1373495763</td>
      <td>2013-07-10</td>
      <td>2013</td>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>454876</td>
      <td>10</td>
      <td>1373621125</td>
      <td>2013-07-12</td>
      <td>2013</td>
      <td>7</td>
      <td>12</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>814500</th>
      <td>60281</td>
      <td>8695030</td>
      <td>1</td>
      <td>1567816456</td>
      <td>2019-09-07</td>
      <td>2019</td>
      <td>9</td>
      <td>7</td>
    </tr>
    <tr>
      <th>814501</th>
      <td>60281</td>
      <td>9398640</td>
      <td>1</td>
      <td>1569026144</td>
      <td>2019-09-21</td>
      <td>2019</td>
      <td>9</td>
      <td>21</td>
    </tr>
    <tr>
      <th>814502</th>
      <td>60282</td>
      <td>816711</td>
      <td>8</td>
      <td>1371972851</td>
      <td>2013-06-23</td>
      <td>2013</td>
      <td>6</td>
      <td>23</td>
    </tr>
    <tr>
      <th>814503</th>
      <td>60283</td>
      <td>1559547</td>
      <td>2</td>
      <td>1373287369</td>
      <td>2013-07-08</td>
      <td>2013</td>
      <td>7</td>
      <td>8</td>
    </tr>
    <tr>
      <th>814504</th>
      <td>60283</td>
      <td>2415464</td>
      <td>2</td>
      <td>1373772560</td>
      <td>2013-07-14</td>
      <td>2013</td>
      <td>7</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
<p>814505 rows × 8 columns</p>
</div>




```python
# 这样就可以直接删掉Rting Timestamp列
ratings.drop('Rating Timestamp', axis = 1, inplace = True)
ratings
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>User ID</th>
      <th>Movie ID</th>
      <th>Rating</th>
      <th>rating_dt</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>111161</td>
      <td>10</td>
      <td>2013-07-07</td>
      <td>2013</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>117060</td>
      <td>7</td>
      <td>2013-07-10</td>
      <td>2013</td>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>120755</td>
      <td>6</td>
      <td>2013-07-10</td>
      <td>2013</td>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>317919</td>
      <td>6</td>
      <td>2013-07-10</td>
      <td>2013</td>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>454876</td>
      <td>10</td>
      <td>2013-07-12</td>
      <td>2013</td>
      <td>7</td>
      <td>12</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>814500</th>
      <td>60281</td>
      <td>8695030</td>
      <td>1</td>
      <td>2019-09-07</td>
      <td>2019</td>
      <td>9</td>
      <td>7</td>
    </tr>
    <tr>
      <th>814501</th>
      <td>60281</td>
      <td>9398640</td>
      <td>1</td>
      <td>2019-09-21</td>
      <td>2019</td>
      <td>9</td>
      <td>21</td>
    </tr>
    <tr>
      <th>814502</th>
      <td>60282</td>
      <td>816711</td>
      <td>8</td>
      <td>2013-06-23</td>
      <td>2013</td>
      <td>6</td>
      <td>23</td>
    </tr>
    <tr>
      <th>814503</th>
      <td>60283</td>
      <td>1559547</td>
      <td>2</td>
      <td>2013-07-08</td>
      <td>2013</td>
      <td>7</td>
      <td>8</td>
    </tr>
    <tr>
      <th>814504</th>
      <td>60283</td>
      <td>2415464</td>
      <td>2</td>
      <td>2013-07-14</td>
      <td>2013</td>
      <td>7</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
<p>814505 rows × 7 columns</p>
</div>



#### 可以看到 Pandas 数据分析非常便捷，几乎不用 for 循环，今天使用的方法也都是 Pandas 中经常使用的，这其中主要包括：

* 读入数据的方法 read_csv, 参数 header, names
* 预览数据的方法 info, describe
* 与补全数据相关的方法 isnull， value_counts, fillna
* 特征工程频繁使用的方法 split, contains, replace，正则方法，dropduplicates，partition，todatetime， drop， str 和 dt 访问器
* Python 内置的 defaultdict, sorted 等
