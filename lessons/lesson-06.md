# FEW 2.2 - Advanced CSS - CSS Custom Properties Scope and Styling Controls

Styling controls like buttons and form elements provide some extra challenges and opportunities.

## Why you should know this?

Form elements and controls are points of interaction in your applications. These need to be extra engaging. Hard to use and confusing forms risk losing potential users for application and customers for your business. 

## Learning Objectives

1. Style form elements
1. Style elements according to state

### Form elements 

Form elements are input, textarea, radio button, and checkbox. 

#### Input 

The input has many types they all look a little different and will look different on different browsers. For now, style the text inputs.

Inputs should always have a label. The label can be a sibling or a parent. Your framework can work with it in either way. 

**The label needs to be associated with with the input!** This will happen automatically if the input is a child of the label. Otherwise, you'll need to use the set the id and for attributes on the input and the label. 

I chose to make the input a child. This makes it hard to style the label text. My framework will require the label text to be wrapped in a span. I will need to include this in the documentation. 

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

For elements should have a label. If the label wraps the form element they will be associated. This means clicking the label is the same as clicking the form element. It also helps screen readers make forms more accessible. 

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

#### The accessibility outline.

That blue outline that appears around form elements is an accessibility feature and should not be removed. Many sites remove this anyway. If you do remove it you should provide another way to show the element is selected for people with disabilities. 

**Stretch challenge:** Apply styles for interactive states. See the guide here: 

https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms

### Challenge: Style checkboxes

The goal of this challenge is to take all of the things covered in class so far and use them to create some good looking radio buttons and checkboxes. 

- Start with the example from class 2 (see the code snippet below). This creates a simple toggle button using a label with a nested checkbox. 
- Style the _label_ to make a good looking checkbox. 
- Use custom properties to your advantage.
- Stretch Goal: The HTML snippet below uses two extra divs to generate the image of the sliding button. This would require anyone using your framework to use this markup. While it's not a deal-breaker, it does provide an opportunity for error. A **better solution** would to `:before` and or `:after` to generate these extra elements. 

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
This switch is toggled on a click. The JavaScript below adds or removes the class .on to change the visual state of the switch. */

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
/* When the .switch has the class .on change the color to green. */

.switch-2 input:checked ~ div {
  background-color: #07e207;
}
/* When the .switch has the .on class change the 
position left to 40px. */

.switch-2 input:checked ~ div {
  left: 40px;
}
```

- https://medium.com/claritydesignsystem/pure-css-accessible-checkboxes-and-radios-buttons-54063e759bb3
- https://www.456bereastreet.com/archive/201211/accessible_custom_checkboxes_and_radio_buttons/
- https://medium.com/claritydesignsystem/pure-css-accessible-checkboxes-and-radios-buttons-54063e759bb3

### Challenge: Style radio buttons

Use the concepts above to style radio buttons. 

### Get inspired by form styles

https://uicookies.com/css-input-text/

## SASS and CSS Custom properties

Use SASS to do what it does best and use custom properties for what they do best. 

What to know? 

**SASS is a preprocessor.** SASS is applied before your code ever reaches the browser. Use SASS to calculate things in advance. 

**Custom Properties are live.** They exist in the browser. If the value of a custom property changes anything that relies on that values renders itself. 

Here is an example. Imagine you have some colors. Often it's good to have tints and shades of your base colors. A tint is a lighter version of a color, imagine you added white. A shade is a darker version of a color, imagine you added black. 

While you could calculate these colors on your own, and this might be best if you are picky about colors, it also could be very tedious. Imagine you had 9 colors and needed 4 lighter (tints) and 4 darker (shades) versions of each base color. You would need to write 81 colors! It would also be very tedious to change the number of tints and shades since you'd have to recalculate each of your colors. 

Let SASS handle this. **Why SASS?** The colors themselves don't change they can be calculated in advance. 

The colors themselves are best defined as Custom Properties. The values are best calculated with SASS. 

Define some colors in a map/dictionary. Using a map you can loop through the values and sue the keys as names. 

```scss
$colors: (
  'gray': rgb(128, 128, 128), 
  'primary': #007bff,
  'info': #17a2b8,
  'success': #28a745,
  'danger': #dc3545,
  'callout': #ffa107,
  'secondary': #ffcd07,
  'other': #ca5ae1,
  'alternate': #a45ae1
);
```

In SASS loop through the map/dictionary with `@each in`. This will give you the`$key` and the `$value` for each item. 

```SCSS
@each $key, $value in $colors {

}
```

SASS provides some functions for working with colors. To make lighter and darker colors you can use `lighten($color, %)` and `darken($color, %)`. These will lighten or darken your colors by the %. For example `lighten(#f00, 10%)` lightens red by 10%. 

Use a `@for from through` to lighten a color in steps. 

``` SCSS
$color: #f00;

:root {
  @for $i from 4 through 1 {
    --color-lighter-#{$i}: #{lighten($color, 10% * $i)};
  }
}
```

This should generate 4 custom properties 10%, 20%, 30%, and 40% lighter. The output should look like: 

```CSS
:root {
  --color-lighter-4: #ffcccc;
  --color-lighter-3: #ff9999;
  --color-lighter-2: #ff6666;
  --color-lighter-1: #ff3333;
}
```

Take note! 

```SCSS
/* Good! */
--color-lighter-#{$i}: #{lighten($color, 10% * $i)};

/* NOT! */
--color-lighter-#{$i}: lighten($color, 10% * $i);

/* This works for a class */
.color-lighter-#{$i}: lighten($color, 10% * $i);
```

This line uses `#{...}` to write the values into the stylesheet. Normally you'd be able use `lighten($color, 10% * $i)` alone. But this didn't work when the property was a custom property! I had to wrap it in `#{...}`. 

Here is a more complete code snippet. The code below 

```SCSS
/* Colors - define an map/dictionary of colors */
$colors: (
  'gray': rgb(128, 128, 128), 
  'primary': #007bff,
  'info': #17a2b8,
  'success': #28a745,
  'danger': #dc3545,
  'callout': #ffa107,
  'secondary': #ffcd07,
  'other': #ca5ae1,
  'alternate': #a45ae1
);
/* Define Custom properties here */
:root {
  @each $key, $value in $colors {
    /* Tints */
    @for $i from 4 through 1 {
      --color-#{$key}-lighter-#{$i}: #{lighten($value, 10% * $i)};
    }

    --color-#{$key}: #{$value}; /* Base Color */

    /* Shades */
    @for $i from 1 through 4 {
      --color-#{$key}-darker-#{$i}: #{darken($value, 10% * $i)};
    }
  }
}
```
The code above should generate something like: 

```CSS
:root {
  /* Tints */
  --color-gray-lighter-4: #e6e6e6;
  --color-gray-lighter-3: #cdcdcd;
  --color-gray-lighter-2: #b3b3b3;
  --color-gray-lighter-1: #9a9a9a;
  --color-gray: gray; /* Base Color */
  /* Shades */
  --color-gray-darker-1: #676767;
  --color-gray-darker-2: #4d4d4d;
  --color-gray-darker-3: #343434;
  --color-gray-darker-4: #1a1a1a;
  ...
}
```

How should you implement this? **Think very carefully about the naming.** The names are what's important here. They will determine how you work with these colors and how useful they will be. 

The scheme I used names every base color with `--color-<name>`. The lighter versions of each color are named: `--color-<name>-lighter-<#>` and the darker colors are named: `--color-<name>-darker-<#>`.

Ask yourself if this is a good naming convention or if you can think of a better system, or just improve on this. 

### Working with SCSS files

Remember your SCSS files need to be compiled into CSS files. Spend a few minutes thinking about your file structure. 

- css
 - framework.css
 - theme.css
- scss
 - colors.scss
 - framework.scss
 - theme.scss

Use `@import` to import one SCSS into another. Above `theme.scss` could import `colors.scss`. 

### Files and Structure

Break your framework into files. This will make it manageable and modular. Here are some ideas. 

- Theming - 
 - Use a file to contain all of the CSS Custom properties. 
 - Use a file to contain all of the base styles
- Use SASS - If you're using SASS you can move styles for various elements into separate files and include these in your compiled CSS. 
- Anyone using your framework will almost always have another style sheet for their customization. **Your framework doesn't have to style all things in all situations** it only needs to provide a good starting point. 
- Use comments to organize your CSS code. CSS Code is verbose and you will write a lot of it. As the length grows it becomes more difficult to track styles. 
- Use a prefix for all of the class names in your framework. This will help in use and prevent namespace collisions. 

## Make a Sample File 

You need to have a sample file to show off your styles and see them in context. Take a clue from the other frameworks they all do this in their documentation. 

## Colors 

Discuss with a partner your colors and choices. There are two questions to answer and get feedback on: 

1. What colors you have? What situations do your colors cover? Do you have a color for a warning? 
2. What do the colors look like? What do you think of the colors? Do they work together well? 

## Naming

You need to make names for things that explain how these things are used. The big two are class names and custom properties. 

Discuss your code with your partner. Read your partner's code and give them feedback on the names used for custom properties and classes. Ask yourself if you understand the purpose of the custom property or class and how you would apply it. 

## Styling Controls 

Controls are important people interact with your web products through the controls you provide. If the controls work well and people can intuit what to do with them they are more likely to create user accounts, submit content, and buy products on your sites. 

### Buttons 

The button is used for taking action. The basic button doesn't look so hot. There is a lot you can do to improve the button. 

```HTML
<button>Click!</button>
```

Set a style for all buttons using the `button` type selector. 

```CSS 
button {

}
```

You'll need to remove the default button styles. Your reset CSS may do more or less of this work if you used a reset. 

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

For a button press, we'll set the fill and text color back to the starting values and make the button darker using `filter`. 

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

Now any changes are applied over 200 milliseconds. 

Below the aggregated code from the samples above. 

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

### Custom properties color recipe

```CSS
:root {
  --hue: 235;
  --sat: 100%;
  --lum: 87%;
  --sat-dark: calc(var(--sat) * 0.6);
  --lum-dark: calc(var(--lum) * 0.7);
  --color: hsla(var(--hue), var(--sat), var(--lum), 1);
  --color-dark: hsla(var(--hue), var(--sat), var(--lum-dark), 1);
}
```

#### Browser/Vendor prefixes

New features require properties prefixed with a browser/vendor prefix. In the example above you see this in `button:active` for the `filter` property. 

- -webkit-filter: brightness(80%);
- -moz-filter: brightness(80%);
- -ms-filter: brightness(80%);
- -o-filter: brightness(80%);
- filter: brightness(80%);

There are two ways to handle this: 

- SASS uses a mixin: https://css-tricks.com/snippets/sass/mixin-prefix-properties/
- CSS Custom property: http://lea.verou.me/2016/09/autoprefixing-with-css-variables/
- You might think of your solution also!

## CSS Custom Properties: Fallback Values 

`var(--variable, fallback-value)`

<!-- ## Scope and Custom properties

Custom properties are used in the scope where they are defined. This local scope is defined by the selector where a custom property is defined. 

```CSS
button {
 --button-color: #47b6e9;
 ...
 background-color: var(--button-color);
}
```

Custom properties are inherited. A variable that exists on the scope of an ancestor is available to descendants. 

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


Setting custom properties via the style property. 

Sharing a custom property through scope. 

Button Example .........

Input Example .......... -->

## Interview Questions 

You need to have flexible UI elements. The default colors work but in some cases, you need to be able to easily redefine the color of a button. 

You need to define a range of font sizes. Imagine you need 4 sizes each larger than the previous. All of the sizes should relative to base size. 

On mobile devices, your range of font sizes needs to be different from the sizes you are using on the desktop. 

## Homework: Framework - Controls

Define some styles for controls in your CSS Framework. See the home description linked below for more details:

- [Framework: Controls](../Assignments/assignment-09-controls.md)

## Wrap Up (5 min)

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

1. Links to additional readings and videos

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time** | **Activity** |
| ----------- | --------- | ------------------------- |
| 0:00 | 0:05 | Objectives |
| 0:05 | 0:15 | Overview |
| 0:20 | 0:45 | In Class Activity I |
| 1:05 | 0:10 | BREAK |
| 1:15 | 0:45 | In Class Activity II |
| TOTAL | 2:00 | |

