![](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

# 配置

###### 生成SSH Key

```shell
$ ssh-keygen -t rsa -C "1078419631@qq.com"
```



# 基本操作

## 仓库

### `git init  `

- 初始化仓库

- ```shell
  # 指定目录
  git init <directory>
  ```



### `git clone`  

- 现有 Git 仓库中拷贝项目





## 修改

### `git add`

- 添加文件到暂存区

- ```shell
  # 暂存所有文件
  git add .
  ```

  







## 提交

### `git commit `

- 提交暂存区到本地仓库

- ```shell
  git commit -m <message>
  ```

- 在 Linux 系统中,commit 信息使用单引号 `'`;Windows 系统,commit 信息使用双引号 `"`









# 远程仓库
### `git remote`

- 远程仓库操作

- ```shell
  # 查看远程库信息
  git remote -v 
  ```

- ```shell
  # 与远程库关联
  git remote add <别名> <仓库>
  ```

- ```shell
  # 重命名远程库
  git remote rename <old_name> <new_name>
  ```

- ```shell
  # 移除远程库
  git remote remove <remote_short_name>
  ```

  







### `git  push`

- 上传远程代码并合并

- ```shell
  git push <远程主机名> <本地分支名>:<远程分支名>
  git push <远程主机名> <本地分支名>	# 本地分支名与远程分支名相同
  ```

  
  
  





### `git pull`

- 下载远程代码并合并

- 是 **git fetch** 和 **git merge FETCH_HEAD** 的简写

- ```shell
  git pull <远程主机名> <远程分支名>:<本地分支名>
  ```

  



# 版本管理

### `git reset`

- `git reset [--soft | --mixed | --hard] [HEAD]`

- `HEAD` 是当前分支引用的指针，它总是指向该分支上的最后一次提交

  - ```
    HEAD~0 表示当前版本
    HEAD~1 上一个版本
    HEAD^2 上上一个版本
    HEAD^3 上上上一个版本
    ```

  - ```
    HEAD 表示当前版本
    HEAD^ 上一个版本
    HEAD^^ 上上一个版本
    HEAD^^^ 上上上一个版本
    ```

- **`--mixed`** 为默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交(commit)保持一致，工作区文件内容保持不变。

- **`--soft`** 参数用于回退到某个版本

- **`--hard`** 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交



### `git revert`

- 撤销 某次操作，此次操作之前和之后的commit和history都会保留，并且把这次撤销
  作为一次最新的提交







# 分支管理

### `git branch`

- ```shell
  # 列出分支
  git branch
  ```

- ```shell
  # 创建分支
  git branch <branchname>
  ```

- ```shell
  # 删除分支
  git branch -d <branchname>
  ```

  







### `git checkout`

- ```shell
  # 切换分支
  git checkout <branchname>
  ```

- ```shell
  # 创建并切换分支
  git checkout -b mybranch
  ```

  

### `git merge `

- ```shell
  # 合并分支
  git merge 
  ```










```

```



# 查看历史











# gitLab