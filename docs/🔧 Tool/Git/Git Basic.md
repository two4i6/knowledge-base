# GIt
分布式版本控制系统

## Repository
仓库，一个可以被 `Git` 管理的目录。

```shell
mkdir mydir
cd mydir
git init
```

## Add
添加文件到仓库
`git add <file>`

```shell
git add readme.md
git add .
```

## Remove
删除缓存区文件

``` shell
git rm readme.md
```

## Commit
提交文件到仓库
`git commit -m <message>`

```shell
git commit -m “wrote a readme file”
```

当`git commit`命令执行成功后会告诉我们，
- `x file change` 有几个文件被改动
- `x insertions` 插入了几行内容

## Status
获取仓库当前状态

```Shell
git status
```

当`git status`执行成功后会告诉我们，
- `On branch` 处于哪个分支
- `mkdified`  哪些文件有变动，但还没有被提交

## Diff
查看修改的内容
`git diff <file>` 

```Shell
git diff readme.txt
git diff HEAD — readme.txt
```

## Log
查看历史

```shell
git log
```
*注* 输出得 `commit id` 不是递增的数字，而是一个SHA1计算出来的非常大的数字，以16进制表示。

- `--graph`  查看分支合并图
- `--pretty=oneline`
- `--abbrev-commit`

## Reflog
查看我们执行的每一个 Git命令
```shell
git reflog
```



