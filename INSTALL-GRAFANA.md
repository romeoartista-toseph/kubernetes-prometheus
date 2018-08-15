# Grafana Installation

##### What you need:
- VirtualBox
- CentOS 7 ISO
---
##### Creating VirtualBox Host:
- **Name:** grafana
- **Type:** Linux
- **Version:** Red Hat (64-bit)
- **Memory size:** 1024 MB
- **Hard disk:** Create a virtual hard disk now
- **Hard disk file type:** VDI (VirtualBox Disk Image)
- **Storage on physical hard disk:** Dynamically allocated
- **File location and size:** 16.00 GB
- **Storage:**
  - **Controller: IDE** (CentOS 7 ISO Image File)
- **Network:**
  - **Adapter 2:**
    - **Attached to:** Host-only Adapter
---
##### Installing Grafana to VirtualBox Host:
Install Grafana dependencies:
```
$ sudo yum -y install initscripts fontconfig freetype* urw-fonts
```

Create new file in `/etc/yum.repos.d/grafana.repo` and save it as `grafana.repo`:
```
[grafana]
name=grafana
baseurl=https://packagecloud.io/grafana/stable/el/7/$basearch
repo_gpgcheck=1
enabled=1
gpgcheck=1
gpgkey=https://packagecloud.io/gpg.key https://grafanarel.s3.amazonaws.com/RPM-GPG-KEY-grafana
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt
```
Update yum package repositories:
```
$ sudo yum update
```
Install Grafana package:
```
$ sudo yum install grafana
```
---
##### Post Installation Setup:
Start Grafana service:
```
$ sudo service grafana-server start
```

Let Grafana start upon booting:
```
# Via init.d service
$ sudo /sbin/chkconfig --add grafana-server

# Via systemd
$ systemctl daemon-reload
$ sudo systemctl enable grafana-server.service
$ systemctl start grafana-server
$ systemctl status grafana-server
```

Open VirtualBox Host in Grafana's TCP Port:
```
$ sudo firewall-cmd --permanent --add-port=3000/tcp
$ sudo firewall-cmd --reload
```

