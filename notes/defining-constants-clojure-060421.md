---
title: "Defining Constants in Clojure"
permalink: defining-constants-clojure-060421
isnote: true
layout: default
category: analysis
tags: [programming, web_development, clojure]
related_notes: 
- clojure-forms-060421.md
references: higginbotham-2015.md
note_id: 64
---

The **def** operator *binds* a name to a value. 

`(def constant-name constant-value)`

In clojure, data structures are *immutable* -- they cannot be reassigned. Therefore, when *defining* a value name, treat the value as a *constant* and not a *variable*, as is typical in other languages.
