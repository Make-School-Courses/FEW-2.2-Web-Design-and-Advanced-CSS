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

When creating web components you are creating new tags. It's possible that the names can clash with existing names. For this reason, custom element names must use a hyphen. 

- `my-component` good
- `frmwork-blink` good
- `mycomponent` bad
- `blink` bad

When using custom tags you must use a closing tag, even if the tag is empty. 

- `<my-component></my-component>` good
- `<frmwrk-blink></frmwrk-blink>` good
- `<my-component />` bad
- `<frmwrk-blink>` worse

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

