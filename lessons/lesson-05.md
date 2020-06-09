# FEW 2.2 - Advanced CSS - CSS Custom Properties 

CSS Custom properties are a feature that allows you to define your own custom properties and use their values in your CSS.

## Why you should know this?

CSS Custom Properties are a new game changing feature. Expect this to be the future of CSS. This expands what you can do with the CSS language immensely. Learning this today will make you feel like an expert when the rest of the world catches on to this feature. 

Besides making your CSS code skills up to date it will empower your projects with cutting edge CSS tech, save you time and make your CSS more flexible and powerful. 

## Learning Objectives

1. Explain CSS Custom Properties their features and use cases 
2. Use CSS Custom properties in real world applications
3. Use Math operations in CSS
4. Use Reset CSS to remove browser inconsistencies

## Custom CSS Framework

You are going to create your own framework. 

Q: What is a framework? 

A: It's a collection of code that works together as a system. 

You have probably used other frameworks before. BootStrap is very popular, there is also Foundation. These frameworks include systems that allow developers to easily create common UI elements. 

let's take a look at some frameworks. 

---

- Explore Frameworks 
  - What is a Framework
  - What is inside the framework? 
  - How do you think it was made? 
    - Take apart Bootstrap and Foundation
- You are going to make a Framework
  - What does your framework need to contain/What does it need to do?

What do other frameworks have? 
- Layout - We will use CSS Grid instead
- Content 
  - Typography
    - Headings - https://getbootstrap.com/docs/4.3/content/typography/#headings
    - Copy 
      - Inline elements - https://getbootstrap.com/docs/4.3/content/typography/#inline-text-elements
        - em, strong, strike, abbr, code, quotes
      - Blocks
        - blockquote
        - pre > code

- Acivities 
  - Sample Code set the fonts 
  - Split code
    - theme.css - contains variable values 
    - style.css - contains styles rules 
---





## CSS Custom Properties

CSS Custom Properties let you define variables in CSS. Really you're defining a new CSS property, hence the name. In use it feels like variables that you are familiar with from other languages. 

### Defining a custom property

Properties names must begin with `--`, rest of the name can be anything that would normally work in CSS (think: kabob-case). 

Assigning a value is like setting the value of a property in CSS. 

```CSS
:root {
  --color: red;
  --primary-color: rgba(123, 37, 44, 0.7);
  --size: 121px;
  --base-font-size: 16px;
  --large-font-size: 1.85em;
  --number-of-columns: 4;
  --golden-ratio: 1.618;
}
```

Any value that would work in CSS can be assigned to a property. 

You can define custom properties anywhere. Where they are defined determines their scope. Scope follows the same rules as inheritence. 

```CSS
:root { /* Define custom properties on :root */
  --golden-ratio: 1.618;
  --base-font-size: 16px;
  --large-font-size: 1.85em;
  ...
}

.main { /* define some custom properties on .main */
  --number-of-columns: 4;
  ...
}

button { /* define some custom properties on each button */
  --color: red;
  --primary-color: rgba(123, 37, 44, 0.7);
  --size: 121px;
  ...
}
```

## What's `:root`?

`:root` is a pseudo element that matches the root element of the document tree. This is identical to the  `<html>` element. `:root` has a higher [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/:root).

By declaring custom properties on `:root` they become global and available everywhere. 

Otherwise declaring a custom property on an element makes it available to that element and inherited by the element's descendents, but unavailable to it's anscestors. 

### Accessing custom property values

To access the value of a custom property use the `val()` function.

```CSS
.some-class {
  width: var(--size);
  color: var(--color);
  background-color: var(--bg-color);
}
```

For example, you might define some values in `:root` then use those values throughout the rest of your stylesheet. 

```CSS
:root {
  --golden-ratio: 1.618;
  --base-font-size: 16px;
  --large-font-size: 1.85em;
  ...
}

.main {
  --number-of-columns: 4;
  ...
  grid-template-columns: repeat(var(--number-of-columns), 1fr);
}

.alert {
  --color: red;
  --size: 121px;
  ...
  color: var(--color);
  width: var(--size);
  ...
}
```

### Math with CSS calc()

CSS supports some basic math through the `calc()` method. You can use `+`, `-`, `*`, and `/`. 

```CSS
.heading {
  font-size: calc(16px * 1.85);
}

.input[type=text] {
  padding: calc(1em * 1.5);
}

.alert {
  margin: calc(1em + 5px);
}
```

The beauty of `calc()` is the ability to mix units! It may not seem like much but ask yourself what you would need to do to make this calculation: 

```CSS
calc(1em * 1.5 + 2%)
```

Custom properties work with `calc()`. 

```CSS
.heading {
  --size: 16px;
  font-size: calc(var(--size) * 1.85);
}

.input[type=text] {
  --scale: 1.5;
  padding: calc(1em * var(--scale));
}
```

Pro tip! If you have a value that is just a number without a unit you can convert it to a number using `calc()` like this:

```CSS
.box {
  --size: 100;
  height: calc(var(--size) * 1px);
}
```

The code sample above changes the value of `--size` from a unitless value of `100` into `100px`.

## Custom properties are Inherited 

```CSS
body {
  --primary-color: #222; /* Defined on an ancestor */
}

.some-element { /* is descendent of body */
  color: var(--primary-color); /* Inherited property */
}
```

## Overriding a custom property

```CSS
body {
  --primary-color: #222; /* Defined on an ancestor */
}

h1 {
  --primary-color: #666; /* Overrides --primary-color for this element! */
  color: var(--primary-color); /* #666 */
}

h3 {
  color: var(--primary-color); /* #222 */
}
```

## Inline Custom properties

Custom properties can be set inline also.

```CSS
body {
  --primary-color: #222; /* Defined on an ancestor */
}

h1 {
  color: var(--primary-color);
}
```

```HTML
<!-- The color is #foo for this element -->
<h1 style="--primary-color: #f00;">CSS Custom Properties FTW!</h1>
```

## Fallback values 

Use a fall back value when a property may not exist. 

```CSS
.box {
  background-color: var(--bg-color, '#2478fe');
}
```

You can use a custom property as a fallback value! 

Imagine `--background-color` is sometimes defined inline. When it is you want to use it. When it is not you want to use `--primary-color` defined in `:root`. 

```CSS
:root {
  --primary-color: #2478fe;
}
...
.box {
  background-color: var(--background-color, var(--primary-color));
}
```

```html
<div class="box"></div><!-- '#2478fe' -->
<div class="box" style="--background-color: #ff8534"></div><!-- '#ff8534' -->
```

In the above example the fallback value allows you to have a value that may not exist first div.box and use a value when it does exist second div.box. 


## Setting Custom properties with JS

With JS you you can set any CSS property on an element. 

```JavaScript
const box = document.getElementById('box')
box.style.width = '100px'
```

All CSS properties work here. Names are comverted to camelcase. 

```JavaScript
box.style.borderWidth = '1em' // border-wdth
box.style.borderColor = 'red' // border-color
```

An alternate method is to use: `element.setProperty()`

```JavaScript
const box = document.getElementById('box')
box.setProperty('width', '100px')
box.setProperty('border-width', '1em')
box.setProeprty('border-color', 'red')
...
```

Custom properties don't exist in the standard JS world and even if they did you couldn't use the `--` in the name. So `element.style.--size` is not going to work. Use `element.setProperty()` for setting custom properties. 

```JavaScript
const box = document.getElementById('box')
box.setProperty('--primary-color', '#ff8844')
box.setProperty('--size', '230px')
box.setProeprty('--font-family', 'Helvetica')
```

You can also get the value of a custom property, or any property via JS. 

```JavaScript
const box = document.getElementById('box')
const size = box.getProperty('--size') // get a custom property
const color = box.getProperty('color') // get a standard property
```

## Example exercises

Open [example 1](lesson-05-example-1.html)

pair up and take a look at the source code. 

1. Change the variables at the top and look at the changes in the in the page.
  - Change the `--color-background` and `--color-foreground`
  - Change `--color-foreground`
  - Change `--vertical-space`
2. Set the values at the top of the page to values that you feel look good. 
  - Adjust the colors
  - Adjust the font stack. Use one of the font stacks from the previous class.
  - Also invent a font stack for `--font-code`

This is working well, but it could be better. There are a few places where the colors are not quite right. Use an inline style to make changes: 

1. Change the second info box has a warning. This should use `--color-danger` or `--color-callout`. 
2. The color of "Important!" is not right. This should use the `--color-light` or another color. 

## Reset CSS

The reason HTML that you write looks the way it does is because browser applies default CSS styles to elements. 

These styles are not always consistent across browsers. While the [W3C](https://www.w3.org) defines the standards for the web it's browser makers that implement those standards. There are a lot moving pieces and things are not always consistent across browsers and platforms. 

This can be a problem for you as a web devopler. You want your products to look consistent across browsers where quirks and inconsistencies create small but sometimes important differences. 

A good strategy to eliminate some problems is eliminate some or all of the default styles applied by the browser.

Take a look at the default styles used by browsers: 

https://bitsofco.de/a-look-at-css-resets-in-2018/

Read the article above and discuss it with your pair. 

Q: Why use a reset style sheet?
Q: How would you apply this to your work? 
Q: What are the differences between these different resets?

Choose one of the stylesheets and apply it to the example code. 

## Apply CSS Custom properties to your work

Take your CSS logo and move all of the values into CSS custom properties. Anything that is a value can be a property. Move these to a location in your code where it makes them easier to access. 

Is this an improvement? 

Take it a step further. Look at the cade and find values that are calculated from other values. Use `calc()` and custom properties to figure these values. 

Discussion: 

Q: What happened here? 
Q: Was it useful? 
Q: Does this make better CSS code?

## Homework: Start your Framework - Fonts 

The goal of this assignment is to start your CSS Framework. This assignment will continue through the next few classes. You'll be adding features with each new assignment until it is complete.  

[Start your Framework: Fonts ](../Assignments/assignment-05-framework-fonts.md) 
Clarify what you are doing by looking at what other people are doing who are doing the same thing. Check out this awesome list of CSS Frameworks. 

- https://github.com/troxler/awesome-css-frameworks

## Additional Resources

1. assignment-05-framework-fonts.md
2. https://www.sitepoint.com/css-theming-custom-properties-javascript/
3. https://codeburst.io/css-variables-explained-with-5-examples-84adaffaa5bd
4. https://css-tricks.com/css-custom-properties-theming/
5. https://github.com/troxler/awesome-css-frameworks

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
