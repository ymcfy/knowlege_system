# git拾遗

# 1.两种rebase情境

一种是必须手动rebase，也就是下图这种带三角号的

![image-20240410194018092](git拾遗.assets/image-20240410194018092.png)

一种是可以线上rebase，也就是下图这种不带三角号，内部有提示的

![image-20240410193805775](git拾遗.assets/image-20240410193805775.png)

# 2.丢弃本地修改的所有文件

有时候需要用命令行方式丢弃本地修改的所有文件

```powershell
git checkout . #本地所有修改的。没有的提交的，都返回到原来的状态
```

[git丢弃本地修改的所有文件（新增、删除、修改）_git本地提交changes新增很多文件-CSDN博客](https://blog.csdn.net/leedaning/article/details/51304690)

# 3.git回退到之前的某个commit

```powershell
git reset --hard 分支名
```

# 4.查看当前所有分支

4.1查看当前本地所有分支

```bash
git branch
```

![image-20240425160150014](git拾遗.assets/image-20240425160150014.png)

4.2查看本地和远程的分支

```bash
git branch -a
```

![image-20240425160249126](git拾遗.assets/image-20240425160249126.png)

这个过程中，如果要退出，可输入:q来退出

4.3显示分支的最后一次提交

```bash
git branch -a -v
```

![image-20240425160432301](git拾遗.assets/image-20240425160432301.png)

