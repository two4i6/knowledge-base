# SSH Key
需要准备SSH key

```shell
cd ~/.ssh/
ssh-keygen -t rsa -C "youremail@example.com"
```

执行后会在 `~/.ssh/` 文件夹中生成 `id_rsa` 和 `id_rsa.pub` 两个文件，这就是SSH key的密钥对。

- `id_rsa` 私钥
- `id_rsa.pub` 公钥

接下来要把它们部署在我们的Github/服务器。


# 添加远程库
如果已有本地仓库但是想进行本地库和远程库的同步，可以备份源码，又可以与其他人通过远程库来协作。

在建立好远程仓库之后, 使用以下命令来与本地仓库进行关联。

```shell
git remote add origin git@github.com:YOURNAME/YOURPROJECT.git
```

- `origin` 是Git默认的远程库名称，这是可以修改的。
- `YOURNAME` 是你的Github用户名。


# 从远程仓库克隆
``` shell
git clone git@github.com:YOURNAME/YOURPROJECT.git
```


# 从远程仓库更新
有两种方式：
- `git fetch` 将远程主机的最新内容拉到本地，用户检查了以后再决决定是否合并到本地。
- `git pull` 将远程主机的最新内容拉到本地后直接合并。
![[6B073B8D-2B11-43B5-B9D8-5D1559D2438A.jpeg]]
`git pull = git fetch + git merge`

## Fetch
```shell
git fetch <远程主机名>
git fetch <远程主机名> <分支名>
```

查看取回的更新信息：
```shell
git log -p FETCH_HEAD
```

接下来需要手动判断是否合并到当前分支。
```shell
git merge FETCH_HEAD
```

## Pull
```shell
git pull <远程主机名>
git pull <远程主机名> <远程分支名>:<本地分支名>
```

# 推送内容
把本地仓库的内容推送到远程仓库上：

```shell
git push -u origin main
```

这里我们把本地 `main` 分支推送到了远程仓库上。
当我们第一次推送的时候需要添加 `-u` 参数。

- `-u` 会把本地的 `main` 分支和远程的分支关联起来，在以后的推送或拉去时就可以简化命令。

现在起，只要本地做了提交，就可以通过命令：

```shell
git push origin <branch>
```

把本地 `main` 分支的最新修改改送至Git服务器了。


# 查看远程仓库

```shell
git remote
git remote -v
```

`-v` 属性可以显示更多信息。


# 删除与远程仓库的联系
如果添加时地址写错了，或者想删除与远程库的联系。
`git remote rm <name>`

```shell
git remote rm origin
```


# 多人协作
当需要在远程的分支工作，比如 `dev`，就必须创建远程 `orgin` 的 `dev` 分支到本地：
```shell
git checkout -b dev origin/dev
```

`-b` 参数同时创建并切换到新分支

## 其他人最近的提交与你的有冲突
解决方法是先用 `git pull` 把最新的提交从 `origin/dev` 抓下来，然后在本地合并，解决冲突，在推送:
```shell
git commit -m 'fix conflict'
git pull
```

#### git pull 失败
如 `git pull` 失败并提示 `no tracking information`, 该问题的原因是没有指定本地 `dev` 分支与远程 `origin/dev` 的链接：
```shell
git branch --set-upstream-to=origin/<branch> dev

git pull
```


# Rebase
在多人同时工作在一个分支上时，很容易出现冲突。即使没有出现冲突，后push的人不得不先pull，在本地合并，然后才能push。这样会让提交看起来很乱，例如：

``` shell
$ git log --graph --pretty=oneline --abbrev-commit
* d1be385 (HEAD -> master, origin/master) init hello
*   e5e69f1 Merge branch 'dev'
|\  
| *   57c53ab (origin/dev, dev) fix env conflict
| |\  
| | * 7a5e5dd add env
| * | 7bd91f1 add new env
| |/  
* |   12a631b merged bug fix 101
|\ \  
| * | 4c805e2 fix bug 101
|/ /  
* |   e1e9c68 merge with no-ff
|\ \  
| |/  
| * f52c633 add merge
|/  
*   cf810e4 conflict fixed
```

*注* Git用 `(HEAD -> master)` 和 `(origin/master)` 标记出当前分支的 `HEAD` 和远程 `origin` 的位置.

`git rebase` 操作可以把提交整理成直线，看上去更直观，但缺点是分叉会被修改。

## 清除某次提交
查找需要清除的 commit id：
``` shell
git log
```

使用 `git rebase - i` 将 `commit_it` 的前缀 `pick` 改为 `drop`：
```shell
git rebase -i <commit_id>
pick <commit_id>
```

推送到远程仓库:
```shell
git push origin HEAD -force
```