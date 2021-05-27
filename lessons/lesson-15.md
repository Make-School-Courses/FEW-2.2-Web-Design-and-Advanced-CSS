# FEW 2.2 - Advanced CSS - Exploring Web Components

Continuing the discussion of Web Components from lesson 8. 

## Why you should know this?

Web Components are probably the most important new and emerging web technology. They will take some practice to master. They are also not complete and will evolve. Learning this now will give important background into this new realm. 

## Learning Objectives 

1. Identify major features of Web Components
1. Create elements with JS
1. Style elements with JS
1. Build Web Components

## Getting Started with Web Components

Work through the challenges here: https://github.com/Make-School-Labs/simple-component

Follow this by studying the guide here:

- https://javascript.info/webcomponents-intro
- https://javascript.info/custom-elements
- https://javascript.info/shadow-dom

The goal is to create a custom element/web component that will be included 
with your CSS framework.

Anyone using your web CSS framework would get a set of styles. Adding your JS they will also be able to use your custom elements.

These components are fairly simple. You'll be tackling more complex components next week.

## Web Components Concepts

### Naming custom elements

When creating web components you are creating new tags. It's possible that the names can clash with existing names. For this reason, custom element names must use a hyphen (-). 

- `my-component` good
- `frmwork-blink` good
- `mycomponent` bad
- `blink` bad

When using custom tags you must use a closing tag, even if the tag is empty. 

- `<my-component></my-component>` good
- `<frmwrk-blink></frmwrk-blink>` good
- `<my-component />` bad
- `<frmwrk-blink>` worse

It's a good idea to prefix all of your names with the name of your framework. For example, if Bootstrap used web components all of their tags could start with `bs-`:

```html
<bs-carousel></bs-carousel>
```

### Extend HTMLElement and define a new tag

Extend HTMLElement and call super in the constructor. 

Call `customElements.define()` with the name of your new tag and the class that will provide the JS for the new tag.

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

Best practice: Use an underscore in front of all of the property names you define. 

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

## Lifecycle Methods 

Use lifecycle methods to initialize and deinitialize your web component. 

The **connectedCallback()** method is called when the component is added to the DOM. Use this to start timers set initial property values, measure the size the size of the component. 

The **disconnectedCallback()** method is called when the component is removed from the DOM. Use this to clean up. Do things like stop timers, and free resources that you may be using. 

```JS
class BlinkText extends HTMLElement {
  constructor() {
    super();
    ...
  }

  connectedCallback() {
    // When the component is added to the DOM
  }

  disconnectedCallback() {
    // When the component is removed from the DOM
  }
}

customElements.define('blink-text', BlinkText);
```

## handling attributes 

Attrbites appear in tags like this: 

```html
<my-element time="1000" min="0" max="5">
  ...
</my-element>
```

The attributes are: time, min, and mac above. 

Attributes allow us to pass data into our custom elements. 

Internally the custom element needs to define when attributes it observes. Some attributes don't need to be observed for example: class, and id. 

```JS
class BlinkText extends HTMLElement {
  constructor() {
    super();
    ...
  }


  // Name the observed attribues 
  static get observedAttributes() {
    return ['time', 'min', 'max'];
  }  

  // Handle changes to observed attributes
  attributeChangedCallback(name, oldValue, newValue) {
    
  }
}

customElements.define('blink-text', BlinkText);
```

Handle changes to attributes by looking at the name to see which attribute has changed, then compare the old and new values to decide how to change the attribute. 

```JS
attributeChangedCallback(name, oldValue, newValue) {
  // If the attribute changed was named time
  if (name === 'time') {
    // parse the new value, we want a number
    const time = parseInt(newValue)
    if (isNanN(time)) {
      // If it's not a number stop!
      return
    }
    // If it is a number use that new value
    this._time = time
    this._clearTimer()
    this._addTimer()
  }
}
```

## Homework: Continue working on your framework

Continue working on your CSS framework. 

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time** | **Activity** |
| ----------- | --------- | ------------------------- |
| 0:00 | 0:05 | Objectives |
| 0:05 | 0:15 | Overview |
| 0:20 | 0:45 | In Class Activity I |
| 1:05 | 0:10 | BREAK |
| 1:15 | 0:45 | In Class Activity II |
| TOTAL | 2:00 | |

