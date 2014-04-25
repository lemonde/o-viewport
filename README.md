o-viewport
==========

Utility for moderating listeners for browser events on window

*Note: within the module and in the documentation below `orientation` is used instead of `orientationchange`, but the actual browser event listened to is `orientationchange`*

## Methods

### `o-viewport#listenTo(event)`
Attaches a debounced/throttled (as appropriate) listener to events on window [`resize`, `scroll` or `orientation`] which in turn fires events within the `oViewport` namespace (see **Events** below)

### `o-viewport#getOrientation()`
Provides a reasonably reliable (more so than `window.orientation`) of obtaining the current orientation of the viewport.

### `o-viewport#setInterval(event, interval)` *Product use only*
Sets the debounce/throttle interval for a given event [`scroll`, `resize` or `orientation`]. 
As a shorthand, calling `setInterval` with 1 - 3 numbers will set the intervals for `scroll`, `resize` and `orientation` in that order e.g. `setInterval(100, undefined, 300)` is equivalent to:

    setInterval('scroll', 100)
    setInterval('resize') // which does nothing
    setInterval('orientation', 300)

### `o-viewport#debug()`
Tuns on debug mode (logging event details to the console). 

## Events
Each of these custom events are fired on `document.body` and `event.detail.originalEvent` contains a reference to the original browser event. Additiional properties in `event.detail` are detailed below:

### `oViewport.resize`
    clientHeight: body.clientHeight
    clientWidth: body.clientWidth

### `oViewport.orientation`

    clientHeight: body.clientHeight
    clientWidth: body.clientWidth
    orientation: 'portrait' or 'landscape'

### `oViewport.scroll`

    clientHeight: body.clientHeight
    clientWidth: body.clientWidth
    scrollHeight: body.scrollHeight
    scrollLeft: body.scrollLeft
    scrollTop: body.scrollTop
    scrollWidth: body.scrollWidth