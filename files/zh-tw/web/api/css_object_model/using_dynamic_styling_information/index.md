---
title: 使用動態樣式資訊
slug: Web/API/CSS_Object_Model/Using_dynamic_styling_information
translation_of: Web/API/CSS_Object_Model/Using_dynamic_styling_information
---
The CSS Object Model (CSSOM), part of the DOM, exposes specific interfaces allowing manipulation of a wide amount of information regarding CSS. Initially defined in the _DOM Level 2 Style_ recommendation, these interfaces forms now a specification, _CSS Object Model (CSSOM)_ which aims at superseding it.

In many cases, and where possible, it really is best practice to dynamically manipulate classes via the {{ domxref("element.className", "className") }} property since the ultimate appearance of all of the styling hooks can be controlled in a single stylesheet. One's JavaScript code also becomes cleaner since instead of being dedicated to styling details, it can focus on the overall semantics of each section it is creating or manipulating, leaving the precise style details to the stylesheet. However, there are cases where actually obtaining or manipulating the rules can be useful (whether for whole stylesheets or individual elements), and that is described in further detail below. Note also that, as with individual element's DOM styles, when speaking of manipulating the stylesheets, this is not actually manipulating the physical document(s), but merely the internal representation of the document.

The basic `style` object exposes the {{domxref("Stylesheet")}} and the {{domxref("CSSStylesheet")}} interfaces. Those interfaces contain members like `insertRule`, `selectorText`, and `parentStyleSheet` for accessing and manipulating the individual style rules that make up a CSS stylesheet.

To get to the `style` objects from the `document`, you can use the {{domxref("document.styleSheets")}} property and access the individual objects by index (e.g., `document.styleSheets[0]` is the first stylesheet defined for the document, etc.).

## 透過 CSSOM 修改樣式表規則

```html
<html>
<head>
<title>Modifying a stylesheet rule with CSSOM</title>
<style type="text/css">
body {
 background-color: red;
}
</style>
<script type="text/javascript">
var stylesheet = document.styleSheets[1];
stylesheet.cssRules[0].style.backgroundColor="blue";
</script>
</head>
<body>
The stylesheet declaration for the body's background color is modified via JavaScript.
</body>
</html>
```

{{ EmbedLiveSample('Modify_a_stylesheet_rule') }}

The list of properties available in the DOM from the style property is given on the [DOM CSS Properties List](/zh-TW/docs/DOM/CSS) page.

To modify styles to a document using CSS syntax, one can insert rules or insert {{HTMLElement("style")}} tags whose `innerHTML` property is set to the desired CSS.

## 修改元素的樣式

The element {{domxref("HTMLElement.style", "style")}} property (see also the section "DOM Style Object" below) can also be used to get and set the styles on an element. However, this property only returns style attributes that have been set _in-line_ (e.g, `<td style="background-color: lightblue">` returns the string "`background-color:lightblue`", or directly for that element using `element.style.propertyName`, even though there may be other styles on the element from a stylesheet).

Also, when you set this property on an element, you override and erase any styles that have been set elsewhere for that element's particular property you are setting. Setting the border property, for example, will override settings made elsewhere for that element's border property in the head section, or external style sheets. However, this will not affect any other property declarations for that element's styles, such as padding or margin or font, for example.

To change a particular element's style, you can adapt the following example for the element(s) you want to style.

```html
<html>
<head>
<title>simple style example</title>

<script type="text/javascript">

function alterStyle(elem) {
  elem.style.background = 'green';
}

function resetStyle(elemId) {
  elem = document.getElementById(elemId);
  elem.style.background = 'white';
}
</script>

<style type="text/css">
#p1 {
  border: solid blue 2px;
}
</style>
</head>

<body>

<!-- passes a reference to the element's object as parameter 'this'. -->
<p id="p1" onclick="alterStyle(this);">
 Click here to change background color.
</p>

<!-- passes the 'p1' id of another element's style to modify. -->
<button onclick="resetStyle('p1');">Reset background color</button>

</body>
</html>
```

{{ EmbedLiveSample('Modify_an_element_style') }}

The {{domxref("window.getComputedStyle", "getComputedStyle()")}} method on the `document.defaultView` object returns all styles that have actually been computed for an element. See [Example 6: getComputedStyle](/en/Gecko_DOM_Reference/Examples#Example_6:_getComputedStyle) in the examples chapter for more information on how to use this method.

## DOM Style Object

The `style` object represents an individual style statement. Unlike the individual rules available from the [`document.styleSheets`](/en/DOM/document.styleSheets) collection, the style object is accessed from the `document` or from the elements to which that style is applied. It represents the _in-line_ styles on a particular element.

More important than the two properties noted here is the use of the `style` object to set individual style properties on an element:

```html hidden
<!DOCTYPE html>
<html>
 <head>
  <title>style Property Example</title>
  <link rel="StyleSheet" href="example.css" type="text/css">
  <script type="text/javascript">
    function stilo() {
      document.getElementById('d').style.color = 'orange';
    }
    function resetStyle() {
      document.getElementById('d').style.color = 'black';
    }
  </script>
 </head>

 <body>
  <div id="d" class="thunder">Thunder</div>
  <button onclick="stilo()">Click here to change text color</button>
  <button onclick="resetStyle()">Reset text color</button>
 </body>
</html>
```

{{ EmbedLiveSample('DOM_Style_Object_code_sample') }}

The **media** and **type** of the style may or may not be given.

### 使用 setAttribute 方法

Note that you can also change style of an element by getting a reference to it and then use its [`setAttribute`](/en/DOM/element.setAttribute) method to specify the CSS property and its value.

```js
var el = document.getElementById('some-element');
el.setAttribute('style', 'background-color:darkblue;');
```

Be aware, however, that `setAttribute` removes all other style properties that may already have been defined in the element's style object. If the `some-element` element above had an in–line style attribute of say `style="font-size: 18px"`, that value would be removed by the use of `setAttribute`.
