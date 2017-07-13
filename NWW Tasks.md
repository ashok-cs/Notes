	## Collapse left side bar by default
  ```js
  $(document).ready(function(){
		$('#collapse-left-sidebar').trigger('click');
	});
  ```


## July 7
Get position details (latitude, longitude) on mouse click

**GlobalViewModel.js**
```
  globe.wwd.addEventListener('click', function (event) {
                self.handleDropClick(event);
                //july
                var x = event.clientX;
                var y = event.clientY;
                var pickList = globe.wwd.pick(globe.wwd.canvasCoordinates(x, y));
                var position = pickList.objects[0].position;
                    alert("test "+ position.latitude +" "+ position.longitude) ;

            });
```

Reference:
- https://webworldwind.org/developers-guide/event-and-gesture-handling/
- http://worldwindserver.net/webworldwind/examples/GoToLocation.js


## July 13
[GetFeatureInfo with BBox from latLon](http://localhost:8080/geoserver/topp/wms?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetFeatureInfo&FORMAT=image%2Fpng&TRANSPARENT=true&QUERY_LAYERS=topp%3Astates&STYLES&LAYERS=topp%3Astates&INFO_FORMAT=text%2Fhtml&FEATURE_COUNT=50&X=50&Y=50&SRS=EPSG%3A4326&WIDTH=101&HEIGHT=101&BBOX=-103.929,44.375,-103.633,44.500)

```javascript
  var xmin = position.longitude;
              var ymin = position.latitude;
              var xmax = xmin + 0.300;
              var ymax = ymin + 0.300;
              var latLon = xmin + "," + ymin + "," + xmax + "," + ymax ;
	      var content  = '<iframe style="border: 0px; "src="http://localhost:8080/geoserver/topp/wms?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetFeatureInfo&FORMAT=image%2Fpng&TRANSPARENT=true&QUERY_LAYERS=topp%3Astates&STYLES&LAYERS=topp%3Astates&INFO_FORMAT=text%2Fhtml&FEATURE_COUNT=50&X=50&Y=50&SRS=EPSG%3A4326&WIDTH=101&HEIGHT=101&BBOX=' + latLon + '" width="100%" height="100%"></iframe>';
	                  var $featuredialog =  $("#feature").html(content).dialog({
              autoOpen: false,
              title: "GetFeatureInfo"
            });
            $featuredialog.dialog("open");
```	      
