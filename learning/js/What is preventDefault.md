Events in this category are said to be cancelable and the behavior they cancel is called their default action. Cancelable event objects can be associated with one or more 'default actions'. To cancel an event, call the preventDefault() method.

Example 1.
A [`mousedown`](https://www.w3.org/TR/DOM-Level-3-Events/#mousedown) event is dispatched immediately after the user presses down a button on a pointing device (typically a mouse). One possible [default action](https://www.w3.org/TR/DOM-Level-3-Events/#default-action) taken by the implementation is to set up a state machine that allows the user to drag images or select text. The [default action](https://www.w3.org/TR/DOM-Level-3-Events/#default-action) depends on what happens next — for example, if the user’s pointing device is over text, a text selection might begin. If the user’s pointing device is over an image, then an image-drag action could begin. Preventing the [default action](https://www.w3.org/TR/DOM-Level-3-Events/#default-action) of a [`mousedown`](https://www.w3.org/TR/DOM-Level-3-Events/#mousedown) event prevents these actions from occurring.


---
#javascript 