---
layout: default
title: The Unix Shell
parent: Tools
nav_order: 1
nav_exclude: true
---

This lesson introduces the **shell**, also known as the **command
line**. There are many different shells: We are using the
**[bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell))** shell.

An *optional* lesson on more advanced [intermediate shell features](
{{ site.baseurl }}{% link modules/setup_unix/Intermediate_Unix_Shell.md %}) is also available
for you if you are interested.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Background and Motivation ##

As a computational scientist you have one primary tool at your hand: a
computer. And like an experimental scientist, you will have to be able
to interact with it, adjust it, tweak it, fix it, and generally make
it do things that it has never done before.

![CLI and GUI provide access to the operating system.]({{ site.baseurl
}}{% link assets/figs/os_shell_organization.png %})
{: .float-right }

You are probably used to interacting with a computer via a graphical
user interface ("GUI") — windows, browsers, a mouse or touch
screen. Although convenient, this limits you to the interactions
designed into the interface. To get more out of a machine you have to
talk to it more directly.

We will interact with the computer using the text-based terminal
through a so-called *command line interface* (CLI). The user types
input commands; the commands are read, executed, and output is
printed. The program responsible for doing this is called the
**shell** (because it "encloses" the operating system to simplify user
interaction with it).

The shell is a program like any other but it's primary purpose is to
run other programs; most of the input "commands" are in fact other
programs. The shell is very good at working with the file system
(files and directories), combining multiple existing tools in powerful
ways, and automating tasks. On a
[Unix](http://en.wikipedia.org/wiki/Unix)-like operating systems
(typically used for high-performance computing) using the shell is a
very powerful (and essential) way to interact with the computer.

## Introductory Shell Tutorial ##

### Accessing the shell ###

* On a typical **Linux** system you open an application called
  *terminal* or *xterm* or *kterm* (or similar).

* On **macOS** you open *Terminal.app* (in the *Utilities* folder in
  *Applications*).

* On Windows we use *Git Bash*: Find it in the Program menu under *All
  Programs/Git/Git Bash*

#### Shell prompt

You should be greeted by the *prompt*, which can look like this

~~~
$
~~~

with the cursor as an underline or block showing that you can
type. Often your prompt is more elaborate, e.g.

~~~
dvader@deathstar.empire.gov  ~$
~~~

#### Executing commands

Commands are executed by typing the *name of the command* (typically an abbreviated English word like `cd` for "change directory", `ls` for "list", but also `python` for the Python interpreter) and then finishing with _return_ (or _enter_).

Type

{% highlight bash %}
whoami
{% endhighlight %}

and hit enter. You should see your username being printed to the
screen.

Type 

{% highlight bash %}
cd
{% endhighlight %}

and hit enter to begin the lesson. From now on, input will just be
shown and you should enter it.

#### General syntax of a shell command

Commands generally take *arguments* (what to operate on, required) and
*options* (modify the standard behavior, optional).

{% highlight bash %}
command_name -v -o optarg --long-opt  arg1 arg2
{% endhighlight %}

Often, omitting the argument also works and a default is assumed. You
can learn more about commands with the help function (try running just
with option `-h` or `--help` or on Linux/macOS, `man command_name`;
the *Git Bash* installation does not come with man pages but you can
use services on the web such as the
[Debian man pages](http://manpages.debian.org/cgi-bin/man.cgi)).



### Navigating Files and Directories ###

The operating system manages access to files and directories in the **file system** (typically, the stuff that you see on your disk).

* **files** = documents, data, pictures, ...
* **directory** = "folder"; may contain any number of files or other directories

![Linux file system (modified from from
https://www.serverkaka.com/2018/01/key-locations-in-linux-file-system_21.html)]({{
site.baseurl }}/{{ site.figs }}/filesystem.png)

Instead of using your graphical File Explorer or Finder we want to use shell commands to
* move around the file system
* get information about files and directories
* specify the location of files and directories


#### Commands ####


* `pwd` (print working directory)
* `ls` (list directory)
* `cd` (change directory)


#### Paths ####

A *path* consists of *directory names* separated by forward-slashes
"`/`" and possibly a final *file name*. 

* `/` (the actual name of the "root" directory)
* `/home/dvader` or `/Users/dvader`
* `/usr/bin/nano`
* `books.txt`
* `/home/dvader/Documents/deathstar/weaknesses.pdf`
* `Documents/deathstar/weaknesses.pdf`

Paths starting with `/` are called *absolute paths*; anything else is
a *relative* path, starting from the current working directory (check
with `pwd`).

Special directory names:

* `.`  is the current directory (e.g., `./Documents`)
* `..` is the parent directory (e.g., `../../home/dvader/..`)
* `~` is the home directory (only when leading the path, e.g., `~/Documents`)

#### Location in the files system: `pwd` ####

Assume user dvader has the following directory layout in his *home
directory* `/home/dvader` [^0]:

~~~
/home/dvader/
         Documents/
              deathstar/
                   weaknesses.pdf
                   electrical_bill.dat
              work/
         data/
              planets.dat
              bases
~~~

When Mr Vader logs in he starts in his home directory, `/home/dvader`. He can
run `pwd` to "print the working directory":

{% highlight bash %}
pwd
{% endhighlight %}

which shows `/home/dvader`.

##### <span class="label" style="background: black">Activity</span> Find Your Home #####

* Open Terminal
* Type
  
  {% highlight bash %}
  pwd
  {% endhighlight %}
  
  and hit enter. Note the directory name: this is your home directory.
  
* share your home directory name (show your neighbor or copy and paste into the chat)


#### Listing file system contents: `ls` ####

If he executes `ls` ("list") he will see something like

~~~
Documents
data
~~~
{: .output}

##### <span class="label" style="background: black">Activity</span> List Your Home directory #####

* open a terminal (or use the open terminal from the last exercise)
* Type

  {% highlight bash %}
  ls
  {% endhighlight %}

* Compare the files that you see with those of your neighbor (show or copy and paste into the chat)


#### Moving around the file system: `cd` ####

If he executes the `cd` command

{% highlight bash %}
cd /home/dvader/Documents/deathstar
{% endhighlight %}

then he will have moved to the `deathstar` directory; confirm with `pwd`!:

{% highlight bash %}
pwd
{% endhighlight %}

will print

~~~
/home/dvader/Documents/deathstar
~~~
{: .output}


If he runs

{% highlight bash %}
ls
{% endhighlight %}

he will see 

~~~ 
electrical_bill.dat  weaknesses.pdf
~~~
{: .output}

The `cd` command took an *argument*, the directory to go to.


##### <span class="label" style="background: black">Activity</span> Going up #####

* Go to the parent directory of your home dir:

  {% highlight bash %}
  cd ..
  {% endhighlight %}

* List the contents

  {% highlight bash %}
  ls
  {% endhighlight %}


##### <span class="label" style="background: black">Activity</span> Going Home #####

* Type

  {% highlight bash %}
  cd
  {% endhighlight %}

* Where are you now? (What command can you use to print the directory
  that you're in?)

##### More on `cd` #####

The command `cd` on its own always returns you to your home
directory. (It is equivalent to `cd ~`.)

In order to get to the `data` directory he could use the command `cd
/home/dvader/data` but instead he uses the *special directory* `..`
(which means "the directory above this one"):

{% highlight bash %}
cd ../../data
{% endhighlight %}

A second special directory is `.` ("this directory"). `.` and `..`
are understood by all commands.

### Autocompletion ###

* Use the `TAB` key while typing: *autocompletion* is one of the best
  features of the shell! <span class="label">Pro Tip!</span>
* The other great interactive feature is the *history*: try using the
  cursor-up and -down keys. <span class="label">Pro Tip!</span>

### Wildcards ###

The shell contains a simple *pattern matching* syntax (wildcards or
"glob patterns") to select all files that match the pattern.  Commonly
used patterns are

* `*`: matches zero or more characters in a name, e.g., `*.dat`
  matches all files ending in `.dat`, and `report_2021-*.txt` matches
  `report-2021-11.txt`, `report-2021-12.txt`, but not
  <strike><code>report-2020-2.txt</code></strike>
* `?` matches a single character in a name, e.g., `?.jpg` matches
  `1.jpg`, `a.jpg`, but not <strike><code>ab.jpg</code></strike>

Neither of them matches a leading `.` in a file name or a space or the directory separator `/`.

#### Example: List all dat files

List all "dat" files in the current directory: Use the character `*`
to match "any part of a file name"

{% highlight bash %}
ls *.dat
{% endhighlight %}

#### Example: List all commands with "oo" in their name

List all files containing "oo" in the `/usr/bin` directory (will only
work on Linux or macOS):

{% highlight bash %}
ls /usr/bin/*oo*
{% endhighlight %}

#### Example: Delete jpg files in directories 19xx


**Warning**
{: .label .label-red .d-inline }
DO NOT COPY AND PASTE ANY COMMAND LINE CONTAINING `rm`
WITHOUT THINKING *TWICE* ABOUT IT. You have been warned.
{: .text-red-300 .d-inline }

Delete all jpg images in directories from the last century

{% highlight bash %}
rm Pictures/19??/*.jpg
{% endhighlight %}

(Note that `19??` matches anything that looks like a year from the
last century such as 1999, 1969, ... although it would also match
19xy; the `*.jpg` pattern matches all files with suffix jpg.)

#### Example: Show all two-letter Unix commands

Show commands with exactly two letters (assuming that you have a
Unix-like OS such as Linux or macOS where the commands are located in
`/bin` and `/usr/bin`):

{% highlight bash %}
ls /bin/?? /usr/bin/??
{% endhighlight %}

(Two letter commands are important — learn more about these commands,
e.g., with the three-letter command `man`.)

#### Example: Copy Jupyter notebooks to another directory

As part of working with code in this class, we will have to copy
Jupyter notebooks from one directory to another directory

{% highlight bash %}
cp ~/PHY432-resources/10_ODEs/*.ipynb ~/PHY432/10_ODEs/
{% endhighlight %}


### Error messages ###

Unix commands are terse: If everything works, they say nothing. If
they fail, you get a short (sometimes cryptic) error message.

Try

{% highlight bash %}
cd bogus
{% endhighlight %}

This gives

~~~~~
bash: cd: bogus: No such file or directory
~~~~~

**Warning**
{: .label .label-red .d-inline }
**Always read error messages!**
{: .text-red-300 .d-inline }


### <span class="label" style="background: black">Activity</span> Explore your file system  ###

1. What does the following sequence of commands show?
   ```bash
   cd
   ls -a
   ```
   
2. Go to the `bin` directory that is located in the root directory (at
   least on Linux and macOS, this would be `/bin`) or to the anaconda
   distribution's `bin` directory (e.g.,`~/Anaconda3/bin`) (on Windows).

   1. List the files there.
   2. Did you find "cp" and "grep" and also "ls"? 
   
   If you cannot find any of these `bin` directories run the command
   ```bash
   which ls
   ```
   
   which should display something like `/PATH/TO/ls` where "/PATH/TO"
   is the *directory* that contains the `ls` command. Use that
   directory as the `bin`-directory to investigate. 
3. What does `ls -R /` show? (Try `^C`, i.e., press CONTROL and C at
   the same time...)
4. Try other options of `ls` such as `-sh` or `-sha`. --- ask `ls` for
   help!
5. Is there a difference between `ls -sha`, `ls -ash`, and `ls -a -s
   -h`?



### Tips to make your (shell) life easy ###

* Use the shell's convenience features:
  * `TAB` completion <span class="label">Pro Tip!</span>
  * up/down arrow to get commands that you already typed. <span class="label">Pro Tip!</span>
  * `history` shows all the commands you typed so far
  * Try out `Control`+`R` (`^R`) to search through your shell
    *history*.
  * `^A` and `^E` will likely take you to the beginning and end of a
    line
* Use `cd ..` to go up, `cd ../..` to go up twice etc.
* Use `cd -` to go to *the previous directory I was in* (only works
  for `cd`).
* Use the tilde character `~` for your home directory, e.g. `cd
  ~/Documents` is equivalent to `cd /home/dvader/Documents`.
* Use wildcards (`*`) but test them with `ls` before using them with `rm`!


### Creating directories and files ###

We want to
* create, copy, rename, and delete files and directories
* edit text files


#### Commands ####

* `mkdir` (make directory)
* your editor of choice (*Visual Studio Code* by default for the class, `nano` is
  an alternative choice [^2])

#### <span class="label" style="background: black">Activity</span> Directory structure for the class ####

Make a directory `PHY432` in your home directory for the class and
inside it, one called `01_shell` for today's lesson, using the
following sequence of shell commands:

{% highlight bash %}
cd ~
mkdir PHY432
cd PHY432
mkdir 01_shell
{% endhighlight %}

Note: 

* *Avoid spaces and most special characters in file names.* All
  letters and numbers together with underscore `_`, minus sign `-`,
  and period `.` are ok. [^1] <span class="label">Pro Tip!</span>
* Plain `mkdir` cannot create multiple directories deep in one go
  unless you have the `-p` option available (check!).

#### <span class="label" style="background: black">Activity</span> Create `Documents/work` ####

1. Inside your `01_shell` directory, create three directories, `data`
   and `Documents/work`.
2. Go to `Documents/work`

#### Creating text files with a text editor ####

Run *Visual Studio Code* by either launching it from a menu or from the commandline [^4]
{% highlight bash %}
code
{% endhighlight %}

You should see something like this:

![Visual Studio Code get started screenshot]({{ site.baseurl }}/{{ site.figs }}/vscode_get_started.jpg)

We will now create a TODO list in a file with name `TODO` and content

    Plan for today:

    1. find rebel base
    2. destroy!


1. Open a new file via the menu option

   *File* → *New File*

   You should have a tab named *Untitled-1*.
   
   Close all the other tabs. It should look like this: 
   
   ![Visual Studio Code new file]({{ site.baseurl }}/{{ site.figs }}/vscode_untitled.jpg)

2. Type the todo list into the editor window.

   ![Visual Studio Code todo list]({{ site.baseurl }}/{{ site.figs }}/vscode_todo.jpg)

3. Save it to file with name 'TODO' with menu option

   *File* → *Save*
   
   Make sure to navigate to your the `PHY432/01_shell/Documents/work` directory.

   ![Visual Studio Code todo list]({{ site.baseurl }}/{{ site.figs }}/vscode_project_file_view.jpg)

   You can hide the "project" view with the directory structure.

4. Quit Visual Studio Code (details depend on your operating system; find the *Exit*
   menu option either under *File*.

5. Check that the file is in the directory with `ls`.


You can re-open the file from the command line [^4]:

{% highlight bash %}
code TODO
{% endhighlight %}

(Alternatively, open Visual Studio Code from your GUI and find the file `TODO` through the *File*
→ *Open file* dialog.)


##### <span class="label" style="background: black">Activity</span> Create a file with your editor #####

* Create a file `~/PHY432/Documents/work/lesson.txt` with three
  lessons from today:

      1. computers are tools
      2. the shell is powerfull
      3. basic shell commands: pwd, cd, ls

* save the file and check that it is there with

  {% highlight bash %}
  ls -l ~/PHY432/Documents/work/lesson.txt
  {% endhighlight %}

* Open the file again and add a 4th lesson regarding file editing.


### Copy, rename, delete ###

* `cp` (copy file, `cp -r` copy recursively, including directories)
* `mv` (move, i.e. rename, also to another directory)
* `rmdir` (remove empty directory)
* `rm` (remove file, `rm -r` remove recursively (**dangerous!**))

  **WARNING**
  {: .label .label-red .d-inline }
  There is no "Trashcan" or built in backup. Once you `rm`
  something, it is gone. Be especially careful with `rm -r`.
  {: .text-red-300 .d-inline }

  `rm` also has the force (`-f`) option to ignore any safeguards such
  as permission settings that would otherwise not let you write to or
  delete a file.

  **WARNING**
  {: .label .label-red .d-inline }
  Do not execute `rm -rf *`. It will erase *everything* permanently.
  {: .text-red-300 .d-inline}

Pro Tip
{: .label .label-inline }
All these commands can also work on multiple filenames.
{: .d-inline }


#### <span class="label" style="background: green">Homework</span> Activity  ####

This is a more extended exercise in using various shell commands. With
the previous examples you should have a directory tree that looks like
this:

    PHY432/
    └── 01_shell
        ├── Documents
        │   └── work
        │       ├── TODO
        │       └── lesson.txt
        └── data


Starting from this directory structure, perform the following file
system manipulations:

1. Make a backup (call it `TODO.bak`) of the TODO list with the `cp`
   command.
2. Rename `TODO` to `TODO.txt` with the `mv` command.
3. Make a directory `notes` under the `data` directory: You should now
   have a directory tree similar to
   
        PHY432/
        └── 01_shell
            ├── Documents
            │   └── work
            │       ├── TODO.bak
            │       ├── TODO.txt
            │       └── lesson.txt
            └── data
                └── notes

   Check with `ls -R ~/PHY432` (or `tree ~/PHY432`)
4. Put a copy of `TODO.txt` into the `notes` directory (using `cp`).
5. Create a new text file `data/notes/hints.txt` and write any
   [hints](https://en.wikipedia.org/wiki/Ice_planet)  for possible
   rebel bases into this file.
6. Open `notes/TODO.txt` in _Visual Studio Code_ and add a note to item 1 too look in the
   `hints.txt` file. Save and exit.
7. Make a copy of your `notes` directory in your work directory. Your
   tree should now look like this:
   
        PHY432/
        └── 01_shell
            ├── Documents
            │   └── work
            │       ├── TODO.bak
            │       ├── TODO.txt
            │       ├── lesson.txt
            │       └── notes
            │           ├── TODO.txt
            │           └── hints.txt
            └── data
                └── notes
                    ├── TODO.txt
                    └── hints.txt

8. Remove `data/notes/hints.txt` with `rm`.
9. Remove `data/notes` with `rmdir`. [^5]
10. Move `Documents/work/notes/hints.txt` into the `work` directory.
11. Remove the useless `Documents/work/notes` directory with `rm -r` (careful !)


## Credits

This lesson builds on [An Introduction to the command
line](https://becksteinlab.physics.asu.edu/learning/24/introduction-to-the-command-line)
with [Unix
Basics](https://becksteinlab.physics.asu.edu/pages/unix/IntroUnix/p01_UNIX.html)
and the [Software Carpentry lesson on The Unix
Shell](https://swcarpentry.github.io/shell-novice/).


------------------------------------------------------------

## Footnotes ##

[^0]:

    You can also see if you have the [`tree`](https://manpages.debian.org/stretch/tree/tree.1.en.html) command installed, which
    shows you beautiful directory trees:
    
        $ tree ~dvader
        /home/dvader/
        ├── Documents
        │   ├── deathstar
        │   │   ├── electrical_bill.dat
        │   │   └── weaknesses.txt
        │   └── work
        └── data
            ├── bases
            └── planets.dat
                
    `tree` is typically *not* included with git-bash.


[^1]:

    If you *must* need spaces then enclose the string in single or
    double quotes, e.g., `'/c/Program Files/'` or `"/c/Program
    Files"`. Double quotes admit shell variable expansions, single
    quotes do not. Note that a tilde `~` within quotes will *not*
    expand to the home directory!


[^2]: 

    **Upgrading nano**: If you are using `nano` as your editor then you want to
    enable a few useful features including syntax highlighting. The
    easiest way is to download the config files as the zip file
    [nanoconfig.zip]({{site.baseurl}}/{{site.siteresources}}/nanoconfig.zip)
    and unpack them in your home directory (`curl` can be used to
    download a file directly instead of having to use the browser):

        cd 
        curl {{ site.url }}{{ site.baseurl }}/{{ site.siteresources }}/nanoconfig.zip -O unzip nanoconfig.zip

    This should create the file `~/.nanorc` (which you can edit to
    customize further) and the directory `~/.nano`.


[^4]:

    If you cannot start `code` from the commandline, go back to
    [Setting up the Environment: Testing: editor (Visual Studio Code)]({{ site.baseurl }}{% link modules/setup_unix/environment_installation.md %}#from-the-shell) and follow
    the steps described there.

[^5]:

    Or rather, *attempt* to remove the directory. This command *should
    fail* for this exercise. If you wanted to really remove the
    directory, which command would you need to use? 
