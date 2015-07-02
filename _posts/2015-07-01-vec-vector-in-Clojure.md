---
layout: post
title: vec and vector in Clojure
categories:
- blog
---

Clojure 里'vec' 和 'vector' 的一些例子

---

# 运行在 lein repl

{% highlight clojure %}
user=> (doc vec)
-------------------------
clojure.core/vec
([coll])
  Creates a new vector containing the contents of coll. Java arrays
  will be aliased and should not be modified.
nil
user=> (doc vector)
-------------------------
clojure.core/vector
([] [a] [a b] [a b c] [a b c d] [a b c d & args])
  Creates a new vector containing the args.
nil
user=> (vec '(2 3 4))
[2 3 4]
user=> (vector 2 3 4)
[2 3 4]
user=> (apply vec ['(2 3 4)])
[2 3 4]
user=> (apply vector [2 3 4])
[2 3 4]
{% endhighlight %}
