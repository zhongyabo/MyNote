# NOTE
before install gcc15.2 ,make sure you gcc version is not too low(>9)

## Prerequisites
```bash
sudo yum groupinstall "Development Tools"
sudo yum install gmp-devel mpfr-devel libmpc-devel texinfo bison flex
```
## Download Source
```bash
wget https://ftp.gnu.org/gnu/gcc/gcc-15.2.0/gcc-15.2.0.tar.xz
tar -xf gcc-15.2.0.tar.xz -C /usr/src/gcc-15.2.0
```

## Requisites
下载GMP、MPFR和MPC依赖
```bash
cd /usr/src/gcc-15.2.0
./contrib/download_prerequisites
```


## Make 
### configure
```bash
mkdir build && cd build
../gcc-15.2.0/configure \
--enable-languages=c,c++ \
--disable-multilib \
--prefix=/usr/local/gcc-15.2
```

### build
编译时间需要几个小时
```bash
make -j$(nproc)
```

### install
```bash
make install
```

##set path
```bash
echo 'export PATH=/usr/local/gcc-15.2/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```