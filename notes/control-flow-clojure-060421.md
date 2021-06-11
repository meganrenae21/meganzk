---
title: "Control Flow in Clojure"
permalink: control-flow-clojure-060421
isnote: true
layout: default
category: analysis
tags: [programming, web_development, clojure]
related_nodes:
- clojure-forms-060421.md
- true-false-boolean-clojure-060421.md
references: higginbotham-2015.md
note_id: 62
---

## Control flow operators

**if**

The structure of an *if* expression in clojure is as follows:

`(if boolean-form
    then-form
    optional-else-form)`

A **[boolean](true-false-boolean-clojure-060421)** form evaluates to a truthy of falsey value. The **then-form** (first operand) is what the if exprssion returns if the boolean form returns as truthy. The else form is a optional second operand for if the boolean form returns falsey (nil).

**do**

Since the second operand in an *if* expression in Clojure will be evaluated automatically as an *else* statement (if falsey), to program multiple forms within your *then* or *else* operands you can wrap them in a *do* operator. 

`(if true
    (do (println "Success!")
        "By Zeus's hammer!")
    (do (println "Failure!")
        "By Aquarman's trident!"))`

**when**

The *when* operator acts the same as the *if* operator except without the else argument. Because of this, *when* can be an alternative to using *do* to evaluate multiple forms, as long as you want the program to return *nil* if it returns a falsey value.
