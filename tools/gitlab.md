# 用docker 安装gitlab教程

> 系统：Ubuntu 16.04　内存：2GB　CPU：双核

### 1. 安装docker
`wget -qO- https://get.docker.com/ | sh`

### 2. 下载iamges
`docker pull gitlab/gitlab-ce:8.11.3-ce.1`

### 3. 运行container

```bash
sudo docker run --detach \
    --hostname code.farzer.com \
    --publish 443:443 --publish 80:80 --publish 2222:2222 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    gitlab/gitlab-ce:8.11.3-ce.1
```

> 上面的 code.farzer.com换成你的域名

### 4. 维护
Where is the data stored?
The GitLab container uses host mounted volumes to store persistent data:

|Local location	| Container location | Usage|
|:-------------:|:-------------:|:----------:|
|/srv/gitlab/data|/var/opt/gitlab|For storing application data|
|/srv/gitlab/logs	| /var/log/gitlab	| For storing logs|
|/srv/gitlab/config | /etc/gitlab	|For storing the GitLab configuration files|

You can fine tune these directories to meet your requirements.
Configure GitLab

This container uses the official Omnibus GitLab package, so all configuration is done in the unique configuration file/etc/gitlab/gitlab.rb.

To access GitLab's configuration file, you can start a shell session in the context of a running container. This will allow you to browse all directories and use your favorite text editor:

`sudo docker exec -it gitlab /bin/bash`

You can also just edit /etc/gitlab/gitlab.rb:

`sudo docker exec -it gitlab vi /etc/gitlab/gitlab.rb`

修改后输入如下重启gitlab生效

```bash
sudo docker restart gitlab
```

### 5. 备份与恢复

以下进入`container`备份与恢复，即首先敲入：`sudo docker exec -it gitlab /bin/bash`

#### 备份

```bash
gitlab-rake gitlab:backup:create
```

使用以上命令会在`/var/opt/gitlab/backups`目录下创建一个名称类似为`1393513186_gitlab_backup.tar`的压缩包，`1393513186`是备份时间

#### 恢复

```bash
gitlab-rake gitlab:backup:restore BACKUP=1393513186
``` 

恢复时间为`1393513186`的备份

```bash
# 重启gitlab
sudo docker restart gitlab
```

### 6. 卸载

- 停止gitlab: `gitlab-ctl stop`
- 卸载gitlab: `rpm -e gitlab-ce`
- 查看gitlab进程: `ps aux | grep gitlab`
- 杀掉第一个进程（带有好多.............的进程): kill -9 18777
- 删除所有包含gitlab文件: `find / -name gitlab | xargs rm -rf`

### 7. 参考
- [GitLab Docker images](http://docs.gitlab.com/omnibus/docker/)
- [Gitlab代码托管和自动化CI](http://blog.mukever.online/Gitlab%E4%BB%A3%E7%A0%81%E6%89%98%E7%AE%A1%E5%92%8C%E8%87%AA%E5%8A%A8%E5%8C%96CI/)
