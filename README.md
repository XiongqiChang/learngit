#### 第一题;

```shell
git init 
touch .gitignore
vim .gitignore
*.class
*.log
*.jar
*.war
.mtj/
.tmp/
git add .
git commit -m "提交.gitignore"
git remote add origin https://github.com/XiongqiChang/learngit.git
git push origin master
```

#### 第二题：

```shell
git clone -b dev from  https://github.com/XiongqiChang/learngit.git
git checkout -b  feature-1
git push --set-upstream origin feature-1
```

####第三题：

```shell
首先fork项目到github的账号下
git clone https://github.com/XiongqiChang/learngit.git
git checkout dev
#新建一个功能分支
git checkout -b feature-tdd
touch test.java
git add .
git commit -m "测试完成"
git checkout dev
git merge --no-ff feature-tdd
git barnch -d feature-tdd
git push origin dev
然后再通过向管理人员发起pull request代码的提交审核,然后同样上诉的操作对测试进行实现
```

#### 第四题：

```shell
git reset --hard HEAD^^
git reflog
git reset --hard commit_id
```

#### 第五题：

```shell
git pull
git merge feature-1
git push origin master
```

#### 第六题：

```shell
git tag -a v0.1 -m 'version 0.1 released'
git push origin v0.1
git tag -d v0.9
git push origin :refs/tags/v0.9
```

#### 第七题：

```shell
git stash
git checkout dev
git checkout -b issue-1
git add .
git commit -m "修复bug"
git switch dev
git merge -no-ff -m "修复bug" issue-1
git cherry pick <commitHash>
git switch feature-1
git stash list
git stash pop

```

#### 第八题：

```shell
git log --pretty="%h - %s"  --comitter="cheny" --since="2020-04-02" --before="2020-08-06" 
```

#### 第九题：

```shell
git reset --hard 01e31c
```

#### 第十题：

```shell
git rebase -i HEAD~5	
然后修改commit的信息将peek的信息为edit然后保存
git rebase -continue
git push origin master
```

#### 第十一题:

```rebase```和```merge```都是从一个分支获取然后合并到当前分支的。```merge```的操作会自动的创建一个新的commit，在发生冲突的时候，需要修改后重新的```commit```，```merge```能够真实的记录```commit```的情况，包括每一个分支的详情，但是在```commit```频繁操作的时候，会发现分支很乱。

```rebase```的话就会形成一条很简介的代码树结构，会合并之前的`commit`的历史，但是这样的话就不是很容易对代码的问题进行定位。

#### 第十二题：

`git fetch`和`git pull`都是从远程仓库拉取代码到本地的，但是`fetch`是只能将代码拉取到本地但是不能合并的，`git pull`是将代码库拉取到本地之后还是会进行`merge`的因此简单的理解为`git pull` 就是`git fetch`和`git merge`的合体。`git pull --rebase`的就是将合并的方式设置为`rebase`，将你本地的`commit`的记录全部取消掉然后和你拉取的分支进行合并。在`rebase`的过程中如果出现了代码的冲突你先是解决代码的冲突然，然后`git add` .不需要再次`commit`，直接使用`git rebase --continue`就也进行合并

第十三题：

**工作区** :指的是你提交代码的那个文件夹。

**暂存区**：存放在.git下的index文件中。

**版本库**: .git 的这个文件下的内容都是版本库内容。

第十四题：

首先是将远程的代码拉取到本地的代码库中，使用`git clone url`然后切换到feature分支 `git checkout -b feature`,然后在`feature`的分支下进行开发，使用`git add`将代码首先提交到暂存区然后`git commit`到本地仓库，为了防止远程的代码发生冲突首先是将远程的代码`git pull`下来如果有冲突的话就解决冲突，然后再次提交使用`git push `到远程仓库。