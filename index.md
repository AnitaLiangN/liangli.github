<h1>通过yum升级gcc/g++至版本4.8.2</h1>
最近在坐一个日期处理的问题，需要安装sxtwl模块，但是gcc版本4.7死活也安装不上，最后测试到只能升级gcc版本到4.8才得以解决


[root@123 bin]# gcc -v
Using built-in specs.
Target: x86_64-redhat-linux
Thread model: posix
gcc version 4.4.7 20120313 (Red Hat 4.4.7-23) (GCC)
4.4.7版本的gcc是不识别c++11语法的。

下面是CentOS6.6将gcc升级至4.8.2的过程：

1. 安装仓库等

#安装仓库
wget http://people.centos.org/tru/devtools-2/devtools-2.repo
mv devtools-2.repo /etc/yum.repos.d

#升级gcc等
yum install devtoolset-2-gcc devtoolset-2-binutils devtoolset-2-gcc-c++
新版本的gcc安装在/opt/rh/devtoolset-2/root/ 下。

2. 配置：

#保存以前的gcc
mv /usr/bin/gcc /usr/bin/gcc-4.4.7
mv /usr/bin/g++ /usr/bin/g++-4.4.7
mv /usr/bin/c++ /usr/bin/c++-4.4.7

#为新版本的gcc创建软连接
ln -s /opt/rh/devtoolset-2/root/usr/bin/gcc /usr/bin/gcc
ln -s /opt/rh/devtoolset-2/root/usr/bin/c++ /usr/bin/c++
ln -s /opt/rh/devtoolset-2/root/usr/bin/g++ /usr/bin/g++
3. 检查：确认已经升级到4.8.2版本。

[root@bin]# gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/opt/rh/devtoolset-2/root/usr/libexec/gcc/x86_64-redhat-linux/4.8.2/lto-wrapper
Target: x86_64-redhat-linux
Configured with: ../configure --prefix=/opt/rh/devtoolset-2/root/usr --mandir=/opt/rh/devtoolset-2/root/usr/share/man --infodir=/opt/rh/devtoolset-2/root/usr/share/info --with-bugurl=http://bugzilla.redhat.com/bugzilla --enable-bootstrap --enable-shared --enable-threads=posix --enable-checking=release --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-gnu-unique-object --enable-linker-build-id --enable-languages=c,c++,fortran,lto --enable-plugin --with-linker-hash-style=gnu --enable-initfini-array --disable-libgcj --with-isl=/dev/shm/home/centos/rpm/BUILD/gcc-4.8.2-20140120/obj-x86_64-redhat-linux/isl-install --with-cloog=/dev/shm/home/centos/rpm/BUILD/gcc-4.8.2-20140120/obj-x86_64-redhat-linux/cloog-install --with-mpc=/dev/shm/home/centos/rpm/BUILD/gcc-4.8.2-20140120/obj-x86_64-redhat-linux/mpc-install --with-tune=generic --with-arch_32=i686 --build=x86_64-redhat-linux
Thread model: posix
gcc version 4.8.2 20140120 (Red Hat 4.8.2-15) (GCC)
<h1>php7.2 php.ini中的so模块放在哪里？</h1>
/etc/php.d/ 
查询swool版本：php --ri swoole | grep Version
升级swool：pecl upgrade swoole
<h1>php7.2安装gd库扩展</h1>
1）安装gd依赖库
2）安装gd库
在gd文件夹下phpize
./configure
make && make install
3)重新去php安装文件下去重新编译
./configure --prefix=/usr/local/php --with-config-file-path=/usr/local/php/etc --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-mysqli --with-pdo-mysql --with-iconv-dir --with-freetype-dir=/usr/local/freetype --with-jpeg-dir=/usr/local/jpeg  --with-png-dir=/usr/local/png --with-gd-dir=/usr/local/libgd --with-zlib --with-libxml-dir=/usr --enable-xml --disable-rpath --enable-bcmath --enable-shmop --enable-sysvsem --enable-inline-optimization --with-curl --enable-mbregex --enable-mbstring --with-openssl --with-mhash --enable-pcntl --enable-sockets --with-xmlrpc  enable-zip --enable-soap --without-pear --with-gettext --disable-fileinfo --enable-maintainer-zts --with-libdir=lib64


<h1>我的测试服务器安装了两个php，我用的是/usr/local/php/bin/php -m</h1>
