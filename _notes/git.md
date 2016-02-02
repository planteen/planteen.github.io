Cloning:
git clone https://github.com/planteen/mine.git

Syncing a fork with upstream:
(only do once, check with git remote -v)
git remote add upstream https://github.com/orig/orig.git

git fetch upstream
git checkout master
git merge upstream/master
git push origin master

Clone a branch:
git clone -b xlnx_3.14 https://github.com/Xilinx/linux-xlnx.git

Switch to a tag:
git checkout tags/petalinux-v2013.10-final

Switch to a hash
git checkout 52ae18dc7cc4f093fbef75e0ee9fa2e21ae08f72
