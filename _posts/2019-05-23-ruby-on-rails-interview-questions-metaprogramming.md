---
layout: post
title: Ruby on Rails Interview questions ( Metaprogramming ).
categories:
- ruby
- rails
- metaprogramming
- interview
---

---
* ### ***class_eval vs instance_eval***

  Now the name here is confusing. *class_eval* creates instance method whereas
  *instance_eval* creates class methods

  Consider the example below

  {% highlight ruby %}
  class HelloWorld
  end

  # Example for class_eval
  HelloWorld.class_eval do
    def hello
      'hello'
    end
  end

  # Example for instance_eval
  HelloWorld.instance_eval do
    def world
      'world'
    end
  end

  # class_eval created an instance method
  HelloWorld.new.hello #=> 'hello'

  # instance_eval created a class method
  HelloWorld.world #=> 'world'

  {% endhighlight %}
