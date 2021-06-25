# FEW 2.2 - Advanced CSS - Web Components

Web components are the future of the web. In a nutshell, they allow you to create _new_ tags that generate elements with encapsulated behavior.

## Why you should know this?

This is the future of the web. More web sites than you suspect are using web components.

## Learning Objectives

1. Define Web Components advantages and use cases
1. Create a simple web component
1. Use a web component on a web page
1. Defining a new tag
1. Create a shadow root
1. Use reflection

## Make a Custom CheckBox

The basic checkbox doesn't look that great. Seriously. It's a little too small. You can't style it either. Seriously. Try it yourself. 

But you can make your custom checkbox. This takes a little effort but it's easier than you think. 

Try it for yourself. 

https://www.w3schools.com/howto/howto_css_custom_checkbox.asp

## What if you could make your checkbox? 

Try this. 

Save this in a file named: `checky-box.js`

```JS 
(function() {
  class CheckyBox extends HTMLElement {
    constructor() {
      super(); // MUST call super!
      this._shadowRoot = this.attachShadow({ mode: 'open' });
      
      this._container = document.createElement('div')
      this._container.style.display = 'flex'
      this._container.style.alignItems = 'center'
      this._container.style.cursor = 'pointer'
      this._shadowRoot.appendChild(this._container)

      this._box = document.createElement('div')
      this._box.style.width = '20px'
      this._box.style.height = '20px'
      this._box.style.display = 'inline-block'
      this._box.style.backgroundColor = 'red'
      this._container.appendChild(this._box)

      this._check = document.createElement('div')
      this._check.style.width = '10px'
      this._check.style.height = '6px'
      this._check.style.display = 'inline-block'
      this._check.style.borderColor = 'white'
      this._check.style.borderLeftStyle = 'solid'
      this._check.style.borderBottomStyle = 'solid'
      this._check.style.transform = 'translate(4px, 2px) rotate(-45deg)'
      this._box.appendChild(this._check)
      
      this._text = this.innerHTML
      this._label = document.createElement('span')
      this._label.innerHTML = this._text
      this._label.style.marginLeft = '0.5em'
      this._label.style.cursor = 'pointer'
      this._container.appendChild(this._label)

      this._isChecked = true

      this._container.addEventListener('click', (e) => {
        this._isChecked = !this._isChecked
        this._check.style.display = this._isChecked ? 'block' : 'none'
      })
    }

    static get observedAttributes() {
      return [] // List an array of names
    }

    attributeChangedCallback(attributeName, oldValue, newValue) {
      
    }

    connectedCallback() {
      
    }
  }
  
  customElements.define('checky-box', CheckyBox);
  // ---------
})()
```

Next, make an HTML file, name it `index.html`

```HTML
<html>
  <head>
    <title></title>
  </head>
  <body>
    <div>
        <checky-box>Check Me</checky-box>
        <checky-box>Check Me</checky-box>

        <input type="checkbox">
        <input type="color">
    </div>
    <script src="checky-box.js"></script>
  </body>
</html>
```

Make these files. Load that page in your browser. What do you see? 

## Web Components

Web components are one of the newest technologies available to web developers. Web Components are the building blocks of modern web applications.

Web Components give developers the ability to extend HTML and create new tags with custom functionality.

Web Components are based on the existing component model. This results in more modular code that can be shared across teams and projects.

Web Components, also are known as custom elements, are a system that allows you to define new HTML tags that generate elements within the DOM with encapsulated behavior you define. 

Who's using Web Components and where are they used?

https://www.youtube.com/watch?time_continue=12&v=YBwgkr_Sbx0

**Web components are:**

- Encapsulate functionality
 - Just by adding the tag to a document you get all of the functionality that comes with the tag. 
- Extend the browser with new components
 - Invent new tags beyond the default predefined tags
- Low-Level Browser API
 - Web components are built into the browser you don't need a library
- Created with HTML and JS
- Portable
 - A web component can be used in any project regardless of the other technologies being used. A React Component will only work in React projects, a Web Component will work in React projects, Angular Projects, and projects that don't use a library. You can use them anywhere. 
- Standard Interface
 - Can work anywhere you can put an HTML tag

**Web Components are not:**

- Not Web Frameworks
 - They don't come with a predefined system they work within. 
- Not opinionated
 - They don't require you to follow any rules and force you to work in any particular way or with any other required systems. 

**Advantages:**

- Works with any app/stack
- Not locked in
- Future Proof

### Shadow DOM

To understand Web Components you need to first understand some of the features that allow them to work. Web Components are built from HTML, CSS, and JS that you are already familiar with. They also use a feature called the **Shadow DOM** which you may not be familiar with. Let's take a look at the Shadow DOM.

A `<div>` displays only a box and it's content. Which is pretty much the same for most tags. A few tags display more. Some display much more.

Tags like `<input>`, `<select>`, and `<video>` all display more than just a box and have encapsulated behaviors? 

Each of these elements has a behavior backed by code and extra display elements backed by DOM elements that are **not** displayed in the inspector. 

The shadow DOM is a hidden DOM tree that is separate from the "light" DOM. 

![Shadow DOM](shadow-dom.png)

Generally speaking a Shadow DOM is separate and not connected to the "light" DOM. 

Terms: 

- **Shadow host** The regular DOM node that the shadow DOM is attached to.
- **Shadow tree** The DOM tree inside the shadow DOM.
- **Shadow boundary** the place where the shadow DOM ends, and the regular DOM begins.
- **Shadow root**: The root node of the shadow tree.

When you use a tag like audio the browser generates a controller with several buttons and other UI elements. These elements are displayed through the shadow DOM. Think of the shadow DOM as a subtree of regular DOM that is invisible to the "light" DOM. 

Why use the shadow DOM? The shadow DOM allows you as a developer to encapsulate web structures that include DOM elements, Styles, and JS. 

## Sample Code for activities 

Download the files here: 

https://github.com/Make-School-Labs/simple-component

### Activity: Explore the shadows

Don't believe me. You've never seen these "shadow" elements. Take a look at them for yourself. 

Open `example-01.html` in your browser. 

Inspect the slider. It should look like this: 

`<input type="range">`

Turn on "Show User-Agent Shadow DOM" option. 

Chrome: In the inspector go to settings, scroll to Elements and check the box: "Show user agent shadow DOM"

Safari: Click the `< >` button in the inspector. 

Pair up and discuss what you find...

- Examine the Markup
- Look for class and id names
- Look at the styles
- Stretch: Look at this with different browsers

Discuss the shadow DOM

Shadow DOM use case 1: Modify elements that use the shadow DOM for consistency across browsers.

For more information: https://css-tricks.com/sliding-nightmare-understanding-range-input/

### Activity: hello shadow world

While modifying the existing shadow DOM is possible where Web Components shine is when you make your _own_ components. Take a look at the Hello World of the Shadow DOM and Web Components. 

Open `lesson-09.html`. Take a close look at this file and discuss it with your partner. Look at these areas: 

- Open the code in the browser
- Inspect the DOM in the browser
- Look at the source code. There are two files: 
  - lesson-09.html
  - hello-world.js
  - Read the comments 
  - Uncomment the code at the bottom of `example-02.html`
  - Read the code and guess what will happen
  - Refresh the browser and check your assumptions

- Q: What did you see? 
- Q: What can you infer about how this operates? 

#### Let's stop and reflect...

There's a very important concept going on here, it's called reflection. 

- With `example-02.html` open in a browser uncomment the code at the bottom of this file (it's in the script tag at the bottom of the page). 
- Open the inspector and look at the first `<hello-world></hello-world>` tag. 
- Refresh the page after 4 seconds an attribute should appear on the tag. 

What is happening here? Answer: Reflection. 

Reflection is a CS concept that describes how a program or structure can modify its structure to display its internal state, or you could say "reflect" it's an internal state. 

The `HelloWorld` class stores a property `this._name`. This holds the extra message the component can display. 

An end-user can set this property through an attribute and conversely if the attribute changes internally it should be reflected in the HTML structure. 

This reflection doesn't happen automatically. To make it happen in the component a couple of methods were used. 

- line 17: `this._name` define a property
- line 21: `static get observedAttributes()` this static method returns an array of properties that can be accessed from outside.
- line 26: `attributeChangedCallback(name, oldValue, newValue)` This callback handles changes to an attribute. Use this to handle changes to an attribute. I compared the `name` of the property changed, and then set `this._name` to the `newValue`, then called `render()`

The goal is to change the internal property when the attribute is changed and change the external attribute when the internal property is changed. 

### Quick Topic: Getters and Setters

Take a look at `getters-setters.js`. 

Getters and setters are methods that look like properties. The class below creates a simple counter. 

Internally it stores a property: _count. 
Externally you can get or set the property: count

The class also creates an HTML element, `el`, which it attaches to the DOM. This class displays the value
of count in this element. 

Then the count property is set we want el to update and display the new value. Normally you'd have to by calling a method since setting a 
the property doesn't run a code block. 

Use a setter you can run a code block when setting
a property. 

In the sample code when `count` changes the new value needs to be displayed. 

Without a getter and setter you might do this: 

```JS
const counter = new Counter()
counter.count = 0 // Sets the property nocode is run internally
counter.render() // So we need to call the render method
console.log(counter.count) // Here we print the value like always. 
// It's not possible to run code here.
```

An alternate idea, still without a getter or setter: 

```JS 
const counter = new Counter()
counter.setCount(0) // Sets the count to 0 by calling a method
// Internally this method calls this.render()
console.log(counter.count) // get the value of count like usual
// It is not possible to run code here. 
```

Let's do all of that with getters and setters

```JS 
const counter = new Counter()
counter.count = 0 // Sets the count and runs the code in the setter function calling this.render()
// Looks like a property from outside
// Acts like a method internally
console.log(counter.count) // Displays the count
// Internally this acts as a method call and 
// you could have run a code block. 
```

**Getters**: are methods preceded with the keyword `get`. These methods must return the value they are responsible for. 

Getters can not take parameters! 

**Setters**: are methods that are preceded by the keyword `set`. These methods can take one parameter. Which should be the new value to be assigned to the property they are responsible for. 

**Note!** You can't use the same name for the getter/setter and the property where the value is stored. 

For example, never do this: 

```JS 
get count() {
 return this.count
}

set count(val) {
 this.count = val
}
```

This creates a recursive situation since setting the property `count` also calls the `set count(val)` method. 

**Challenge**: Add a new getter and setter for a property that defines an increment for the count. 

### Quick Topic: Static Properties and Methods

A static method or property is a property or method that belongs to the class and is not owned by an instance of that class. 

Use static methods when a method is shared by all instances and that method DOESN'T any values owned by that instance. 

Static properties are properties that belong to the class NOT to an instance of the class. 

At this time only Chrome allows the static keyword for properties.

Static methods and properties are accessed from the class! NOT with `this`. For example: 

```js 
class Dog {
 ...
}

const sparky = new Dog()
sparky.bark() // Call on an instance to bark
Dog.numOfLegs // 4 since all dogs have 4 legs
```

Take a look at the sample code: `static-methods-properties.js`.

- Read the code and discuss it with your partner. 
- Assume what the code will output. 
- Run the code and test your assumptions. 

Challenge: 

- Tesla is updating its factory every car must have a serial number that includes the year and the color along with the unique id number in use at the moment. For example: `2019red1`, `2019red2`, `2019red3`, `2019red4` etc. 
- Tesla also needs to track the serial numbers of all cars sold. Store the serial numbers in an array. This should be a static property since there is a single list. 

### Activity: Copyright Component

Take a look at `example-03.html`. This example creates a simple Web Component that prints a copyright message. You don't want to update the date every year. Why not have it appear automatically. While you could write the code to do this on every page. You could easily make a component that encapsulated that code. 

Open `example-03.html` in the browser. Note the copyright messages. 

Open the source code. You should see `frmwrk-copy.js` imported at the top of the page.

Read the comments and find the tags at the bottom. The code defines a new tag: `frmwrk-copy`. This works with two attributes: `year` and `title`. You'll see these in use in the sample code. 

With your partner try and define a new web component. Reference the `hello-world.js` component. You can peek at the `frmwrk-copy` source code if you need to but do as much on your own as you can. 

Challenges: 

- Make the Copyright component. Your component should: 
 - Display "Copyright <year>" where the year is generated in code to get the current year. 
 - Takes an attribute for the year and displays this or the current year if it has not been set.
 - Takes a title attribute that is optionally displayed before the copyright and year, or is not displayed if it is missing. 
- Create a blink component. Everyone is lamenting the fact the blink tag has been removed. 
 - Your blink component should take an attribute that defines the text it displays.
 - Use `setInterval()` to make the text "blink". You'll need to add an interval when the Component is created and remove when the component is removed from the DOM. Use the lifecycle methods for this. 
 - Use `connectedCallback()`
 - Use `disconnectedCallback()` to clear your interval
 - Use an attribute to set the time between blinks
 - Use two properties, one to set the on-time and another for the off-time. 

### Homework 

Choose one of the tutorials below. 

- Web Component Todo list: https://dev.to/thepassle/web-components-from-zero-to-hero-4n4m
- Tabs display: https://developers.google.com/web/fundamentals/web-components/examples/howto-tabs

Due to Class 9 (this Wednesday)

## Wrap Up

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

1. https://bitsofco.de/what-is-the-shadow-dom/
1. https://developers.google.com/web/fundamentals/web-components/shadowdom
1. https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM
1. https://blog.logrocket.com/understanding-shadow-dom-v1-fa9b81ebe3ac/
1. https://css-tricks.com/playing-shadow-dom/
1. https://www.youtube.com/watch?v=YBwgkr_Sbx0

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time** | **Activity** |
| ----------- | --------- | ------------------------- |
| 0:00 | 0:05 | Objectives |
| 0:05 | 0:15 | Overview |
| 0:20 | 0:45 | In Class Activity I |
| 1:05 | 0:10 | BREAK |
| 1:15 | 0:45 | In Class Activity II |
| TOTAL | 2:00 | |

