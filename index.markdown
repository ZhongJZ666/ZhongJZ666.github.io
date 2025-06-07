---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: 欢迎来到我的个人博客
---

# 欢迎来到我的个人博客

这里记录我的学习、生活与成长。

## 最新文章

{% for post in site.posts %}
  <article>
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <p>{{ post.excerpt }}</p>
  </article>
{% endfor %}
