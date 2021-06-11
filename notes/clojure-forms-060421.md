---
title: "Clojure Forms"
permalink: clojure-forms-060421
isnote: true
layout: default
category: analysis
tags: [programming, web_development, clojure]
related_notes:
- control-flow-clojure-060421.md
- true-false-boolean-clojure-060421.md
references: higginbotham-2015.md
note_id: 61
---

Clojure code can have one of two structure:

- Literal representation of data structures 
- Operations

Operations have the following structure:

`(operator operand1 operand2 ... operandn)`

Operands are separated by whitespace.

The **operator** is the function -- it tells the program *what to do*. The **operands** tells the program what the operator is acting on. 

Example: 
(+ 1 2 3)

The operator "+" tells the program to *add* the operands 1, 2, and 3. This will return a value of 6.
