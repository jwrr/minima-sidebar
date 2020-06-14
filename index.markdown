---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title : Inline TOC Demo
layout: home
---

Why?
----

Minima is the default jekyll theme.  It does most of what I want. Except I
couldn't figure out how to put the table of contents into the sidebar.  So
I hacked the Minima theme.  There's probably better ways to do what I want,
but this works for me.

<button class="favorite styled" type="button">
  <a href="https://github.com/jwrr/minima-sidebar">Clone It</a>
</button>

Below is a demonstration of the inline TOC that is available in minima. It
takes up a significant amount of above-the-fold page space.

Table of Contents
-----------------
* TOC
{:toc}

This is an example of an inline Table of contents.  Just paste the following 
into your page.

```
* TOC
{:toc}
```

Examples
--------
Check out [Sidebar](/sidebar-toc), [Sidebar2](/sidebar-toc2) and [Sidebar Fixed](/sidebar-fixed) for more 
examples.


How to Use
---------

### Clone it
If you're creating a Github.io Page for your user account then you should `git clone` and specify
you top-level git repo, `username.github.io` where username is your Github username.

```
git clone https://github.com/jwrr/minima-sidebar username.github.io
cd username.github.io
```

If you're creating a page for a projec then you should always specify `docs` as the repo
destination.

```
cd your_project
git clone https://github.com/jwrr docs
cd docs
```

### Try it
Run the Jekyll Server using script `JEKYLL_SERVE` and press `Ctrl+C` when done.

```
JEKYLL_SERVE
```

### Configure it
Edit the site configuration file, `_config`, search for `FIXME` and change the 
settings as needed.

### Remove .git
If this is your user page then skip this.  If this is a project page (in the 
`docs` folder) then remove the `.git` folder (unless you want this as a submodule,
which is unlikely).

```
cd docs
rm -rf .git
```

### Git Add, Commit and Push
Finally, It's time to wrap it up.

```
git add Gemfile.lock assets/main.scss 404.html index.markdown Gemfile README.md _config.yml _debug.yml JEKYLL_SERVE
git commit -m "Create Github.io Page"
git push

```


Jekyll Serve
------------

You can view this repo locally with the following command (I'm assuming you've
already installed [jekyll](https://jekyllrb.com/docs/) and cloned this repo.

```
jekyll serve --trace
```

### Load Error
You may get an error similar to the following:

```
/usr/lib/ruby/2.7.0/bundler/runtime.rb:312:in `check_for_activated_spec!': You 
have already activated rouge 3.20.0, but your Gemfile requires rouge 3.19.0. 
Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
```

This means the `gem.lock` file is out of date.  To fix run the following 
command.  You may have to iterate multiple times if more than one gem is 
out of date.

```
bundle update rouge
```

Please send me a pull request with your fix.

### Jekyll Serve Page Not Found
This is sometimes caused when baseurl (in _config.yml) is not correct.
When you're working on your user page (for example jwrr.github.io) then
baseurl should be "". When you're working on a project page (for example
jwrr.github.io/minima-sidebar) then baseurl should be "/projname" when
the page is publically displayed on Github.  **BUT** when the page is
being displayed locally with `jekyll serve` the baseurl should be "".
A script, `JEKYLL_SERVE` takes care of this for you and is recommended.

```
> JEKYLL_SERVE
```


Lorem Ipsum
-----------

You can ignore the following documentation.  I'm using the
[Lued Text Editor](https://jwrr.github.io/lued/)
documentation as Lorem Ipsum.


<hr>


What is it?
-----------

Lued is a text editor that runs in the console like [emacs](https://www.gnu.org/software/emacs/)
and [vim](https://www.vim.org/).  The goal is to be comfortable 
for Windows users.  Common Windows keystrokes are supported.  For example,
<kbd>Ctrl+C</kbd>, <kbd>Ctrl+X</kbd>, <kbd>Ctrl+V</kbd> do copy, cut and paste, 
respectively. <kbd>Ctrl+Z</kbd> and <kbd>Ctrl+Y</kbd> undo and redo. 
<kbd>Ctrl+S</kbd>, <kbd>Ctrl+Q</kbd> save and quit. You move arrow using the 
arrow keys. PgUp, PgDn, Home and End work as expected. For more advanced 
commands, Lued attempts to be similar to [Sublime](https://www.sublimetext.com/)
or [VScode](https://code.visualstudio.com/).  You can use the
mouse to copy and paste and the scroll wheel lets you easily navigate up
and down the document.
 
Lued is compatible with most xterms such as Konsole and Gnome Terminal. It also
works well with [PuTTy](https://www.chiark.greenend.org.uk/~sgtatham/putty/)
and [tmux](https://github.com/tmux/tmux).


Get it
------

Lued source code is available under the [MIT License](https://opensource.org/licenses/MIT)
at [github.com/jwrr/lued](http://github.com/jwrr/lued).  You can download a zip file or 
clone the repo.

<button class="favorite styled" type="button">
  <a href="https://github.com/jwrr/lued/archive/master.zip">Download Lued from Github</a>
</button>

```
git clone https://github.com/jwrr/lued
```

Build it
--------

To build Lued just run the <code>COMPILE</code> script.  The script handles downloading Lua 5.2, applying
a few minor patches to the Lua release, running cmake and compiling lued.

You will need cmake.  On Ubuntu you can install with apt-get.

```
sudo apt-get -y install cmake
```

Try it
------

```
> ./lued filename.txt
```


Use it
------

You've gotten this far and you haven't turned away.  You want to know more.
Lued offers many ways to move, select, find and delete. I recommend you first
take a quick look at the [key bindings](/bindings).  And then dive into the
[User Guide](/ug).


Tweak it
-----------------------

You can easily change the key bindings.  The key bindings are defined in file
`lua_src/bindings/lued_bindings.lua`.  The bindings have the format alt_xxx and
ctrl_yyy (these are actually lua function calls but don't worry about that).  To 
change a binding, just find it and replace it with what you want.  For example,
say you want to change the replace to end-of-line command from <kbd>alt+XE</kbd> to
<kbd>ctrl+K</kbd>, as it is in Emacs.  You would open the lued_bindings.lua file
(using lued or your editor of choice), find 'alt_xe', <kbd>ctrl+F</kbd> and change
it to 'ctrl_K'.  Now restart lued and you're good to go. BTW, <kbd>Ctrl+K</kbd>
is not currently used, and is waiting for you to make this change.


Extend it
---------

All commands are implemented in Lua (there's some C under the hood but you'll 
never see it... unless you want to).  Lua is an easy to learn scripting language that
is powerful and blazingly fast.  You can modify the Lua code directly or you 
can develop a plugin (also written in Lua).  The plugins support 
[emmet](https://emmet.io/) snippets where you type a user-defined tag followed 
by <kbd>Tab</kbd> and a pre-defined template is printed out.


Fix it
------

Submit your [pull requests](https://github.com/jwrr/lued/pulls). Thanks


<hr style="margin-top:4em;">







