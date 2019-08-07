# FEW 2.2 - Advanced CSS - Web Components part 2

Getting started building your own components. 

## Why you should know this?

Web Components are new and possibly game changing web technology. They sit in the center of frontend development. If you want to be a frontend developer experience with Web Components will be useful. 

## Learning Objectives 

1. Build simple web components
1. Define custom tags that encapsulate functionality
1. Use attributes to configure components
1. Reflect properties and attributes 
1. Use Web Component Lifecycle methods

## Web Components

Web Components are allow you to define new tags with encapsulated functionality. The goal of this class is to begin exploring web components by creating your own.

A good start to getting a handle on what Web Components are and how they work is to make a few simple components for yourself!

## Best practices 

be sure to wrap your component code in a IIFE. This will keep it separate from other code that migth be running in the browser: 

```JS 
(function() {

  class MyComponent extends HTMLElement {
    ...
  }

  customElements.define('my-component', MyComponent)

})()
```

Component names must contain a hypen: 

- `my-component` good
- `frmwork-blink` good
- `mycomponent` bad
- `blink` bad

When using custom tags you must use a closing tag, even if the tag is empty. 

- `<my-component></my-component>` good
- `<frmwrk-blink></frmwrk-blink>` good
- `<my-component />` bad
- `<frmwrk-blink>` worse



## Concepts 

There are few concepts that are important to Web Components. The challenge problems here build components from the ideas presented in class 9. 

- Shadow Root 
- Attributes, Properties, and refelction
- Component Lifecycle methods 
- Templates 
- Defining Custom Elements 

## Activity 

Pair up with someone and try solving the problems below. Be prepared to present your solution to the class. 

**Challenge 1** - Copyright component.

This component should display a copyright message along with the current year. When a `year` attribute is present it should display the year set in the value. 

For example: 

`<copyright></copyright>`

Should display: &copy; 2019

`<copyright year="1965"></copyright>`

Should display: &copy; 1965 

Stretch goal: Handle a second attribute: `title`. When this attribute is present the component shows the value to the left of the copyright. For example: 

`<copyright title="Frango Mints" year="1965"></copyright>`

Displays: Frango Mints &copy; 2019

**Challenge 2** - Blink Component

The bink tag has been sorely missed for many years it's time for it's return! 

Make a new component that flashes a text message. The text should appear and disappear about once per second. 

Hint: Use CSS styles to make the text blink. By alternating color of the text between `#000` and `transparent` the text will appear and disappear. Using transparent is better than removing the text since removing the text would change the size of the element. 

Use the lifecycle methods. Use `connectedCallback()` to create an interval with `setInterval()` and `disconnectedCallback()` to remove the interval with `clearInterval()`. In this way your component can clean up resources it is using when it is removed. 

Stretch Challenge: Use an attaribute to set the speed of the blinking. When this attribute is not present the default blink rate should be a resonable value. 

Stretch Challenge: Make the text that appears inside your blink tag blink. For example: 

`<my-blink>This text blinks</my-blink>`

To do this you'll need to get the content text of the element and add it to the shadow root. 

**Challenge 3** - Simple Slide Show 

Make a simple slide show. Your slide show should cycle through a series of img tags that provided in the custom tag. For example: 

```HTML
<simple-slides>
  <img src="image-0.jpeg">
  <img src="image-1.jpeg">
  <img src="image-2.jpeg">
<simple-slides>
```

The slide show would display one img at a time in the shadow root and change images every 3 secs. 

Stetch Challenge: Add an attribute that sets the time between slides. 

Stretch Challenge: Display the number of the slide in the component. 

Stretch Challenge: Make a cross fade between images. To do this you'll need two img tags. Make one fade out while the other fades in. Alternate these with each image change. 

## Wrap Up

- 

## Additional Resources

1. 

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
