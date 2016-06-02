# Download entire site with wget
-r recursive
-np don't go to parent dirs
-k make links point to local files
wget -r -np -k http://site.com/dir
