![](https://i.imgur.com/oJs2tlc.png)

the event object passes through one or more [event phases](https://www.w3.org/TR/DOM-Level-3-Events/#event-phase). There are three event phases: [capture phase](https://www.w3.org/TR/DOM-Level-3-Events/#capture-phase), [target phase](https://www.w3.org/TR/DOM-Level-3-Events/#target-phase) and [bubble phase](https://www.w3.org/TR/DOM-Level-3-Events/#bubble-phase).

A phase will be skipped if it is not supported, or if the event object’s propagation has been stopped.

*if the bubbles attribute is set to false, the bubble phase will be skipped, and if stopPropagation() has been called prior to the dispatch, all phases will be skipped.*

> note: you need to understand all 3 phases and its working as well


---
#javascript