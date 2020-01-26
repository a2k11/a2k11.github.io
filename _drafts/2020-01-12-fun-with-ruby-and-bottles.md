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

I started my career in software development learning about [ruby](https://www.ruby-lang.org/en/).  The language has a unique beauty & style when writing complex web applications or scripts that execute simple functions.  Dynamically typed languages like ruby rely on trust.  There are expectations for objects to respond appropriately to messages and presumptions about the message results.  On my list of **must reads** was [99 Bottles of OOP](https://www.sandimetz.com/99bottles), which I enjoyed during the 2019 holiday.
<br /><br />

### **Liskov Substitution Principle**
Barbara Liskov was one of the first women to earn a computer science doctorate in 1968 at Stanford.  She gave a keynote presentation called 'Data Abstraction & Hierarchy' which introduced behavioral subtyping.  It was described more precisely as the Liskov Substitution Principle.  It states: if for each object of type **A** there is an object of type **B** such that when object of type **B** is substituted and replaced by object of type **A**, and the program's behavior remains unchanged, we can say A is a subtype of B.  Barbara Liskov would receive the Turing Award in 2008 for her contributions related to data abstraction.
<br /><br />

### **Polymorphism**
 Polymorphism is defined as the concept of 2 or more classes having the ability to respond to the same directive.  In __99 Bottles of OOP__, there is a strategy titled "replace the conditional with polymorphism."  It outlined steps to remove unwanted conditionals using inheritance.  Here is a quick example.  I'm using one of my favorite games, **Mega Man 2**, as the subject.  

|Bubble Man|Air Man|Quick Man|Heat Man|Wood Man|Metal Man|Flash Man|Crash Man|
|----------|-------|---------|--------|--------|---------|---------|---------|
|![Bubble Man](/assets/megaman2/bubbleman.gif)|![Air Man](/assets/megaman2/airman.jpg)|![Quick Man](/assets/megaman2/quickman.png)|![Heat Man](/assets/megaman2/heatman.png)|![Wood Man](/assets/megaman2/woodman.png)|![Metal Man](/assets/megaman2/metalman.jpg)|![Flash Man](/assets/megaman2/flashman.png)|![Crash Man](/assets/megaman2/crashman.png)|

<br />

{% highlight ruby %}
class MegaMan2
  def robot(name)
    character = Robot.new(name)

    "The #{character.morality} #{character} was " \
      "created by #{character.creator}.\n"
  end

  def game
    names = ["Mega Man", "Metal Man", "Flash Man", "Crash Man", "Heat Man",
      "Wood Man", "Bubble Man", "Air Man", "Quick Man"]
    
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
class MegaMan2
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
