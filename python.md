如果出现ssl  connect error
cat /etc/yum.repos.d/nss.repo 
[updates]
name=centos-updates
baseurl=https://mirrors.aliyum.com/centos/6.9/os/x86_64
gpgcheck=0
yum repolist
yum update nss
安装pyenv参照如下两个地址，pyenv实际就是python版本管理器
https://github.com/pyenv/pyenv
https://github.com/pyenv/pyenv-installer
安装python的依赖环境
yum install -y gcc make patch gdbm-devel openssl-devel sqlite-devel readline-devel zlib-devel bzip2-devel
pyenv install --list 查看pyenv可以安装的包
pyenv  install 3.5.3  --verbose

