# PyQt拾遗

# 1.提醒用户

常用的五种对话框

## 消息对话框

```python
QMessageBox.information(self,'标题','消息对话框正文',QMessageBox.Yes|QMessageBox.No,QMessageBox.Yes)
```

![image-20240226195241973](D:\t_Knowlege\knowlege_system\PyQt拾遗.assets\image-20240226195241973.png)

## 提问对话框

```python
QMessageBox.question(self,'标题','提问框消息正文',QMessageBox.Yes|QMessageBox.No,QMessageBox.Yes)
```

![image-20240226195331505](D:\t_Knowlege\knowlege_system\PyQt拾遗.assets\image-20240226195331505.png)

## 警告对话框

```python
QMessageBox.warning(self,'标题','警告框消息正文',QMessageBox.Yes|QMessageBox.No,QMessageBox.Yes)
```

![image-20240226195401623](D:\t_Knowlege\knowlege_system\PyQt拾遗.assets\image-20240226195401623.png)

## 严重错误对话框

```python
QMessageBox.critical(self,'标题','严重错误对话框消息正文',QMessageBox.Yes|QMessageBox.No,QMessageBox.Yes)
```

![image-20240226195438632](D:\t_Knowlege\knowlege_system\PyQt拾遗.assets\image-20240226195438632.png)

## 关于对话框

```python
QMessageBox.about(self,'标题','关于对话框'
```

![image-20240226195506340](D:\t_Knowlege\knowlege_system\PyQt拾遗.assets\image-20240226195506340.png)

参考链接：[PyQt5基本控件详解之QMessageBox(十三)-CSDN博客](https://blog.csdn.net/jia666666/article/details/81540785)

# 2.自定义QMessageBox的按钮内容

参考链接：[PyQt5的QMessageBox属性及自定义中文按钮_qt如何替换qmessagebox的按钮图标-CSDN博客](https://blog.csdn.net/Yselin_c/article/details/104676474)

