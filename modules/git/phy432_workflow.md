---
layout: default
title:  PHY432 git workflow
parent: Tools
nav_exclude: true
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## PHY432 Workflow: Resources and Workspace ##

Code, notebooks, and files are being made available on GitHub in the
**resources** repository
[{{ site.resources.name }}]({{ site.resources.url }}).
For the rest of the semester it will be assumed that you have a
`~/{{ site.resources.shortname }}` repository that you can update with a simple `git
pull` as soon as new material is posted.

If you have not [done so already]({{ site.baseurl }}/{% link
modules/git/Git_basics.md
%}#activity--initializing-from-remote-git-clone), clone `~/{{
site.resources.shortname }}`:

{% highlight bash %}
cd ~
git clone {{ site.resources.giturl }}
{% endhighlight %}

You should also [have your own **workspace** repository `~/PHY432` set
up]({{ site.baseurl }}/{% link modules/git/Git_basics.md
%}#activity-set-up-your-own-github-repositories).
 
### Overview ###

When we start a new lesson you will typically go through the following steps to
get code and data files.

1. pull latest changes from {{ site.resources.shortname }}
2. copy the new directories and files into your workspace PHY432
3. work in your workspace
4. commit changes in your workspace
5. (optional) push changes in your workspace your GitHub repository

### Update resources ("pull resources") ###

Update when your instructor changed anything on the remote:

{% highlight bash %}
cd ~/{{ site.resources.shortname }}
git pull
{% endhighlight %}

Check what's new
{% highlight bash %}
ls -lt
{% endhighlight %}
(newest at top)

### Copy new files and directories to workspace ("copy resources") ###

You should not be changing anything inside `~/{{ site.resources.shortname }}`
(because the next `git pull` might try to change something that you
did [^6]) but instead *copy* whatever you want to change to your own work
directory.

For example:

{% highlight bash %}
cp -r ~/{{ site.resources.shortname }}/00_setup ~/PHY432
cd ~/PHY432/00_setup
{% endhighlight %}


{% comment %}
For example, in the
Fix as many bugs as possible! challenge you
would copy all the `bugs_*.py` files to your own `~/PHY432` repo and
work there:

{% highlight bash %}
cp -r ~/{{ site.resources.shortname }}/05_debugging ~/PHY432
cd ~/PHY432/05_debugging
{% endhighlight %}

{% endcomment %}


### Work, commit, push ###
Then work on the files **in the workspace**.

When you have changes that you want to track, `git add /
commit / push`:
{% highlight bash %}
git add .
git commit -m 'updated 00 setup files'
git push
{% endhighlight %}


------------------------------------------------------------
  
## Footnotes

[^6]:

    If you happen to have accidentally edited files inside
    `~/{{ site.resources.shortname }}` you might run into *merge conflicts* when you
    run `git pull` the next time. If that happens, copy *all files
    that you edited* (use `git status` to see which ones are modified)
    to a safe directory and then reset with the command

        cd ~/{{ site.resources.shortname }}
        # Next command only if you ran into a merge conflict
        # during a 'git pull'
        git merge --abort
        
        # undo ALL of YOUR changes
        git reset --hard HEAD

    **WARNING** 
	{: .label .bg-red-300 .float-left }
	This will undo *all your changes* but will allow you to
    just run the next `git pull` command again without problems.
    {: .text-red-300 }
