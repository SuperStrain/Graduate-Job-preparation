# 本地库（Git）与远程库（GitHub）连接方式

* 一共有两种连接方式，https和ssh，其中ssh需要设置钥匙，比较推荐ssh。

# 本地库与远程库间传输的命令或过程

## Git

### 首次上传

第一步当然要在远端创建仓库并把链接复制下来（ssh或https）

```
git init            
git add first.txt
git commit -m"本次传输的日志信息"
git remote add origin https://github.com/IsMrChen/Test.git
git push -u origin master
1. 初始化本地库
2. 添加文件到暂存区
3. 提交文件到本地库
4. 在本地添加远程库的地址，并给这个地址取别名为“origin”
5. 将本地库的内容推送到远程库的主分支（自动创建的）上
```

> 可以用`git remote -v` 去查看链接远程仓库的信息

> 可以用`git status` 去查看当前状态

### 更新

* 本地库变化，更新远程库：

```
git add .
git commit -m"更新日志"
git push  <远程仓库别名或仓库地址>  <要上传的本地分支名>
或 git push
```

* 远程库变化，更新本地库：

```
   git pull <远程仓库别名或仓库地址>  <远程分支名>
   将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并
```

### 克隆（clone):从无到有

* 克隆所有分支：

` git clone <远程仓库地址>`

* 克隆单个分支：

`git clone -b <分支名> <远程仓库地址>`

---

**与分支有关的命令：**

* 查看现有分支(包含隐藏分支)：`git branch -a`
* 切换分支：       `git checkout <分支>`

---

## Visual Studio

### 首次上传

`选择Git-创建Git存储库(即远程库)并填写仓库信息-创建并推送`

### 更新

* 本地库变化，更新远程库：`写好提交日志-提交本地库-推送（push）`

* 远程库变化，更新本地库：`拉取（pull）`

### 克隆（clone）

直接点克隆即可。

# 协作

## 团队内

`Collaborators 内添加成员-clone-改代码-push`

(如有冲突后面有解决描述)

## 团队外

`fork-（clone-改代码-push）或（在线修改）-pull requests` 

# 冲突

## 本地库和远程库均发生变化

在push后，发现上传远程仓库失败，使用命令`git remote show origin`后发现本地仓库与远程仓库不同步即`out of date`则需要使用命令` git pull <远程仓库别名或仓库地址>  <远程分支名>`,**根据出现的不同情况进行处理：**

1. 出现`Fast-forward`,远程仓库比本地仓库有着更多内容，是包含于被包含的关系，就自动合并向前更新。

2. 出现`conflict`,两者是交叉关系，会提示冲突文件。只需：

   ```
   vim <冲突文件>
   a并回车
   修改
   ：wq（保存）
   git add .
   git commit -m"日志"
   git push
   ```

3. 另一种情况，希望有空解决

# 一些工作需要的配置

## **配置** **Git** **忽略文件**

就是上传所有的文件时，自动过滤掉不必要的文件。

[配置Git忽略文件](https://www.bilibili.com/video/BV1vy4y1s7k6?p=27 "点击即可")

