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
