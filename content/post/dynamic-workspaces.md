+++
date = "2012-04-21T17:30:00-05:00"
draft = false
title = "Dynamic desktop workspaces"
author = "Andrew Gallant"
url = "dynamic-workspaces"
+++

Do you have dynamic workspaces in your window manager?

You might be wondering: what in the world are dynamic workspaces?
A dynamic workspace model allows one to add, remove or rename workspaces on the
fly.
Comparatively, in a typical window manager (or desktop environment)
configuration, you tell the window manager to have **x** number of workspaces.
When you start your window manager, you'll have **x** workspaces, and you can
typically cycle between them using some variation of "next workspace" or
"previous workspace" commands.
The disadvantage with this model is that it's difficult to have a large number
of workspaces---else you might forget which window is on each workspace.

<!--more-->

Another approach (if you have a particularly nice window manager) is to specify
the *names* of each workspace available to you.
This lets you segregate windows into nice groups.
Perhaps one workspace is named "web" and is dedicated to web browsing.
Perhaps another one is named "editing" and is full of vim windows.
And so on.
Named workspaces are useful because they are easier to manage in large
number---all one needs is to glance at the name of a workspace and you'll know
what kind of windows are there.

Dynamic workspaces extend upon the named workspace approach.
While named workspaces don't change in size or name, dynamic workspaces can.
Named workspaces encourage general groups like "web" or "editing",
dynamic workspaces encourage *task-oriented* groups.

For example, while developing this blog application, I created several
workspaces to manage windows related to development.
Namely, `blog`, `view` and `geils`.
`blog` contained terminals running vim for editing the source code, `view`
contained a browser window I used to view my changes and `geils` contained a
terminal logged into my web server (named
[Geils](http://en.wikipedia.org/wiki/J_Geils_Band)).
After I was done working on my blog, I simply deleted those three workspaces.
(I could also leave them there to come back to later---which is something I
often do with persistent projects like my [window
manager](https://github.com/BurntSushi/wingo).)

I really enjoy this approach to workspace management because it's so specific
to the tasks you're working on.
A static approach is too restraining for me; sometimes windows don't fit nicely
in each category you've created or sometimes you can't forsee how a certain
window will be used.
Additionally, sometimes you want to have more than one workspace dedicated to
some general task like "web".
But how many should you make up front?
Too few and you're restrained; but too many and you have unused workspaces
cluttering up your environment.

### Okay, you convinced me. How can I get dynamic workspaces?

Typically, your window manager has to support it.
[Xmonad](http://xmonad.org) comes to mind, as it has a
[DynamicWorkspaces](http://xmonad.org/xmonad-docs/xmonad-contrib/XMonad-Actions-DynamicWorkspaces.html)
module in
[xmonad-contrib](http://xmonad.org/xmonad-docs/xmonad-contrib/index.html).
I'd also be willing to bet that [Awesome](http://awesome.naquadah.org/) could
also do it, given its flexible Lua configuration (but I have never used Awesome
extensively).

If you're using [Openbox](http://openbox.org) (or possibly any EWMH compliant
window manager), I've developed
[a pager](https://github.com/BurntSushi/pager-multihead) that provides dynamic
workspaces.
(If you're using Archlinux, it's in the
[AUR](http://aur.archlinux.org/packages.php?ID=51536).)

The pager is configured in Python, and by default, `Super+Return` is bound to a
prompt that will show all available workspaces.
If you type in a workspace name that exists, you'll switch to that workspace.
If you type in a workspace name that *doesn't* exist, the pager will create
that workspace and switch you to it.
Finally, `Super+BackSpace` will delete a workspace (only when it doesn't have
any windows).

(If there's demand, I may write another post that describes my pager in more
detail. It actually has quite a few more nice features other than dynamic
workspaces.)

