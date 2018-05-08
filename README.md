# 同步 github 上的项目

包括:
* 自己的项目(含组织)
* 标心的项目

解决:
收藏和备份自己的代码库
及时 clone star 的项目

> 有时候某些喜欢的项目可能顺手就 clone 或者 star 了. 但是可能因为作者删除或者违反了 github 规则被移除, 到时候才想起来没有 clone 到本地而后悔...

## 配置文件

```json
{
  "user": "your_github_username",
  "token": "your_github_token",
  "repo_root_dir": "git_repo_dir"
}
```

```text
user          :  github 用户名
token         :  https://github.com/settings/tokens 到这里创建一个 access token
repo_root_dir :  本地要保存仓库的根目录
```

## 依赖

* 需要安装 git, 并且将服务器的 ssh 公钥添加到 github

## 提示Permission denied解决方法
极大多数情况是由于github账号没有设置ssh公钥信息所致。 
前往 GitHub 网站的"account settings"依次点击"Setting -> SSH Keys"->"New SSH key" Title处填写“id_rsa.pub”或其他任意信息。 
key处原样拷贝下面命令的打印 `~/.ssh/id_rsa.pub` 
文件的内容： ``` cat ~/.ssh/id_rsa.pub ```
如没有则按下述方法生成：  ssh-keygen -t rsa  一路回车......  
最后，输入“ssh -T git@github.com”确认OK即可。
再尝试输出就应该有了```cat ~/.ssh/id_rsa.pub


## 使用场景

我的使用场景是放在家里的服务器上, crontab 跑一个定时任务, 每天凌晨定时跑一下将代码 clone/pull 到本地磁盘

> 如果你 star 的项目很多的话... 可能会吃掉很大一块磁盘, 我的情况是用了 34G (这已经超乎我的想象了)
