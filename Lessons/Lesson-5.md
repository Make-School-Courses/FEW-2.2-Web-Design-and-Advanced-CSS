# FEW 2.2 - Advanced CSS - CSS Custom Properties 

CSS Custom properties are a feature that allows you to define your own custom properties and use their values in your CSS. 

## Why you should know this?

CSS Custom Properties are a new game changing feature. Expect this to be the future of CSS. This expands what you can do with the CSS language immensely. Learning this today will make you feel like an expert when the rest of the world catches on to this feature. 

Besides making your CSS code skills up to day it will empower your projects with cutting edge CSS tech, save you to time and make your CSS more flexible and powerful. 

## Learning Objectives

1. Explain CSS Custom Propertis their features and use cases 
2. Use CSS Custom properties in real world applications
3. Use Math operations in CSS

## Logos 

Look at the logo exercise from the previous class

## CSS Custom Properties

CSS Custom Properties let you define variables in CSS. Really you're defining a new CSS property, hence the name. In use it feels like variables that you are familiar with from other languages. 

### Defining a custom property

Properties names must begin with `--`, rest of the name can be anything that would normally work in CSS. 

Assign a value like setting the value of a property in CSS. 

```CSS
--color: red;
--primary-color: rgba(123, 37, 44, 0.7);
--size: 121px;
--base-font-size: 16px;
--large-font-size: 1.85em;
--number-of-columns: 4;
--golden-ratio: 1.618;
```

Any value that would work in CSS can be assigned to a property. 

You can assign values with and without a unit. When you use a value you need to include a unit! (see calc() below)

You can define custom properties anywhere. Custom properties have scope, more on this later. 

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
}

.alert {
  --color: red;
  --primary-color: rgba(123, 37, 44, 0.7);
  --size: 121px;
  ...
}

```

### Accessing custom property values

To access the value of a custom property use the `val()` method.

```CSS
var(--size)
var(--base-font-size)
var(--color)
va(--background-color)
```

Here in context

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

`calc(1em * 1.5 + 2%)`

Custom properties work with `calc()`. 

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

## Apply CSS Custom properties to your work

Take your CSS logo and move all of the values into CSS custom properties. Anything that is a value can be a property. Move these to a location in your code where it makes them easier to access. 

Is this an improvement? 

Take it a step further. Look at the cade and find values that are calculated from other values. Use `calc()` and custom properties to figure these values. 

Discussion: 

Q: What happened here? 
Q: Was it useful? 
Q: Does this make better CSS code?

## Homework 

The goal of the homework assignment is to update a past project with CSS Custom properties. 

[Assignment 3](https://github.com/Make-School-Courses/FEW-2.2-Web-Design-And-Advanced-CSS/blob/master/Assignments/assignment-2-update-past-project.md) 

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
