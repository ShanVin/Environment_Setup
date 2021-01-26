
### 软件

    VMware-workstation-full-16.0.0-16894299.exe
    CentOS-8.2.2004-x86_64-dvd1.iso

### 分区（40G）

    /           31.5G
    /boot       500M
    /var        4G
    biosboot    2M
    swap        4G

### 用户

    root/root

### IP

    cp /etc/sysconfig/network-scripts/ifcfg-ens33 /etc/sysconfig/network-scripts/ifcfg-ens33.bak
    vim /etc/sysconfig/network-scripts/ifcfg-ens33
        BOOTPROTO="static"
        PREFIX=24
        IPADDR=192.168.220.128
        GATEWAY=192.168.220.2
        NETMASK=255.255.255.0
	cp /etc/resolv.conf /etc/resolv.conf.bak
    vim /etc/resolv.conf
        nameserver 114.114.114.114
        nameserver 8.8.8.8

### 关闭SELinux

    cp /etc/sysconfig/selinux /etc/sysconfig/selinux.bak
    vim /etc/sysconfig/selinux
        SELINUX=enforcing -> SELINUX=disabled

### 阿里源

    mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
    wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-8.repo
    sed -i -e '/mirrors.cloud.aliyuncs.com/d' -e '/mirrors.aliyuncs.com/d' /etc/yum.repos.d/CentOS-Base.repo
    yum makecache
