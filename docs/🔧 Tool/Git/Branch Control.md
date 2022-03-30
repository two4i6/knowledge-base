# 分支基础
- Git对分支操作非常快，所以Git鼓励我们使用分支完成某个任务，合并后再删除分支，这样更加安全。
- Git把每次提交都串成一条时间线，每条时间线都是一个分支。 `main` 是主分支。
- `HEAD` 严格来说不是指向提交，而是指向 `main`，`main` 指针才是指向的提交，所以 `HEAD` 指向的就是当前分支。
- 最初，`main` 分支是一条线，Git用`master` 指向最新的提交, 在用 `HEAD` 指向 `main`, 就能确定当前分支，以及当前分支的提交点：
![[58BDEA30-8BE6-4BC1-B642-0844A5D62DE6.png]]

- 每次提交，`main` 分支都会向前移动一步，随着不断提交，`main` 分支的线也会越来越长。

## 创建分支
``` shell
git checkout -b <branch>
``` 
	- `-b` 参数表示创建并切换，相当于执行了两条命令：
 ```shell
git branche <branch>
git checkout <branch>
```

或者
```shell
git switch -c <branch> 
```

- 当创建新的分支，例如 `dev`，Git会新建一个指针叫 `dev`, 指向 `main` 相同的提交，再把 `HEAD` 指向 `dev`, 以此表示分支在 `dev` 上：
![[F74A098B-D258-4941-BFBF-BC7D283B9325.png]]
- 因此，Git创建一个分支很快，因为除了增加一个 `dev` 指针，改变了 `HEAD` 的指向，工作区的文件都没有任何变化。
- 从现在开始，对工作区的修改和提交就是针对 `dev` 分支了，比如新提交一次后，`dev` 指针往前移动一步， 而 `main` 指针不变。
 ![[C1377BB4-23C6-46E5-AE7B-FB761C8A73AC.png]]

## 查看分支
```shell
git branch
*  <branch>
	main
```
`*` 表示当前分支

## 查看分支差异
```shell
git diff <branch1> <branch2>
```

### 仅差异部分
```shell
git diff <branch1> <branch2>
```

### 每个提交是在哪个分支
``` shell
git diff <branch1>..<branche2>
```

## 切换分支
```shell
git checkout <branch>
```

新版本的Git提供了新的 `git switch` 命令来切换分支。
```shell
git switch <branch>
```

*注*：在切换分支之前我们需要先[[Git Basic#Commit|提交]]或者暂存当前的修改。

## 合并分支
在切换分支后我们可以合并分支。
```shell
git merge <branch>	
```

![[5D3C71DA-4E1D-4565-83C8-054B69011218.png]]
- 把 `dev` 合并到 `main` 上，最简单的办法就是把 `main` 指向 `dev` 的当前提交。所以Git合并分支也很快，同样就是改变指针，工作区内容也不变。
![[D7E559BD-64D8-45B9-BE34-E626BE71B713.png]]
- 当合并完成后，可以删除 `dev` 分支。该操作其实就是把 `dev` 指针给删掉，删掉后，我们就剩下一条 `master` 分支。
![[16205865-6E5D-413B-8B00-D7E3C92AE223.png]]

## 合并模式
当执行合并命令后会输出合并模式，比如 `Fast-forward`：
```shell
git merge dev
Updating d46f35e..b17d20e
Fast-forward
 readme.txt | 1 +
 1 file changed, 1 insertion(+)
```

- `Fast-forward`  快速模式，直接把当前分支的指针移动到被合并的分支。
- 我们可以强制禁止 `Fast-forwad` 模式，这样Git会在merge时胜场一个新的commit，这样就可以从历史上看出分支信息。
```shell
git merge dev --no-ff
```
*注* ：`--no-ff` 表示禁止 `Fast-forward`。

这样当我们查看[[Git Basic#Log|log]]的时候就可以看到如下：
``` shell
git log --graph --pretty=oneline --abbrev-commit
*   e1e9c68 (HEAD -> master) merge with no-ff
|\  
| * f52c633 (dev) add merge
|/  
*   cf810e4 conflict fixed
```

也就是说，当不使用 `Fast-forward` 的时候merge就像：
![[E47597E5-9027-4C40-9D37-19100D77C936.png]]

## 删除分支
```shell
git branch -d <branch>
```

对于那些没有提交过的分支，需要 `-D` 参数来强行丢弃。
```shell
git branch -D <branch>
```


## 分支策略
在开发过程中应该按照几个基本原则进行分支管理：

- `main` 仅用来发布新版本，平时不应在上面工作。
- `dev` 工作分支，在某个时间把 `dev` 合并到 `main`, 如发布版本。

### Bug分支
每个bug都可以通过一个新的临时分支来修复，修复后在合并分支，并删除临时分支。

当我们把修复的bug分支与 `main` 分支合并后，我们可以把这个提交也与 `dev` 分支合并：
```shell
git checkout dev //切换分支
git branch //检查分支
* dev
  main
git cherry-pick <修复bug的提交id>
```

### Feature分支
因为我们不希望一些实验性质的代码把主分支搞乱了，所以，每添加一个新功能，最好新建一个 `feature` 分支，并在上面进行开发。完成后，合并进 `dev`，删除 `feature` 分支。


## Stash
但是通常当我们修复bug的时候，在当前分支的工作才做了一半，但是我们又不想提交它。这时候就需要使用 `stash` 功能，它就相当于把工作现场“存储“起来，等以后恢复现场后继续工作。

### 暂存
```shell
git stash 
git stash save <description>
```

### 列出
```shell
git stash list
```

### 取出
```shell
git stash pop
git stash pop stash@{1}
```

### 删除
```shell
git stash clear
git stash drop stash@{1}
```

### 差异
```shell
git stash show 
git stash show stash@{1}
```

### 新分支
当重新应用暂存的时候如果造成冲突，我们可以用暂存新建一个分支。
```shell
git stash branch <new_branch_name> stash@{1}
```




