# FEW 2.2 - Advanced CSS - Custom Controls

Add custom controls with pseudo elements. 

## Why you should know this?

The default check box and radio button offer very few options for customization. Using pseudo elements opens up a lot of options. 

## Learning Objectives

1. Describe the relationship between an input and it's label
1. Define a label and input that are asscoiated 
1. Use pseudo classes ::before and ::after
1. Create custom check boxes and radio buttons
1. Use ridiculously complicated CSS selectors

## Slides

https://docs.google.com/presentation/d/1bVVX2ELbGEPktG6Cv_DiA2I4uxYyEGALr7WUAga0RLw/edit?usp=sharing

## Pseudo Elements

`::before` and `::after` are pseudo classes. These create new elements via CSS that don't exist in the DOM. 

Imagine you have: 

`<div> * </div>`

With this style:

```CSS
div::before {
  content: "Hello";
}

div::after {
  content: "World";
}
```

Your div would appear as: 

`Hello * World`

The before element goes before the existing content and the after element goes after. 

You can think of DOM like this: 

```HTML
<div>
  <span>Hello</span>
  *
  <span>World</span>
</div>
```

Though the inspector will show: 

```HTML
<div>
  ::before
  *
  ::after
</div>
```

## What can you do with pseudo elements?

Using ::before and ::after you can add elements to the DOM that don't actually exist in your mark up, and you can style these new elements. 

### Fancy Blockquote

Making fancy blockquote styles is a possible application. Imagine you want to add a fancy quotation mark before and after the text in a block quote. 

```HTML
<style>
  blockquote::before {
    content: open-quote;
    font-size: 3em;
    color: tomato;
  }
  blockquote::after {
    content: close-quote;
    font-size: 3em;
    color: tomato;
  }
  blockquote {
    /* Set the quote style */
    quotes: "\201C""\201D""\2018""\2019";
  }
</style>

<blockquote>
  The way to get started is to quit talking and begin doing. 
</blockquote>
-Walt Disney
```

![block quote](images/fancy-quotes.png)

Here the ::defore and ::after elements have content that is an open and closing quote. They also have styles that set the font-size and color of their elements. 

https://css-tricks.com/almanac/properties/q/quotes/

### Fancy Undline

The goal here is to make a line that draws itself under a word. To do this we need another new element to appear. This would be a difficult addition to existing markup and as a visual effect should not really part of that markup, remember the separation of concerns. 

The solution is to generate the extra element with ::after. 

```HTML
<style>
  .add-box {
    display: inline-block;
    color: tomato;
  }
  .add-box::after {
    content: "";
    display: block;
    width: 0;
    height: 3px;
    background-color: tomato;
    transition: 400ms;
  }
  .add-box:hover::after {
    width: 100%;
  }
</style>

<blockquote>
  If you set your goals <span class="add-box">ridiculously</span> high and it's a failure, you will fail above everyone else's <span class="add-box">success</span>. 
  -James Cameron
</blockquote>
```

![fancy hover](images/hover-effecft.gif)

Here the class .add-box adds a new pseudo element with ::after. That element is styled with display: block, width, height, and a background color. It also has a transition, so changes to these properties will be animated. 

Notice the last rule: .add-box:hover::after. This selector applies to the ::after element when it's parent is in the :hover state. Changing the width here starts the animation. 

## Research Pseudo elements

Read this article. It talks about the uses for ::before and ::after. 

https://css-tricks.com/pseudo-element-roundup/

## Custom Check boxes and radio buttons

The checkbox and radio button are limited in what the browser allows you to style. With Pseudo elements we open up the possiblity to customize these elements. 

### How are checkboxes and radio buttons marked up?

Usually you will want to markup up checkboxes and radio buttons like this: 

```HTML
<label>
  <input type="checkbox">
  Pickles?
</label>

<label>
  <input type="radio" name="choice" checked>
  Converse
</label>

<label>
  <input type="radio" name="choice">
  Vans
</label>
```

The label is an important element here. Besides providing a label that can be read, the label provides an element that can be interacted with. 

**With the label wrapped around the input clicking the label is the same as clicking the input.**

What are the elements needed for a checkbox or radio button? 

![checkbox radio](images/checkbox-radio.png)



## The State of your CSS Framework 

Use this checklist to check the progress of your framework. 

[project-css-framework.md](../Assignments/project-css-framework.md)

## Activity 



## Homework: Framework - Nav Bar and Footer

Add a Navbar to your framework. See the description linked below for more details on this assignment: 

[project-css-framework.md](../Assignments/project-css-framework.md)

## Additional Resources

1. https://cssreference.io/flexbox/

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time** | **Activity** |
| ----------- | --------- | ------------------------- |
| 0:00 | 0:05 | Objectives |
| 0:05 | 0:15 | Overview |
| 0:20 | 0:45 | In Class Activity I |
| 1:05 | 0:10 | BREAK |
| 1:15 | 0:45 | In Class Activity II |
| TOTAL | 2:00 | |

