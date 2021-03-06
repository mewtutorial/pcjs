Git "Cheat Sheet"
===

Committing files
---

To automatically stage files that have been modified and deleted, include -a; eg:

	git commit -a

Creating a new branch ("386dev")
---

You could use `git branch`, but if you've already modified some files that you now want to 
move to a new branch:

	git checkout -b 386dev
	
Pushing a new branch ("386dev")
---

Since a simple `git push` will report:

	fatal: The current branch 386dev has no upstream branch.
    To push the current branch and set the remote as upstream, use
    
        git push --set-upstream origin 386dev

do what it recommends (*-u* is shorthand for *--set-upstream*):

	git push -u origin 386dev

Reverting (resetting) a single file [[link](http://www.norbauer.com/rails-consulting/notes/git-revert-reset-a-single-file.html)]
---

If you have an uncommitted change (it's only in your working copy) that you wish to revert (in SVN terms)
to the copy in your latest commit, do the following:

	git checkout filename

This will checkout the file from HEAD, overwriting your change. This command is also used to checkout branches,
and you could happen to have a file with the same name as a branch. All is not lost, you will simply need to type:

	git checkout -- filename

You can also do this with files from other branches, and such. `man git-checkout` has the details.

The rest of the Internet will tell you to use `git reset --hard`, but this resets all uncommitted changes you’ve
made in your working copy. Type this with care.

Amending a commit
---

Sometimes I'm too quick with the "Commit and Push" button, and I've left a stale comment in the comment field.
To correct that:

	git commit --amend -m "New comment"

Unfortunately, updating the remote is not as simple as `git push`, which will complain:

	Updates were rejected because the tip of your current branch is behind its remote counterpart.
	Integrate the remote changes (e.g. 'git pull ...') before pushing again.

But in this case, there's nothing to pull, so force the push (this example assumes the current branch is *master*):

	git push -f origin master

Bringing the "gh-pages" branch up-to-date with the "master" branch
---

First, make sure all changes have been checked into the "master" branch (or stashed).

Next, issue these commands:

	git checkout gh-pages
	git merge master
	git push origin gh-pages
	git checkout master

Here's a sample run:

	[~/Sites/pcjs] git checkout gh-pages
	Branch gh-pages set up to track remote branch gh-pages from origin.
	Switched to a new branch 'gh-pages'
	
	[~/Sites/pcjs] git merge master
	Updating 33098e4..ab4f241
	Fast-forward
	 README.md                                           |   2 +-
	 _config.yml                                         |   2 +-
	 _posts/2015-12-10-rebuilding-the-pcjs-website.md    |  28 ++++---
	 apps/c1p/README.md                                  |   2 +-
	 blog/README.md                                      |   4 +-
	 devices/pc/machine/5170/ega/1152kb/rev1/machine.xml |   2 +-
	 disks/pc/README.md                                  |   2 +-
	 docs/about/README.md                                |  21 ++---
	 docs/about/pcjs/README.md                           |   2 +-
	 docs/pcjs/demos/pc-dbg.js                           |  86 ++++++++++----------
	 modules/markout/lib/markout.js                      | 174 +++++++++++-----------------------------
	 pubs/pc/reference/intel/8087/README.md              | 347 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	 versions/c1pjs/1.20.2/components.css                |   4 -
	 versions/pcjs/1.20.2/components.css                 |   4 -
	 versions/pcjs/1.20.2/pc-dbg.js                      | 104 ++++++++++++++++++++++++
	 15 files changed, 572 insertions(+), 212 deletions(-)
	 create mode 100644 pubs/pc/reference/intel/8087/README.md
	 
	[~/Sites/pcjs] git push origin gh-pages
	Total 0 (delta 0), reused 0 (delta 0)
	To git@github.com:jeffpar/pcjs.git
	   33098e4..ab4f241  gh-pages -> gh-pages
	   
	[~/Sites/pcjs] git checkout master
	Switched to branch 'master'
	Your branch is up-to-date with 'origin/master'.


Node "Cheat Sheet"
===

Installing Node (and NPM)
---
I downloaded and installed Node v0.11.11 [node-v0.11.11.pkg](http://nodejs.org/dist/v0.11.11/node-v0.11.11.pkg),
which appears to be the newest version of Node that does *not* suffer from a [serious regression](https://github.com/joyent/node/issues/9310)
on OS X.  In newer versions of Node, the REPL blocks execution of the application until keys are typed.

That Node package came bundled with its own version of NPM as well: v1.3.25.

Miscellaneous Tips
===

Connecting to a VMware Fusion Serial Port
---

Step 1: Add a custom serial port to a VM, by appending the following lines to its *.vmx* file; eg:

	serial0.present = "TRUE"
    serial0.fileType = "pipe"
    serial0.yieldOnMsrRead = "TRUE"
    serial0.startConnected = "TRUE"
    serial0.fileName = "/tmp/serial0"

If this is the VM's first serial port, then it should appear as COM1.  If the VM is running Windows 95,
add the following to its *system.ini*:

	[386Enh]
    device=wdeb386.exe
    device=debugcmd.vxd
    LoadDebugOnlyObjs=Yes
    debugcmd=y /n
    debugcom=1
    debugbaud=9600
    debugsym=dos386.sym vmm.sym
    debugsym=krnl386.sym gdif.sym userf.sym kernel32.sym gdi32.sym user32.sym

Step 2: Run *netcat* (aka *nc* on OS X):

	stty raw && nc -U /tmp/serial0

Alternatively, you can run *socat* instead of *netcat*:

	socat -d -d UNIX-CONNECT:/tmp/serial0 PTY

which will report:

	PTY is /dev/ttys002

indicating the name of serial device to connect to:

	screen /dev/ttys002

The advantage of using *nc* is that no "middle man" is required: your terminal window will be connected directly
to the virtual serial port.  And *nc* is included with OS X, whereas *socat* must installed separately (see
[http://www.dest-unreach.org/socat/](http://www.dest-unreach.org/socat/)).


Markdown "Cheat Sheet"
===

To convert PCjs' special links, such as:

	![IBM PC XT w/CGA, 10Mb Hard Drive](/devices/pc/machine/5160/cga/256kb/demo/thumbnail.jpg "link:/devices/pc/machine/5160/cga/256kb/demo/:200:100")

to normal Markdown links, search using this regex:

	\!\[(.*?)\]\((.*?) \"link:(.*?):([0-9]*):([0-9]*)\"\)
	
and replace using this regex:

	[<img src="$2" width="$4" height="$5" alt="$1"/>]($3)

For magazines (eg, BYTE), change:

	\!\[(.*?)\]\(../static/([^)]*) \"link:../static/(.*?):([0-9]*):([0-9]*)\"\)

to:

	[<img src="http://archive.pcjs.org/pubs/pc/magazines/BYTE/$2" width="$4" height="$5" alt= "$1"/>](http://archive.pcjs.org/pubs/pc/magazines/BYTE/$3)


Jekyll "Cheat Sheet"
===

I created screenshot.html in the **_includes** folder, so that I could do this:

	{% include screenshot.html src="/devices/pc/machine/5150/cga/64kb/donkey/thumbnail.jpg" width="200" height="100" link="/devices/pc/machine/5150/cga/64kb/donkey/" title="IBM PC running DONKEY.BAS" %}

instead of this:

	[<img src="/devices/pc/machine/5150/cga/64kb/donkey/thumbnail.jpg" width="200" height="100"/>](/devices/pc/machine/5150/cga/64kb/donkey/ "IBM PC running DONKEY.BAS")

The latter is better for pure Markdown environments, but the former enables Jekyll to properly style screenshots.
