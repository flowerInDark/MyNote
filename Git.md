# Git

初始化





git init 		初始化git

cd..      	返回上一级目录





> 出现fatal: detected dubious ownership in repository at 'D:/java项目/untitled2'报错
>
> 输入: git config --global --add safe.directory "*";
>
> 即可解决

git add 文件名

将该文件加入暂存区（该文件夹中不能有.git）



git commit -m "日志"  要提交的暂存区文件名

将暂存区文件提交到本地库



git reflog 查看日志（版本信息）

![image-20230510125227256](https://s2.loli.net/2023/10/14/4qplgv2cyEw3j9a.png)

git log 查看详细日志（版本详细信息）

![image-20230510125241568](https://s2.loli.net/2023/10/14/fuNTk9ClUoMgQ5j.png)

如果在暂存区的文件修改过就会显示：

![image-20230510125130341](https://s2.loli.net/2023/10/14/hTQCJntRwPi6Yf5.png)

然后将修改过后的东西再次添加进暂存区

![image-20230510125619436](https://s2.loli.net/2023/10/14/Xjybr1fOwZuxA36.png)

如果添加进本地库的话，就能看到和原版本的不同

![image-20230510125740252](https://s2.loli.net/2023/10/14/aErWqRwOf9MN4l2.png)

（git按行存，所以他修改是删除一行再加一行）

我们可以看到日志：

![image-20230510125909748](https://s2.loli.net/2023/10/14/PgSDxazGuBKIMyj.png)



### 版本穿梭

我们在查看版本信息中前边的7个字符即**版本号**（详细信息的话，为长码前7位）

![image-20230510130329261](https://s2.loli.net/2023/10/14/GcKFyJj2UYmxSDl.png)



git reset --hard 版本号

让版本穿越到该版本

![image-20230510130741136](https://s2.loli.net/2023/10/14/9sgjQUvuXfaHxKq.png)

查看版本号则可看到：

![image-20230510130839845](https://s2.loli.net/2023/10/14/AdY1feUMWZnzFB7.png)

此时指针会指向该版本号，.git中有关HEAD的文件也会跟着修改

注意，进行版本穿梭，工作区的文件也会跟着修改成该版本的文件！

### 分支

git branch -v   查看分支

![image-20230510132017860](https://s2.loli.net/2023/10/14/giwSYb9O8KUGMHt.png)

绿色且带*的分支表示我们现在所在的分支上

git branch 分支名   创建分支

git branch -m new_branch_name  修改当前分支的名字

git checkout 分支名    切换到该分支

![image-20230510132157982](https://s2.loli.net/2023/10/14/BY1RwV7btUHDcfG.png)

切换的分支也可进行add，commit操作

![image-20230510132423814](https://s2.loli.net/2023/10/14/HF4mhr5oKa8bCAv.png)

此时查看日志，将会是一个新的

![image-20230510132516606](https://s2.loli.net/2023/10/14/KfdPyGjF7Emb3lt.png)

切换后的HEAD指向的是新分支的HEAD，新提交将会接在该HEAD之后



git merge 分支A的名字   将当前分支和分支A合并

![image-20230510133007424](https://s2.loli.net/2023/10/14/voLMC1VS2EW79IN.png)

会出现合并后的结果与差异



> 冲突合并：当两个分支在**同一个文件的同一个位置**有**两个不同的修改**，此时处于合并中，因为git无法决定保留哪种方案，需要自己**手动合并**（进文件去修改），然后添加入暂存区并执行提交且**提交时不能带文件名**





 git remote -v ，查看所有仓库别名

git remote add   别名	远程仓库链接	，创建别名

![image-20230510182512645](https://s2.loli.net/2023/10/14/TafyF1sYHSJEA5w.png)

有两个是因为有两个操作





然后push，push的基本单位是分支

git push 别名/链接  分支名

将分支添加到远程仓库





拉取pull

git pull 别名/链接  分支名

- 拉取会**自动提交本地库**，此时本地库与远程库同步



凭据管理器可以用来**删除电脑的登录信息**



克隆到本地（克隆不需要登录）

git clone 链接  

克隆的是远程仓库的**默认分支**（default）

![image-20230510185616838](https://s2.loli.net/2023/10/14/XQIjMVHyhJz3a6q.png)



git clone --single-branch --branch 分支名 git远程仓库地址

克隆指定分支