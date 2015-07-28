Vim 7.4
=======
CentOS 6.6 ships with vim 7.2.411. Vim 7.4 has adds some nice features, such as
markdown syntax highlighting and colored columns. Here is how to build from
source, installing binaries to /opt/vim74.

Build source with steps below, with the appropriate development packages. If
running into problems with getting GUI to compile, try
`yum groupinstall "Desktop Platform Development"`.
```
curl ftp://ftp.vim.org/pub/vim/unix/vim-7.4.tar.bz2 -o vim-74.tar.bz2
tar xvjf vim-74.tar.bz2
cd vim74
./configure --prefix=/opt/vim74 --with-compiledby="planteen" \
--with-features=huge --enable-pythoninterp --disable-tclinterp --with-x=yes \
--enable-xim --enable-multibyte --enable-gui=gnome2 --enable-cscope \
--enable-netbeans \
make
sudo make install
```

Add the following lines to your .bashrc:
    alias vim="/opt/vim74/bin/vim"
    alias gvim="/opt/vim74/bin/gvim"

