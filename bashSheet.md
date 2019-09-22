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




--env JAVA_OPTS="-Xmx256m -XX:MaxPermSize=512m" jenkins
docker run -itd -v data:/var/jenkins_home/ -p 8080:8080 -p 50000:50000 --name jenkins --env JAVA_OPTS="-Xms256 -Xmx256m -Djenkins.install.runSetupWizard=false" jenkinsci/blueocean

docker run -itd -p 3000:3000 --name gitea gitea/gitea
 --mount type=bind,source="$(pwd)"/target,target=/app

all jenkins JAVA_ARGS parameters are stored in /ect/default/jenkins
docker run -itd --mount type=bind,source="data",target=/var/jenkins_home/ -p 8080:8080 -p 50000:50000 --name jenkins --env JAVA_OPTS="-Djenkins.install.runSetupWizard=false" jenkinimg

docker cp mycontainer:/foo.txt foo.txt
docker cp src/. mycontainer:/targe



54023d7a1d747112785826016c975fec6722f71a
