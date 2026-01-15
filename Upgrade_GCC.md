## 1.安装centos-release-scl

### 1.1修改CentOS-SCLo-scl.repo
```bash
vi /etc/yum.repos.d/CentOS-SCLo-scl.repo
```
```ini
[centos-sclo-sclo]
name=CentOS-7 - SCLo sclo
baseurl=https://mirrors.aliyun.com/centos/7/sclo/x86_64/sclo/
# mirrorlist=http://mirrorlist.centos.org?arch=$basearch&release=7&repo=sclo-sclo
gpgcheck=0
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-SCLo
```
###　1.２修改CentOS-SCLo-scl-rh.repo
```bash
vi /etc/yum.repos.d/CentOS-SCLo-scl-rh.repo
```
```ini
[centos-sclo-rh]
name=CentOS-7 - SCLo rh
baseurl=https://mirrors.aliyun.com/centos/7/sclo/x86_64/rh/
# mirrorlist=http://mirrorlist.centos.org?arch=$basearch&release=7&repo=sclo-rh
gpgcheck=0
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-SCLo
```
### 1.3刷新缓存
```bash
yum repolist
yum clean all
yum makecache
```
## 2 安装devtoolset
> 注意事项，如果想安装7.版本的，就改成devtoolset-7-gcc，以此类推

```bash
sudo yum install devtoolset-8-gcc*
```
## 3.激活对应的devtoolset
> 这条激活命令只对本次会话有效

```bash
scl enable devtoolset-8 bash
```
>切换版本

```bash
source /opt/rh/devtoolset-8/enable
```

## 4.替换GCC
```bash
mv /usr/bin/gcc /usr/bin/gcc-4.8.5
ln -s /opt/rh/devtoolset-8/root/bin/gcc /usr/bin/gcc
mv /usr/bin/g++ /usr/bin/g++-4.8.5
ln -s /opt/rh/devtoolset-8/root/bin/g++ /usr/bin/g++
gcc --version
g++ --version
```