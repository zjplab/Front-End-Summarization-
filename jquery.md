# Dom Manipulation 

Adding jQuery to the web is easy:
```html
    <body>
        <!-- your page -->
        <script src="[location of minified jQuery JavaScript file]"></script>
        <script>
            // your custom scripts that use jQuery
        </script>
    </body>
```
## [Dollar Sign Usage](https://programming.argmax.club/2019/07/dollar-sign-in-jquery.html)
`S(content)`
 `$.method()`
## [CSS Selectors in jQuery](https://programming.argmax.club/2019/07/using-css-selectors-with-jquery.html)
```javascript
$('h1') // selects all h1 elements
$('.class-name') // selects all elements with a class of class-name
$('#demo') // selects all elements with an id of demo

// selects **all** elements with an attribute matching the specified value
$('[demo-attribute="demo-value"]') 

// selects all **h1** elements with an attribute matching the specified value
$('h1[demo-attribute="demo-value"]')

//If you wish to find all elements where the value starts with a string, use the ^= operator.
$('[class^="col"]')

//If you wish to find all elements where the value contains a string, use the *= operator.
$('[class*="md"]')

// Selects all a elements that are direct descendants nav element
$('nav > a')

// Selects all a elements that are descendants nav element
// The elements can appear anywhere inside of the element listed first
$('nav a')

```
## [Navigating the DOM](https://programming.argmax.club/2019/07/navigate-dom-with-jquery.html)
CSS offers quite a bit of power when it comes to selecting items. However, there are a couple of limitations. First, CSS selectors aren't dynamic; if new items are added later those new items aren't part of the selection. Second, there are times when it's just easier to express the items you want programatically rather than using CSS. Fortunately, jQuery allows us to select items by using code as well.
## [DOM Manipulation](https://programming.argmax.club/2019/07/dom-manipulation.html)
```javascript
currentElement.addClass('class-name');
currentElement.removeClass('class-name');

//retrieve an attribute
alert($('selector').attr('attribute-name'));
//modify an attribute
$('selector').attr('attribute-name', 'new value');

// update the text
$(item).text('Hello, world!!');

// update the HTML
$(item).html('
Hello, world!!
');

//event handler 
// click event
// raised when the item is clicked
$(item).click(function() {
    alert('clicked!!');
});

// hover event
// raised when the user moves their mouse over the item
$(item).hover(function() {
    alert('hover!!');
});

// mouseout
// raised when the user moves their mouse away from an item
$(item).mouseout(function() {
    alert('mouse out');
});
```
