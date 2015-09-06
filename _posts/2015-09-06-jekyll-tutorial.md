---
title: Jekyll Tutorial
---

#### Default Variable

Insted of declaring common variable in each post or page we can declare them as default variable in _config.yml

##### Example
How to add post and page default variable in _config.yml

> Remove **author**,**layout**,**category** from post files

>Remove **layout** from pages(ex: about.md)

{% highlight xml %}
defaults:
  -
    scope:
      path: "" # an empty string here means all files in the project
      type: "posts" # previously `post` in Jekyll 2.2.
    values:
      author: Shekar
      layout: "post"
      category:  Android
  -
    scope:
      path: "" # an empty string here means all files in the project
      type: "pages" # previously `post` in Jekyll 2.2.
    values:
      layout: "page"
{% endhighlight %}   
