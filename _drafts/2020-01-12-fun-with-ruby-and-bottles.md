---
layout: post
title: "Fun with ruby & bottles"
date: 2020-01-12
categories: ruby OOP polymorphism
permalink: /:year/:month/:day/:title.html
---


I started my career in software development learning about [ruby](https://www.ruby-lang.org/en/).  The language has a unique beauty & style when writing complex web applications or scripts that execute simple functions.  It wasn't hard to pick up [99 Bottle of OOP](https://www.sandimetz.com/99bottles) which has been on my list of **must reads** for a long time.  Here are a few of the many highlights I found interesting.

---


 ### Using Polymorphism
 ---
 Polymorphism is defined as the concept of 2 or more classes having the ability to respond to the same directive.  This usually involves a child class that can react in the same way as the parent class to a message.  For example:

{% highlight ruby %}
class Fruit
  def edible
    True
  end
end

class Raspberry < Fruit
  def color
    "red"
  end
end
{% endhighlight %}

Here we say `Raspberry` is a child of the `Fruit` class.  
