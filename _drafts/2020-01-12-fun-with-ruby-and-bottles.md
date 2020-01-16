---
layout: post
title: "Fun with ruby & bottles"
date: 2020-01-12
categories: ruby OOP polymorphism
permalink: /:year/:month/:day/:title.html
---


I started my career in software development learning about [ruby](https://www.ruby-lang.org/en/).  The language has a unique beauty & style when writing complex web applications or scripts that execute simple functions.  It wasn't hard to pick up [99 Bottles of OOP](https://www.sandimetz.com/99bottles) which has been on my list of **must reads** for a long time.  Here are a few of the many highlights I found interesting.

---


 ### Using Polymorphism
 ---
 Polymorphism is defined as the concept of 2 or more classes having the ability to respond to the same directive.  This usually involves a child class that can react in the same way as the parent class to a message.  For example, we say `Raspberry` is a child of the `Fruit` class.  



{% highlight ruby %}
class Fruit
  def container
    "bag"
  end
end

class Raspberry < Fruit
  def container
    "box"
  end

  def color
    "red"
  end
end
{% endhighlight %}



The technique called "Replace the Conditional with Polymorphism" is a nice skill to practice in your code.  It might take longer and it may create more problems in the short term to build such a solution.  The steps listed to take this approach are:


1. create a subclass to stand in for the value upon which you switch
    1. copy one method that switches on the value in the subclass
    1. in the subclass remove everything but the true branch of the conditional
    * create a factory if it doesnt exist yet
    * add the subclass to the factory if not yet included
    1. in the superclass, remove everything but the false branch of the conditional
    1. repeat steps a-c until all methods that switch on the value are dispersed
2. Iterate until a subclass exists for every different value upon which you switch


The Liskov Substitution Principle is very similar to these ideas as it is defined as if an object of type **raspberry** extends an object of type **fruit**, then an object of type **raspberry** can always be used whereever type **fruit** is expected.  Dynamically typed languages, like `ruby`, rely on this trust and expect these objects to respond appropriately to their messages.  
