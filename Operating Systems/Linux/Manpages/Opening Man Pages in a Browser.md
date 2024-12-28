---
title: "Opening Man Pages in a Browser"
date: 2024-12-13
tags:
  - Linux
  - manpage
  - Tips and Tricks
categories:
  - Linux Commands
  - Productivity
author: "TheTechMokey"
summary: "Learn how to open Linux man pages in a browser using the -H option for a more accessible and visual experience."
features:
  - Open man pages in an HTML format
  - Use your preferred browser for reading documentation
  - Simplify navigation of complex man pages
related_links:
  - Official Manpage Documentation: https://man7.org/linux/man-pages/
---

To open a manpage in a browser, use the following:
```sh
export BROSWER=firefox
```
Use the `-H` option when using `man` to open **HTML**
```sh
man -H <MANPAGE>
```

## ex:
```sh
man -H usermod
```

`file:///tmp/hman961pTH/usermod.html`
This will open the respective man page in Firefox.
