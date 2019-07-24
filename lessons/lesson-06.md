# FEW 2.2 - Advanced CSS - CSS Custom Properties Scope and Styling Controls

Styling controls like buttons and form elements provides some extra challenges and opportunities.

## Why you should know this?

Form elements and controls are points of interaction in your applications. These need to be extra engaging. Hard to use and confusing forms risk losing potential users for application and customers for your business. 

## Learning Objectives

1. Styling controls
1. Use Custom property scope
1. Use CSS Filters
1. Use browser prefixes to make styles work across all browsers

## Styling Controls 

Controls are important people interact with your web products through the controls you provide. If the controls work well and people can intuit what to do with them they are more likely create user accounts, submit content, and buy products on your sites. 

### Buttons 

The button is used for taking actions. The basic button doesn't look so hot. There is a lot you can do to improve the button. 

```HTML
<button>Click!</button>
```

Set a style for all buttons using the `button` type selector. 

```CSS 
button {

}
```

You'll need to remove the default button styles. Your reset css may do more or less of this work if you used a reset. 

```CSS
button {
  /* Remove the default styles */
  border: none;
  font: inherit;
  color: inherit;
  box-shadow: none;
  background-color: transparent;
}
```

Add some style to the button. 

```CSS
button {
  ...

  /* Give the button a finger cursor */
  cursor: pointer;
  /* Style the button */
  border-width: 2px;
  border-style: solid;
  border-color: transparent;
  border-radius: 0.5em;
  padding: 0.7em 1em; /* Use padding to give the text some space */
  font-size: 1em;

  ...
}
```

Prepare for an interactive state and inherit some colors from our defaults. 

```CSS
button {
  ...
  /* Use some variables to control the appearance */
  background-color: var(--background-color, var(--primary-color));
  color: var(--light-color);
}
```

Be sure to style the interactive states of the button: `:hover` and `:active`. _These should be applied in this order!_

```CSS
/* Style the interactive states of the button */
button:hover {
  /* When the cursor is over the button */
}

button:active {
  /* When the mouse is pressed over the button */
}
```

Add some styles. Use custom property values to your advantage. The example below sets the border color and the text color to the primary color and makes the background transparent. 

```CSS
/* Style the interactive states of the button */
button:hover {
  /* Use the variables here */ 
  background-color: var(--body-color);
  border-color: var(--background-color, var(--primary-color));
  color: var(--background-color, var(--primary-color));
}

button:active {
  /* When the mouse is pressed over the button */
}
```

For a button press we'll set set the fill and text color back to the starting values and make the button darker using filter. 

```CSS
/* Style the interactive states of the button */
button:hover {
  /* Use the variables here */ 
  background-color: var(--body-color);
  border-color: var(--background-color, var(--primary-color));
  color: var(--background-color, var(--primary-color));
}

button:active {
  background-color:var(--primary-color);
  color: var(--light-color);
  /* Use filter to make the button darker */
  -webkit-filter: brightness(80%);
  -moz-filter: brightness(80%); 
  -ms-filter: brightness(80%);
  -o-filter: brightness(80%);
  filter: brightness(80%);
}
```

Notice the vendor prefixes on the filter property! See the section below on Browser/Vendor prefixes for more info. 

Think about adding a transition. A little bit of motion adds some interest. 


```CSS 
button {

  ...

  /* Animate changes */
  transition: 200ms;
}
```

Now any changes changes are applied over 200 milliseconds. 

Below of the agregated code from the samples above. 

```CSS
button {
  /* Remove the default styles */
  border: none;
  font: inherit;
  color: inherit;
  box-shadow: none;
  background-color: transparent;

  /* Give the button a finger cursor */
  cursor: pointer;
  /* Style the button */
  border-width: 2px;
  border-style: solid;
  border-color: transparent;
  border-radius: 0.5em;
  padding: 0.7em 1em; /* Use padding to give the text some space */
  font-size: 1em;

  /* Think about adding a transition */
  transition: 200ms;
  
  /* Use some variables to control the appearance */
  background-color: var(--background-color, var(--primary-color));
  color: var(--light-color);
}

/* Style the interactive states of the button */
button:hover {
  /* Use the variables here */ 
  background-color: var(--body-color);
  border-color: var(--background-color, var(--primary-color));
  color: var(--background-color, var(--primary-color));
}

button:active {
  background-color:var(--background-color, var(--primary-color));
  color: var(--light-color);
  /* Use filter to make the button darker */
  -webkit-filter: brightness(80%);
  -moz-filter: brightness(80%); 
  -ms-filter: brightness(80%);
  -o-filter: brightness(80%);
  filter: brightness(80%);
}
```

#### Browser/Vendor prefixes

New features require properties prefixed with a browser/vendor prefix. In the example above you see this in `button:active` for the `filter` property. 

- -webkit-filter: brightness(80%);
-	-moz-filter: brightness(80%);
-	-ms-filter: brightness(80%);
-	-o-filter: brightness(80%);
-	filter: brightness(80%);

There are two ways to handle this: 

- SASS use a mixin: https://css-tricks.com/snippets/sass/mixin-prefix-properties/
- CSS Custom property: http://lea.verou.me/2016/09/autoprefixing-with-css-variables/
- You might think of your own solution also!

### Form elements 

Form elements are input, textarea, radio button, and checkbox. 

#### Input 

The input has many types they all look a little different and will look different on different browsers. For now style the text inputs.

Inputs should always have a label. The label can be a sibling or a parent. Your framework can work with it in either way. 

**The label needs to be associated with with the input!** This will happen automatically if the input is a child of the label. Otherwise you'll need to use the set the id and for attributes on the input and the label. 

I chose to make the input a child. This makes it hard to style the label text. My framework will require the label text be wrapped in a span. I will need to include this in the documentation. 

```html
<label>
  <span>Text:</span>
  <input type="text" placeholder="What is your name?">
</label>
```

Use the group selector and the attribute selector to style the text, email, and password inputs. 

```CSS
input[type=text], 
input[type=email], 
input[type=password], 
textarea {
  --border-color: var(--color-medium);
  padding: 0.7em 1em;
  border: 2px solid var(--border-color);
  border-radius: 0.5em;
  font-size: 1em;

  /* Add a transition */
  transition: 200ms;

  /* 
    This removes the accessibility outline 
    which should never be removed
    https://a11yproject.com/posts/never-remove-css-outlines/
  */
  outline: none !important; 
}
```

For elements should have a label. If the label wraps the form element they will be associated. This means clicking the label is same as clicking the form element. It also helps screen readers make forms more accessible. 

```CSS
label {
  display: block;
  margin: 0 0 1em 0;
}

label > span {
  font-size: 0.75em;
  display: block;
  margin: 1em 0;
}
```

Use the `:focus` selector to style form elements when they have focus. 

```CSS
input[type=text]:focus, 
input[type=email]:focus, 
input[type=password]:focus, 
textarea:focus {
  --border-color: var(--color-primary);
}
```

#### The accessiblity ouline.

That blue outline that appears around form elements is an accessibility feature and should not be removed. Many sites remove this any way. If you do remove it you should provide another way to show the element is selected for people with disabilities. 

**Stretch challenge:** Apply styles for interactive states. See the guide here: 

https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms

### Challenge: Style checkboxes

The goal of this challenge is to take all of the things covered in class so far and use them to create some good looking radio buttons and check boxes. 

- Start with the example from class 2 (see the code snippet below). This creates a simple toggle button using label with a nested checkbox. 
- Style the _label_ to make a good looking checkbox. 
- Use custom properties to your advantage.
- Stretch Goal: The HTML snippet below uses two extra divs to generate the image of the sliding button. This would require anyone using your framework to use this markup. While it's not deal breaker, it does provide opportunity for error. A **better solution** would to `:before` and or `:after` to generate these extra elements. 

```HTML
<!-- Switch with Click -->
<div>
  <label id="switch-2" class="switch-2">
    <input type="checkbox">
    <div>
      <div></div>
    </div>
  </label>
  <span>Click Switch no JS</span>
</div>
```

```CSS
/* Switch Click 
This switch is toggled on a click. The JavaScript 
below adds or removes the class .on to change the 
visual state of the switch. */

.switch-2 {
  width: 100px;
  height: 60px;
  border-radius: 30px;
  border: 1px solid #ddd;
  background-color: #efefef;
  position: relative;
  transition: 200ms;
  cursor: pointer;
}

.switch-2 > input {
  display: none;
}

.switch-2 > div {
  width: 56px;
  height: 56px;
  background-color: #fff;
  border-radius: 50%;
  margin: 2px;
  position: absolute;
  left: 0;
  transition: 200ms
}
/* When the .switch has the class .on change the 
color to green. */

.switch-2 input:checked ~ div {
  background-color: #07e207;
}
/* When the .switch has the .on class change the 
position left to 40px. */

.switch-2 input:checked ~ div {
  left: 40px;
}
```

### Challenge: Style radio buttons

Use the concepts above to style radio buttons. 

### Get inspired by form styles

https://uicookies.com/css-input-text/

### Media Queries 









## CSS Custom Properties: Fallback Values 

`var(--variable, fallback-value)`

## Scope and Custom properties

Custom properties are used in the scope where they are defined. This local scope is defined by the selector where a custom property is defined. 

```CSS
button {
  --button-color: #47b6e9;
  ...
  background-color: var(--button-color);
}
```

Custom properties are inherited. A variable that exists on the scope of an ancestor is available to descendents. 

```CSS
body {
  --button-color: #47b6e9; /* common color */
  ...
}

button {
  border-width: 2px;
  border-color: transparent;
  background-color: var(--button-color);
}

button:hover {
  background-color: transparent;
  border-color: var(--button-color);
}
```

The `:root` selector represents the root of the document. This 

## Media Query

Use `@media` to target a platform with features. 

Custom properties and @media for mobile styles

examples........

## Form element strategies 


Setting custom proeprties via the style property. 

Sharing a custom property through scope. 

Button Example .........

Input Example ..........

## Interview Questions 

You need to have flexible UI elements. The default colors work but in some cases you need to be able to easily redefine the color of a button. 

You need to define a range of font sizes. Imagine you need 4 sizes each larger than the previous. All of the sizes should relative to a base size. 

On mobile devices your range of font sizes need to be different from the sizes you are using on the desktop. 

## Wrap Up (5 min)

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

1. Links to additional readings and videos

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
