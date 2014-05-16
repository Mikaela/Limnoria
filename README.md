# Mikaela's fork of Limnoria.

There are mainly two branches. This which you are looking at, gh-pages 
which is the source of https://mkaysi.github.io/Limnoria .

**testing** which will be synced with [ProgVal/Limnoria] when needed. It 
is used as base for my changes which will be pull requested.

[ProgVal/Limnoria]:https://github.com/ProgVal/Limnoria.git

## .html.md --> .html

Everything except index.html is primarily typed in markdown. To convert it 
to html, I use `pandoc`.

```
pandoc -i index.real.html.md -o index.real.html
```

