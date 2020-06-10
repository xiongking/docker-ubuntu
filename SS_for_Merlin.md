cd /tmp
wget --no-check-certificate https://raw.githubusercontent.com/hq450/fancyss_history_package/master/fancyss_arm/shadowsocks_4.2.2.tar.gz
mv shadowsocks_4.2.2.tar.gz shadowsocks.tar.gz
tar -zxvf /tmp/shadowsocks.tar.gz
chmod +x /tmp/shadowsocks/install.sh
sh /tmp/shadowsocks/install.sh
