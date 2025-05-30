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
3. a [text editor](#text-editor) (by default, *Visual Studio Code* / `code`)
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

For Windows, we install the bash shell together with the git version
control software:

<ol>
	<li>Download the Git for Windows <a href="https://git-for-windows.github.io/">installer</a>.</li>
	<li>Run the installer and follow the steps below:
	  <ol>
		<li>Click on "Next" four times (two times if you've previously installed Git). You don't need to change anything in the Information, location, components, and start menu screens. </li>
		<li>
		<strong> 
			From the dropdown menu, "Choosing the default editor used by Git", select "Use the Nano editor by default" (NOTE: you will need to scroll up to find it) and click on "Next".
		</strong>
		</li>
		<li>On the page that says "Adjusting the name of the initial
			branch in new repositories", ensure that "Let Git decide" is
			selected.</li>
		<li>Ensure that "Git from the command line and also from
			3rd-party software" is selected and click on "Next". (If you don't
			do this Git Bash will not work properly, requiring you to remove
			the Git Bash installation, re-run the installer and to select the
			"Git from the command line and also from 3rd-party software"
			option.)</li>
		<li>Select "Use bundled OpenSSH".</li>
	    <li>Ensure that "Use the native Windows Secure Channel Library" is selected and click on "Next".</li>
		<li>Ensure that "Checkout Windows-style, commit Unix-style line endings" is selected and click on "Next".</li>
		<li><strong>Ensure that "Use Windows' default console window" is selected and click on "Next".</strong></li>
		<li>Ensure that "Default (fast-forward or merge) is selected and click "Next".</li>
		<li>Ensure that "Git Credential Manager" is selected and click on "Next".</li>
		<li>Ensure that "Enable file system caching" is selected and click on "Next".</li>
		<li>Click on "Install".</li>
		<li>Click on "Finish" or "Next".</li>
	</ol>
	</li>
</ol>

<p>
This will provide you with both Git and Bash in the Git Bash program.
</p>

<p>
If your "HOME" environment variable is not set (or you don't know what
this is): 
</p>

<ol>
	<li>Open command prompt (Open <i>Start Menu</i> then type <code>cmd</code> and press
		<kbd>Enter</kbd>).</li>
	<li>Type the following line into the command prompt window exactly as
		shown:
   	    <pre>
        setx HOME "%USERPROFILE%"
        </pre></li>
    <li>Press <kbd>Enter</kbd>, you should see <code>SUCCESS: Specified value
        was saved.</code></li>
	<li>Quit command prompt by typing <code>exit</code> then pressing
	<kbd>Enter</kbd>.</li>
</ol>	


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


#### ChromeOS ####
[ChromeOS](https://www.google.com/chromebook/chrome-os/) is the
operating system from a **Chromebook**. 

In order to install software for the class on a Chromebook you need to
first *enable the Linux system on the Chromebook*, following the
instructions below. (You can check [How to enable Linux on your
Chromebook (and why you
should)](https://www.zdnet.com/article/how-to-enable-linux-on-your-chromebook-and-why-you-should/)
to enable Linux.) This will, amongst other things, **install the Bash
shell**.

We found that you can enable Linux on Chromebook, and it will just
work as a Linux system. Please follow the [instructions to enable
Linux](https://code.visualstudio.com/blogs/2020/12/03/chromebook-get-started#_enable-linux-on-your-chromebook),
which can be summarized as:

1. open your system's *Settings*
2. look for *Linux (Beta)* on the sidebar
3. turn on Linux support: Follow the instructions on screen to
   configure the Linux environment (for most people, accepting the
   default values should be enough). Your Chromebook will then
   download the tools to create the Linux environment and configure it
   for you.
4. Once the Linux environment has been set up, you'll see a new
   terminal window popping up.
5. In the *Terminal*, run the following commands to install some
   needed Linux packages
   ```bash 
   sudo apt-get update
   sudo apt-get install -y gnome-keyring
   ```

##### Terminal #####

*Terminal* is an application in the Linux folder that gives you access
to the command line. It runs the *bash* shell (which is what we need for
the class).

Keep a shortcut for Terminal handy.

(You can also run Terminal inside VS Code although we commonly open it as a separate application.)


##### Installing missing packages with `apt-get` #####

`apt-get` is the package manager that knows where to find software
packages and how to install them.

If you later find that something is missing, you can install it with
```bash
sudo apt-get install PACKAGE_NAME
```
where PACKAGE_NAME is the name of the package (e.g., "git").


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

Recent versions of macOS should have `git` already
installed (or you had it installed together with
[Xcode](https://developer.apple.com/xcode/)). 
Check on the command line by running the command
```bash
git version
```
If this gives an output such as *git version 2.41.0* then you have `git`.

For older macOS/Mac OS X 10.9 and higher, install Git for Mac by
downloading and running the most recent "mavericks" installer from <a
href="https://sourceforge.net/projects/git-osx-installer/files/">this
list</a>.  Because this installer is not signed by the developer, you
may have to right click (control click) on the .pkg file, click Open,
and click Open on the pop up window. After installing Git, there will
not be anything in your <code>/Applications</code> folder, as Git is a
command line program.



#### Linux

If Git is not already available on your machine you can try to install
it via your distro's package manager. For *Debian/Ubuntu* run 
```bash
sudo apt-get install git-all
```
and for *Fedora* run 
```bash
sudo dnf install git-all
```

#### ChromeOS ####

You should have the `bash` shell and `git` already installed. 

If `git` is missing, install it with 
```bash
sudo apt-get install -y git
```
in the *Terminal*.


### Text Editor ###

When you're writing code, it's nice to have a text editor that is
optimized for writing code, with features like automatic color-coding
of key words.  The default text editor on macOS and Linux is usually
set to <a href="http://www.vim.org/">Vim</a>, which is not famous for
being intuitive.  if you accidentally find yourself stuck in it, try
typing the escape key, followed by <code>:q!</code> (colon, lower-case
'q', exclamation mark), then hitting Return to return to the shell.


For this class we will use <a href="https://code.visualstudio.com/">
Visual Studio Code</a> as the default editor. It is free, open source,
available on Windows, macOS, Linux, and ChromeOS, powerful but also
accessible for entry-level programmers.
  

#### Windows

<a href="https://code.visualstudio.com/">Visual Studio Code</a> is a good editor that is suitable
for professional coding but also accessible to newcomers with is
graphical user interface.[^1]  To install it, download a suitable
installer from <a href="https://code.visualstudio.com/">code.visualstudio.com</a> and double click
on the file to run it. (For more details see <a
href="https://code.visualstudio.com/docs/setup/windows">Visual Studio Code on Windows</a>.)


<!-- 
#### Windows (on ASU laptop)
	  
On the ASU school laptops, <b>Visual Studio Code</b> should pre-installed
and you can use. Launch the editor from the Start Menu.

-->

#### macOS

We recommend <a href="https://code.visualstudio.com/">Visual Studio Code</a> as a good editor that
is suitable for professional coding but also accessible to newcomers
with is graphical user interface.[^2]

##### Install Visual Studio Code for macOS

To install *Visual Studio Code*, 

1. download a suitable installation zip file from <a
   href="https://code.visualstudio.com/">code.visualstudio.com</a>
2. double click on the file to unpack it. 
3. Open your Applications directory from the Finder in the Go menu. 
4. Drag the unpacked Visual Studio Code application to your
   Applications directory. 

(For more details see <a
href="https://code.visualstudio.com/docs/setup/mac">Visual Studio Code on macOS</a>.)

##### Install the `code` command for VS Code

⚠️ If you are using **Visual Studio Code** then you need to install the
`code` command so that we can launch Visual Studio Code from the
command line:

1. Launch <b>Visual Studio Code</b>. 
2. Open the <b>Command Palette</b> (`Cmd+Shift+P`).
3. Type "shell command" to find <b>Shell Command</b>: Install `code`
   command in <b>PATH</b> command.
   
Restart the terminal for the new `$PATH` value to take effect. 

You'll be able to type `code .` in any folder to start editing files
in that folder. (For more details see <a
href="https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line">
Launching from the command line</a>.


#### Linux

We recommend <a href="https://code.visualstudio.com/">Visual Studio Code</a> as a good editor that
is suitable for professional coding but also accessible to newcomers
with is graphical user interface.[^3]

Please follow the instructions on <a
href="https://code.visualstudio.com/docs/setup/linux">Visual 
Studio Code on Linux</a> and ask an instructor for help if anything is
unclear.


#### ChromeOS ####

Follow [Chromebook: Install Visual Studio
Code](https://code.visualstudio.com/blogs/2020/12/03/chromebook-get-started#_install-vs-code)
for all instruction.

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

The installation has two steps:
1. Download and install the anaconda distribution.
2. Modify a Git Bash startup file so that you can easily use the
   programs in the anaconda distribution from the Git Bash command line.

##### Windows anaconda installation
We first download and install the <a href="https://www.anaconda.com/products/distribution#windows">anaconda distribution</a>:

<ol>
	<li>Open <a href="https://anaconda.com/download/#windows">https://anaconda.com/download/#windows</a> with your web browser.</li>
	<li>Download the Python 3 64-Bit installer for Windows.</li>
	<li>Install Python 3 using all of the defaults for installation <em>except</em> make sure to check <strong>Make Anaconda the default Python</strong>.</li>
</ol>

##### Modify Git Bash startup file for anaconda

The next step is a hack that ensures that you can call
<code>python</code> and any other commands from the anaconda
distribution (such as <code>conda</code>) from the Git Bash command line.

We are adding additional information to your bash shell startup file so that Anaconda will be found.

⚠️ These instructions assume that **you installed Anaconda3 in the
default location** (`C:\Users\YOUR-USERNAME\anaconda3`)— if _you_
changed the location in the installation process then you will have to
change the content of the `MYCONDA` variable below to use your custom
location (ask an instructor for help if you are unsure how to do
this).

The following commands must be typed exactly in *Git Bash*:

1. open *Git Bash* (from the *Start Menu*)
2. type 
   ```bash
   cd
   echo $HOME
   ```
   (always hit RETURN after typing a command)

   You should see output such as `/c/Users/YOUR-USERNAME` (where "YOUR-USERNAME" stands for your user name, e.g., "alice", "bob", or "dvader")
3. type exactly (or copy & paste --- you paste with right-mouse click
   in *Git Bash*):
   ```bash
   cat >> $HOME/.bash_profile << 'EOF'
   # PHY432 bash startup for local Anaconda
   MYCONDA="$HOME/anaconda3"
   export PATH="$MYCONDA:$MYCONDA/Scripts:$MYCONDA/Library/bin:$PATH"
   unset MYCONDA
   EOF
   ```
4. close Git Bash
5. open a new Git Bash (this is important so that the changes take effect)
6. type
   ```bash
   which conda
   ```
   Should print something like `/c/Users/YOUR-USERNAME/anaconda3/Scripts/conda`.

⚠️ If the last step did not work then **ask an instructor for help**. 
You can also look at the detailed explanation in the PHY432
troubleshooting wiki, [solution: pip or python are not found in
  git-bash]({{ site.wiki.url }}/installation-troubleshooting#pip-or-python-are-not-found-in-git-bash).


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
    Anaconda the default Python</strong> and set the destination folder to <strong>C:\ProgramData\anaconda3</strong>.</li>
		<li>Open the Git Bash command line</li>
		<li>Append (<tt>>></tt>) to the file <tt>$HOME/.bash_profile</tt> the following content by typing
		<pre>
cat >> $HOME/.bash_profile << 'EOF'
# PHY432 bash startup for local Anaconda
MYCONDA="/c/ProgramData/anaconda3"
export PATH="$MYCONDA:$MYCONDA/Scripts:$MYCONDA/libs/bin:$PATH"
unset MYCONDA
EOF
</pre>This will instruct Bash to look for your conda installation
before anything else.</li>
    <li>Close the Git Bash window.</li>
	<li>Open a new Git Bash window and type <strong>conda init bash</strong> (so that your conda can work under bash).</li>
	<li>Close current Git Bash window and open a new one to let all settings take effect.</li>
	<li>If you still have problems running conda/python on windows, please visit: <a href="https://github.com/ASU-CompMethodsPhysics-PHY494/PHY494-resources/wiki/installation-troubleshooting#pip-or-python-are-not-found-in-Git Bash">trouble shooting</a>.</li>
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
	(⚠️ Installation requires using the shell. If you aren't
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

#### ChromeOS ####

Because ChromeOS only reserves a relatively small virtual disk for
Linux we will not install the full Anaconda installation. Instead we
install the small [miniconda
installer](https://conda.io/projects/conda/en/latest/glossary.html#miniconda-glossary)
and then only install the packages that we need for the class. But you
can easily install any other packages that you might need yourself.


##### Install miniconda

We generally follow the original [installation instructions for
Linux](https://conda.io/projects/conda/en/latest/user-guide/install/linux.html)
but we will manually download the installer because we cannot easily
transfer a downloaded file from Chrome's download folder to the Linux
system.

1. Open the *Terminal*.
2. Create a download directory in your home directory
   ```bash
   cd
   mkdir -p Downloads
   ```
3. Change to the Download directory
   ```bash
   cd Downloads
   ```
4. In your Chrome web browser: Obtain the **download link** for latest **Miniconda3** installer:
   1. Go to the [miniconda Linux
      installers](https://docs.conda.io/en/latest/miniconda.html#linux-installers)
      page.
   2. Find the latest Python version (e.g., 3.10). 
   3. Look for the name **Miniconda3 Linux 64-bit**. 
   4. **Copy the link** (E.g. in Chrome, hover over the [Miniconda3
   Linux
   64-bit](https://repo.anaconda.com/miniconda/Miniconda3-py310_22.11.1-1-Linux-x86_64.sh)
   entry and from the context menu choose *Copy Link Address*.)
5. In *Terminal*: type `wget` and then **paste the URL**: it should
   look like the following (but your link may be different) 
   ```bash
   wget https://repo.anaconda.com/miniconda/Miniconda3-py310_22.11.1-1-Linux-x86_64.sh
   ```
   Execute the `wget` command. You should see download progress.

   (`wget` downloads from the commandline instead of using the browser.)
6. You now have the installer file
   `Miniconda3-py310_22.11.1-1-Linux-x86_64.sh` in your Downloads
   directory (your name may be different but always start with
   "Miniconda3-"). Run the installer with 
   ```bash
   bash Miniconda3-*-Linux-x86_64.sh
   ```
   * Press Enter to review the license agreement. Then press and hold Enter to scroll.
   * Enter "yes" to agree to the license agreement.
   * Use Enter to accept the default install location. (It will show something like `/home/YOUR_USERNAME/miniconda3`.)
   * The installer prompts you to choose whether to initialize Anaconda Distribution by running `conda init`. Enter “yes”.
   * The installer finishes.
7. Close and reopen *Terminal*.

   (You need to open a new Terminal so that the changes can take
   effect that the installer made so that all conda packages are
   found.)

You can delete the miniconda installer unless you want to later
re-install.

#####  Install Python packages for the class

We need a number of packages. In the following we install all of them
at once but if you have issues with the process timing out then
execute each installation separately.

In the *Terminal*, run
```bash
conda install numpy pytest matplotlib scipy ipython jupyter ipympl pytest-timeout
```


## Testing

Once you have installed everything, go through the individual steps
below and executed every command. Compare what happens in your case to
what is described. 

⚠️ If you don't get equivalent output, ask an instructor for
clarification or help.

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

### editor (Visual Studio Code)

#### First time

Open `Visual Studio Code` using your GUI
* Windows: from the start menu
* macOS: from the Application folder
* Linux: varies (but you might be able to skip to ["From the shell"](#from-the-shell))

A window should open showing the Visual Studio Code logo and get started screen, similar
to 

![Visual Studio Code get started screenshot]({{ site.baseurl }}/{{ site.figs }}/vscode_get_started.jpg)

Then exit the editor again (Exit from the menu or close the
window).

#### From the shell

In the shell, type

```bash
code
```

It should open the editor. Exit the editor.


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

* On Windows, the `python` (or `conda` or `pip`)  commands are not found. Follow the
  steps under [solution: pip or python are not found in
  git-bash]({{ site.wiki.url }}/installation-troubleshooting#pip-or-python-are-not-found-in-git-bash)
* On macOS, if you get the error *OSError: [Errno 49] Can't assign
  requested address* you might need to use `jupyter notebook
  --ip=127.0.0.1`
* Wrong `conda` is used. Check `which conda` in the terminal: it
  should show a path in your home directory (e.g., for user "physics":
  Windows: `/c/Users/Physics/anaconda3/conda`, macOS:
  `/Users/physics/anaconda3/conda`, Linux:
  `/home/physics/anaconda3/conda`). Try exiting the terminal and open
  a new terminal (or Git Bash) and try again. Changes to `PATH` only
  take effect when a new shell is opened.

See also [trouble shooting problems during the installation]({{ site.wiki.url }}/installation-troubleshooting)


## Credits

The instructions were originally taken from [Software
Carpentry](https://software-carpentry.org/) (in particular [David
Dotson's 2016 workshop at
ASU](http://smallerthings.org/2016-01-07_asu_physics/) and the [SWC
Workshop Template](https://carpentries.github.io/workshop-template/)) and adapted
for the PHY 432 class.

Instructions for Chromebooks come from [Learning with VS Code on
Chromebooks](https://code.visualstudio.com/blogs/2020/12/03/chromebook-get-started)
(December 3, 2020) by Alessandro Segala
[@ItalyPaleAle](https://twitter.com/ItalyPaleAle).

------------------------------------------------------------

## Footnotes ##

[^1]:

     Others editors that you can use in **Windows** are <a
	 href="http://notepad-plus-plus.org/">Notepad++</a> or <a
	 href="http://www.sublimetext.com/">Sublime Text</a>.  <strong>Be aware
	 that you must add its installation directory to your system
	 path.</strong> Please ask your instructor to help you do this.

[^2]:

     **Alternative editors for macOS**: If you don't want to use VS Code, you can always use <a
     href="https://www.nano-editor.org/">nano</a>, which is a basic editor.
     It should be pre-installed.
     Others editors that you can use are <a
     href="http://www.barebones.com/products/textwrangler/">Text
     Wrangler</a> or <a href="http://www.sublimetext.com/">Sublime
     Text</a>.

[^3]:

     **Alternative editors for Linux**:
	 [nano](https://www.nano-editor.org/) is a basic editor.  It
	 should be pre-installed.
	 Others editors that you can use are
	 [Gedit](https://wiki.gnome.org/Apps/Gedit),
	 [Kate](http://kate-editor.org/) or [Sublime
	 Text](http://www.sublimetext.com).
  	 More old-school (but very powerful) are
 	 [Emacs](http://www.gnu.org/software/emacs/) and
 	 [Vim](http://www.vim.org/) (both of which come with a steep
 	 learning curve)
