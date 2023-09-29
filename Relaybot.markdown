---
layout: page
title: Ignoring RelayBot
permalink: /Relaybot.html
---

RelayBot is the bot which relays between #supybot,#limnoria at a couple of
networks (TODO/FIXME, which ones?). It
is currently using the [LinkRelay](https://github.com/ProgVal/Supybot-plugins/tree/master/LinkRelay)
plugin to do this.

It's sometimes considered as annoyance as it has lately mostly spammed
with join (part messages aren't working, because of a bug (2014-06-23))
messages of people who usually say nothing and this is why this page is
here to tell how to ignore it on various client.

We(who? I?) encourage you to ignore only notices from RelayBot instead of
everything as there are people whom should be heard at OFTC (mainly main
Supybot developer). (TODO/FIXME: is this the case in 2021?)

Related links:

- [LinkRelay plugin](https://github.com/ProgVal/Supybot-plugins/tree/master/LinkRelay)
- [Feature request for smart filtering of joins/quits/parts](https://github.com/ProgVal/Supybot-plugins/issues/66)
- [Feature request for RELAYMSG for more native look&feel](https://github.com/ProgVal/Supybot-plugins/issues/338)

Hostmask of RelayBot on Libera.Chat 2021-06-06:

- `RelayBot!~limnoria@helium.progval.net`
  - This is absolute hostmask, also known as NUH (`nick!user@host`)
- `RelayBot*!*@helium.progval.net`
  - This is recommended hostmask as it matches RelayBot even if it
    cannot use it's primary nickname or networks cannot connect to it's
    identd.

## HexChat

From the "Window" menu you can find "Ignore list". Click "Add" and add
one of the hostmasks mentioned above (the lower is recommended).

Uncheck the other checkboxes than "Notice" and you can close the window
and you won't see spamming.

## KVIRC

I am not primarily KVIRC user and I cannot say anything else than right
click RelayBot and select something that matches only RelayBot.

**WARNING: KVIRC makes it very easy to also ignore pinkieval which you
don't want to do as they are author of Limnoria and help people often!**

## Linkinus

According to another person, there is a GUI where you can easily ignore
notices from specific hostmask.

## WeeChat

```
/filter add relaybotnotices * irc_notice+nick_RelayBot *
```

This creates a new filter with the name "relaybotnotices" which filters
all notices from the nickname "RelayBot".

---

This page is very likely missing many IRC clients. Could you
[open an issue](https://github.com/mikaela/limnoria/issues)
about how to do this with your IRC client that isn't mentioned here?

---
