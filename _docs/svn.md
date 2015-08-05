Subversion
==========
Git may be nicer than Subversion, but in my experience, some teams do not use
SVN correctly. If everyone on your team is developing using working copies off
trunk, you are not using SVN to its full potential. And someday you are
probably going to lose work on a failed update or accidental revert.

Kdiff3
------
I like kdiff3 as graphical 3-way merge tool for resolving conflicts or for use
during code reviews.

Launch kdiff3 for diff
----------------------
    svn --diff-cmd kdiff3 diff file.c

Color diffs
-----------
cdiff is a tool for color diffs the command line
https://github.com/ymattw/cdiff

After installing:
    svn diff | cdiff

Create a branch from trunk
--------------------------
    svn cp http://server/repo/svn/trunk http://server/repo/svn/branches/branch

Update branch from trunk
------------------------
Check out a working copy, if one does not already exist.
    svn co http://server/repo/svn/branches/branch .

Merge trunk into the branch.
    svn merge http://server/repo/svn/trunk .

Resolve merge conflicts, build, test. Everything is local in the working copy.
Nothing changes on the branch until commit.

    svn ci -m "commit message"

If updating, and have deleted on branch, will see conflicts in `svn stat`:
  local delete, incoming edit upon merge

To keep deleted:
    svn resolve --accept working <file/dir>

Merge branch into trunk
-----------------------
    svn co http://server/repo/svn/trunk .
    svn merge --reintegrate http://server/repo/svn/branches/branch


