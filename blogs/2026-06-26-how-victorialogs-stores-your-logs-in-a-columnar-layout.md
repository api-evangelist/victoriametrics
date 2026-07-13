---
title: "How VictoriaLogs Stores Your Logs in a Columnar Layout"
url: "https://victoriametrics.com/blog/victorialogs-internals-columnar-storage-on-disk/"
date: "2026-06-26"
author: ""
feed_url: "https://victoriametrics.com/index.xml"
---
A beginner-friendly tour of how VictoriaLogs stores your logs on disk: streams and daily partitions, immutable parts, blocks and columns, and the files inside a part (timestamps, values, bloom filters, column headers, and the two-level index) that let a query read only the bytes it needs.
