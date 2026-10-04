---
title: "How Linux readahead works, and the two ways to change it"
url: "https://victoriametrics.com/blog/linux-readahead-and-fadvise/"
date: "2026-09-29"
feed_url: "https://victoriametrics.com/index.xml"
---
The kernel reads your files before you ask for them, guessing from where your reads land. Here is how that guessing actually works (the window, the marker, the background fetch) and the two ways to influence it: read_ahead_kb on the device, and posix_fadvise from inside the program. Neither does quite what its name suggests.
