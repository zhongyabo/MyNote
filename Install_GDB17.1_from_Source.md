## 1.Prerequisites
```bash
yum groupinstall -y "Development Tools"
yum install -y ncurses-devel texinfo python3-devel libmpc-devel gmp-devel mpfr-devel expat-devel
```
## 2.Download and Extract
```bash
wget https://ftp.gnu.org/gnu/gdb/gdb-17.1.tar.xz
tar -xvf gdb-17.1.tar.xz
cd gdb-17.1
```
## 3.Configure with CentOS 7 Fixes
```bash
./configure \
--prefix=/usr/local/gdb-17.1 \
--disable-tui \
--enable-static \
--disable-shared LDFLAGS="-static-libstdc++ -static-libgcc"
```
## 4.Build and Install
```bash
make -j$(nproc)
make install
```
## 5.Setup PATH
```bash
echo 'export PATH=/usr/local/gdb-17.1/bin:$PATH' >> /etc/profile
source /etc/profile
```