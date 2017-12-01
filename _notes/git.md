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

Switch to a tag/hash/branch:
git checkout tags/petalinux-v2013.10-final
git checkout 52ae18dc7cc4f093fbef75e0ee9fa2e21ae08f72
git checkout feature_branch

Creating a branch:
git checkout -b new_branch

Do work, commit, test, etc.

git push origin new_branch

If get error
error: The requested URL returned error: 403 Forbidden while accessing https://github.com/planteen/COSMOS.git/info/refs

In repo directory, edit .git/config
add planteen@ to url for remote "origin", like this:
url = https://planteen@github.com/planteen/COSMOS.git

Reverting a commit:
git revert a8802e052821bb985a54684f3d8be0f4decb4557

Adding all modified/new files in status:
git add .

Reverting a single file:
git checkout -- file
