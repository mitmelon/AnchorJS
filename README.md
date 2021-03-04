# Anchor 1.0.0
 Anchor is a tiny ES6 JavaScript library used to track elements on a page without using google analytics or any third party scripts. It tracks mouse events and clicks and sends tracking to your backend code to store inside your database.

 You can also pass custom event names to anchor

# Supported Browsers
 ![3c8x9](https://user-images.githubusercontent.com/55149512/109938700-a0ef2100-7cd0-11eb-9c52-66ecea2cd046.png)

 # How to use it:

1. Add Anchor to your page inside the head tag or footer

```
<script src="anchor.min.js"></script>
```

2. Initialize Anchor by adding this code to your page

```js

if (document.getElementsByClassName('MAnchors_').length) {
    var tracking = document.getElementsByClassName('MAnchors_');
    var tracker = new Anchor;
    tracker.endpoint = 'PLACE_YOUR_ANCHOR_TRACKER_BACKEND_LINK_HERE';
    for (const tt of tracking) {
      tracker.init(tt);
    }
  }

```

3. Add Anchors to the elements you want to track

```html
<!-- For Div -->
<div class="MAnchors_" anchor-name="Payment Button">Make Payment</div>

<!-- For Links -->
<a href="" class="MAnchors_" anchor-name="Download Button">Download File</a>

```

 # Use custom events:

 You can overwite the existing events with your own.

```js
//Default events are 
 
['click', 'dblclick', 'touchstart', 'touchend', 'contextmenu', 'mousedown', 'mouseenter', 'mouseleave', 'mousemove', 'mouseout', 'mouseover', 'mouseup']

if (document.getElementsByClassName('MAnchors_').length) {
    var tracking = document.getElementsByClassName('MAnchors_');
    var tracker = new Anchor;
    //Your custom events here
    tracker.events = ['drag','dragend', 'dragenter']//etc
    tracker.endpoint = 'PLACE_YOUR_ANCHOR_TRACKER_BACKEND_LINK_HERE';
    for (const tt of tracking) {
      tracker.init(tt);
    }
  }
```

# Backend Implementation:

At your backend, receive the post data as below.

```php

$anchorName = strip_tags($_POST['anchor_name']);
$eventName = strip_tags($_POST['trigger']);
$positionx = strip_tags($_POST['x']);
$positiony = strip_tags($_POST['y']);
$screenX = strip_tags($_POST['screenX']);
$screenY = strip_tags($_POST['screenY']);
$pageName = strip_tags($_POST['page_name']);
$origin = strip_tags($_POST['origin']);
$platform = strip_tags($_POST['platform']);
$connectionSpeed = strip_tags($_POST['connection_speed']);
$userAgent = strip_tags($_POST['userAgent']);
$timezone = strip_tags($_POST['timezone']);

//Store in DB
//call_db_function()

//You can also use python or any language of your choice for your backend implimentation.

```

If you find any bugs, please post an issue or send me a note at manomitehq@gmail.com.

If you want to contribute to this code, make a pull request.