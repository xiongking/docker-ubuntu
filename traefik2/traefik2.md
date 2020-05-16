## 准备traefik安装目录和文件 ##
```
cd ~/docker   #创建用户docker目录
mkdir traefik   #创建docker下的traefik目录
mkdir traefik/acme   #创建traefik下的acme目录
touch ~/docker/traefik/acme/acme.json   #创建acme.json文件，用于储存域名证书
chmod 600 ~/docker/traefik/acme/acme.json   #设置acme.json权限
mdkir ~/docker/traefik/rules  #创建rules文件夹，用于储存traefik配置规则
mkdir ~/docker/yml   #创建yml文件夹，用于储存docker配置规则
```

## 配置/etc/enviroment 参考如下##

```
$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"

PUID=1000
PGID=998
TZ="Asia/Shanghai"

DOMAINNAME="xiongnas.top"

DOWNLOADDIR="/mnt/disk/download"
DISKDIR="mnt/disk/nextcloud"

USERDIR="/home/xiongjin"
DOCKERDIR="/home/xiongjin/docker"

CLOUDFLARE_EMAIL=****************
CLOUDFLARE_API_KEY=******************
CLOUDFLARE_DNS_KEY=**********
CLOUDFLARE_ZoneID=****************

CF_Email=**************
CF_Key=*******************

MYSQL_ROOT_PASSWORD="***********"
FLEXGET_PASSWORD="***************"

GOOGLE_CLIENT_ID=******************
GOOGLE_CLIENT_SECRET=***************

GOOGLE_OAUTH_SECRET=************
MY_EMAIL=*****************
````

## docker-compose  ##

$ docker-compose -f ~/docker/yml/traefik.yml up -d
