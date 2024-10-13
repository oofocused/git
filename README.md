Git 的命令行接口

为了避免重复信息，我们将不会详细解释以下命令行。强烈推荐您阅读 Pro Git 中文版

    git help <command>: 获取 git 命令的帮助信息
    git init: 创建一个新的 git 仓库，其数据会存放在一个名为 .git 的目录下
    git status: 显示当前的仓库状态
    git add <filename>: 添加文件到暂存区
    git commit: 创建一个新的提交
        如何编写 良好的提交信息!
        为何要 编写良好的提交信息
    git log: 显示历史日志
    git log --all --graph --decorate: 可视化历史记录（有向无环图）
    git diff <filename>: 显示与暂存区文件的差异
    git diff <revision> <filename>: 显示某个文件两个版本之间的差异
    git checkout <revision>: 更新 HEAD 和目前的分支

分支和合并

    git branch: 显示分支
    git branch <name>: 创建分支
    git checkout -b <name>: 创建分支并切换到该分支
        相当于 git branch <name>; git checkout <name>
    git merge <revision>: 合并到当前分支
    git mergetool: 使用工具来处理合并冲突
    git rebase: 将一系列补丁变基（rebase）为新的基线

远端操作

    git remote: 列出远端
    git remote add <name> <url>: 添加一个远端
    git push <remote> <local branch>:<remote branch>: 将对象传送至远端并更新远端引用
    git branch --set-upstream-to=<remote>/<remote branch>: 创建本地和远端分支的关联关系
    git fetch: 从远端获取对象/索引
    git pull: 相当于 git fetch; git merge
    git clone: 从远端下载仓库

撤销

    git commit --amend: 编辑提交的内容或信息
    git reset HEAD <file>: 恢复暂存的文件
    git checkout -- <file>: 丢弃修改
    git restore: git2.32 版本后取代 git reset 进行许多撤销操作

Git 高级操作

    git config: Git 是一个 高度可定制的 工具
    git clone --depth=1: 浅克隆（shallow clone），不包括完整的版本历史信息
    git add -p: 交互式暂存
    git rebase -i: 交互式变基
    git blame: 查看最后修改某行的人
    git stash: 暂时移除工作目录下的修改内容
    git bisect: 通过二分查找搜索历史记录
    .gitignore: 指定 故意不追踪的文件



配置ssh-key过程


第1步：查看 或者 生成一个SSH-Key

// 新环境大概率会报错 ，因为这个目录不存在
$ cd ~/.ssh
使用下面命令生成ssh-key
ssh-keygen -t rsa -C "xxx@xxx.com"  // 将 "xxx@xxx.com" 替换为你自己GitHub的邮箱地址
然后一直按 “enter”键


第2步：获取ssh key公钥内容

// 进入ssh目录
$ cd ~/.ssh
// 查看ssh 公钥  进行复制
$ cat id_rsa.pub


第3步：GitHub设置中添加公钥

点击GitHub中设置标签，然后点击 SSH and GPG keys 、 New SSH key 将复制好的链接粘贴进去


第4步：检查是否设置成功

$ ssh -T git@github.com
看到successfully字样就成功


第5步：GitHub中创建仓库，并使用ssh链接进行下拉

$ git clone + "ssh链接"


第6步：编码，代码上传

// 查看更改项
$ git status
// 添加所有更改项
$ git add .
// 提交commit , 这一步可能会有问题
$ git commit -m "feat:add code"
// 推送至远端
$git push
//添加远程仓库
git remote add

在commit的时候可能会碰到问题 “please tell me who you are”,按照提示进行设置就行

$ git config --global user.email "you@example.com"   // "you@example.com"替换为你的GitHub邮箱地址
$ git config --global user.name "Your Name"   // "Your Name"替换为你的GitHub名称


