:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

# groundOverlay.setClickable()

Change clickability of the circle.

```html
<div id="map_canvas">
  <span class="smallPanel"><input type="checkbox" id="toggleCheckbox" checked="checked">circle.setClickable(true)</span>
</div>
```

```js
var bounds = [
  {"lat": 40.712216, "lng": -74.22655},
  {"lat": 40.773941, "lng": -74.12544}
];
var div = document.getElementById("map_canvas");
var map = plugin.google.maps.Map.getMap(div, {
  camera: {
    target: bounds,
    padding: 40
  }
});
map.addEventListener(plugin.google.maps.event.MAP_READY, function() {

    // All gestures (such as pinch-zooming) are disabled.
    map.setAllGesturesEnabled(false);

    // Add ground overlay
    map.addGroundOverlay({
      'url': "../images/newark_nj_1922.jpg",
      'bounds': bounds,
      'opacity': 0.5,
      'clickable': true // default = false
    }, function(groundOverlay) {

        var checkbox = document.getElementById("toggleCheckbox");
        checkbox.addEventListener("change", function() {

            // Change the clickable property
            groundOverlay.setClickable(checkbox.checked);
        });

        // Catch the GROUND_OVERLAY_CLICK event
        groundOverlay.on(plugin.google.maps.event.GROUND_OVERLAY_CLICK, function(latLng) {
            alert("The ground overlay is clicked!");
        });
    });
});
```

![](image.gif)
