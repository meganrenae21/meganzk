---
title: "True, False, and Boolean Expressions in Clojure"
permalink: true-false-boolean-clojure-060421
isnote: true
layout: default
category: analysis
tags: [programming, web_development, clojure]
related_notes: 
- clojure-forms-060421.md
- control-flow-clojure-060421.md
references: higginbotham-2015.md
note_id: 63
---

## Truthiness and falsiness**

*Nil* and *false* represent logical falsiness. Any value that isn't *falsey* is *truthy*. You can check if a value is *nil* (or *falsey*) using the *nil?* operand: 

`(nil? 1)` returns false because 1 is not nil
`(nil? nil)` returns true because nil is nil

**Boolean expressions** will treat values as truthy or falsey. The **equality** operator ("=") will evaluate if operands are *equal* (in other words, use "=" when evaluating *truth* rather than *truthiness*).

## Boolean operators

- *or* returns the first truthy value or the last value (if none are truthy) of a list of operands
- *and* returns the first falsey value or the last truthy value (if none are falsey) of a list of operands

`(or false nil 1 2 3)`
- does not return the first operand, "false", because it is falsey
- does not return the second operand, "nil", because it is also falsey
- it *will* return the third operand, 1, which evaluates as truthy

`(or false nil)`
- does not return the first operand, "false" because it is falsey
- *does* return the second operand, "nil" even though it is falsey, because it is the *last* value in the list

`(and 1 2 nil 3 false)`
- does not return the first operand, 1, because it is truthy
- does not return the second operand, 2, because it is truthy as well
- *does* return the third operand, "nil", because it is falsey
- will not evaluate further once it finds a value to return
  
`(and 1 2 3)`
- will not return the first operand, 1, which is truthy
- will not return the second operand, 2, which is truthy
- *will* return the third and final operand, 3, even though it is truthy, because it is the last operand in the list.
