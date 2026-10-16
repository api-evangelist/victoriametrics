---
title: "The Data Race That Wasn't a Bug (and the One That Was)"
url: "https://victoriametrics.com/blog/http-race-condition/"
date: "2026-10-06"
feed_url: "https://victoriametrics.com/index.xml"
---
You turn on Go’s race detector and get a data race inside net/http that makes no sense at first. This post digs into how Go’s HTTP client really sends a request body, why it can keep reading your buffer after Client.Do has returned, why we decided that race is harmless in vmagent, and why the same behavior could corrupt data in vmauth, so we fixed it there.
