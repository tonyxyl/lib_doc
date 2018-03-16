**ubuntu操作手册**

**挂载windows共享目录**

> 先在virtualbox上设置固定分配的共享文件夹,共享名为share(举例), 
然后在ubuntu上`sudo mkdir /mnt/share`, `mount -t vboxsf share /mnt/share/`,
如果提示文件系统有问题, 记得安装增强工具.
然后去访问共享目录, 如果提示权限不够, 执行命令`sudo adduser xxx vboxsf`, 重启即可.

**换源**

> 先备份`/etc/apt/sources.list`,然后替换成其他源头，比如阿里源.

```
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
##测试版源
deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
# 源码
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
##测试版源
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
# Canonical 合作伙伴和附加
deb http://archive.canonical.com/ubuntu/ xenial partner
deb http://extras.ubuntu.com/ubuntu/ xenial main
```

**安装chrome**
```
sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-chrome-stable
/usr/bin/google-chrome-stable
```

**安装mysql**
```
sudo apt-get update
sudo apt-get install mysql-server
sudo mysql_secure_installation 

systemctl status mysql.service
sudo systemctl mysql start
mysqladmin -p -u root version
```

**安装postgresql**
```
sudo apt-get install postgresql

sudo -u postgres psql  #以postgres用户进入交互

systemctl status postgresql.service
sudo systemctl postgresql start

#配置文件
/etc/postgresql/9.5/main.postgresql.conf
#修改配置文件允许远程链接
sudo gedit /etc/postgresql/9.5/main/postgresql.conf
listen_addresses = '*'
sudo gedit /etc/postgresql/9.5/main/pg_hba.conf
host all all 0.0.0.0 0.0.0.0 md5
```

**安装php**
```
sudo apt-get install software-properties-common  
sudo LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php  
sudo apt-get update
apt-cache search php7.1
sudo apt-get -y install php7.1
sudo apt-get -y install php7.1-mysql  
sudo apt-get -y install php7.1-fpm
sudo apt-get -y install php7.1-curl php7.1-xml php7.1-mcrypt php7.1-json php7.1-gd php7.1-mbstring  
```
****