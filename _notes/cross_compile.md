libssh2:
./configure --host arm-xilinx-linux-gnueabi

http://stackoverflow.com/questions/11841919/cross-compile-openssh-for-arm


ppp-ppp-2.4.7:
./configure --host arm-xilinx-linux-gnueabi
make CC=arm-xilinx-linux-gnueabi-gcc
mkdir ~/ppp_arm
make install DESTDIR=~/cross_compile/ppp_arm INSTALL="install --strip-program=arm-xilinx-linux-gnueabi-strip"

zlib-1.2.8:
export CC=arm-xilinx-linux-gnueabi-gcc
./configure --prefix=~/cross_compile/zlib_arm
make
make install

openssl-1.0.2d:
export cross=arm-xilinx-linux-gnueabi-
./Configure dist --prefix=~/cross_compile/openssl_arm -fPIC
make CC="${cross}gcc" AR="${cross}ar r" RANLIB="${cross}ranlib"
make install


try:
no-ssl2 no-ssl3 no-zlib no-comp no-dtls no-threads no-psk no-srp -DOPENSSL_USE_IPV6=0 no-shared

need makedepend, aka imake
NOTE: yum install makedepend

export cross=arm-xilinx-linux-gnueabi-
./Configure dist --prefix=~/cross_compile/openssl_arm_small -fPIC no-ssl2 no-ssl3 no-zlib no-comp no-dtls no-threads no-psk no-srp -DOPENSSL_USE_IPV6=0 no-shared
make depend
make CC="${cross}gcc" AR="${cross}ar r" RANLIB="${cross}ranlib"
make install

reducing size:
https://wiki.openssl.org/index.php/Compilation_and_Installation

 So, here are the results: I added a big bunch of no-includes: no-asm no-ssl2 no-zlib no-rc2 no-idea no-des no-bf no-cast no-md2 no-mdc2 no-dh no-err no-ripemd no-rc5 no-camellia no-seed no-krb5. The end result is the size is down my 200Kb. Original size = 650Kb, with full OpenSSL = 1416Kb, with the exclusion 1257. I am now looking at other implementation. – JP. Mar 24 '11 at 17:19 

openssh-7.1p1.tar.gz:
./configure --host=arm-linux --with-libs --with-zlib=$HOME/cross_compile/zlib_arm --with-ssl-dir=$HOME/cross_compile/openssl_arm --disable-etc-default-login CC=arm-xilinx-linux-gnueabi-gcc AR=arm-xilinx-linux-gnueabi-ar

reduce size by calling strip after build on ssh and sftp!

NEGLIGIBLE SIZE DIFFERENCE:
./configure --host=arm-linux --with-libs --with-zlib=$HOME/cross_compile/zlib_arm --with-ssl-dir=$HOME/cross_compile/openssl_arm_small --disable-etc-default-login CC=arm-xilinx-linux-gnueabi-gcc AR=arm-xilinx-linux-gnueabi-ar --without-x 


spi-tools:
git clone https://github.com/cpb-/spi-tools.git
autoreconf -fim
./configure --host=arm-linux CC=arm-xilinx-linux-gnueabi-gcc
make

Outputs spi-config and spi-pipe in src

sqlite:
To create smaller amalgamation, download source and edit Makefile, e.g.:
OPTS += -DSQLITE_OMIT_TRIGGER=1
OPTS += -DSQLITE_OMIT_WAL=1
OPTS += -DSQLITE_OMIT_AUTOVACUUM=1
OPTS += -DSQLITE_OMIT_UTF16=1
OPTS += -DSQLITE_OMIT_EXPLAIN=1
OPTS += -DSQLITE_OMIT_LOAD_EXTENSION=1

Then make sqlite3.c
