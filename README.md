# ungrading

Research project on ungrading.

The *ungrading.md* file is the main source file.
This paper was submitted as a juried paper
proposal to the [ALISE](https://alise.org)
2022 annual conference.

This proposal was not accepted to the conference, but
I'm continuing this project with others.

Manuscript draft on 2022-03-18: [https://cseanburns.net/WWW/ungrading-2022-03-18.html](https://cseanburns.net/WWW/ungrading-2022-03-18.html)

The ODT file was generated with the Bash function below,
which uses
[Pandoc][pandoc],
[Zotero][zotero],
and the
[Zotcite][zotcite]
plugin for
[Vim][vim].

The ODF file required minor stylistic changes to
conform with the conference paper guidelines
and then was exported as a PDF file from LibreOffice.

[pandoc]:https://pandoc.org/
[zotero]:https://www.zotero.org/
[zotcite]:https://github.com/jalvesaq/zotcite
[vim]:https://www.vim.org/


```
#!/usr/bin/bash

# Date: 2022-3-14
# Convert a markdown file into an APA formatted file. 
# To be used with the Zotcite plugin for Zotero and Vim 
# Demo: https://cseanburns.net/WWW/my-plain-text-social-science.html

makeapa () {
  local sourcefile="$1"
  local zotfile="${HOME}/.vim/plugged/zotcite/python3/zotref.py"
  local apafile="${HOME}/Zotero/styles/apa.csl"
  pandoc "${sourcefile}" -s -o \
    "$(basename -s md "$sourcefile")"odt -F\
    "${zotfile}" --citeproc --csl "${apafile}"
}


makeapa "$@"
```
