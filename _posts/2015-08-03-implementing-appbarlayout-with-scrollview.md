---
layout: post
title: Implementing AppbarLayout with ScrollView
date: 2015-09-03
categories: Explore
author: Shekar
published: true
---

As there were some bugs in Coordinator layout, I got the requirement to implement same behavior with scroll view. So here is how we can do it.

Expected Output

![](/images/1.gif)

Step 1: Not reinventing the wheel

This library is very good as starting point for our final goal, and here you will find detail explanation about how to create this.

![](/images/2.gif)

Let's see the basic structure of the this implementation.

{% highlight xml %}
<FrameLayout>
    <ImageView android:id="@+id/image" android:layout_height="240dp"/>
    <View android:id="@+id/overlay" android:layout_height="240dp"//>
    <ObservableScrollView android:id="@+id/scroll">
        <LinearLayout android:orientation="vertical">
            <View android:id="@+id/paddingtop" android:layout_height=“240dp”/>
            <TextView android:id="@+id/main_content"/>
        </LinearLayout>       
    </ObservableScrollView>
    <LinearLayout android:id="@+id/titletext_container" android:orientation="vertical">
        android:paddingLeft="@dimen/margin_standard">
        <TextView android:id="@+id/title"   android:minHeight="?attr/actionBarSize"/>
        <View android:id="@+id/animating_area"   android:minHeight="184dp"/>
    </LinearLayout>
    <FloatingActionButton android:id="@+id/fab"/>
</FrameLayout>
{% endhighlight %}

FrameLayout is used for moving children separately.
ImageView(@id/image) is the image that will be translated with parallax effect.
View(@id/overlay) is an overlay view as the name suggests.You can see the image is fading in and out. This view overlaps with the image and its opacity is changed by scroll position.
Screen Shot 2015-09-01 at 4.14.37 PM
![My helpful screenshot](/images/3.png)

ObservableScrollView provide virticle scroll value which is used to scroll other views
LinearLayout holds the actual content
View(@id/paddingtop) provide top padding of 240dp so that main content start below header view.
TestView(@id/main_content) this represet main content below header.
![My helpful screenshot](/images/4.png)

LinearLayout(@id/titletext_container) holds title text and the animating area
TextView(@id/titletext) holds title text which will be scaled and translated on top of the action bar, its minimum height is equal to action bar height.
View(@id/animating_space) This view provides space for title text to animate. its height is (header height - action bar height).
![My helpful screenshot](/images/5.png)

Step 2: Identifying what need to be done

The toolbar should stick at the top.
Title text should stick at the top with scale animation.
The status bar should be transparent initially and fade in with the primary color.
Image View should start under the status bar.
Step 3: Toolbar should stick at top

As ObservableScrollView content should scroll below image view, move image view and overlay on top of ObservableScrollView.

{% highlight xml %}
<FrameLayout>
    <ObservableScrollView android:id="@+id/scroll">
        <LinearLayout android:orientation="vertical">
            <View/>
            <TextView/>
        </LinearLayout>       
    </ObservableScrollView>
<span style="color: #ff0000;">   <ImageView android:id="@+id/image" android:layout_height="240dp"/>
    <View android:id="@+id/overlay" android:layout_height="240dp"//></span>
    <LinearLayout/>
        <TextView/>
        <View/>
    </LinearLayout>
   <FloatingActionButton />
</FrameLayout>
{% endhighlight %}













<!-- {% highlight java linenos %}
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
</ul> -->
