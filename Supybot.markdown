---
layout: page
title: Security issues
permalink: /Supybot.html
---

<!-- @format -->

Supybot git repository was declared dead on 2018-05-10 and archived on GitHub.
[v0.84.0 was the last release at that time](https://github.com/Supybot/Supybot/releases/tag/v0.84.0).
0.83.4.1 used to be a very common release available through several Linux
distributions for years and thus I made this page, which I guess is now
available more of for historical reasons.

**_WARNING: most of the content originates from 2014!_**

## The issues of 0.83.4.1.

### 1. Anyone can crash it and computer where it's running on

And this is very easy. Just run the command

`!misc last --regexp m/(.*\w){512}/`

where ! is the prefix character.

Misc is loaded by default and cannot be unloaded without modifying the config.

- [Limnoria issue #157](https://github.com/ProgVal/Limnoria/issues/157)
  - Fixing commits:
    [3526d5d](https://github.com/ProgVal/Limnoria/commit/3526d5dabf587457a43af8bee8d4db21986e8222)
    &
    [e11dc28](https://github.com/ProgVal/Limnoria/commit/e11dc28025de877b1b6cf059013eef88337b7e44)
- [Ubuntu bug #996947](https://bugs.launchpad.net/ubuntu/+source/supybot/+bug/996947)
- [Debian bug #672214](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672214)

### 2. The previous wasn't the only way to do this

Everyone can also make the bot count an equation, which brings it and the host
computer down.

For example:

`!math calc factorial(999999)`

This requires Math plugin which comes with Supybot, but isn't load by default.

- [Limnoria issue #354](https://github.com/ProgVal/Limnoria/issues/354)
  - Fixing commit:
    [695078e](https://github.com/ProgVal/Limnoria/commit/695078edeb91e5ff1eec728fedf0e0c27b55c505)
- [Ubuntu bug #996950](https://bugs.launchpad.net/ubuntu/+source/supybot/+bug/996950)
- [Debian bug 672215](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672215)

### 3. Anyone can access network services via the bot.

I don't have example command for this, but it happens by nesting "format cut"
and "misc tell".

What does this mean? Anyone can tell the bot to ghost someone else on same
account, take over a channel by telling the bot to give flags (if it has correct
flags), change password of the account and everything else what you do with
network services.

- _This was only reported at IRC and I am unable to find issue report or fixing
  commit. ~~Mikaela on 2015-01-04._

### 4. Web page with special characters in \<title\> can be used to send DCC/CTCP commands.

This doesn't mean only things like CTCP actions (also known as /me), but known
problems with old routers ( `FF ? DCC SEND “ff???f??????????????” 0 0 0` ) which
make them reconnect to the internet.

Usage:

- `!web title <malicious.page.here>`
- `!web fetch <malicious.page.here>`

_This was only reported at IRC and I am unable to find issue report or fixing
commit. ~~Mikaela on 2015-01-04._

### 5. Web Titlte/Fetch can be used for DoS

They are vulnerable to queries to servers which have custom headers which can
lead to DoS.

_This was only reported at IRC and I am unable to find issue report or fixing
commit. ~~Mikaela on 2015-01-04._

### 6. QuoteGrabs grab command also works in PM

and can grab private content such as `user register` or `user identify` or with
the case of owner possibly NickServ passwords and others not so nice things.

- _It appears this issue was only reported at IRC._
  - Fixing commit:
    [a3346343679f3bdf8c77d9efb5a2097e215d51df](https://github.com/ProgVal/Limnoria/commit/a3346343679f3bdf8c77d9efb5a2097e215d51df)

### Are these issues publicly known?

**Of course they are.** Issue reports are below the actual issues.

The first issue has been also used to take down some of
[Ubuntu IRC bots](https://wiki.ubuntu.com/IRC/Bots) several times. At least
UbotX (I don't remember the number) and meetingology.

Some of these issues are fixed in git repository, but most people aren't using
it. If you wish to start using it, please scroll down to installation
instructions lower this page even though [Limnoria] and [gribble] are more
recommended.

### How to avoid them?

You can add anticapability for these commands using `owner defaultcapability`,
but that is only a temporary solution. There can also be other issues.

There are also two active Supybot forks, known as [Limnoria] and [Gribble],
which are actively developed and have fixed these issues. If you want permanent
solution, you should install either of them.

## Possibly interesting links

- [Comparsion of commit activity between Limnoria, Gribble and Supybot](https://www.openhub.net/p/compare?project_0=Limnoria&project_1=Gribble%3A+Support+Bottie&project_2=Supybot).
- [Gribble's modifications to stock Supybot](https://sourceforge.net/p/gribble/wiki/Gribble_Project_Git_Repository/)
- [Limnoria's modifications to Gribble.](https://github.com/ProgVal/Limnoria/wiki/LGC)
  - Features of Gribble are fully merged to Limnoria.

Your current botname.conf is **100% compatible with forks**.

[Join Supybot channels on LiberaChat!](ircs://irc.libera.chat:6697/#supybot,#gribble,#limnoria)

[Limnoria]: https://github.com/ProgVal/Limnoria
[Gribble]: http://github.com/nanotube/supybot_fixes

## Installing forks

_This section has been removed in order to not duplicate
[Limnoria's documentation.](http://doc.supybot.aperio.fr/en/latest/use/install.html)_

---

Do you know issue that isn't mentioned here? If it's not already reported,
please report it
on [Limnoria's issue tracker.](https://github.com/ProgVal/Limnoria/issues) If
it's known, but just not reported here,
[please feel free to add it.](https://github.com/Mikaela/limnoria/edit/gh-pages/Supybot.markdown)
