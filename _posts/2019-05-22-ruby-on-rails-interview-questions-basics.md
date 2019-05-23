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

