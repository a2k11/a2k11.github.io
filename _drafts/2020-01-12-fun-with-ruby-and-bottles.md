---
layout: post
title: "Fun with ruby & bottles"
date: 2020-01-12
categories: ruby OOP polymorphism
permalink: /:year/:month/:day/:title.html
---


I started my career in software development learning about [ruby](https://www.ruby-lang.org/en/).  The language has a unique beauty & style when writing complex web applications or scripts that execute simple functions.  On my list of **must reads** is [99 Bottles of OOP](https://www.sandimetz.com/99bottles).  I'll be sharing a little blurb about polymorphism.
 
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
 
And the Liskov Substitution Principle states if a type **B** uses an extension of type **A**, then a **B** object can be used and replace a **A** object.  Dynamically typed languages like `ruby`, rely on trust, expect these objects to respond appropriately to the message sent, and have presumptions about the message results.  

Polymorphism is used to better organize our code.  I created a simple code snippet below to show polymorphism and how it can be used to share information and override the parent class's data.  


{% highlight ruby %}
class Robot
  attr_reader :name
  def initialize(name)
    @name = name
  end

  def creator
    if name == "Mega Man"
      "Dr. Light"
    else
      "Dr. Wily"
    end
  end

  def character
    if name == "Mega Man"
      "protagonist"
    else
      "antagonist"
    end
  end
end
{% endhighlight %}




