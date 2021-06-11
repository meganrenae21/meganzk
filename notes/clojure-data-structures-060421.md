---
title: "Clojure Data Structures"
permalink: clojure-data-structures-060421
isnote: true
layout: default
category: analysis
tags: [programming, web_development, clojure]
related_notes: 
- clojure-forms-060421.md
- defining-constants-clojure-060421.md
references: higginbotham-2015.md
note_id: 65
---

In most cases, the values defined as [constants](defining-constants-clojure-060421) are in the form of one of clojure's many embedded data structures. 

## Numbers

- Integers: whole numbers (93)
- Floats: numbers that have a decimal in place (1.2)
- Ratios: or fractions (1/5)

## Strings

Strings represent text directly. 

Strings can only be delineated with double-quotes (not single quotes). In order for a quotation mark to be part of a string, the quote must be escaped with a preceding backslash `\`.

The **str** function concatenates multiple values into a string. Example:

`(def name "Chewbacca")
    (str "\"Uggllglglglglglglglll\" - " name)`
The above returns *"Uggllglglglglglglglll" - Chewbacca*

## Maps

Maps are used to associate or group key-value pairs. They are encased in curley brackets - `{}`. Map *literals* take this form:

{ :keyword-one "Value-1"
    :keyword-two "Value-2" }

Keys can also be associated with an operator or function: `{"string-key" +}`

Maps can be nested (a map acts as a value associate with a keyword for a parent map):

`{:name {:first "John" :last "Smith"}}`

Map values can be values of *any* data type. 

An alternative to map literals is using the **hash-map** function:

`(hash-map :a 1 :b 2)`
This will return {:a 1 :b 2}

### Retrieving values within maps

The **get** function will retrieve a value by its key. The function takes the following order:
(get **map** **key**)

`(get {:a 0 :b 1} :b)`
This will retrieve the value to the keyword `:b`, or 1.

An optional argument can be added to the end of the **get** expression that will tell the program what to return if it cannot find a value for the key given. If this argument is not given, then the program will return *nil* if there is no value for the key given.

`(get {:a 0 :b 1} :c "unicorns?")`
This returns "unicorns?" as there is no value for the key `:c`

The **get-in** function retrieves values within nested maps. They take the following order:
(get-in **map-with-nested-map** [:a :b])
In the above, `:b` is a key within the map value of the key `:a`. 

`(get-in {:a 0 :b {:c 3}} [:b :c])`
Returns 3

A map can be treated as a *function* in the clojure expression, in which a specific *key* for that map can be an operand to retrieve that value of that key. 

`({:a 1} :a)`
Returns 1

## Keywords

Keywords are used to define values, primarily in maps. A colon (:) precedes the key. Examples:

:a
:name
:32

Keywords can be used as a function to look up a value. If no value is found, it will return "nil" unless an optional default value is given as the last operand in the expression. 

`(:a {:a 1 :b 2 :c 3})`
Returns 1

`(:c {:a 1 :b 2})`
Returns nil

`(:c {:a 1 :b 2} "hello world")`
Returns "hello world"

## Vectors

Vectors are zero-indexed arrays. 

The **get** function can be used with a vector to get a value by its index. The order for such an expression is:
(get **vector** **index**)

`(get [1 2 3] 0)`
Returns 1

Vector values can be of any type.

Vectors can be created with a **vector** function:

`(vector 1 2 3)`
Returns [1 2 3]

The **conj** function adds elements to the end of an existing vector:

`(conj [1 2 3] 4)`
Returns [1 2 3 4]

## Lists

Like vectors, lists are a linear collection of values, with key differences - for example, the **get** function doesn't work with lists (instead use the **nth** function which is described below).

List literals are forms by inserting all the elements in parentheses, each element separated by a space, and placing a single-quote mark before the first parenthesis:

'(1 2 3 4)

When evaluted, the program with drop the preceding single-quote.

To retrieve a specified element in the list, use 

`(nth '(:a :b :c) 0)`
will return `:a`

Lists can also be created via the **list** function. 

`(list 1 2 3 4)`
Returns (1 2 3 4)

The **conj** function can be used with lists, like with maps, but elements are added to the *beginning* of the list and *not* the end:

`(conj '(1 2 3) 4)`
Returns (4 1 2 3)

## Sets

Sets are collections of unique (in other words, unrepeated) values. They come in two forms: **hash sets** and **sorted sets**.

Literal notation of a hash set:

#{"kurt vonnegut" 20 :icicle}

The function **hash-set** can be used to create a set:

`(hash-set 1 1 2 2)`
Returns #{1 2}

You cannot add a value to a set if the value already exists in the set -- the set will not change.

`(conj #{:a :b} :b)`
This will just return `#{:a :b}`

Create a set from existing vectors and lists using the **set** function:

`(set [3 3 3 4 4])`
Returns `#{3 4}`

The **contains?** function checks if a value is included within a set. It returns *true* or *false*. 

`(contains? #{:a :b} :a)`
Returns true

`(contains? #{:a :b} 3)`
Returns false

Using a keyword as the function with a set as its operand will return the keyword if it exists within the set, or nil if it does not:

`(:a #{:a :b})`
Returns :a

The **get** function on a set works the same way, except the value you are searching for is the last operand. 
