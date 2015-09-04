---
layout: post
title: First Post
date: 2015-08-03
summary: "Excited Yahoo!!"
categories: Explore
author: Shekar
published: true
---



{% highlight java linenos %}
public class A{
  System.print.ln("Test");
}
{% endhighlight %}

Mug milk a mocha, fair trade est doppio as pumpkin spice saucer robusta iced. Milk cup frappuccino arabica ut fair trade grinder saucer. Est, fair trade mocha, crema wings, extra id spoon coffee frappuccino.
… which is shown in the screenshot below:
#Testing
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
![My helpful screenshot](/images/me.jpeg)
