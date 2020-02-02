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

# Contents, Events and Effects

## [Mofiying Elements](https://programming.argmax.club/2019/08/modifying-elements.html)
```javascript
//If you wish to retrieve the value of an input control, all you have to do is call val().
var value = $('#some-input-control').val();

/*If you wish to set the value, simply pass the new value in as a parameter to the val function. If you wish to set a textbox to a blank value, simply use an empty string.*/
// Empty a textbox
$('#some-textbox').val('');

//Remember that attr is going to replace the style attribute, not update it, so any existing styles would be lost. Trying to add or remove styles using attr becomes a challenge.
$('#target').attr('style', 'color: red');

// Retrieve an item's color
var color = $('#target').css('color');

// Change an item's color to red
$('#target').css('color', 'red');

var style = {
	color: 'red',
	backgroundColor: yellow
};

$('#target').css(style);
```
## [Adding New Elements](https://programming.argmax.club/2019/07/dom-manipulation.html)
```javascript
// prepend is called on the target, and accepts the new content as the parameter
$('#target').prepend('<div>New content</div>');

// prependTo is called on the new content, and accepts the target as the parameter
$('<div>New content</div>').prependTo('#target');

// append is called on the target, and accepts the new content as the parameter
$('#target').append('<div>New content</div>');

// appendTo is called on the new content, and accepts the target as the parameter
$('<div>New content</div>').appendTo('#target');

// after is called on the target, and accepts the new content as a parameter
$('target').after('
New content
');

// insertAfter is called on the new content, and accepts the target as a parameter
$('
New content
').insertAfter('#target');

// before is called on the target, and accepts the new content as a parameter
$('target').before('
New content
');

// insertBefore is called on the new content, and accepts the target as a parameter
$('
New content
').insertBefore('#target');

$('#target').wrap('<section></section>');

//wrapAll behaves differently. Rather than wrapping each returned element, wrapAll wraps all returned content with one new element. As a result, the JavaScript
$('.demo').wrapAll('<section></section>');

//wrapInner is different from both wrap and wrapAll in that wrapInner operates on the children of the target, rather than on the target itself.
$('#target').wrapInner('<section></section>');
```
## [Removing, Replacing and Cloning](https://programming.argmax.club/2019/09/removing-replacing-and-cloning.html)
```javascript
//Remove and emptyy
 $('#target').remove()
 $('#target').empty()
 
 // replaceWith replaces the content on the left with the new content in the parameter
$('#target').replaceWith('<div>NEW content</div>');

// replaceAll replaces the target in the parameter with the content on the left
$('<div>NEW content</div>').replaceAll('#target');
```
Clone:
```html
<button type="button" id="add-line">Add new line</button>
<div id="container">
	<div class="user-entry">
		<label>Email:</label>
		<input type="email" />
		<label>Password:</label>
		<input type="password" />
	</div>
</div>
```
```javascript
 $(function() {
 	$userForm = $('.user-entry').clone;
	$('#add-line').click(function() {
		$('#container').append($userForm.clone()); //clone() again to make a deep copy
	});
 });
 ```
 
 ## [Event Handlers](https://programming.argmax.club/2019/08/event-handlers.html)
 ```javascript
 $('button').click(function() {
    // this is linked to button that was clicked, but is a DOM object
    // convert it to a jQuery object by using the jQuery factory
    $(this).text('Clicked!!');
});

// Write out the x/y coordinates of the mouse on click
$('button').click(function(e) {
    $('#output').text(e.pageX + 'x' + e.pageY);
});

//click
$('#target').click(function() { alert('hello, world!'); });

//double click 
$('#target').dblclick(function() { alert('hello, world!'); });

<!-- sample HTML -->
<div>
	<span id="target">Basic data</span>
	<span id="target-help"></span>
</div>
$('#target').mouseenter(function() {
	$('#target-help').text('More data');
}).mouseleave(function() {
	$('#target-help').text('');
});

$('#target').hover(function() {
	// mouseenter
	$('#target-help').text('More data');
}, function() {
	// mouseleave
	$('#target-help').text('');
});

// sample JavaScript
$('#phone').focus(function() {
    // Control has focus. Display help
    $('#phone-help').text('Please enter your phone number as all digits');
}).blur(function() {
    // Control lost focus. Clear help
    $('#phone-help').text('');
});

$('#target').blur(function() {
    // retrieve the value using val
    var value = $('#target').val();
    alert(value);
})
```
   
## [Registering Event Handlers](https://programming.argmax.club/2019/08/registering-event-handlers.html)



# Asynchrouonus programming and AJax

## 
