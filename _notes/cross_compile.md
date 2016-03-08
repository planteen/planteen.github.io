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

openssh-7.1p1.tar.gz:
./configure --host=arm-linux --with-libs --with-zlib=$HOME/cross_compile/zlib_arm --with-ssl-dir=$HOME/cross_compile/openssl_arm --disable-etc-default-login CC=arm-xilinx-linux-gnueabi-gcc AR=arm-xilinx-linux-gnueabi-ar

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
