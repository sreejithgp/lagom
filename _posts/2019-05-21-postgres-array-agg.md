---
layout: post
title: Postgres array_agg
categories:
- postgres
---

Postgres gives an aggregate function called *array_agg* which can be used in
group clause.

This will give you the result as an array.

Lets jump into an example and see where it can be useful

Consider two tables.

#### Chapters

|  id 	|     name     	|
|:---:	|:------------:	|
|  1  	| Introduction 	|
|  2  	| Summary     	|

#### Pages

|  id 	| chapter_id 	|  name 	|
|:---:	|:---------:	|:-----:	|
|  1  	|     1     	| Page1 	|
|  2  	|     1     	| Page2 	|
|  3  	|     1     	| Page3 	|
|  4  	|     2     	| Page1 	|

#### Required result

|  chapter_id 	| chapter_name 	|  page_ids 	|
|:-----------:	|:------------:	|:---------:	|
|      1      	| Introduction 	| [1, 2, 3] 	|
|      2      	|    Summary   	|    [4]    	|

Now if you want to get the id's of pages that are associated with all chapters as an array similar to the above table.

Using SQL

{% highlight sql %}
  SELECT chapters.id AS chapter_id,
  chapters.name AS chapter_name,
  array_agg(pages.id) as pageids FROM "chapters"
  INNER JOIN "pages" ON "pages"."chapter_id" = "chapters"."id"
  GROUP BY chapters.id
  ORDER BY "chapters"."id" ASC
{% endhighlight %}

Using ActiveRecord.

{% highlight ruby %}
  Chapter.joins(:pages)
    .select('chapters.id AS chapter_id, chapters.name AS chapter_name, array_agg(pages.id) as pageids')
    .group('chapters.id')
{% endhighlight %}
