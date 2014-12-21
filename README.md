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
### Credits
Mozilla Developer's Network
