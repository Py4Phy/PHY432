---
layout: default
title: Installing the environment
nav_exclude: true
has_children: false
---

Follow the instructions on this page in order to **install all the
software that you will need for this class**.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Overview

You will need to install

1. [The Bash Shell](#the-bash-shell)
2. [Git](#git)
3. a [text editor](#text-editor) (by default, `atom`)
4. [Python](#python) (including a number of additional packages
required for scientific computing)

In each section, find the instructions for your operating system
(Windows, macOS, or Linux).

Once you have installed everything, [test your
installation](#testing).


## Setup

To participate in a the class, you will need access to the software
described below. In addition, you will need an up-to-date web browser.

If you encounter <strong>problems during the installation</strong> ask
an instructor for help.  We also maintain resources for [trouble
shooting problems during the installation]({{ site.wiki.url
}}/installation-troubleshooting)


### The Bash Shell

Bash is a commonly-used shell that gives you the power to do simple
tasks more quickly.


#### Windows
  <ol>
	<li>Download the Git for Windows <a href="https://git-for-windows.github.io/">installer</a>.</li>
	<li>Run the installer and follow the steps below:
	  <ol>
		<li>Click on "Next".</li>
		<li>Click on "Next".</li>
		<li>Click on "Next".</li>
		<li>Click on "Next".</li>
		<li>Click on "Next".</li>			
		<li>
	<strong> 
		Select "Use Git and optional Unix tools from the Command Prompt" and click
		on "Next".
	</strong>
	</li>
		<li>Click on "Next".</li>
		<li>
		  Click on "Next".
		  <strong>
			Keep "Checkout Windows-style, commit Unix-style line endings" selected.
		  </strong>
		</li>
		<li>
		  <strong>
			Select "Use Windows' default console window" and click on "Next".
		  </strong>
		</li>
		<li>Click on "Next".</li>
		<li>Click on "Install".</li>
	  </ol>
	</li>
  </ol>
  <p>This will provide you with both Git and Bash in the Git Bash program.</p>

#### macOS

You can access Bash from the Terminal (found in
<code>/Applications/Utilities</code>). You may want to keep Terminal
in your dock for this class.

Recent versions of macOS (starting with Catalina 10.15) ship wth zsh
as the default shell but also have Bash installed.  You can either
type <code>bash</code> in the terminal to switch to Bash or <a
href="https://www.howtogeek.com/444596/how-to-change-the-default-shell-to-bash-in-macos-catalina/">change
permanently to Bash</a> by executing the following command in the
terminal:
	
```bash	
chsh -s /bin/bash
```

(and enter your password when asked).

In earlier versions, the default shell is Bash, so no need to install
or change anything.

#### Linux

The default shell is usually Bash, but if your machine is set up
differently you can run it by opening a terminal and typing
<code>bash</code>.  There is no need to install anything.



### Git ###

Git is a version control system that lets you track who made changes
to what when and has options for easily updating a shared or public
version of your code on <a
href="https://github.com/">github.com</a>. You will need a <a
href="https://help.github.com/articles/supported-browsers/">supported</a>
web browser (current versions of Chrome, Firefox, Safari, Microsoft
Edge, or Internet Explorer version 11 or above).

#### Windows

Git should be installed on your computer as part of your Bash install
(described above).

#### macOS

<strong>For macOS/Mac OS X 10.9 and higher</strong>, install Git for
Mac by downloading and running the most recent "mavericks" installer
from <a
href="https://sourceforge.net/projects/git-osx-installer/files/">this
list</a>.  After installing Git, there will not be anything in your
<code>/Applications</code> folder, as Git is a command line program.


#### Linux

If Git is not already available on your machine you can try to install
it via your distro's package manager. For Debian/Ubuntu run <code>sudo
apt-get install git</code> and for Fedora run <code>sudo yum install
git</code>.


### Text Editor ###

When you're writing code, it's nice to have a text editor that is
optimized for writing code, with features like automatic color-coding
of key words.  The default text editor on macOS and Linux is usually
set to <a href="http://www.vim.org/">Vim</a>, which is not famous for
being intuitive.  if you accidentally find yourself stuck in it, try
typing the escape key, followed by <code>:q!</code> (colon, lower-case
'q', exclamation mark), then hitting Return to return to the shell.


For this class we will use <a href="https://atom.io/">atom</a> as the
default editor. It is free, open source, available on Windows, macOS,
and Linux, powerful but also accessible for entry-level
programmers.
  
  <!-- 
    Other editors that you can consider for serious work are
	[Emacs](http://www.gnu.org/software/emacs/),
	[Vim](http://www.vim.org/) (both of which come with a steep
	learning curve), or a graphical editor such as
	[Gedit](http://projects.gnome.org/gedit/), [Sublime
	Text](https://www.sublimetext.com/). On Windows, a free editor is
	[Notepad++](http://notepad-plus-plus.org/).
	-->
  
#### Windows

<a href="https://atom.io/">atom</a> is a good editor that is suitable
for professional coding but also accessible to newcomers with is
graphical user interface.  To install it, download a suitable
installer from <a href="https://atom.io/">atom.io</a> and double click
on the file to run it. (If you cannot find an appropriate installer,
look for a file "AtomSetup-x64.exe" or "AtomSetup.exe" in the <a
href="https://github.com/atom/atom/releases/latest">list of latest
releases</a>.)  For more details see <a
href="https://flight-manual.atom.io/getting-started/sections/installing-atom/#platform-windows">Installing
atom on Windows</a>.  

Others editors that you can use are <a
href="http://notepad-plus-plus.org/">Notepad++</a> or <a
href="http://www.sublimetext.com/">Sublime Text</a>.  <strong>Be aware
that you must add its installation directory to your system
path.</strong> Please ask your instructor to help you do this.

#### Windows (on ASU laptop)
	  
On the ASU school laptops, <b>atom</b> should pre-installed
and you can use. Launch the editor from the Start Menu.

#### macOS

We recommend <a href="https://atom.io/">atom</a> as a good editor that
is suitable for professional coding but also accessible to newcomers
with is graphical user interface.  To install it, download a suitable
installation zip file from <a href="https://atom.io/">atom.io</a> and
double click on the file to unpack it. Open your Applications
directory from the Finder in the Go menu. Drag the unpacked Atom
application to your Applications directory. (If you cannot find an
appropriate installer, look for a file "atom-mac.zip" or in the <a
href="https://github.com/atom/atom/releases/latest">list of latest
releases</a>.) For more details see <a
href="https://flight-manual.atom.io/getting-started/sections/installing-atom/#platform-mac">Installing
atom on Mac</a>.  

Alternatively, <a href="https://www.nano-editor.org/">nano</a> is a
basic editor.  It should be pre-installed.  

Others editors that you can use are <a
href="http://www.barebones.com/products/textwrangler/">Text
Wrangler</a> or <a href="http://www.sublimetext.com/">Sublime
Text</a>.

#### Linux

We recommend <a href="https://atom.io/">atom</a> as a good editor that
is suitable for professional coding but also accessible to newcomers
with is graphical user interface.

Please follow the instructions on <a
href="https://flight-manual.atom.io/getting-started/sections/installing-atom/#platform-linux">Installing
atom on Linux</a> and ask an instructor for help if anything is
unclear.

Alternatively, <a href="https://www.nano-editor.org/">nano</a> is a
basic editor.  It should be pre-installed.

Others editors that you can use are <a
href="https://wiki.gnome.org/Apps/Gedit">Gedit</a>, <a
href="http://kate-editor.org/">Kate</a> or <a
href="http://www.sublimetext.com/">Sublime Text</a>.


### Python ###

<a href="http://python.org">Python</a> is a popular language for
scientific computing, and great for general-purpose programming as
well.  Installing all of its scientific packages individually can be a
bit difficult, so we recommend <a
href="https://anaconda.com/download">Anaconda</a>, an all-in-one
installer.

Regardless of how you choose to install it, <strong>please make sure
you install Python version 3.x</strong> (e.g., 3.9 or 3.10 is fine).

We will teach Python using the Jupyter notebook, a programming
environment that runs in a web browser. For this to work you will need
a reasonably up-to-date browser. The current versions of the Chrome,
Safari and Firefox browsers should all be supported (some older
browsers, including Internet Explorer version 9 and below, are not).

#### Windows
  <ol>
	<li>Open <a href="https://anaconda.com/download/#windows">https://anaconda.com/download/#windows</a> with your web browser.</li>
	<li>Download the Python 3 64-Bit installer for Windows.</li>
	<li>Install Python 3 using all of the defaults for installation <em>except</em> make sure to check <strong>Make Anaconda the default Python</strong>.</li>
  </ol>



<!--
<h4 id="python-windows-asu">Windows (on ASU laptops without
      sysadmin and existing outdated system anaconda)</h4>
	  <p>If you are stuck with a laptop where you can only install as
    a user <em>and</em> there is already a system-wide anaconda installation
    present that you do not want to used then you will need to install your own anaconda <em>and</em> make
    sure that it is being used.</p>
      <ol>
        <li>Open <a href="https://anaconda.com/download/#windows">https://anaconda.com/download/#windows</a> with your web browser.</li>
        <li>Download the Python 3 installer for Windows.</li>
        <li>Install Python 3 using all of the defaults for
    installation <em>except</em> make sure to check <strong>Make
    Anaconda the default Python</strong> and set the destination folder to <strong>C:\ProgramData\Anaconda3</strong>.</li>
		<li>Open the Git-Bash command line</li>
		<li>Append (<tt>>></tt>) to the file <tt>$HOME/.bash_profile</tt> the following content by typing
		<pre>
cat >> $HOME/.bash_profile << 'EOF'
# PHY432 bash startup for local Anaconda
MYCONDA="/c/ProgramData/Anaconda3"
export PATH="$MYCONDA:$MYCONDA/Scripts:$MYCONDA/libs/bin:$PATH"
unset MYCONDA
EOF
</pre>This will instruct Bash to look for your conda installation
before anything else.</li>
    <li>Close the Git-Bash window.</li>
	<li>Open a new Git-Bash window and type <strong>conda init bash</strong> (so that your conda can work under bash).</li>
	<li>Close current Git-Bash window and open a new one to let all settings take effect.</li>
	<li>If you still have problems running conda/python on windows, please visit: <a href="https://github.com/ASU-CompMethodsPhysics-PHY494/PHY494-resources/wiki/installation-troubleshooting#pip-or-python-are-not-found-in-git-bash">trouble shooting</a>.</li>
    </ol>
-->	

#### macOS
  <ol>
	<li>Open <a href="https://anaconda.com/download/#macos">https://anaconda.com/download/#macos</a> with your web browser.</li>
	<li>Download the Python 3 installer for MacOS.</li>
	<li>Install Python 3 using all of the defaults for
	installation.</li>
  </ol>
	  
#### Linux
  <ol>
	<li>Open <a href="https://anaconda.com/download/#linux">https://anaconda.com/download/#linux</a> with your web browser.</li>
	<li>Download the Python 3 installer for Linux. (Most likely the 64-Bit (x86) Installer is correct for your laptop.)</li>
	<li>Install Python 3 using all of the defaults for installation.
	(Installation requires using the shell. If you aren't
	comfortable doing the installation yourself
	stop here and request help.)</li>
	<li>
	  Open a terminal window.
	</li>
	<li>
	  Type <pre>bash ./Anaconda-</pre> and then press
	  tab. The name of the file you just downloaded should
	  appear.
	</li>
	<li>
	  Press enter. You will follow the text-only prompts.  When
	  there is a colon at the bottom of the screen press the down
	  arrow to move down through the text. Type <code>yes</code> and
	  press enter to approve the license. Press enter to approve the
	  default location for the files. Type <code>yes</code> and
	  press enter to prepend Anaconda to your <code>PATH</code>
	  (this makes the Anaconda distribution the default Python).
	</li>
  </ol>



## Testing

Once you have installed everything, go through the individual steps
below and executed every command. Compare what happens in your case to
what is described. If you don't get equivalent output, ask an
instructor for clarification or help.

### Bash shell

Open a *terminal* (macOS, Linux) or open *Git Bash* (under
*All Programs/Git/Git Bash*) in Windows.

Type


```bash
echo $SHELL
```

Should show `/bin/bash` or `/usr/bin/bash` (or similar).

We use "shell" and "terminal" (and "console") pretty much
interchangeably.

### Git

In the shell, type

```bash
git --version
```

which should show something like `git version 2.7.0`.

### editor (atom)

#### First time

Open `atom` using your GUI
* Windows: from the start menu
* macOS: from the Application folder
* Linux: varies (but you might be able to skip to "From the shell"

A window should open showing the atom logo and welcome screen, similar
to 

![atom welcome screenshot]({{ site.baseurl }}/{{ site.figs }}/atom_welcome.jpg)

If it tries to install additional commands (`atom` and `apm`) then let
it do it and provide your system administrator password if required.

Then exit the editor again (Quit from the menu or close the
window).

#### From the shell

In the shell, type

```bash
atom
```

It should open the editor. Exit the editor.

If this does not work then you need to let atom install additional
commands. The Atom menu bar has a command named *"Install Shell
Commands"* which installs the atom and apm commands, as described
under [Opening a
File](https://flight-manual.atom.io/getting-started/sections/atom-basics/#opening-a-file)
(and provide your system administrator password if requested). Then
add the atom directory to your bash start file manually as described
under Wiki:[start atom from the git-bash
commandline]({{ site.wiki.url }}/installation-troubleshooting#start-atom-from-the-git-bash-commandline).)


### Python

#### python interpreter
In the shell, type

```bash
python -c 'import sys; print(sys.version)'
```

which should give something similar to `Python 3.8.5 (default, Sep 4
2018, 07:30:14)` (and more stuff). Important: You should have **Python
3**, i.e., a version like 3.8.x or 3.10.x

Also try
```bash
which conda 
which python
```

which should give something similar to `/homes/USERNAME/anaconda3/bin/conda`, `/homes/USERNAME/anaconda3/bin/python`

#### Jupyter notebook

<ol>
<li>
In the shell, type

{% highlight bash %}
jupyter notebook
{% endhighlight %}

This should open a browser window at <a href="http://localhost:8888">http://localhost:8888</a>. 
</li>
<li>Open the <tt>New</tt> menu on the right hand side.</li>
<li>Under <tt>Notebooks</tt> select <tt>Python</tt> or <tt>Python
[conda root]</tt> (if it is shown)</li>
<li>In the new window ("Untitled"), type
{% highlight python %}
print("Hello World!")
{% endhighlight %}
and press <tt>shift</tt> and <tt>return</tt> keys simultaneously to evaluate the
cell. It should print "Hello World!".</li>
<li>Close the browser tab with menu <tt>File: Close and Halt</tt>.</li>
</ol>

If you have problems, ask an instructor.


#### Common problems

* On Windows, the `pip` or `python` commands are not found. Follow the
  steps under [solution: pip or python are not found in
  git-bash]({{ site.wiki.url }}/installation-troubleshooting#pip-or-python-are-not-found-in-git-bash)
* On macOS, if you get the error *OSError: [Errno 49] Can't assign
  requested address* you might need to use `jupyter notebook
  --ip=127.0.0.1`
* Wrong `conda` is used. Check `which conda` in the terminal: it
  should show a path in your home directory (e.g., for user "physics":
  Windows: `/c/Users/Physics/Anaconda3/conda`, macOS:
  `/Users/physics/Anaconda3/conda`, Linux:
  `/home/physics/Anaconda3/conda`). Try exiting the terminal and open
  a new terminal (or git bash) and try again. Changes to `PATH` only
  take effect when a new shell is opened.

See also [trouble shooting problems during the installation]({{ site.wiki.url }}/installation-troubleshooting)


## Credits

The instructions were originally taken from [Software
Carpentry](https://software-carpentry.org/) (in particular [David
Dotson's 2016 workshop at
ASU](http://smallerthings.org/2016-01-07_asu_physics/)) and adapted
for the PHY 432 class.

