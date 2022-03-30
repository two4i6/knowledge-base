# 显示颜色
让命令输出看起来更醒目，git会适地的显示不同的颜色。

```shell
git config --global color.hi true
```


# 默认编辑器
Git默认的编辑器是 `vi`， 如果觉得难用可以用其他编辑器替代。如 `vscode` ：
```shell
git config --global core.editor "code --wait"
```


# 忽略特殊文件
有些在工作区但又不需要提交的文件，比如数据库密码配置之类。可以使用 `.gitignore` 文件忽略这些文件。

``` shell
# 单个文件
sql.db
desktop.ini

# 排除所有.开头的文件
.*

# 排除所以log结尾的文件
*.log

# 排除history文件夹
./history

# 不排除.gitignore
!.gitignore
```

当我们尝试在添加一些出现在 `.gitignore` 中的文件就会发现无法添加，比如：
```shell
git add sql.db

The following paths are ignored by one of your .gitignore files:
sql.db
Use -f if you really want to add them
```

## 检查.gitignore格式
```shell
git check-ignore -v <file>
```


# 配置账户
```shell
git config --global user.email <your-email-address>
```


# 配置别名
比如我们想让 `git st` 表示 `git status`
``` shell
git config --global alias.st status
```

我们还可以配置一个 `git last`, 显示最后一次提交的信息：
```shell
git config --global alias.last 'log -1'
```

当然也可以更加复杂:
```shell
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

*注* `--global` 是针对当前用户起作用，如果不加，那只针对当前的仓库起作用。


# 配置文件
每个仓库的Git配置文件都在 `.git/config` 文件中：
```shell
cat .git/config

[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    url = git@github.com:michaelliao/learngit.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[alias]
    last = log -1
```

用户的配置文件则在主目录`$home` 下的一个隐藏文件 `.gitconfig` 中:
```shell
cat ~/.gitconfi
[alias]
    co = checkout
    ci = commit
    br = branch
    st = status
[user]
    name = Your Name
    email = your@email.com
```

