---
layout: post
title: Ruby on Rails Interview questions ( The Basics ).
categories:
- ruby
- rails
- basics
- interview
---

---
* ### ***Operators in Ruby?***

  We use most of these operators on a day to day basis but somehow it is hard to
remember those names.
  * Unary
  * Arithemetic
  * Bitwise
  * Logical
  * Terenary

  There are like many more that are beautifully
explained [here](https://www.rubyguides.com/2018/07/ruby-operators)

---
* ### ***Variables in Ruby?***

  This is another straight forward question that we use on a daily basis.
  * Local
  * Class
  * Instance
  * Global

  More explanation [here](https://www.geeksforgeeks.org/ruby-types-of-variables/)

---
* ### ***Ruby Gems?***

  We must be using a lot of ruby gems in our project but when asked to define what
it is, becomes a bit tricky.

  Gems are standard format for distributing ruby programs & libraries. It works as
a package manager for the ruby programing language.

---
* ### ***Data types in Ruby?***

  Simplest of the lot

  * Numbers
  * Arrays
  * Strings
  * Symbols
  * Hashes
  * Boolean

  More info [here](https://www.geeksforgeeks.org/ruby-data-types/)

---
* ### ***Can private methods be called outside class definition?***

  Normally it's not possible to call a private method outside it's class
  definition, but this can be possible by using ruby's send method.

  {% highlight ruby %}
  class Hello

    private

    def world
      'world'
    end
  end

  Hello.new.world  #=> NoMethodError: private method `world' called for #<Hello:0x007ff321017a68>
  Hello.new.send(:world) #=> 'world'
  {% endhighlight %}

* ### ***Difference between class & module?***

  Modules are collection of methods and constants. These can be used as mixins
  to extend the functionality of a class. Modules cannot generate instances.

  We can see that these methods are not available for a module.
  {% highlight ruby %}
  Class.new.methods - Module.new.methods #=> [:new, :allocate, :superclass]
  {% endhighlight %}
  Don't confuse `Module.new` here, as everything in ruby is an object. We are
  simply creating a module using this.
  This can be simply transformed as 
  {% highlight ruby %}
  class Hello
  end

  module World
  end

  Hello.methods - World.methods #=> [:new, :allocate, :superclass]

  World.new #=> NoMethodError: undefined method `new' for World:Module
  {% endhighlight %}
