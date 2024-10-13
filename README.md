配置过程
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

点击GitHub中设置标签

，然后点击 SSH and GPG keys 、 New SSH key 将复制好的链接粘贴进去


第4步：检查是否设置成功

$ ssh -T git@github.com

看到successfully字样就成


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

在commit的时候可能会碰到问题 “please tell me who you are”,按照提示进行设置就行

$ git config --global user.email "you@example.com"   // "you@example.com"替换为你的GitHub邮箱地址
$ git config --global user.name "Your Name"   // "Your Name"替换为你的GitHub名称
