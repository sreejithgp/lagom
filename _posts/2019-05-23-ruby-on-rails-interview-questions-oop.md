---
layout: post
title: Ruby on Rails Interview questions ( OOP ).
categories:
- ruby
- rails
- oop
- interview
---

---
* ### ***What is an Objects?***

  Objects are nothing but resemblence of a real life entity. A simple example
  could be a Dog, which is a real life entity and it has it's own
  characteristics ( color, age, weight etc ) and behaviour ( bark ). Now an
  object will have it's own characteristics known as variables and it's own
  behaviour known as functions. These are instance of a class.

---
* ### ***What is a Class?***

  Classes are simply the specification of an object, meaning how the object will
  look like.

---
* ### ***Four principles of OOP?***

  * Abstraction
  * Polymorphism
  * Inheritance
  * Encapsulation


* ### ***Three levels of method access control for classes?***

  * Public

  As the name suggest these methods can be accessed by any instance of the
  class, aswell as from inside the class.

  {% highlight ruby %}
  class Hello
    def world_caller
      # public method called from inside the class
      world
    end

    def world
      'world'
    end
  end

  Hello.new.world_caller #=> 'world'
  Hello.new.world #=> 'world'
  {% endhighlight %}

  * Private

  These are methods accessible only from inside the class
  {% highlight ruby %}
  class Hello
    def world_caller
      # private method called from inside the class
      world
    end

    private

    def world
      'world'
    end
  end

  Hello.new.world_caller #=> 'world'
  Hello.new.world #=> NoMethodError: private method `world' called for #<Hello:0x007f894301cf60>
  {% endhighlight %}

  * Protected

  This is where it gets tricky. We can call an object's protected method as long
  as the default object self is an instance of the same class as the object
  whose method you are calling.

  Confused!!!

  Let's break this down using an example


  {% highlight ruby %}
  class Person
    def initialize(age)
      @age = age
    end

    def older_than?(other_person)
      # protected method of different object called, which is the instance of
      # this same class. This will raise an error if this method were private.
      # change the method age to private and see for yourself.
      age > other_person.age
    end

    private

    attr_reader :age
  end

  person1 = Person.new(10) #=> #<Person:0x007f894280dae0 @age=10>
  person1.age #=> NoMethodError: protected method `age' called for #<Person:0x007f894280dae0 @age=10>

  person2 = Person.new(20) #=> #<Person:0x007f89429b7bc0 @age=20>

  person2.older_than?(person1) #=> true
  {% endhighlight %}
