# 搭建git服务器
### 搭建git服务器
1. 安装git：

  ```cmd
$ sudo apt-get install git
```

> [CentOS安装最新版git](https://my.oschina.net/antsky/blog/514586)

2. 创建一个git用户，用来运行git服务：

  ```cmd
$ sudo adduser git
```
3. 创建证书登录：

  收集所有需要登录的用户的公钥，就是他们自己的id_rsa.pub文件，把所有公钥导入到/home/git/.ssh/authorized_keys文件里，一行一个。

4. 初始化Git仓库：

  先选定一个目录作为Git仓库，假定是/srv/sample.git，在/srv目录下输入命令：

  ```cmd
$ sudo git init --bare sample.git
```
  Git就会创建一个裸仓库，裸仓库没有工作区，因为服务器上的Git仓库纯粹是为了共享，所以不让用户直接登录到服务器上去改工作区，并且服务器上的Git仓库通常都以.git结尾。然后，把owner改为git：

  ```cmd
$ sudo chown -R git:git sample.git
```
5. 禁用shell登录：

  出于安全考虑，第二步创建的git用户不允许登录shell，这可以通过编辑/etc/passwd文件完成。找到类似下面的一行：
  ```
git:x:1001:1001:,,,:/home/git:/bin/bash
```
  改为：
  ```
git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell
```
  这样，git用户可以正常通过ssh使用git，但无法登录shell，因为我们为git用户指定的git-shell每次一登录就自动退出。

6. 克隆远程仓库：

  现在，可以通过git clone命令克隆远程仓库了，在各自的电脑上运行：
  ```cmd
$ git clone git@server:/srv/sample.git
Cloning into 'sample'...
warning: You appear to have cloned an empty repository.
```

### 管理公钥
如果团队很小，把每个人的公钥收集起来放到服务器的/home/git/.ssh/authorized_keys文件里就是可行的。

### 来源
- [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000)
