# Directory
Git 跟踪的是修改，而非文件。
修改包括：
- 新增
- 删除
- 更改

## Working Directory
工作区，就是我们电脑里能看到的目录。

## Repository
版本库，工作区中有一个隐藏的 `.git` 目录，这不算工作区，而是一个Git的版本库。

版本库中存在很多东西：
- stage (index)： 暂存区
- 分支：包括Git自动为我们创建的第一个分支 `main`, 以及指向 `master` 的一个指针 `HEAD`。

![[3550E7F3-8556-4EC1-9839-C792DA938423.jpeg]]

## Stage
暂存区，需要提交的文件修改暂时放到暂存区直到提交。
- 当我们使用 `git add` 把文件添加进去，实际上就是把文件修改添加到暂存区。
- 当我们使用 `git commit` 提交更改，实际上就是把文件提交到当前分支，如默认的 `main`。

当所有工作区里的文件都被提交，并且没有在做任何修改，那么工作区就是‘干净’的。

```shell
git status
On branch master
nothing to commit, working tree clean
```


