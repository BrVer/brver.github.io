---
layout: single
title:  "Notes: Ruby concurrency, parallelism and non-blocking I/O"
date:   2021-01-03 16:55:24 +0200
tags: ruby concurrency parallelism threads fibers ractors async
---
### Concurrency vs parallelism, threads/fibers/ractors(guilds), blocking/non-blocking I/O etc

**parallelism:**
- <3.0: only with threads + JRuby/rubinius (GIL makes parallelism impossible in CRuby)
- since 3.0 - ractors/guilds

**concurrency:**
- threads (implicit concurrency)
- fibers (developer manipulates concurrency explicitly)

**non-blocking I/O:**
- before: run multiple threads (they are smart enough to pass execution to another thread when blocking I/O occurs)
- now: use `async` gem - uses fibers + fiber scheduler (introduced in ruby 3), so it’s much more fast/lightweight