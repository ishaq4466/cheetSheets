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