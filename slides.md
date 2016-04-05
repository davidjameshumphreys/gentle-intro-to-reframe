## What is Re-frame?

|||
|:---|---:|
|<!-- .element class="fragment" -->Language|JS|
|<!-- .element class="fragment" -->Framework|React|
|<!-- .element class="fragment" -->Language|ClojureScript|
|<!-- .element class="fragment" -->Library|Reagent|
|<!-- .element class="fragment" -->Pattern|Re-frame|

---

## Not another ...

Just patterns<sup>*</sup>

<!-- .element class="fragment" --> (* with some code attached)

---

## Why?

Large-scale code exaggerates problems

---

## Large CLJS apps

Some patterns emerge
* Cross-component chatter
  * chans everywhere
* State
  * Synchronising
  * Updating
  * Naming
* <!-- .element class="fragment" -->&c.
* <!-- .element class="fragment" -->etc.
* <!-- .element class="fragment" -->et cetera
* <!-- .element class="fragment" -->How to structure the code?

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

## Anatomy

```clojure
(defn widget [prop1 prop2]
  (fn render [prop1 prop2]
   [:div
    (if (:a @prop1) ...)]))
```

---

## Better
```clojure
(defn widget [prop1 prop2]
  (let [val (reaction (:a @prop1))]
    (fn render [prop1 prop2]
      [:div
        (if @val ...)])))
```

---

## But Channels

Won't work this way.

---

## Enter Re-frame

_[Reagent remains on stage]_

---

## Why Re-frame?

* One-way data-flow
* Isolate logic
* Testable
* Reasonable

---

## Re-frame

* dispatch
* handler
* subscribe
* <!-- .element class="fragment" -->middleware

---

## Dispatch

```clojure
(dispatch [:go-to-page "/page-one/"])
```

fire & forget

---

## Handler
```clojure
(register-handler
 :go-to-page
 [middleware]
 (fn [db [action page-url]]
 ;;mutate the snapshot
 db))
```

pure handlers please

---

## Subscribe
```clojure
(register-sub
  :active-page
  (fn [db _]
    ;;computation on the app-state
    (reaction (:active-page @db))))
```

---

## Middleware

Transform the messages
* Clean
* Validate
* Debug

---

## Demo