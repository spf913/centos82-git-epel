# centos82-git-epel


Docker
Kubernetes
EPEL
Mesosphere

```bash
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
curl -L https://github.com/spf913/centos82-git-epel/raw/main/git/git-2.18.4-2.el8_2.x86_64.rpm -o git-2.18.4-2.el8_2.x86_64.rpm
yum install -y --cacheonly --disablerepo=* git-2.18.4-2.el8_2.x86_64.rpm
git clone https://github.com/spf913/centos82-git-epel.git
# First Install epel and mesosphere repo
cd /root/centos82-git-epel
yum install -y --cacheonly --disablerepo=* /root/centos82-git-epel/epel/*.rpm && \
yum install -y --cacheonly --disablerepo=* /root/centos82-git-epel/mesosphere/*.rpm
# update yum cache
yum makecache
```
