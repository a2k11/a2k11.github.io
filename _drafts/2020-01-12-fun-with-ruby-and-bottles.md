---
layout: default
title: Fun with ruby & bottles
date: 2020-01-12
month: January
day: 26
year: 2020
categories: [ruby, OOP, polymorphism]
permalink: /:year/:month/:day/:title.html
---

I started my career in software development learning about [ruby](https://www.ruby-lang.org/en/).  The language has a unique beauty & style when writing complex web applications or scripts that execute simple functions.  Dynamically typed languages like ruby rely on trust.  There are expectations for objects to respond appropriately to messages and presumptions about the message results.  On my list of **must reads** was [99 Bottles of OOP](https://www.sandimetz.com/99bottles), which I enjoyed during the 2019 holiday.  I'm sharing one of the many parts I found interesting ...
<br/><br/>
### **Using Polymorphism**
<br/>
 Polymorphism is defined as the concept of 2 or more classes having the ability to respond to the same directive.  Barbara Liskov was one of the first women to earn a doctorate in computer science in 1968 at Standford.  In 1987, she gave a presentation called 'Data Abstraction & Hierarchy' which introduced behavioral subtyping.  It was described more precisely later as the Liskov Substitution Principle, which states if a type **B** uses an extension of type **A**, then a type **B** object can be used and replace a type **A** object.  In __99 Bottles of OOP__, there was a strategy titled "replace the conditional with polymorphism."  It outlined steps to remove unwanted conditionals using inheritance.  Here is a quick example...  
<br/>

{% highlight ruby %}
class MegaManOne
  def robot(name)
    character = Robot.new(name)

    "The #{character.morality} #{character} was " \
      "created by #{character.creator}.\n"
  end

  def game
    names = ["Mega Man", "Cut Man", "Ice Man", "Guts Man", "Bomb Man",
      "Fire Man", "Elec Man"]
    
    names.each do |name|
      robot(name)
    end
end

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

  def morality
    if name == "Mega Man"
      "good"
    else
      "evil"
    end
  end

  def health
    "20 HP"
  end

  def to_s
    "#{name}"
  end
end
{% endhighlight %}

<br/>
We can see the name "Mega Man" is special.  Let's create a subclass to stand in for this value and copy the methods which switch on it too.
<br/><br/>

{% highlight ruby %}
class MegaManRobot < Robot
  def creator
    "Dr. Light"
  end

  def morality
    "good"
  end
end
{% endhighlight %}

<br/>
Since we don't have a factory to create MegaManRobot objects, we can add one to the beginning of the class in order to demonstrate how these Robot objects will be funneled.  
<br/>

{% highlight ruby %}
class MegaManOne
  def robot(name)
    character = robot_for(name)

    "The #{character.morality} #{character} was " \
      "created by #{character.creator}.\n"
  end  
  
  def robot_for(name)
    if name == "Mega Man"
      MegaManRobot
    else
      Robot
    end.new(name)
  end
  # ...
end
{% endhighlight %}

<br/>
Now we can reduce the superclass' conditional branch to the false path.  
<br/>

{% highlight ruby %}
class Robot
  # ...
  def creator
    "Dr. Wily"
  end

  def morality
    "evil"
  end
  # ...
end
{% endhighlight %}

<br/>
This concludes the process.  I didn't work through tests which you are encouraged to create and follow.  It is an important part of software development, especially when refactoring code to make sure you always have the green light.  
