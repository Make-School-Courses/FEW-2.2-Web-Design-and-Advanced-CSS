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

### Extend HTMLElement and define a new tag

Extend HTMLElement and call super in the constructor. 

```JS 
// Create a class that backs the new element
class MyElement extends HTMLElement {
  constructor() {
    super()
    ...
  }
  ...
}

// Define the new element
customElements.define('my-element', MyElement)
```

### Property names 

Since you are extending HTMLElement you'll need to be careful about overriding properties that exist in HTMLElement. 

Best practice: Use and underscore in front of all of the property names you define. 

```JS 
this._name = 'widget' // good
this.name = 'wonky' // bad
```

### Shadow Root 

Create a shadow root in your constructor. Probably a good idea to store this in a property. 

This attaches a shadow root and stores it in a property: `_shadowRoot`

```JS 
...
  constructor() {
    super()
    this._shadowRoot = this.attachShadow({ mode: 'open' })
    ...
  }
  ...
```

### Templates 

If the markup is complex make a template. You can add styles also. 

You may not need this if the markup in your component is simple. 

Think of a template as some markup you can use in your shadowroot. This can also contain styles in a style tag. 

Best practice: define a template in a variable outside of your class inside the IFFE. 

```JS 
(function() {
   const template = document.createElement('template')
  template.innerHTML = `
    <style>
      /* some styles */
    </style>
    <div class="container">
      <!-- some markup -->
    </div>
  `
  class MyComponent extends HTMLElement {
    ...
```

### Lifecycle methods 

Use these to setup and take down your components. 

Use the contructor to initialize class properties and create the shadow root. 

Use `connectedCallback()` to handle things that should happen when the component is added to the DOM. For example adding a timer. 

Use `disconnectedCallback()` to clean up when a component is removed from the DOM. For example remving a timer. 

```JS 
...
class MyComponent extends HTMLElement {
...
    connectedCallback() {
      // Create a timer and save a reference 
      this._timer = setInterval(() => {
        this._nextImg()
      }, 3000)
    }

    disconnectedCallback() {
      // Clear your timer
      clearInterval(this._timer)
    }
    ...
```

In some cases you may not be able to get at the content of a node in your custom tag. There are a couple things you can try. 

Make sure to include your JS files at the bottom of the body tag. This gaurantees the custom tags are loaded before the code runs. 

You can also use `customElements.whenDefined()`. This method returns a promise. 

```JS 
class MyComponent extends HTMLElement {
...
    connectedCallback() {
      ...
      customElements.whenDefined('simple-slides').then(() => {
        // do stuff after elements are defined
      })
    }
    ...
```

### Attributes 

If you are using attributes to confgure your component. You'll need to list the attribute names that are being observed and listen for changes. 

Listening for changes and look at the name of the property that changed with `attributeChangedCallback(name, oldValue, newValue)`. 

```js
class MyComponent extends HTMLElement {
  ...
  static get observableAttibutes() {
    return ['title', 'time']
  }
  ...
  attributeChangedCallback(name, oldValue, newValue) {
    console.log(name, oldValue, newValue)
    if (name === 'title') {
      this._title = newValue
    } 
    this.render()
  }
  ...
```

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

**Challenge 3** - Rainbow text 

The goal is to make a component that colors all of it's in a rainbow of colors. Imagine each word is a different color. 

Follow these steps:

- Make a new custom element `rainbow-text`
- Make a shadowroot
- Get the text from the host element
- Split the text on the space to get an array of words
- Transform the array of words into an array of `<span>` tags
- Append these spans to the shadow root
- Assign each span a color style

**Challenge 4** - Simple Slide Show 

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
