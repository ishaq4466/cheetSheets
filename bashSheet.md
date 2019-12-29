Table of Contents
===================
1. Users and Groups






1. Check the groups
```
cat /ect/groups
cat /ect/passwd
```

2. Allow the SSH to user
```
# modify the /etc/ssh/sshd_config
PasswordAuthentication yes # for enable passwd based authentication
X11Forwarding yes # for X11 forwarding

```

3. ssh -o "StrictHostKeyChecking no" user@ip

# Centos
```
yum repolist
yum install epel-release -y # installing epel repo
yum install sudo # if vi sudo not found
yum install net-tools openssh openssh-server -y

# https://www.howtogeek.com/307701/how-to-customize-and-colorize-your-bash-prompt/
set # geeting all variable
PS1="\[\033[01;32m\]\u@manager\[\033[00m\]\$ " # setting PS1 color full 
#32m for setting color green

yum -y install initscripts && yum clean all
```
# Maven installation on centos
```
# Installation for maven
# https://tecadmin.net/install-apache-maven-on-centos/

wget https://www-eu.apache.org/dist/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.tar.gz
tar -xvf apache-maven-3.6.2-bin.tar.gz 
ln -s apache-maven-3.6.2 maven

export M2_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}	
mvn -version

```

# Fedora

1. Commands related to repolist
```
/etc/yum.repos.d
sudo yum repolist
sudo dnf repolist
sudo dnf clean all
sudo rm -r /var/cache/dnf
sudo dnf upgrade

sudo groupadd docker

```
