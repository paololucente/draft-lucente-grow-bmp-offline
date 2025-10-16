Making BMP fruible offline
==========================

> ### draft-lucente-grow-bmp-offline

- - -

Generating text from xml
------------------------

> One time only

* Install the latest [xml2rfc](https://xml2rfc.tools.ietf.org/)
* On Mac, you can install it using ```brew install xml2rfc```

> You'll do this each time you want to generate a text version

```
$ xml2rfc draft-lucente-grow-bmp-offline.xml --text
Parsing file draft-lucente-grow-bmp-offline.xml
Created file draft-lucente-grow-bmp-offline.txt
```

Generating ascii+svg artsets
----------------------------

Using the kramdown-rfc markdown toolchain combined with
[aasvg](https://github.com/martinthomson/aasvg/), we can generate
SVG figures from ascii art.

* Install [kramdown-rfc](https://github.com/cabo/kramdown-rfc/) so `kdrfc` is in PATH
* Install `aasvg` via npm/yarn and make sure the binary is in PATH

Make the figures in `figures.md` and run
```
kdrfc figures.md --html --txt
```

Check the created `figures.html` and `figures.txt` to see if the output is as
expected. Then, copy the raw XML from `figures.xml` into the main doc.
