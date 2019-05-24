---
layout: post
title: Ruby on Rails Interview questions ( ActiveRecord ).
categories:
- ruby
- rails
- active record
- interview
---

---
* ### ***Types of association?***
  * belongs_to
  * has_one
  * has_many
  * has_many :through
  * has_one :through
  * has_and_belongs_to_many

  More info [here](https://guides.rubyonrails.org/association_basics.html)

---
* ### ***Object Relational Mapping?***

  ORM is a programming technique for converting data between incompatible type
  systems using object-oriented programming languages. This creates a virtual
  object database and can be used in OOP language.

  Simply in ActiveRecord terms, classes are mapped to table in the database, and
  objects are mapped to the rows of the table.

---
* ### ***Difference between perload, includes, eager_load & joins?***

  **Preload** always loads the asscociated table results in a seperate query.
  This means that we cannot use a where condition on the associated table.

  **Includes** is similar to preload, it uses two queries to fetch the results.
  But if there is a where condition in the associated table, includes is smart
  enough to convert it into a single query using LEFT OUTER JOIN to get the
  results.

  **Eager** load uses a single LEFT OUTER JOIN query to fetch the results.
  Similar to includes using a where condition in associated table.

  **Joins** uses a single INNER JOIN on the associated table.

  A better explation is provided [here](https://blog.bigbinary.com/2013/07/01/preload-vs-eager-load-vs-joins-vs-includes.html)

