### 一些git操作

#### 1.分支合并：

git merge [branch_name] 当前所在分支合并[branch_name]分支

#### 2.commit撤销:

​	2.1 revert: git revert [commit_hashName] 会逆向做一次commit_hashName对应的内容本地的操作都会被重置，会丢失数据。

> 操作过程： 先git revert [commit_hashName] 在 git push origin [branch_name]

​	2.2 reset

- git reset reset head~ --soft 撤销上一次的commit (head~代表上一次 head1,2,3分别代表上1次2次3次)

  --soft会保存git add，本地内容不会被更改

- git reset reset head~ :不保存git add,本地内容不会被更改
- git reset reset head~ --hard:不保存git add且本地内容会退回到上一次commit之前。会丢失数据。

3.查看git add缓存区里面的内容

git status

eg:

![image-20240719144243375](./MD_img/image-20240719144243375.png)