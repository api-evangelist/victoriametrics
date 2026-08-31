---
title: "Understanding Go's sync.Map from API to Hash Trie"
url: "https://victoriametrics.com/blog/go-sync-map-hash-trie/"
date: "2026-08-26"
feed_url: "https://victoriametrics.com/index.xml"
---
Go’s sync.Map now uses a hash trie. This article builds the implementation from a normal map, then explains lock-free reads, fine-grained writer locking, collisions, retries, deletion, Clear, Range, and the trade-offs against map plus RWMutex.
