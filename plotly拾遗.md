# plotly拾遗

# 1.安装版本

学习期间安装版本未5.17.0.pip默认安装版本为4.1.1.这个版本有个问题，那就是下面这种代码会报错

```python
import plotly.express as px
fig = px.scatter(x=[0,1,2,3,4],y=[0,1,4,9,16])
fig.show()
```

报错原因是没有给需要的参数data_frame赋值。现在新版本把这个参数设置为默认为None了

# 2.Scatter

## 2.1直接输入x与y的数值

```python
import plotly.express as px
import numpy as np
x = range(1,100)
y = np.power(x,2)
fig = px.scatter(x=x,y=y)
fig.show()
```

![image-20230918192421871](C:\Users\TR\AppData\Roaming\Typora\typora-user-images\image-20230918192421871.png)

## 2.2根据data_frame生成scatter

需要注意，x y等都必须是列名，不能自己自定义

```python
import plotly.express as px
import numpy as np

# 2.根据data_frame绘制散点图
df = px.data.iris()
fig = px.scatter(df,x="sepal_length",y="sepal_width")
fig.show()
```

![image-20230918193027772](C:\Users\TR\AppData\Roaming\Typora\typora-user-images\image-20230918193027772.png)

## 2.3用列名设置大小和颜色

```python
import plotly.express as px
import numpy as np

# 2.根据data_frame绘制散点图,并且设置颜色和大小
df = px.data.iris()
fig = px.scatter(df,x="sepal_length",y="sepal_width",color="species",size="petal_length",hover_data=['petal_width'])
fig.show()
```

点击右上角图例，可以实现图例对应数据的显示与隐藏

![image-20230918193729523](C:\Users\TR\AppData\Roaming\Typora\typora-user-images\image-20230918193729523.png)

颜色除了上述这种分类的，也可以是连续的，例如

```python
import plotly.express as px
import numpy as np

# 2.根据data_frame绘制散点图,并且设置颜色和大小
df = px.data.iris()
fig = px.scatter(df,x="sepal_length",y="sepal_width",color="petal_length",size="petal_length",hover_data=['petal_width'])
fig.show()
```

![image-20230918194113880](C:\file\t_Knowlege\knowlege_system\plotly拾遗.assets\image-20230918194113880.png)

设置symbol

```python
import plotly.express as px
import numpy as np

# 2.根据data_frame绘制散点图,并且设置颜色和大小
df = px.data.iris()
fig = px.scatter(df,x="sepal_length",y="sepal_width",color="species",size="petal_length",hover_data=['petal_width'],symbol="species")
fig.show()
```

![image-20230918194356173](C:\file\t_Knowlege\knowlege_system\plotly拾遗.assets\image-20230918194356173.png)

## 2.4散点图坐标轴类型

散点图坐标轴可以是线性、对数、分类或者日期等类型

