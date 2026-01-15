## 1.备份原有YUM源文件
```bash
sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
```

## 2.下载国内镜像源配置文件
- 阿里云镜像源
```bash
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```
- 清华大学镜像源
```bash
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.tuna.tsinghua.edu.cn/repo/Centos-7.repo
```
- 网易镜像源
```bash
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo
```
## 3.清理缓存并生成新缓存
```bash
sudo yum clean all
sudo yum makecache
```
## 4.验证新源是否生效
```bash
sudo yum repolist
```
>输出中应包含所选镜像源的地址，例如 mirrors.aliyun.com