# matplotlib拾遗

# 1.relim()函数

更新Axes范围，适应Axes内曲线或其他元素的坐标轴范围

```python
axes.relim()
```

# 2.autoscale()函数

自动调整坐标轴范围

```python
axes.autoscale()
```

# 3.draw_idle()函数

局部刷新

```python
figure.canvas.draw_idle()
```

# 4.槽函数

```python
def connect(self):
    self.cid_key_press = self.ax.figure.canvas.mpl_connect(
         'key_press_event', self.on_key_press)
    # self.cidpress = self.line.figure.canvas.mpl_connect(
    #     'button_press_event', self.on_press)
    
def on_key_press(self, event):
    if event.key == 'ctrl+c':
        self.line_copy()
        return
        
def disconnect(self):
    self.fig.canvas.mpl_disconnect(self.cid_key_press)
```

