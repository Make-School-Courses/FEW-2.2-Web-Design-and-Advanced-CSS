# FEW 2.2 - Advanced CSS - Layout

CSS Grid is amazing. It needs no abstraction! Flexbox is also amazing and needs no abstractions. This lesson will take a look at both of these and how they can be used in your CSS framework.

## Why you should know this?

To create the layouts that you envision you'll need to use both of these tools. 

## Learning Objectives

1. Create one-dimensional layouts with flexbox
1. Arrange elements on an axis
1. Create a navbar
1. Create a footer

## Slides

https://docs.google.com/presentation/d/1rJcp_j90I4v8zP_xTMlOpb-MEAsnEF4Gb7YrpsFH3u4/edit?usp=sharing

## Framework Project 

Check your CSS framework against the checklist here: 

[project-css-framework.md](../Assignments/project-css-framework.md)

## Nav Bars

What makes a good nav bar? 

Look at some navbars. 

- Bootstrap - https://getbootstrap.com/docs/4.0/components/navbar/
- Foundation - https://foundation.zurb.com/sites/docs/v/5.5.3/components/topbar.html

## Markup

The first step is to define some markup that will represent a navbar. The navbar will share markup with other elements to separate it and identify it as unique use a class name. 

```HTML
<div class="navbar">
  ...
</div>
```

Links items on the bar should probably be grouped. A list makes a lot of sense. 

```HTML
<div class="navbar">
  <ul>
    <li></li>
    <li></li>
    <li></li>
  </ul>
</div>
```

The bar is used for navigation so each list item should contain an anchor.

```HTML
<div class="navbar">
    <ul>
        <li><a href="#">Link 1</a></li>
        <li><a href="#">Link 2</a></li>
        <li><a href="#">Link 3</a></li>
        <li><a href="#">Link 4</a></li>
    </ul>
</div>
```

### Title 

Almost always you'll have a title in the navbar. You need to single this out as unique to give it a style that works with the navbar. 

Use a class name. 

```HTML
<div class="navbar">
    <ul>
        <li><h1 class="title">TITLE</h1></li>
        <li><a href="#">Link 1</a></li>
        <li><a href="#">Link 2</a></li>
        <li><a href="#">Link 3</a></li>
        <li><a href="#">Link 4</a></li>
    </ul>
</div>
```

## Styles 

The navbar will need some styles to make it look like a navbar. The colors will be different from what is on the main part of the page but should use colors from your palette of colors. 

Document your code showing the expected structure of the navbar. You can use the child and descendant selectors to your advantage. 

```CSS
.navbar { /* styles for navbar */ }
.navbar > ul { /* style lists in a navbar */ }
.navbar a { /* style anchor in a navbar */ }
```

The navbar links should have interactions. The styles applied to these will interact with styles applied to your general link style. You may need to override some of the styles you defined earlier. 

```CSS
.navbar a:link { /* navbar link */ }
.navbar a:visited { /* navbar vidsited */ }
.navbar a:hover { /* navbar hover */ }
.navbar a:active { /* navbar active */ }
```

You may not have to style some of these. 

### Removing base styles 

The ul and li come with a lot of base styles. Your reset styles may remove some or all of these, you'll need to take care of anything that wasn't covered by reset. 

The ul has the following default styles: 

- padding 
- margin
- list-style

```CSS
.navbar > ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
}
```

## Flexbox 

Use flexbox to arrange things in the navbar. At the top level, you'll want to arrange groups of links on the left and right. 

```CSS
.navbar {
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    align-items: baseline;
}
```

Use `space-between` and `row`. This should place the first list on the left. If there is a second list it should appear on the right. 

Within a ul, you'll also want to arrange elements in a row. 

```CSS
.navbar > ul {
  /* Remove the default styles */
    margin: 0;
    padding: 0;
    list-style-type: none;
  /* Arrange all of the links in a row */
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: baseline;
}
```

https://cssreference.io/flexbox/

## The State of your CSS Framework 

This is class 7 You should have been working on your CSS framework for ~2 weeks by now. Consider this a big project. You should be investing time and energy into this. It is your final project. 

So far you should have styles in your framework that cover: 

- Type - Set the basic font styles for common elements: 
  - p, h1-6, strong, em, blockquote, etc. 
- Colors - You should have defined some custom properties for colors that will be used by your framework. This should include colors for: 
  - foreground, background
  - primary, info, danger, and success operations
- You should also have styled form elements and controls. These styles should cover:
  - Text input, buttons, radio buttons, and checkboxes. 

This week you should be adding styles for: 

- Navbar
- Footer

## Documentation for your framework

You must document your framework. This inlcudes code samples showing the framework in use. Show a sample for each of the styles the framework generates. 

You can follow the example I have created here: https://github.com/soggybag/frmwrk-cs

## Activity 

Follow the guide above to get your navbar started. Build from there and style the navbar to make it fit the design and theme of your framework. 

We will remove all of these at the break to get comments from your peers. After the break, we will work to improve the navbars and review a second time. 


## Homework: Framework - Nav Bar and Footer

Add a Navbar to your framework. See the description linked below for more details on this assignment: 

- [Framework: Nav Bar and Footer](../Assignments/assignment-07-flexbox.md)

## Wrap Up

- Continue working on your framework. 
- Update the documentation for your framework.

## Additional Resources

1. https://cssreference.io/flexbox/

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
