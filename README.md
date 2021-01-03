# Pageable

[![Maintenance](https://img.shields.io/maintenance/yes/2020?style=for-the-badge)](https://github.com/Mobius1/Pageable/graphs/commit-activity)
[![Code Climate maintainability](https://img.shields.io/codeclimate/maintainability/Mobius1/Pageable.svg?style=for-the-badge)](https://codeclimate.com/github/Mobius1/Pageable/maintainability)
![](http://img.badgesize.io/Mobius1/Pageable/master/dist/pageable.min.js?style=for-the-badge) 
![](http://img.badgesize.io/Mobius1/Pageable/master/dist/pageable.min.js?compression=gzip&label=gzipped&style=for-the-badge)
[![npm](https://img.shields.io/npm/dt/pageable.svg?style=for-the-badge)](https://www.npmjs.com/package/pageable)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=for-the-badge)](https://github.com/Mobius1/Pageable/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/release/Mobius1/Pageable.svg?style=for-the-badge)](https://github.com/Mobius1/Pageable/releases)
[![npm](https://img.shields.io/npm/v/pageable.svg?style=for-the-badge)](https://www.npmjs.com/package/pageable)
[![GitHub issues](https://img.shields.io/github/issues-raw/Mobius1/Pageable.svg?style=for-the-badge)](https://github.com/Mobius1/Pageable)
[![GitHub issues](https://img.shields.io/github/issues-closed-raw/Mobius1/Pageable.svg?style=for-the-badge)](https://github.com/Mobius1/Pageable)

Pageable transforms a web page into a full page scrolling presentation.

  - Lightweight (less than 3kb gzipped)
  - Responsive
  - Performant
  - Touch support
  - Easy to set up
  - IE10+

---

## Install

### npm
```
npm install pageable --save
```

---

### Browser

Grab the file from one of the CDNs and include it in your page:

```
https://unpkg.com/pageable@latest/dist/pageable.min.js
```

You can replace `latest` with the required release number if needed.

You can also include the optional stylesheet that applies styling to the nav pips and buttons: 

```
https://unpkg.com/pageable@latest/dist/pageable.min.css
```

---

## Custom Events

You can listen to Pageable's custom events with the `on(type, callback)` method.

The callback has one argument which returns the data object:
```javascript
{
    index: // the current page index
    scrolled: // the current scroll offset
    max: // the maximum scroll amount possible
    percent: // the scroll position as a percentage of the maximum scroll (v0.6.7 and above)
}
```

The `percent` property can be helpful when adding progress indicators (see [Adding Progress Bars](https://mobius1.github.io/Pageable/progress.html)).

### Examples
```javascript
const pages = new Pageable("#container");

pages.on("init", data => {
    // do something when the instance is ready
});

pages.on("update", data => {
    // do something when the instance is updated
    
    // this event also fires when the screen size changes
});

pages.on("scroll.before", data => {
    // do something before scrolling starts
    
    // this event will fire when the defined delay begins
    
    // e.g. if the delay is set to 400, this event will
    // fire 400ms BEFORE the "scroll.start" event fires    
});

pages.on("scroll.start", data => {
    // do something when scrolling starts
    
    // this event will fire when the defined delay ends
    
    // e.g. if the delay is set to 400, this event will
    // fire 400ms AFTER the "scroll.before" event fires
});

pages.on("scroll", data => {
    // do something during scroll
});

pages.on("scroll.end", data => {
    // do something when scrolling ends
});
```
