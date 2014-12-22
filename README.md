A Front-End Cheatsheet
====================

Aggregation of my favorite front end scripts and other useful client side code.

### Do something when the window loads
```
# the script
window.onload = function() {...}
# example usage
window.onload = function() {
  heading = document.createElement("h1");
  heading_text = document.createTextNode("Big heading!");
  heading.appendChild(heading_text);
  document.body.appendChild(heading);
}
```
### Tying elements together with user input
BLUF: Take user input and use it to respond, label, etc.
```
# the script
function setStyle(ele) {
  var color = document.getElementById("colorButton").value;
  ele.style.background = color;
}
# example usage
<input placeholder="type a color..." type="text" id="colorButton">
<button onclick="setStyle(this);">Submit</button>
```
### Using onChange to Manipulate the DOM

```
# the script
function setBodyAttr(attr, value) {
  if (document.body) eval('document.body.'+attr+'="'+value+'"');
  else notSupported();
}
# example usage
<div style="margin: .5in; height: 400;"> 
  <p><b><tt>text</tt>color</b></p> 
  <form> 
    <select onChange="setBodyAttr('text',
    this.options[this.selectedIndex].value);"> 
      <option value="black">black 
      <option value="darkblue">darkblue 
    </select>
  </form>
</div>
```
### Get the user's current location
```
function geoFindMe() {
  # get an html target destiation
  var output = document.getElementById("out");
  # if the browser doesn't support the geolocation API
  if (!navigator.geolocation) {
    output.innerHTML = "<p>Geolocation is not supported by your browser.</p>"
    return;
  }
  # if successful, post to screen
  function success(position) {
    var latitude = position.coords.latitude;
    var longitude = position.coords.longitude;

    output.innerHTML = '<p>Latitude is ' + latitude + ' and longitude is ' + longitude + '</p>';

    var img = new Image();
    # build a google maps rendering
    img.src = "http://maps.googleapis.com/maps/api/staticmap?center=" + latitude + "," + longitude + "&zoom=13&size=300x300&sensor=false";
    # put the map on the screen
    output.appendChild(img);

  }
  # error callback
  function error() {
    output.innerHTML = "Unable to retrieve your location.";
  }

  output.innerHTML = "Locating...";

  navigator.geolocation.getCurrentPosition(success, error);
}
```
### Credits
Mozilla Developer's Network
