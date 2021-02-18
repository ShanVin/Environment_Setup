
### 软件

    zookeeper-3.4.13.tar.gz

### 安装

	mkdir -p /usr/local/zookeeper
    tar -xvf zookeeper-3.4.13.tar.gz
	
	mkdir -p /usr/local/zookeeper/zookeeper-3.4.13/data

	cd /usr/local/zookeeper/zookeeper-3.4.13/conf
	cp zoo_sample.cfg zoo.cfg
	
	vim zoo.cfg
	
		dataDir=/tmp/zookeeper -> dataDir=/usr/local/zookeeper/zookeeper-3.4.13/data
		server.1=192.168.47.128:2888:3888
		server.2=192.168.47.129:2888:3888
		server.3=192.168.47.130:2888:3888
		
	cd /usr/local/zookeeper/zookeeper-3.4.13/data
	echo 1 > myid

    firewall-cmd --zone=public --add-port=2181/tcp --permanent
	firewall-cmd --zone=public --add-port=2888/tcp --permanent
	firewall-cmd --zone=public --add-port=3888/tcp --permanent
    firewall-cmd --reload

	cd /usr/local/zookeeper/zookeeper-3.4.13/bin
	./zkServer.sh start
	./zkServer.sh stop
	./zkServer.sh restart
	./zkServer.sh status
