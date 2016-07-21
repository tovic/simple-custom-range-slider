Simple Custom Range Slider
==========================

> The simplest JavaScript custom range slider ever!

[View Demo](https://rawgit.com/tovic/range-slider/master/range-slider.html)

Basic Usage
-----------

The required HTML is:

~~~ .html
<div id="range-slider-1"></div>
~~~

Execution…

### Basic

~~~ .javascript
// horizontal slider
RS(document.getElementById('range-slider-1'), function(value, target, event) {
    console.log(value);
});

// vertical slider
RS(document.getElementById('range-slider-1'), function(value, target, event) {
    console.log(value);
}, true);
~~~

### Advance

~~~ .javascript
// horizontal slider
RS(document.getElementById('range-slider-1'), {
    value: 1, // initial value
    vertical: false, // vertical or horizontal slider?
    create: function(value, target) { … }, // create event
    start: function(value, target, event) { … }, // start event
    drag: function(value, target, event) { … }, // drag event
    stop: function(value, target, event) { … } // stop event
});
~~~

Examples
--------

Showing the range slider value into a particular area:

~~~ .javascript
RS(document.getElementById('range-slider-1'), function(value) {
    document.getElementById('result-area').innerHTML = value + '%';
});
~~~

Set default value on initiation:

~~~ .javascript
RS(document.getElementById('range-slider-1'), {
    value: 10, // 10% of total width
    drag: function(value) {
        document.getElementById('result-area').innerHTML = value + '%';
    }
});
~~~

Creating custom `min` and `max` value in range slider as pixels:

~~~ .javascript
var min = 2,
    max = 40;

function pixelToPercent(pixel) {
    return ((pixel - min) / (max - min)) * 100;
}

function percentToPixel(percent) {
    return ((percent / 100) * (max - min)) + min;
}

RS(document.getElementById('range-slider-1'), {
    value: pixelToPercent(10),
    drag: function(value) {
        document.getElementById('result-area').innerHTML = Math.round(percentToPixel(value));
    }
});
~~~

Folks
-----

> **Update 2016/07/21: Is now has support for touch/mobile devices by default.

 - Added support for touch/mobile devices by @beard86 &rarr; [link](https://github.com/beard86/simple-custom-range-slider)