---
layout: single
title:  "Materials for Ruby devs"
date:   2021-04-16 16:55:24 +0200
tags: ruby OOP
excerpt: list of good small articles helping to quickly improve the code quality
---

**Disclaimer:**
There's lots of awesome books regarding OOP and how to write a good code
(for example, 99 bottles of OOP, but there are tons of them)!

However, books take longer time to read,
so here I attempted to compose a list of small but very useful articles which address the most crucial (IMO) problems.

---

### OOP
[**Code smells list**](https://refactoring.guru/refactoring/smells) <br/>
most frequent non-trivial ones: `Feature envy`, `Primitive obsession`, `Data class`
(lots of articles across the web, a couple I was able to recall below)

[**FeatureEnvy**](https://github.com/troessner/reek/blob/master/docs/Feature-Envy.md)

[**PrimitiveObsession - awesome video**](https://www.youtube.com/watch?v=LhX5COR8WXc)

related to `DataClass` code smell: [**Anemic domain model anti-pattern**](https://en.wikipedia.org/wiki/Anemic_domain_model)

[**Tell-don't-ask**](https://thoughtbot.com/blog/tell-dont-ask)

Composition vs inheritance, 4 articles:
- [part 1: inheritance](https://thoughtbot.com/blog/reusable-oo-inheritance) 	
- [part 2: modules](https://thoughtbot.com/blog/reusable-oo-modules)
- [part 3: composition](https://thoughtbot.com/blog/reusable-oo-composition (the most interesting one))
- [part 4: composition-vs-inheritance](https://thoughtbot.com/blog/reusable-oo-composition-vs-inheritance)

### SOLID

A million of articles, what I was able to find in 2 minutes:
- [https://thoughtbot.com/blog/back-to-basics-solid](https://thoughtbot.com/blog/back-to-basics-solid) 	
- [https://www.honeybadger.io/blog/ruby-solid-design-principles/](https://www.honeybadger.io/blog/ruby-solid-design-principles/) 	
- [http://marcyliao.me/2018/11/26/solid-in-ruby/](http://marcyliao.me/2018/11/26/solid-in-ruby/)

### Typical abstractions
[https://codeclimate.com/blog/7-ways-to-decompose-fat-activerecord-models/](https://codeclimate.com/blog/7-ways-to-decompose-fat-activerecord-models/)

[https://www.sitepoint.com/7-design-patterns-to-refactor-mvc-components-in-rails/](https://www.sitepoint.com/7-design-patterns-to-refactor-mvc-components-in-rails/) ([the same but with better syntax highlighting](https://www.programmersought.com/article/3113725477/))

Overkill for small tasks, but good in bigger projects: [**dry-rb family**](https://dry-rb.org/) <br/>
For example, on the last project we used `dry-container`, `dry-auto-inject`, `dry-validation`, `dry-schema`, `dry-struct`
(and I think we could also use `dry-events` instead of self-made implementation).
Recommend to take a look at, there are some useful abstractions.

### Testing
[Good general article about testing pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)

Rspec-specific:
a lot of people overuse fancy stuff like `let`, [Let's not](https://thoughtbot.com/blog/lets-not) helps to understand how to keep the balance between them and pure ruby functions to make specs better

### Misc
[Readable code](https://thoughtbot.com/blog/letting-your-code-speak-for-itself)