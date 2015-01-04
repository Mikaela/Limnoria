---
layout: page
title: Security issues
permalink: /Supybot.html
---

All activity happens in git repository of Supybot nowadays and it happens 
seldomly. The latest version, which was released in 2009 is 0.83.4.1 
has multiple security issues documented here. This version is available 
from Debian repositories, Ubuntu repositories and repositories of many 
other Linux distributions.

## The issues of 0.83.4.1.

### 1. Anyone can crash it and computer where it's running on

And this is very easy. Just run the command 

```
!misc last --regexp m/(.*\w){512}/
```

where ! is the prefix character.

Misc is loaded by default and cannot be unloaded without modifying the
config.

* [Ubuntu bug #996947](https://bugs.launchpad.net/ubuntu/+source/supybot/+bug/996947)
* [Debian bug #672214](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672214)

### 2. The previous wasn't the only way to do this

Everyone can also make the bot count an equation, which brings it and the
host computer down. 

For example:

```
!math calc factorial(999999)
```

This requires Math plugin which comes with Supybot, but isn't load by 
default.

* [Ubuntu bug #996950](https://bugs.launchpad.net/ubuntu/+source/supybot/+bug/996950)
* [Debian bug 672215](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672215)

### 3. Anyone can access network services via the bot.

I don't have example command for this, but it happens by nesting 
"format cut" and "misc tell".

What does this mean? Anyone can tell the bot to ghost someone else on same
account, take over a channel by telling the bot to give flags
(if it has correct flags), change password of the account and everything
else what you do with network services.

### 4. Web page with special characters in \<title\> can be used to send DCC/CTCP commands.

This doesn't mean only things like CTCP actions (also known as /me),
but known problems with old routers
( `FF ? DCC SEND “ff???f??????????????” 0 0 0` ) which make them reconnect
to the internet.

Usage:

```
!web title <malicious.page.here>
!web fetch <malicious.page.here>
```

### 5. Web Titlte/Fetch can be used for DoS

They are vulnerable to queries to servers which have custom headers
which can lead to DoS.

### 6. QuoteGrabs grab command also works in PM

and can grab private content such as `user register` or `user identify` or
with the case of owner possibly NickServ passwords and others not so nice
things.

### Are these issues publicly known?

**Of course they are.** Issue reports are below the actual issues.

The first issue has been also used to take down some of
[Ubuntu IRC bots](https://wiki.ubuntu.com/IRC/Bots) several times.
At least UbotX (I don't remember the number) and meetingology.

Some of these issues are fixed in git repository, but most people aren't
using it. If you wish to start using it, please scroll down to
installation instructions lower this page even though [Limnoria] and
[gribble] are more recommended.

### How to avoid them?

You can add anticapability for these commands using
`owner defaultcapability`, but that is only a temporary solution.
There can also be other issues.

There are also two active Supybot forks, known as [Limnoria] and
[Gribble], which are actively developed and have fixed these issues.
If you want permanent solution, you should install either of them.

## Interesting things

* [Comparsion of commit activity between Limnoria, Gribble and Supybot](https://www.openhub.net/p/compare?project_0=Limnoria&project_1=Gribble%3A+Support+Bottie&project_2=Supybot).
* [Gribble's modifications to stock Supybot](https://sourceforge.net/p/gribble/wiki/Gribble_Project_Git_Repository/)
    * SourceForge and that link are a little broken, when they are moved 
    elsewhere, please remove this notice!
* [Limnoria's modifications to Gribble.](https://github.com/ProgVal/Limnoria/wiki/LGC) 
    * Features of Gribble are fully merged to Limnoria.

Your current botname.conf is **100% compatible with forks**.

[Join Supybot channels on freenode!](ircs://chat.freenode.net:6697/#supybot,#gribble,#limnoria)

[Limnoria]:https://github.com/ProgVal/Limnoria
[Gribble]:http://github.com/nanotube/supybot_fixes

## Installing forks

*This section has been removed in order to not duplicate
[Limnoria's documentation.](http://doc.supybot.aperio.fr/en/latest/use/install.html)*
