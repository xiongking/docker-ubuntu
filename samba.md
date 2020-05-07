            $ sudo apt install samba samba-common 
		$ sudo nano /etc/samba/smb.conf

		[DISK]
		      path = /mnt/disk/download
		      available = yes
		      browseable = yes
		      public = yes
		      writable = yes

		$ sudo service smbd restart
