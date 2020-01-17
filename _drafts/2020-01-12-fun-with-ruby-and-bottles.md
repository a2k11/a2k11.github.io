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
 Polymorphism is defined as the concept of 2 or more classes having the ability to respond to the same directive.  This usually involves a child class that can react in the same way as the parent class to a message.  "Replace the Conditional with Polymorphism" removes unwanted conditionals by using inheritance.  The steps for using this method are listed below:

1. create a subclass to stand in for the value upon which you switch
    1. copy one method that switches on the value in the subclass
    1. in the subclass remove everything but the true branch of the conditional
    * create a factory if it doesnt exist yet
    * add the subclass to the factory if not yet included
    1. in the superclass, remove everything but the false branch of the conditional
    1. repeat steps a-c until all methods that switch on the value are dispersed
2. Iterate until a subclass exists for every different value upon which you switch
 
And the Liskov Substitution Principle states if let's say a type **Raspberry** extends type **Fruit**, then a **Raspberry** object type can always be used wherever a **Fruit** object type is expected.  Dynamically typed languages like `ruby`, rely on trust, expect these objects to respond appropriately to the message, and have presumptions about the message results.  

So polymorphism is woven into each of these ideas in order to better organize and describe our code.  I created a simple code snippet below to show polymorphism and how it can be used to share information and override the parent class's data.  


{% highlight ruby %}
class Fruit
  def edible
    true
  end

  def quantity
    'one'
  end
end

class Raspberry < Fruit
  def color
    "ruby red"
  end

  def quantity
    "one pint"
  end
end
{% endhighlight %}





