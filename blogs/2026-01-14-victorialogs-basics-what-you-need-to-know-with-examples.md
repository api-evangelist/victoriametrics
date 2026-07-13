---
title: "VictoriaLogs Basics: What You Need to Know, with Examples & Visuals"
url: "https://victoriametrics.com/blog/victorialogs-architecture-basics/"
date: "2026-01-14"
feed_url: "https://victoriametrics.com/index.xml"
---
Cluster mode in VictoriaLogs is not a separate build. It is the same victoria-logs binary started with different flags, so you can scale out without a migration step. Storage nodes persist data on disk, while gateway nodes can stay stateless by pointing to storage with -storageNode.
