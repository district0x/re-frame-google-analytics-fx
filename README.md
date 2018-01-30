# re-frame-google-analytics-fx

This is [re-frame](https://github.com/Day8/re-frame) library, which contains several [Effect Handlers](https://github.com/Day8/re-frame/tree/develop/docs) for working with Google Analytics.

## Installation
```clojure
[district0x.re-frame/google-analytics-fx "1.0.0"]
```
```clojure
(ns my.app
  (:require [district0x.re-frame.google-analytics-fx])
```
Add Google Analytics snippet to your page. **Don't copy this one, may be outdated**
```html
<script>
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');
ga('create', 'UA-XXXXX-Y', 'auto');
</script>
```


## Usage
To enable or disable logging use:
```clojure
(district0x.re-frame.google-analytics-fx/set-enabled! false)
; To Disable while developing:
(district0x.re-frame.google-analytics-fx/set-enabled! (not goog.DEBUG))
```

Following effect handlers are available. Note, none of parameters is mandatory. `fields-object` always goes through `clj->js`
#### :ga/page-view
[Page Tracking](https://developers.google.com/analytics/devguides/collection/analyticsjs/pages)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/page-view [url fields-object]}))
```

#### :ga/event
[Event Tracking](https://developers.google.com/analytics/devguides/collection/analyticsjs/events)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/event [category action label value fields-object]}))
```
#### :ga/social
[Social Interactions](https://developers.google.com/analytics/devguides/collection/analyticsjs/social-interactions)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/social [social-network social-action social-target fields-object]}))
```
#### :ga/screen-view
[Screen Tracking](https://developers.google.com/analytics/devguides/collection/analyticsjs/screens)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/screen-view [fields-object]}))
```
#### :ga/timing
[User Timings](https://developers.google.com/analytics/devguides/collection/analyticsjs/user-timings)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/timing [timing-category timing-var timing-value timing-label fields-object]}))
```
#### :ga/exception
[Exception Tracking](https://developers.google.com/analytics/devguides/collection/analyticsjs/exceptions)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/exception [description fatal?]}))
```
#### :ga/send
[Send](https://developers.google.com/analytics/devguides/collection/analyticsjs/command-queue-reference#send)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/send [fields-object]}))
```
#### :ga/set
[Set](https://developers.google.com/analytics/devguides/collection/analyticsjs/command-queue-reference#set)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/set [fields-object]}))
```
#### :ga/create
[Create](https://developers.google.com/analytics/devguides/collection/analyticsjs/command-queue-reference#create)
```clojure
(reg-event-fx
  :some-event
  (fn []
    {:ga/create [tracking-id cookie-domain name fields-object]}))
```






