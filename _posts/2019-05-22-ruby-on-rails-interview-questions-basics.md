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
* ### ***Difference between blocks, procs and lambda?***

  Blocks, procs and lambdas are all closures, but blocks are not objects in
  ruby ( and hence the term *almost* everything in ruby is an object ). A method
  can accept only one block, but can accept any number of procs. Also a method
  can return procs but not blocks.

  There is always a block in as the last argument when you define a method in ruby.

  {% highlight ruby %}

  def hello
    puts 'world'
  end

  hello { puts 'there' }
  # world
  # => nil

  # inorder to execute what's inside the block we need to yield.

  def hello
    puts 'world'
    # block_given? guards when the method is called without a block
    yield if block_given?
  end

  hello
  # world
  # => nil

  hello { puts 'there' }
  # world
  # there
  # => nil
  {% endhighlight %}

  Now the difference between procs and lambdas are on how they handle the
  arguments and their return statements.

  Procs don't strict enforce the arguments you pass in.

  {% highlight ruby %}

  a = lambda { |name| "Greetings #{name}!!" }
  a.call('Mark') #=> "Greetings Mark!!"
  a.call #=> ArgumentError: wrong number of arguments (given 0, expected 1)

  b = Proc.new { |name| "Greetings #{name}!!" }
  b.call('Mark') #=> "Greetings Mark!!"
  b.call #=> "Greetings !!"
  {% endhighlight %}

  Now lets see how both handle the return statement when called inside a method.

  {% highlight ruby %}

  def lambda_returns
    a = lambda { return }
    a.call
    puts 'Hello'
  end

  lambda_returns #=> "Hello"

  def proc_returns
    b = Proc.new { return }
    b.call
    puts 'Hello'
  end

  proc_returns #=> nil
  # proc returns out of the method enclosing it.
  {% endhighlight %}
  [More about blocks, procs and lambdas](https://medium.com/@AdamKing0126/ruby-whats-the-deal-with-procs-and-lambdas-165450cdf573)

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

* ### ***How to create getter and setter methods in Ruby?***

  The easiest way would be to use the ruby helper `attr_accessor` which will
  create both setter and getter methods. `attr_reader` if you only want to
  create getter method and `attr_writer` if you only want to create setter
  method.

  If you want to create them manually then
  {% highlight ruby %}

  class Hello
    # getter method
    def world
      @world
    end

    # setter method
    def world=(value)
      @world = value
    end
  end
  obj = Hello.new
  obj.world #=> nil
  obj.world = 'world'
  obj.world #=> 'world'
  {% endhighlight %}


* ### ***Your top 10 ruby gems?***

  This is a more generic question and the answer varies for each programmers.
  But the trick is to include all testing and development gems that you might
  end up using in every rails project.

  * Testing gems
    * capybara
    * simplecov
    * factorybot
    * database_cleaner
    * faker
    * shoulda-matchers

  * Development gems
    * guard-rails
    * rubycop
    * bullet
    * pry
