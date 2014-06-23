<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<!-- <meta http-equiv="refresh" content="60" /> -->
<meta name="description" content="Ignoring unneeded messages from RelayBot the bot relaying \#Supybot between freenode and OFTC." />
<meta name="keywords" content="IRC Supybot Limnoria Gribble ignoring" />
<meta name="author" content="Mikaela Suomalainen" />
<link rel="canonical" href="https://mkaysi.github.io/limnoria/Relaybot.html">
<title>Ignoring nonimportant messages from RelayBot</title>
<link rel="stylesheet" type="text/css" href="css.css" />
</head>
<body>

RelayBot is the bot which relays between #supybot at freenode and oftc. It 
is currently using the [LinkRelay](https://github.com/ProgVal/Supybot-plugins/tree/master/LinkRelay) plugin to do this.

It's sometimes considered as annoyance as it has lately mostly spammed 
with join (part messages aren't working, because of a bug (2014-06-23)) 
messages of people who usually say nothing and this is why this page is 
here to tell how to ignore it on various client.

We encourage you to ignore only notices from RelayBot instead of 
everything as there are people whom should be heard at OFTC (mainly main 
Supybot developer).

Related links:

* [LinkRelay plugin](https://github.com/ProgVal/Supybot-plugins/tree/master/LinkRelay)
* [Feature request for smart filtering of joins/quits/parts](https://github.com/ProgVal/Supybot-plugins/issues/66)

Hostmask of RelayBot on 2014-06-23:

* RelayBot!progval@pdpc/supporter/student/progval
    * This is absolute hostmask
* RelayBot*!*@pdpc/supporter/student/progval
    * This is recommended hostmask as it matches RelayBot even if it 
    cannot use it's primary nickname or networks cannot connect to it's 
    identd.

## Linkinus

According to another person, there is a GUI where you can easily ignore 
notices from specific hostmask.

## WeeChat

```
/filter add relaybotnotices * irc_notice+nick_RelayBot *
```

This creates a new filter with the name "relaybotnotices" which filters 
all notices from the nickname "RelayBot".

<hr/>

This page is very likely missing many IRC clients. Could you [open issues](https://github.com/mkaysi/limnoria/issues) 
about how to do this with IRC clients that aren't mentioned here?

<hr/>

</body>
</html>
<!-- vim : set ft=markdown-->
