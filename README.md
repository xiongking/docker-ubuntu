# docker for ubuntu20.04 #

## 修改ip ##

    $sudo nano /etc/netplan/00-installer-config.yaml
    network:
      ethernets:
        ens16:
          dhcp4: no
          addresses: [10.0.1.200/24]
          optional: true
          gateway4: 10.0.1.1
          nameservers:
            addresses: [10.0.0.1,223.5.5.5]
        ens17:
          dhcp4: no
          addresses: [10.0.0.2/24]
          optional: true
          nameservers:
            addresses: [10.0.0.1,223.5.5.5]
      version: 2

## 安装Docker ##
docker及docker-compose安装

配置安装环境
`sudo apt install apt-transport-https ca-certificates curl software-properties-common`

添加阿里云的docker GPG密钥
`curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -`

#官方的docker GPG密钥 
#curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

添加阿里镜像源
`sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"`

官方镜像源
#sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

更新源
`sudo apt update`

查看有哪些版本
`apt-cache madison docker-ce`

安装最新版/指定版本
#安装最新版
`sudo apt install -y docker-ce`
#安装5:19.03.6~3-0~ubuntu-bionic版
sudo apt install -y docker-ce=5:19.03.6~3-0~ubuntu-bionic

配置docker镜像加速源
`$ sudo tee /etc/docker/daemon.json <<-'EOF'`
`heredocd> {`
`heredocd>        "registry-mirrors": ["https://sn85pe6o.mirror.aliyuncs.com"]`
`heredocd> }`
`heredocd> EOF`
`{`
 `"registry-mirrors": ["https://sn85pe6o.mirror.aliyuncs.com"]`
`}`

运行hello-world
`sudo docker run hello-world`

查看docker-compose版本：https://github.com/docker/compose/releases

安装docker-compose脚本
`sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-uname -s-uname -m -o /usr/local/bin/docker-compose`

设置运行权限
`sudo chmod +x /usr/local/bin/docker-compose`

查看版本
`docker-compose --version`

添加用户到docker组
`sudo usermod -aG docker ${USER}`

查看用户和组
`cat /etc/passwd`
`cat /etc/group`

`$ id`
`uid=1000(xiongjin) gid=1000(xiongjin) groups=1000(xiongjin),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),131(lxd),132(sambashare),998(docker)`

$ groups xiongjin
`xiongjin : xiongjin adm cdrom sudo dip plugdev lpadmin lxd sambashare docker`

设置docker目录权限
`sudo chmod -R 775 ~/docker`

重启docker
`sudo systemctl restart docker`
