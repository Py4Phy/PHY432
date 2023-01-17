---
layout: default
title:  Git Basics
nav_exclude: true
---

This is a short introduction to one of the most essential tools in
software development: a
[version control system](https://swcarpentry.github.io/git-novice/reference#version-control)
and in particular the [Git](https://git-scm.com/) tool.[^0]

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Introduction to version control

A **version control system** (VCS) or **source code management** (SCM)
tool manages files and tracks changes to those files. It stores the
complete **history** and allows you to recover files at any stage of
the history (think "undo" to the beginning). Any serious software
project uses version control but its uses go beyond software, e.g.,
documents and data can also be version controlled.

![PhD Comics: "FINAL".doc (c) 2012 Jorge Charm](https://www.phdcomics.com/comics/archive/phd101212s.gif)

A set of changes is called a **commit**. It typically contains changes
to multiple files. It also contains a timestamp, information about
the user who made the changes, and a **commit message** that explains the
changes. The history consists of all the commits. The VCS stores the
history in a storage area called a **repository**.

![Illustration of branches, merging, and multiple revisions in
git. (Source: https://git-scm.com/)](https://git-scm.com/images/branching-illustration@2x.png)

Modern distributed VCS such as *Git* or *mercurial* make it easy for
multiple developers to work on the same project. They have support for
**merging changes** from different people into a single new file, and
for **resolving conflicts**, i.e., the case when the same part of a
file was changed (the changes "collided"). Online platforms such as
[GitHub](https://github.com), [Bitbucket](https://bitbucket.org/), or
[GitLab](https://gitlab.com/explore) provide free repositories in the
cloud (but you don't need these platforms to use a VCS!).

We will use [Git](https://git-scm.com/). For the class you should get
into the habit to version-control your work: in class notes, home
works, and projects. You will use GitHub to submit code that you
develop as part of your assignments and projects.


## Tutorial
Let's use `git` to manage what we have done so far.

If you want to read more about *Git*, have a look at the free [Pro Git
Book](https://git-scm.com/book) by Scott Chacon and Ben Straub and see
the [other resources](#more).

### Configuring Git ###

The first time you use `git` you need to tell it who you are: this
information will be the user information in the commit history. 

#### <span class="label" style="background: black">Activity</span> Personalization

##### Your identity #####
Set your name and email. 

Use a name and email address that can appear in the clear in the world
because you will also use it to sign up and access the
[GitHub](https://github.com/) web site; if you are concerned about
privacy, please review [GitHub’s instructions for keeping your email
address
private](https://help.github.com/articles/keeping-your-email-address-private/). During
this class we will use GitHub all the time:

* Homework will be submitted to *private* git repositories (only
  visible to you and the instructors).
* Projects will be submitted to *private* repositories only visible to
  you, your team, and the instructors.
* The final project can be submitted to a *public* repository,
  visible to everyone in the world (e.g., to use it as part of a portfolio)

Set the name and email associated with your commits (*Use your own
name and email address!*) (and how to color output):

{% highlight bash %}
git config --global user.name "Darth Vader"
git config --global user.email "dvader@empire.gov"
git config --global color.ui "auto"
{% endhighlight %}

##### Line endings #####
There are subtle differences between how Windows and Linux/macOS treat
line endings, which matters for programming. [Without going into
details](https://swcarpentry.github.io/git-novice/02-setup/), please
set the following

On **Windows**
{% highlight bash %}
git config --global core.autocrlf true
{% endhighlight %}

On **macOS** or **Linux**
{% highlight bash %}
git config --global core.autocrlf input
{% endhighlight %}

##### Default branch name #####
Git histories can have different *branches*. The main development branch (the one we typically work on)
used to be called "master" but this name is falling rapidly out of favor and the generally used name
is now simply *"main"*. Newer version of git may use "main" by default but for consistency we can
configure git to do so: 
{% highlight bash %}
git config --global init.defaultBranch main
{% endhighlight %}


##### Config settings listing #####
You can see a list of all your configuration settings with `git config
--list`.

#### <span class="label" style="background: black">Activity</span> Git Editor

You also tell what editor to use to write commit messages [^1]; here
we configure [Visual Studio Code to be used with git](https://help.github.com/articles/associating-text-editors-with-git/). 

{% highlight bash %}
# choose Visual Studio Code as your editor
git config --global core.editor "code --wait"
{% endhighlight %}

(If you want to choose another editor such as `nano`, ask an instructor. 
If you do not make any choices, then the default editor is chose by the 
system and it might be [`vim`](https://www.vim.org/), which is powerful
but initially hard to learn.)  



#### `git` basic command syntax

Git commands always follow the pattern 

    git <verb> [options] [arguments ...]
	
In particular, `--help` is always an option. Also
try `git help` and `git help tutorial`.


### Creating a repository ###

A repository starts from a directory with files.

#### <span class="label" style="background: black">Activity</span> Create your `~/PHY432` directory ####

During the class you will work on programs. We will store all this work in a specific directory
for the class named `~/PHY432`, to keep things tidy. 

Make a directory `~/PHY432` where you will do your work:[^0]
{% highlight bash %}
mkdir ~/PHY432
{% endhighlight %}
Create subdirectories for lessons:
{% highlight bash %}
cd ~/PHY432
mkdir 01_shell 02_git
{% endhighlight %}

If you have done the [shell exercises]({{ site.baseurl }}{% link
 modules/setup_unix/Unix_Shell.md %}#activity-directory-structure-for-the-class)
then your PHY432 might now look like the following:

~~~
~/PHY432/
  ├── 01_shell
  │   ├── Documents
  │   │   └── work
  │   │       ├── TODO
  │   │       └── lesson
  │   └── data
  └── 02_git
~~~

Create a `README.md` file in `01_shell` and `02_git` with [your
editor]({{ site.baseurl }}{% link modules/setup_unix/Unix_Shell.md
%}#creating-text-files-with-a-text-editor) that contains text like the
following: 
{% highlight markdown %}
# 01 Shell

Work with the `bash` shell.
{% endhighlight %}
and
{% highlight markdown %}
# 02 git

Working with the `git` *version control software*; see https://git-scm.com/.
{% endhighlight %}
(or write whatever you want — the exact content is not
important). Also create a file `01_shell/hello.sh` with content
{% highlight markdown %}
# simple bash script example
echo "Hello ${USER}!"
{% endhighlight %}

Your directory structure should now have two `README.md` files and `hello.sh` (you can
use `ls -R ~/PHY432` to check):

~~~
~/PHY432/
  ├── 01_shell
  │   ├── Documents
  │   │   └── work
  │   │       ├── TODO
  │   │       └── lesson
  │   ├── README.md        <---- should be present
  │   ├── hello.sh         <---- should be present
  │   └── data
  └── 02_git
      └── README.md        <---- should be present
~~~

#### <span class="label" style="background: black">Activity</span> Initializing a repository with `git init` ####

Turn the `PHY432` directory into **repository** with the `git init` command:

{% highlight bash %}
cd ~/PHY432
git init
{% endhighlight %}

That's it. Although, not much happened yet... except, check with

{% highlight bash %}
ls -la
{% endhighlight %}

A new hidden directory `~/PHY432/.git/` appeared. This is your actual
repository (or database) where Git stores all its information. **Do
not change anything in this directory** (unless you really know what
you are doing) and **do not delete the `.git`** directory. If you
delete it, your repository is irrevocably gone (and there is no undo
for that!).

Now try the (possibly) most-used git command:

{% highlight bash %}
git status
{% endhighlight %}

which gives
~~~
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	01_shell/
	02_git/
~~~

... but what does it mean? For this
[gobbledygook](https://www.merriam-webster.com/dictionary/gobbledygook)
to make sense we need to know about *the three stages of git*:


### The three states of Git ###

For Git, a file can reside in one of *three states*

- **Modified** means that you have changed the file but have not
  committed it to your database yet; the file is in the **working directory**. 
- **Staged** means that you have marked a modified file in its current
  version to go into your next commit snapshot; it lives in the
  **staging area** [^5].
- **Committed** means that the data is safely stored in your local
  database (the **git repository** in the `.git` directory).

![Git working tree, Staging Area, and repository (database). (Source: https://git-scm.com/book/en/v2)](https://git-scm.com/book/en/v2/images/areas.png)

The *basic Git workflow*:
1. modify files in working directory
2. selectively stage changes that you want to include in your next
   commit (adds only those files to the staging area)
3. commit your changes (takes files from the staging area and stores
   them permanently in your Git repository)


### <span class="label" style="background: black">Activity</span> Adding files ###

Prepare the modified files to be committed to the repository: `git
add` adds files and directories to the *staging area*:


{% highlight bash %}
git add 02_git 01_shell/hello.sh
git status
{% endhighlight %}


Add more files and directories:
{% highlight bash %}
git add 01_shell
git status
{% endhighlight %}


(Use `git reset FILENAME` to unstage any files that you might have
added accidentally. For instance, do not add backup files that were
created by your editor.)

The files are not committed yet. You can do more work, add more files
and directories...


### <span class="label" style="background: black">Activity</span> Committing ###
Check-in (or **commit**) your changes to your git repository:

{% highlight bash %}
git commit
{% endhighlight %}

* When your editor pops up, enter a **commit message**: Convention:
  - first line (<60 char): one line summary
  - second line: blank
  - third and following lines: more details
  The first line is mandatory (you cannot have a commit without a
  message), the rest is optional. *The commit message should
  succinctly summarize the changes in the commit.*
  
  As an example, the following would make a good message:
  
  ~~~
  initial commit of PHY432 class work
  
  * lesson 01 on shell
  * lesson 02 on git
  ~~~
  
* After you wrote and saved the message ("save" in `code`, `^O` in
  `nano`; `i` to write and `ESC :wq` to save and exit in `vim`) and
  exited ("exit" in `code`, `^X` in `nano`), your changes will be
  committed to the repository.
* You can also supply the message as an argument: `git commit -m "one
  line summary of changes"`.
* **If you are having problems to make `git commit` with your editor
  work** then instead use `git commit -m 'one line summary message'`
  and debug this problem later.[^1]
* Check the status with `git status`...

For a new commit, [add files](#adding-files) and [commit](#committing)
again.

For good measure:
{% highlight bash %}
git commit
{% endhighlight %}
should show that you have no uncommited changes in your working directory.

### <span class="label" style="background: black">Activity</span> History

Git stores complete snapshots of your working tree in the repository:
each version (or commit) can be used to recreate an exact state of all
your files:

![Git checkins over time are snapshots of the WHOLE project. (Source: https://git-scm.com/book/en/v2)](https://git-scm.com/book/en/v2/images/snapshots.png)


Read the history with

{% highlight bash %}
git log
{% endhighlight %}



### Removing and renaming files

Removing files and directories via git allows you to get them back later.

{% highlight bash %}
git rm FILENAME
git rm -r DIRECTORY
{% endhighlight %}

Renaming is the same as removing the old file and adding the new one
but there is also a simple command

{% highlight bash %}
git mv OLD NEW
{% endhighlight %}

The `git rm` and `git mv` commands are similar to the `git add`
command in that they stage these changes; you still have to
[commit](#committing) them.


### Working with remote repositories

Repositories can live in your local file system or remotely on another
server ("in the cloud"). Git provides a way to synchronize local and
remote repositories.

There's nothing special about remote repositories. They do not really
differ from your local repository. Git is a *distributed version
control system* and any repository holds all the relevant history.

There exist many services that host remote repositories "in the
cloud". One of them is [GitHub](https://github.com) (which we use for
this class).[^7]


#### <span class="label" style="background: black">Activity</span>  Initializing from remote: `git clone`

To initialize a local repository from a remote source we use `git clone`:

{% highlight bash %}
git clone URL
{% endhighlight %}

For instance, let's clone the class repository where code and data
will be posted by the instructor:

{% highlight bash %}
cd ~
git clone {{ site.resources.giturl }}
cd {{ site.resources.shortname }}
{% endhighlight %}

Note:

* The local name of your repository can be any name you like but it is
  customary (and less confusing) if you go with the default, which is
  the remote repository name without the ".git" suffix, i.e.,
  *{{ site.resources.shortname }}* for us.
* For all other `git` commands you *must* be *inside* your local
  repository:

  ```bash
  cd ~/{{ site.resources.shortname }}
  ```

#### Getting changes (reading): `git pull`

Update your local repository with any "upstream" changes by
**pulling** from the remote repository:

{% highlight bash %}
git pull
{% endhighlight %}

#### Updating the remote (writing): `git push`

If one has write access to a remote repository then one can also
update the remote repository with local changes (commits) by
**pushing** all commits that the local repository has:

{% highlight bash %}
git push
{% endhighlight %}

(This will *not* work for *{{ site.resources.shortname }}* because only instructors
have write access but we will use it below for [your own GitHub
repositories](#set-up-your-own-github-repositories)).



## Set up your own GitHub repositories ##

Let's set up a remote repository for your work in the class. 

### <span class="label" style="background: black">Activity</span> Create GitHub repo and authentication ###

0. You might already have created the `~/PHY432` directory in an earlier lesson. If this is the
   case then your `mkdir ~/PHY432` command will fail. That's ok. Just use the directory that
   you have.
1. Go to <https://github.com> and create a new account. It is
   free.[^2] Remember your
   GitHub **username** and the **password**.
2. Create a new repository *PHY432* (do not initialize it with a
   README or other file). You can make it *private* if you like.
3. Note the repository URL
   https://github.com/USERNAME/PHY432.git   
4. Set-up **authentication** with a [Personal Access
   Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
   [^3].
   
   Follow the instructions to [create a
   token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-token).
   
   - Name it "PHY432 class" (something that tells you what to use
     it for).
   - You can set an expiration date at the end of the class in May
	 (as a security precaution).
   - For *scope* select only **repo**.
   - Generate the token. (It will look like "ghp_6HA...6i5Dy".)
   
   - *Copy the token*, you will only see it *once*. 
	 Store it in a safe place.
	 {: .text-red-300 }
	 
   - **Warning**: Treat the token like a password and keep it
	 **secret**.
	 {: .text-red-300 }	 


   When you need to authenticate yourself in order to work with your
   GitHub repositories you will enter
   - your *username* for username
   - your *personal access token* instead of a password
   
   You can always regenerate a new token.
   
   
### <span class="label" style="background: black">Activity</span> Link local and remote repositories ###

We now have to set the newly created, empty GitHub repository as the remote repo for your local one:

1. Add the remote repository to your local repository `~/PHY432`
   (replace *USERNAME* with your GitHub username) [^8]:

   ```bash
   git remote add origin https://github.com/USERNAME/PHY432.git
   ```

   We named the remote "origin", which is a common choice for the main
   repository. You can have many different remotes, just give them
   different names. You can list them with

   ```bash
   git remote -v
   ```

2. Traditionally, git used the name "master" for the main branch of
   the work. However, this name is falling rapidly out of favor and
   newer version of git default to the name **"main"**. 
   
   If you have a version of git that insists on "master", rename our
   branch to "main":

   ```bash
   git branch -M main
   ```

   (You only have to do this once.)


### <span class="label" style="background: black">Activity</span> Update (push) local content for the first time ###

**push** your local history to the remote repository:

{% highlight bash %}
git push --set-upstream origin main
{% endhighlight %}

Look at the web interface at
https://github.com/USERNAME/PHY432 and see your changes
appear.

You only need the `--set-upstream origin main` (or `-u origin main`) for the
first time (it tells git which "branches" to associate with each other in local
and remote) [^4]. 

### <span class="label" style="background: black">Activity</span> Update (push) local content ###

For the rest of the semester, commit what you did during each class
session to the `~/PHY432` repository on your laptop (and also push
to your GitHub repository as a backup).

**Note**
{: .label .label-yellow .float-left .text-grey-dk-300 }
Your GitHub repository is for in-class work. Do not commit homeworks
there; you will receive *private* repositories for the duration of the
class for this purpose.


All further push operations will simply be

```bash
git push
```

Try out the following
1. update your `01_shell/hello.sh` script with a second line `echo "Good bye,
   $USER"`.
2. stage your changes 

   ```bash
   git add 01_shell/hello.sh
   ```

3. commit changes

   ```bash
   git commit -m 'add bye to hello script'
   ```
		
4. push changes to remote repository

   ```bash
   git push
   ```


## Using git in PHY432 ##

For the class we will use git and GitHub in multiple ways:

- Homework assignments and Participation Activities will be provided as
  repositories (using GitHub Classroom) and you will submit your work by
  pushing your solutions to a remote repository.
- Projects will be submitted to repositories.
- Materials for the class will be made available in the **resources**
  repository [{{ site.resources.name }}]({{ site.resources.url }}). 
  
  The notes on the [PHY432 workflow]({{ site.baseurl }}/{% link
  modules/git/phy432_workflow.md %}) describe in more detail how you should use
  the resources repository and your own `~/PHY432` workspace.
- You should push your own work that you do during the class in your workspace
  to [your own (private) PHY432
  repository](#set-up-your-own-github-repositories).



## Contributing to Open Source on GitHub ##

[GitHub](https://github.com) is a provider for remote repositories. It
enables you to easily contribute to other projects. This includes

* filing bug reports or feature requests (*raising issues*); for
  instance, if you do not agree with some of the Star Wars data from
  the previous lessons, raise an issue in the
  [issue tracker for the PHY494-auxilliary repository](https://github.com/ASU-CompMethodsPhysics-PHY494/PHY494-auxilliary/issues).
* proposing to add your own code and changes through
  *[pull requests](https://help.github.com/articles/using-pull-requests/)*
  (but this is too advanced for a our short introduction today --- see
  the additional resources under [More...](#more)).


## More... ##

* For a longer introductory tutorial see the Software Carpentry lesson on
  [Version Control with Git](https://swcarpentry.github.io/git-novice/).
* [Resources to learn Git](https://try.github.io/), including cheat sheets.
* Blischak JD, Davenport ER, Wilson G
  (2016). [A Quick Introduction to Version Control with Git and GitHub](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668). PLoS
  Comput Biol 12(1): e1004668. doi:10.1371/journal.pcbi.1004668 
* For in-depth discussion read the
  [Pro Git](https://git-scm.com/book/) book by Scott Chacon and Ben
  Straub.
  
------------------------------------------------------------
  
## Footnotes

[^0]:

     Acknowledgements: This lesson uses ideas from Software
     Carpentry's
     [Version Control with Git](https://swcarpentry.github.io/git-novice/)
     and includes an image from Jorge Cham's
     [PhD Comics](http://www.phdcomics.com/)
     ["FINAL".doc](http://www.phdcomics.com/comics.php?n=1531) (which
     is &copy; 2012 Jorge Cham). It also uses images and ideas from
     [git-scm.com](https://git-scm.com) (used under the [Creative
     Commons Attribution 3.0 Unported
     License](https://creativecommons.org/licenses/by/3.0/)) and from 
     [git-scm.com/book](https://git-scm.com/book) (used under the 
     [Creative Commons Attribution Non Commercial Share Alike 3.0
     license](https://creativecommons.org/licenses/by-nc-sa/3.0/)).

[^1]:

     See also Software Carpentry's list of
     [git configuration options for different
	 editors](https://swcarpentry.github.io/git-novice/02-setup/) and 
     [Associating text editors with
     Git](https://help.github.com/articles/associating-text-editors-with-git/)
     for details, especially for *Visual Studio Code*.

	 For problems with setting up editors in Windows, see the
     StackOverflow question
     [How can I set up an editor to work with Git on Windows?](https://stackoverflow.com/questions/10564/how-can-i-set-up-an-editor-to-work-with-git-on-windows)
     as a starting point for various recipes.
	 
[^2]:

     An unlimited number of *public* (i.e., visible for everyone)
     repositories are free on GitHub but private repositories cost
     money. However, if you use your school email address
     (e.g. @asu.edu) you can also get private
     repositories for free through the
     [GitHub educational
    discount](https://help.github.com/en/github/setting-up-and-managing-billing-and-payments-on-github/discounted-subscriptions-for-github-accounts);
    see also the [GitHub Education](https://education.github.com/) site.
	 
[^3]:

     There are ways to set up remote repositories so that you don't
     have to provide username and password for every push and which
     are also more secure. Namely one can use SSH keys instead of the
     HTTPS protocol, as described in the GitHub tutorial on
     [Generating SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).

[^4]:

    *Branching* is a more advanced topic, which is explained in the
    materials linked under [More...](#more). We barely scratched the
    surface of Git but this will be sufficient to already make good
    use of this very powerful tool.

[^5]:

    Technically, the *staging area* (or *index*) is also located in
    the `.git` directory but that is not really
    relevant. Conceptually, the staging area is different from the Git
    repository. See more in Git Pro under [Gettings Started – Git
	Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics).
	 
[^7]:

    Other commonly used git repository hosters are
    [https://gitlab.com](https://gitlab.com) and
    [https://bitbucket.org/](https://bitbucket.org/).
    
[^8]:

    If you do not want to have to enter your username and password
    every time you do a remote operation, you can also store username
	and access token in the remote name. In the following, replace
    *USERNAME* with your GitHub username and  *TOKEN* with
    your personal access token
   
         git remote add origin https://USERNAME:TOKEN@github.com/USERNAME/PHY432.git

    (*USERNAME* and *TOKEN* are separated by a colon "`:`" and
	prefixed to the URL with the "at" "`@`" character.)
	
	If you want to replace your remote setting then use `set-url`:
   
         git remote set-url origin https://USERNAME:TOKEN@github.com/USERNAME/PHY432.git
   
    **WARNING** 
	{: .label .label-red .float-left }
	Note that storing your token in this way exposes it
    to anyone who can get hold of your computer because it is stored
    in clear text in the `.git` repository and is visible with `git
    remote -v`.
	{: .text-red-300 }
