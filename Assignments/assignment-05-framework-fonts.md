# FEW 2.2 - Assignment 4 - Start your Framework: Fonts 

## Description 

This is the first step in the larger goal of creating CSS framework. 

The goal of this first step is explore CSS frameworks and start deciding what you'd like to include in your framework. 

### Why this assignment?

The web is dominated by text content. To get noticed and make sites that people enjoy reading your type should look good. If you're making web sites having some consistent styles that you can easily apply without having to write all of the styles from scratch will speed up your work flow. 

## Getting Started 

Start by exploring CSS frameworks. The framework we will be making will make use of all of the things we have covered in class. 

- SASS - It can be written in the scss language. Remember it will need to be compiled into CSS form! 
- CSS Custom properties - Use variables to make your framework easily cusomizable
- CSS Grid - Where Frameworks like Bootstrap dedicate a lot of code to layout with a grid we will be using CSS grid and **won't** be including CSS that defines grid. This will have the advantage of making your framework smaller and easier to manage. 

Explore some existing frameworks.

- https://getbootstrap.com 
  - https://getbootstrap.com/docs/4.3/components/alerts/
  - https://getbootstrap.com/docs/4.3/examples/
- https://bulma.io
  - https://bulma.io/documentation/
- https://tailwindcss.com
  - https://tailwindcss.com/components
- https://semantic-ui.com
  - https://semantic-ui.com/elements/button.html
- https://foundation.zurb.com
  - https://foundation.zurb.com/develop/building-blocks

Look through the code in the frameworks above. Look particularly 

- What the components and features of the framework look like?
- How they implement the features 
  - These frameworks use class names combined with an html structure to create many of the standard UI elements you might find on any website. Exmine these closely you will be implementing your own set of UI elements. 

## Project requirements

You need to create a repo for your framework. Think of a name for your framework. This is a software product it needs a name! Here are a few I thought of: 

- Frmwrk
- Framwërk
- Chonky CSS
- Ninja CSS
- CSSS - Chonky Styles Solidly Served
- CSSSS - CSS Served with Solid Sagacious Style 
- CSSSSS - Colorful Simple Seamless Safely Served Styles 

The goal for this assignment is to start your framework by defining styles that define good looking typography. 

You need to define typographic styles for your framework. Think about making a legible, easy read, and good type. You should style all of the default text. Style the color and the background color. Make sure the contrast meets the [guide lines](https://webaim.org/resources/contrastchecker/). 

### What should you style? 

Concentrate on applying styles to basic elements. Link your stylesheet the [sample HTML doc from class 4](../lessons/lesson-04.html).

Your styles should cover the elements listed below. Remember, styles are inherited, by setting the `font-family` and `font-size` on the body all of the other elements will inherit these values. Use this to your advantage whenever possible. 

- body - all of your base styles here
  - font-family
  - line-height
  - font-size
  - color
- h1-6 - most important here is the sizes, use em to make these elements relative to the base size you set on the body
  - color
  - font-size
- strong and em 
  - color
  - font-weight
- blockquote and q
  - font-size
  - font-family
  - margin
  - padding
  - color
- a - Be sure to style the :link, :visited, :hover, and :active styles (in this order!)
  - color
  - text-decoration

You must set a base font style on body. All other elements will inherit from this. You can use a px size here. 

Style all of the other elements using a relative size in em. 

What's important here is choosing a good font stack and setting reasonable values for font size and line height. 

### Use Reset 

Choose one of the reset styles from [lesson 5](../lessons/lesson-05.md). 

Either include this in your stylesheet or include it as a CSS file that will be linked to when using your framework. 

Be sure to attribute/credit the creator of the reset. It should clear where this came from. 

### Use Custom Properties 

Move as many values as practical into CSS custom properties in an easily accessible location of your stylesheet. 

Use CSS Custom Properties. Set all of the things that should adjustable in a custom property and move it to the top. 

Consider using a separate stylesheet for all of the custom properties. By putting these into a separate file you can can create multiple files that define different themes. For example linking to 'chonky-dark.css' and 'chonky.css' would give you the dark theme. 

### Deliverable

Link to your repo.  

### Due date

Class 6

## Assessing the assignment

[Assignment Name Rubric](assignment-05-framework-rubric.md)


