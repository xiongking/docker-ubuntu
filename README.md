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


		$ sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
		[sudo] password for xiongjin: 
		Reading package lists... Done
		Building dependency tree       
		Reading state information... Done
		ca-certificates is already the newest version (20190110ubuntu1).
		ca-certificates set to manually installed.
		curl is already the newest version (7.68.0-1ubuntu2).
		curl set to manually installed.
		software-properties-common is already the newest version (0.98.9).
		software-properties-common set to manually installed.
		The following NEW packages will be installed:
		  apt-transport-https gnupg-agent
		0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
		Need to get 6940 B of archives.
		After this operation, 206 kB of additional disk space will be used.
		Do you want to continue? [Y/n] y
		Get:1 http://cn.archive.ubuntu.com/ubuntu focal/universe amd64 apt-transport-https all 2.0.2 [1704 B]
		Get:2 http://cn.archive.ubuntu.com/ubuntu focal/universe amd64 gnupg-agent all 2.2.19-3ubuntu2 [5236 B]
		Fetched 6940 B in 3s (2156 B/s)  
		Selecting previously unselected package apt-transport-https.
		(Reading database ... 70818 files and directories currently installed.)
		Preparing to unpack .../apt-transport-https_2.0.2_all.deb ...
		Unpacking apt-transport-https (2.0.2) ...
		Selecting previously unselected package gnupg-agent.
		Preparing to unpack .../gnupg-agent_2.2.19-3ubuntu2_all.deb ...
		Unpacking gnupg-agent (2.2.19-3ubuntu2) ...
		Setting up apt-transport-https (2.0.2) ...
		Setting up gnupg-agent (2.2.19-3ubuntu2) ...
		$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
		OK
		$ sudo apt-key fingerprint 0EBFCD88
		pub   rsa4096 2017-02-22 [SCEA]
		      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
		uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
		sub   rsa4096 2017-02-22 [S]

		$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
		Reading package lists... Done
		Building dependency tree       
		Reading state information... Done
		ca-certificates is already the newest version (20190110ubuntu1).
		curl is already the newest version (7.68.0-1ubuntu2).
		software-properties-common is already the newest version (0.98.9).
		apt-transport-https is already the newest version (2.0.2).
		0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
		$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu eoan test"
		Hit:1 http://cn.archive.ubuntu.com/ubuntu focal InRelease                                                                        
		Get:2 http://cn.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]                                                       
		Get:3 https://download.docker.com/linux/ubuntu eoan InRelease [43.0 kB]
		Get:4 http://cn.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
		Get:5 http://cn.archive.ubuntu.com/ubuntu focal-security InRelease [107 kB]
		Get:6 https://download.docker.com/linux/ubuntu eoan/test amd64 Packages [4064 B]
		Fetched 359 kB in 5s (79.2 kB/s)
		Reading package lists... Done
		$ sudo apt install docker-ce docker-ce-cli containerd.io
		Reading package lists... Done
		Building dependency tree       
		Reading state information... Done
		The following additional packages will be installed:
		  aufs-tools cgroupfs-mount pigz
		The following NEW packages will be installed:
		  aufs-tools cgroupfs-mount containerd.io docker-ce docker-ce-cli pigz
		0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
		Need to get 85.7 MB of archives.
		After this operation, 385 MB of additional disk space will be used.
		Do you want to continue? [Y/n] y
		Get:1 https://download.docker.com/linux/ubuntu eoan/test amd64 containerd.io amd64 1.2.13-1 [20.1 MB]
		Get:2 http://cn.archive.ubuntu.com/ubuntu focal/universe amd64 pigz amd64 2.4-1 [57.4 kB]    
		Get:3 https://download.docker.com/linux/ubuntu eoan/test amd64 docker-ce-cli amd64 5:19.03.8~3-0~ubuntu-eoan [42.6 MB]
		Get:4 http://cn.archive.ubuntu.com/ubuntu focal/universe amd64 aufs-tools amd64 1:4.14+20190211-1ubuntu1 [104 kB]
		Get:5 http://cn.archive.ubuntu.com/ubuntu focal/universe amd64 cgroupfs-mount all 1.4 [6320 B]
		Get:6 https://download.docker.com/linux/ubuntu eoan/test amd64 docker-ce amd64 5:19.03.8~3-0~ubuntu-eoan [22.9 MB]
		Fetched 85.7 MB in 6s (14.8 MB/s)    
		Selecting previously unselected package pigz.
		(Reading database ... 70826 files and directories currently installed.)
		Preparing to unpack .../0-pigz_2.4-1_amd64.deb ...
		Unpacking pigz (2.4-1) ...
		Selecting previously unselected package aufs-tools.
		Preparing to unpack .../1-aufs-tools_1%3a4.14+20190211-1ubuntu1_amd64.deb ...
		Unpacking aufs-tools (1:4.14+20190211-1ubuntu1) ...
		Selecting previously unselected package cgroupfs-mount.
		Preparing to unpack .../2-cgroupfs-mount_1.4_all.deb ...
		Unpacking cgroupfs-mount (1.4) ...
		Selecting previously unselected package containerd.io.
		Preparing to unpack .../3-containerd.io_1.2.13-1_amd64.deb ...
		Unpacking containerd.io (1.2.13-1) ...
		Selecting previously unselected package docker-ce-cli.
		Preparing to unpack .../4-docker-ce-cli_5%3a19.03.8~3-0~ubuntu-eoan_amd64.deb ...
		Unpacking docker-ce-cli (5:19.03.8~3-0~ubuntu-eoan) ...
		Selecting previously unselected package docker-ce.
		Preparing to unpack .../5-docker-ce_5%3a19.03.8~3-0~ubuntu-eoan_amd64.deb ...
		Unpacking docker-ce (5:19.03.8~3-0~ubuntu-eoan) ...
		Setting up aufs-tools (1:4.14+20190211-1ubuntu1) ...
		Setting up containerd.io (1.2.13-1) ...
		Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
		Setting up docker-ce-cli (5:19.03.8~3-0~ubuntu-eoan) ...
		Setting up pigz (2.4-1) ...
		Setting up cgroupfs-mount (1.4) ...
		Setting up docker-ce (5:19.03.8~3-0~ubuntu-eoan) ...
		Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
		Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
		Processing triggers for systemd (245.4-4ubuntu3) ...
		Processing triggers for man-db (2.9.1-1) ...
		Processing triggers for libc-bin (2.31-0ubuntu9) ...
		$ sudo curl -L https://github.com/docker/compose/releases/download/1.25.5/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
		  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
		                                 Dload  Upload   Total   Spent    Left  Speed
		100   638  100   638    0     0    801      0 --:--:-- --:--:-- --:--:--   800
		100 16.7M  100 16.7M    0     0  3617k      0  0:00:04  0:00:04 --:--:-- 5629k
		$ sudo usermod -aG docker ${USER}

