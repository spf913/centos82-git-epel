# centos82-git-epel

```bash
################### Repo  ############ Add start #############
Docker
Kubernetes
EPEL
Mesosphere


# Docker Repo ADD
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum-config-manager  --add-repo  http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo



# Kubernetes Repo ADD
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo > /dev/null
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
       https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF




# Adding Repo for EPEL, mesosphere
# Deploying Stack for SPF913 (ADDING REPO FOR MESOS CLUSTER)
cd /root
yum install -y git
git clone https://github.com/spf913/centos82-git-epel.git
# First Install epel and mesosphere repo
cd /root/centos82-git-epel
yum install -y --cacheonly --disablerepo=* /root/centos82-git-epel/epel/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/centos82-git-epel/mesosphere/*.rpm
# update yum cache
yum makecache

################### Repo  ############ Add Finish #############



################### package download  ############ start #############


yumdownloader --assumeyes --destdir=/root/spf913-depend/se --resolve container-selinux && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/yum --resolve yum-utils && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/ip --resolve iptables && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/cgroup --resolve libcgroup && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/libtool --resolve libtool-ltdl && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/lvm2 --resolve lvm2 && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/unzip --resolve unzip && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/wget --resolve wget && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/iproute --resolve iproute-tc && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/devicemapper --resolve device-mapper-persistent-data && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/ebtables --resolve ebtables && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/vim --resolve vim && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/net-tools --resolve net-tools && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/chrony --resolve chrony && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/ntpstat --resolve ntpstat && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/keepalived --resolve keepalived && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/nginx --resolve nginx && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/policycoreutils-python-utils --resolve policycoreutils-python-utils && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/kernel-headers --resolve kernel-headers && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/kernel-devel --resolve kernel-devel && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/libssl --resolve libssl.so.10 && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/compat --resolve compat-openssl10 && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/mesos --resolve mesos && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/marathon --resolve marathon-1.4.13-1.0.683.el7.x86_64 && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/zookeeper --resolve mesosphere-zookeeper && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/unzip --resolve unzip && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/java --resolve java && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/subversion --resolve subversion && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/cyrus --resolve cyrus-sasl-md5 && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/libevent --resolve libevent-devel && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/dnf --resolve dnf-plugins-core && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/gcc --resolve gcc && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/socat --resolve socat && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/conntrack --resolve conntrack && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/libcgroup --resolve libcgroup && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/container-selinux --resolve container-selinux && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/iptables --resolve iptables && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/nftables --resolve nftables && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/docker1806 --resolve docker-ce-18.06.0.ce-3.el7 && \
yumdownloader --assumeyes --destdir=/root/spf913-depend/kubernetesv1.15.0 --resolve kubeadm-1.15.0 kubelet-1.15.0 kubectl-1.15.0




################### package download  ############ finish #############


########################### SPF913 DEPLOYING STACK CORE #################
cd /root
git clone https://github.com/spf913/spf913-depend.git
cd spf913-depend
tar -zxvf marathon.tar.gz && \
tar -zxvf mesos.tar.gz


yum install -y --cacheonly --disablerepo=* /root/spf913-depend/se/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/yum/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/ip/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/cgroup/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/libtool/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/lvm2/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/unzip/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/wget/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/iproute/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/devicemapper/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/ebtables/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/vim/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/net-tools/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/chrony/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/ntpstat/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/keepalived/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/nginx/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/policycoreutils-python-utils/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/kernel-headers/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/kernel-devel/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/libssl/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/compat/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/mesos/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/marathon/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/zookeeper/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/unzip/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/java/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/subversion/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/cyrus/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/libevent/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/dnf/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/gcc/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/socat/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/conntrack/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/libcgroup/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/container-selinux/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/iptables/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/nftables/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/docker1806/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/spf913-depend/kubernetesv1.15.0/*.rpm


















##########################  SPF913 CORE DEPLOYED            ##################
```
