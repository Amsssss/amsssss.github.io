---
title: ssh保存服务器密码免登录
date: 2021-05-14 18:12:12
tags:
---

### 生成公私钥
```
ssh-keygen -t rsa
```
一直enter下保存id_rsa和id_rsa.pub在~/.ssh/目录下

### 新建config文件并配置以下信息
```
#AAAAA为服务器主机名
Host vultr_cloud
#写服务器ip地址
HostName xxx.xxx.xxx.xxx
#root为登陆用户名
User root
#主机端口，默认是22
Port 22
#自己生成的私钥的文件路径
IdentityFile C:\\Users\\ST\\.ssh\\id_rsa
```

### 登录到远程服务器在用户目录下新增.ssh/authorized_keys文件并添加id_rsa.pub文件

### 修改/etc/ssh/sshd_config文件
```
PubkeyAuthentication yes 
AuthorizedKeysFile .ssh/authorized_keys
```
保证上述配置没有被注释，AuthorizedKeysFile为上一步拷贝的公钥文件

### 至此本地的ssh就可以实现免密码登录
```
ssh vultr_cloud
```
直接使用config中配置的host登录