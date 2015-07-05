---
layout: post
title: Add Weibo social link in Jekyll
comments: true
categories:
- blog
---

Jekyll 模板中添加微薄(weibo.com)的社交链接

---

### 在" _include/social.html "中添加

{% highlight html %}
{{ "{% if site.data.theme.social.weibo " }}%}
<a title="{{ site.data.theme.name  }} on weibo" href="http://www.weibo.com/{{ site.data.theme.social.weibo  }}">
  <i class="fa fa-weibo"></i>
</a>
{{ "{% endif " }}%}
{% endhighlight %}

### 在" _data/theme.yml "中添加

{% highlight yaml  %}

social:
   github: yeahnoob
   #tumblr: animalygifs
   weibo: rockrollfree
{% endhighlight %}
