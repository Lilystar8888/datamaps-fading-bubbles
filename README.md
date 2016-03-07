# DataMaps - Fading Bubbles Plugin

The fading bubbles plugin can be used to visualize location-based, time-lapse data on a DataMap. An example of this plugin can be viewed on this [block](http://bl.ocks.org/mitch-seymour/ba096bc96ff6fe6e66c5).

## Basic Usage ##
First, include d3, topojson, datamaps, and the fading bubbles plugin in your page.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.12/d3.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/topojson/1.6.20/topojson.min.js"></script>
<script src="datamaps.world.min.js"></script>
<script src="datamaps.fading-bubbles.js"></script>
```
Now, add a container for the map to be rendered on.

```html
<div id="map"></div> 
```

Finally, initiate the map and add the fading bubbles plugin.

```js
// map options
var options = {
    element: document.getElementById('map'),
    fills: {
        defaultFill: '#2c3e50'
    },
    geographyConfig: {

        highlightFillColor: 'rgba(52, 73, 94, .9)',
        highlightBorderOpacity: 0
    },
    scope: 'world',
    projection: 'orthographic',
    projectionConfig: {
        rotation: [97, -30]
    }
};
        
// initiate the map    
var map = new Datamap(options);
            
// add the fading bubbles plugin
map.addPlugin('fadingBubbles', fadingBubbles);
```

Now, the plugin is ready to go, you just need to add the data. The fading bubbles plugin accepts an array of data. Each item in the array is an object, with a `latitude`, `longitude`, and optional `magnitude` property.

```js
var data = [
    {
        "latitude": "28.014067",
        "longitude": "-81.728676"
    },
    {
        "latitude": "40.750793",
        "longitude": "-73.989525",
        "magnitude": 3
    }
];

map.fadingBubbles(data);
```
  
The `latitude` and `longitude` properties control tell the plugin where to add the bubbles, while the `magnitude` property controls the size of the fading bubble. More options will be coming soon, so please check back or contribute!
