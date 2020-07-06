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

Web Components allow you to define new tags with encapsulated functionality. The goal of this class is to begin exploring web components by creating your own.

A good start to getting a handle on what Web Components are and how they work is to make a few simple components for yourself!

### Isolating your Code

Since all elements in JS are global it's possible that code from other files might interfere with the code you have written. This problem can be prevented by wrapping your code in an anonymous function. 

```JS
function myCode() {
	// Your code here
	const x = 99
	// Variables defined here are scoped to this function
	function otherFunction() {
		// Other functions can be defined in other other functions
	}
	// ...
}

myCode() // Must call this function!
```

For the code to run you'll have to call that function. You could also call the function more than once, which might cause problems. Solve these issues with a Immediately Invoked Function Expression. 

```JS 
// Start with two sets of parenthesis
()() 

// Put a function in the first 
(function() { 
	// ... Code here ... 
})()
```

### Templates

One of the problems with Web Components is creating elements and styling those elements. The process is rather verbose compared to creating elements in an .html file and writing CSS in a .css file. 

Web Components provides a solution: templates. 

You may not need this if the markup in your component is simple. 

Think of a template as some markup you can use in your shadowroot. This can also contain styles in a style tag. 

A template is an HTML element that is not displayed. The template is used as block of code you can duplicate when needed. 

Best practice: define a template in a variable outside of your class inside the IFFE.

```JS 
(function() {
	// Create a template
	const template = document.createElement('template')
	// Set the content of the template
  template.innerHTML = `
    <style>
      /* some styles ... */
    </style>
    <div class="container">
      <!-- some markup ... -->
    </div>
	`
	
  class MyComponent extends HTMLElement {
		constructor() {
			super() 
			// Clone the template node and copy it's content into the shadowroot
			this._shadowRoot.appendChild(template.content.cloneNode(true))
		}
	}

})()
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
