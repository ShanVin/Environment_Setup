
### 软件

    mysql-8.0.21-1.el8.x86_64.rpm-bundle.tar

### 安装

    tar -xvf mysql-8.0.21-1.el8.x86_64.rpm-bundle.tar

    rpm -ivh mysql-community-common-8.0.21-1.el8.x86_64.rpm
    rpm -ivh mysql-community-libs-8.0.21-1.el8.x86_64.rpm
    rpm -ivh mysql-community-client-8.0.21-1.el8.x86_64.rpm
    rpm -ivh mysql-community-server-8.0.21-1.el8.x86_64.rpm

    cp /usr/lib/tmpfiles.d/mysql.conf /usr/lib/tmpfiles.d/mysql.conf.bak
    vim /usr/lib/tmpfiles.d/mysql.conf
        /var/run/mysqld -> /run/mysqld

    cp /usr/lib/tmpfiles.d/subscription-manager.conf /usr/lib/tmpfiles.d/subscription-manager.conf.bak
    vim /usr/lib/tmpfiles.d/subscription-manager.conf
        /var/run/rhsm -> /run/rhsm

    cp /etc/my.cnf /etc/my.cnf.bak
    vim /etc/my.cnf
        user=mysql

    reboot

    ps -ef | grep mysql
    cat /etc/group | grep mysql
    cat /etc/passwd | grep mysql
    mysqladmin --version

    systemctl start mysqld
    systemctl stop mysqld
    systemctl restart mysqld
    systemctl status mysqld

    cat /var/log/mysqld.log | grep password
    mysql -uroot -p
        alter user "root"@"localhost" identified by 'MySQL3306!';
        flush privileges;

    firewall-cmd --zone=public --add-port=3306/tcp --permanent
    firewall-cmd --reload
