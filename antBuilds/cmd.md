# ANT installation pon ubuntu
apt-get install ant junit
yum install ant ant-junit

# ANT CMD's 
ant -f otherbuild.xml // for building other than build.xml
ant -Dproperty=name -build otherbuild.xml // setting the property value through cmd
ant -find otherbuild.xml // finding the otherbuild.xml and start building



