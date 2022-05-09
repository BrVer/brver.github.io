---
layout: single
title:  "Generate ruby Flamegraph with stackprof"
date:   2021-03-31 16:55:24 +0200
tags: flamegraph stackprof
excerpt: Recently found, a better way to generate flamegraph for ruby, using stackprof
---
Some time ago [I spoke about Flamegraph]({% post_url 2019-11-20-rubylnik-conference-flamegraph %}),
but only recently found that there's better way to generate it for ruby:

**USAGE:**

**1.**
add `gem 'stackprof'` to your `Gemfile`

**2.**
```ruby
# HINT: play with `ignore_gc` and `aggregate` options (both boolean)
StackProf.run(mode: :wall, raw: true, ignore_gc: true, out: 'tmp/stackprof-cpu-myapp.dump') do 
  # do some heavy work
end
```

**3.**
**EITHER**

use [stackcollapse option](https://github.com/tmm1/stackprof/commit/453bb7f2831b110e7e8b983267e640a26897cdd6) + `flamegraph.pl`
```bash
stackprof --stackcollapse tmp/stackprof-cpu-myapp.dump > tmp/stackcollapse
stackprof-flamegraph.pl tmp/stackcollapse > tmp/real-flamegraph.html # (this will produce an HTML file, ready to be open)
```

**OR**

use [stackcollapse option](https://github.com/tmm1/stackprof/commit/453bb7f2831b110e7e8b983267e640a26897cdd6) + `speedscope` service
- `stackprof --stackcollapse tmp/stackprof-cpu-myapp.dump > tmp/stackcollapse`
- open [speedscope.app](https://www.speedscope.app/) , drag&drop `tmp/stackcollapse`, switch to `Left Heavy` tab at the top left corner

**OR**

use [d3-flamegraph](https://github.com/tmm1/stackprof/pull/113)
```bash
# (this will produce an HTML file, ready to be open)
stackprof --d3-flamegraph tmp/stackprof-cpu-myapp.dump > tmp/d3-flamegraph.html
```

**OR**

use [alphabetical flamegraph](https://github.com/tmm1/stackprof/pull/112)
```bash
stackprof --alphabetical-flamegraph tmp/stackprof-cpu-myapp.dump > tmp/alpha-flamegraph
stackprof --flamegraph-viewer=tmp/alpha-flamegraph # then open the URL Stackprof gives you and enjoy!
```

---

**TIP:** [other possible options](https://github.com/tmm1/stackprof/blob/master/bin/stackprof)