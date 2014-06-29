<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<meta name="description" content="Supybot security issues," />
<meta name="keywords" content="Security,Issues,Supybot,crash,Debian,Ubuntu,IRC" />
<meta name="author" content="Mikaela Suomalainen" />
<link rel="canonical" href="https://mkaysi.github.io/limnoria/Supybot.html">
<title>Security issues of Supybot</title>
<link rel="stylesheet" type="text/css" href="css.css" />
<script>
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','//www.google-analytics.com/analytics.js','ga');
ga('create', 'UA-40171169-1', 'mkaysi.github.io');
ga('send', 'pageview');
</script>
</head>
<body>

All activity happens in git repository of Supybot nowadays and it happens 
seldomly. The latest version, which was released in 2009 is 0.83.4.1 
has multiple security issues documented here. This version is available 
from Debian repositories, Ubuntu repositories and repositories of many 
other Linux distributions.

**Note: Development has moved from SourceForge to GitHub so I won't refer 
to the old SF page.**

## The issues of 0.83.4.1.

### 1. Anyone can crash it and computer where it's running on

And this is very easy. Just run the command 

```
!misc last --regexp m/(.*\w){512}/
```

where ! is the prefix character.

Misc is loaded by default and cannot be unloaded without modifying the 
config.

### 2. The previous wasn't the only way to do this

Everyone can also make the bot count an equation, which brings it and the 
host computer down. 

For example:

```
!math calc factorial(999999)
```

This requires Math plugin which comes with Supybot, but isn't load by 
default.

### 3. Anyone can access network services via the bot.

I don't have example command for this, but it happens by nesting 
"format cut" and "misc tell". 

What does this mean? Anyone can tell the bot to ghost someone else on same 
account, take over a channel by telling the bot to give flags 
(if it has correct flags), change password of the account and everything 
else what you do with network services.

### 4. Web page with special characters in <title> can be used to send DCC/CTCP commands.

This doesn't mean only things like CTCP actions (also known as /me), 
but known problems with old routers ( `FF ? DCC SEND “ff???f??????????????” 0 0 0` ) 
which make them reconnect to the internet.

Usage:

```
!web title <malicious.page.here>
!web fetch <malicious.page.here>
```

### Are these issues publicly known?

**Of course they are.** They have been reported to

* [Ubuntu](https://ubuntu.com)
    * [issue 1](http://pad.lv/996947])
    * [issue 2](http://pad.lv/996950)
* [Debian](https://debian.org/)
    * [issue 1](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672214)
    * [issue 2](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672215)
* [#supybot](ircs://chat.freenode.net:6697/#supybot)


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

I recommend [Limnoria], because it seems to be more active 
(activity of [Gribble] isn't announced anywhere) and it has additional 
commands, translations and new plugin called [PluginDownloader], which 
makes installing of 3rd party plugins easy. 

Ohloh supports comparing different projects, [here is comparsion of Limnoria, Gribble and Supybot](https://www.ohloh.net/p/compare?project_0=Limnoria&project_1=Gribble%3A+Support+Bottie&project_2=Supybot).

[Gribble modifications when compared to stock Supybot](https://sourceforge.net/p/gribble/wiki/Gribble_Project_Git_Repository/)

**SourceForge and that link are a little broken, when they are moved 
elsewhere, please remove this notice!**

[Limnoria modifications when compared to Gribble.](https://github.com/ProgVal/Limnoria/wiki/LGC) 
Features of Gribble are fully merged to Limnoria.

Your current botname.conf is **100% compatible with forks**.

[Join Supybot channels on freenode!](ircs://chat.freenode.net:6697/#supybot,#gribble,#limnoria)

[Limnoria]:https://github.com/ProgVal/Limnoria
[Gribble]:http://github.com/nanotube/supybot_fixed
[PluginDownloader]:https://github.com/ProgVal/Limnoria/tree/master/plugins/PluginDownloader

## Installing forks

### For all of them.

You should install [pip] (usually python-pip in repositories) and [git].

Windows users should also install [pip] and [msysgit] and in [msysgit] 
select to run **unix tools in PATH**.

Note: pip is included with Python =< 3.4! Python 3 is only supported by 
Limnoria.

For **rootless installation and upgrading**, please see 
[Limnoria's documentation.](http://supybot.aperio.fr/doc/use/install.html#local-installation) which you should be able to modify to install stock 
Supybot or gribble with the information below.

If you don't have sudo, please simply remove it from beginnings of lines 
and run the commands as root or Administrator.

[git]:http://git-scm.com/
[pip]:http://pip.readthedocs.org/en/latest/reference/pip_install.html
[msysgit]:https://msysgit.github.io/

### Supybot

**Not recommended as it's not actively developed.**

```
sudo pip install git+https://github.com/supybot/supybot.git
```

### gribble

Less actively developed than Limnoria and doesn't support Python 3.

```
sudo pip install git+https://github.com/nanotube/supybot_fixes.git
```

### Limnoria

At the time of writing, the most active Supybot fork which includes 
embedded HTTPd for plugins needing it, supports other languages than 
English and also runs with Python 3.

The first command installs requirements of Limnoria and the second 
Limnoria itself. Only Limnoria has requirements.txt file at the moment.

```
sudo pip install -r https://raw.githubusercontent.com/ProgVal/Limnoria/master/requirements.txt
sudo pip install git+https://github.com/ProgVal/Limnoria.git@master
```

<hr/>
[Changelog of this page.]()https://github.com/Mkaysi/Limnoria/commits/gh-pages/Supybot.html
<hr/>
</body>
</html>
