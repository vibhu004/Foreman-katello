# 🇮‌🇳‌🇸‌🇹‌🇦‌🇱‌🇱‌🇮‌🇳‌🇬‌ 🇫‌🇴‌🇷‌🇪‌🇲‌🇦‌🇳‌ 2.4 🇸‌🇪‌🇷‌🇻‌🇪‌🇷‌ 🇼‌🇮‌🇹‌🇭‌ 🇰‌🇦‌🇹‌🇪‌🇱‌🇱‌🇴‌ 4.0 🇵‌🇱‌🇺‌🇬‌🇮‌🇳‌ 🇴‌🇳‌ 🇪‌🇳‌🇹‌🇪‌🇷‌🇵‌🇷‌🇮‌🇸‌🇪‌ 🇱‌🇮‌🇳‌🇺‌🇽‌

# CentOS 7
<details>
### 1.  Configuring Repositories

####Clear any metadata:
```bash
# yum clean all
```
####Install the foreman-release.rpm package:

```bash
# yum install https://yum.theforeman.org/releases/2.4/el7/x86_64/foreman-release.rpm
```

####Install the katello-repos-latest.rpm package:

```bash 
# yum install https://yum.theforeman.org/katello/4.0/katello/el7/x86_64/katello-repos-latest.rpm
```
####Install the puppet6-release-el-7.noarch.rpm package:

```bash
# yum localinstall https://yum.puppet.com/puppet6-release-el-7.noarch.rpm
```
####Install the epel-release package:
```bash
# yum install epel-release
```
####Install the centos-release-scl-rh package:
```bash
# yum install centos-release-scl-rh
```
