
# INSTALLING FOREMAN 2.4 SERVER WITH KATELLO 4.0 PLUGIN ON ENTERPRISE LINUX

### Quick Read Before jumping to installation 

* The Foreman installer is a collection of Puppet modules that installs everything required for a full working Foreman setup.
* Before you install Foreman, apply all operating system updates if possible.
* Install Foreman server on a freshly provisined system.
* The installation will require 8GB of memory and 2 CPU at minimum to work properly,
* It's not advisable to follow the steps below on an existing system, since the installer will affect the configuration of several components.
* This guide is for CentOS 7 based machine and # represents root user.
<br>

# CentOS 7

<details>
<summary> <h3> 1.  Configuring Repositories </h3> </summary>
<br>
<h4> Clear any metadata: </h4>

```bash
# yum clean all
```

<h4>Install the foreman-release.rpm package: </h4>

```bash
# yum install https://yum.theforeman.org/releases/2.4/el7/x86_64/foreman-release.rpm
```

<h4>Install the katello-repos-latest.rpm package: </h4>

```bash 
# yum install https://yum.theforeman.org/katello/4.0/katello/el7/x86_64/katello-repos-latest.rpm
```

<h4>Install the puppet6-release-el-7.noarch.rpm package:</h4>

```bash
# yum localinstall https://yum.puppet.com/puppet6-release-el-7.noarch.rpm
```

<h4>Install the epel-release package:</h4>

```bash
# yum install epel-release
```
<h4>Install the centos-release-scl-rh package:</h4>

```bash
# yum install centos-release-scl-rh
```
</details>

<details>
<summary> <h3>2. Installing Foreman server Packages</h3> </summary>
<br>
<h4>Update all packages:</h4>

```bash
# yum update
```
<h4>Install foreman-installer-katello

```bash
#yum install foreman-installer-katello
```
</details>

<details>
<summary> <h3> Running the Installer </h3></summary>
<br>
<h4>To run the installer, execute:</h4>

```bash
#foreman-installer --scenario katello
```

</details>
