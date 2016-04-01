## What is Re-frame?

|||
|:---|---:|
|Language|JS|
|<!-- .element class="fragment" -->Framework|React|
|<!-- .element class="fragment" -->Language|ClojureScript|
|<!-- .element class="fragment" -->Library|Reagent|
|<!-- .element class="fragment" -->Pattern|Re-frame|

---

## Not another Framework

Just patterns<sup>*</sup>

<!-- .element class="fragment" --> (with some code attached)

---

## Large CLJS apps

Some patterns emerge
* Cross-component chatter
* Synchronising state
* Updating state
* Naming bits of state
* <!-- .element class="fragment" -->&c.
* <!-- .element class="fragment" -->etc.
* <!-- .element class="fragment" -->et cetera
* <!-- .element class="fragment" -->How to structure the code?

---

## Why?
Large-scale code exaggerates problems

---

## Channels, Resets & App-state

* One large app-state
* core.async
* Cursors for access (think getters & setters)
* Reactions: read-only signals

---

## Not Enough

Better patterns (not more!)

---
