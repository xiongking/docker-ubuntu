# docker for ubuntu20.04

## 修改ip
$sudo nano /etc/netplan/00-installer-config.yaml

# This is the network config written by 'subiquity'
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

