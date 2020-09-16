# FEW 2.2 - Web Component Lab

Continue working on your CSS Framework. This class will be dedicated to completing the challenegs from class 9 and use any left over time to improving your CSS framework. 

## Learning Objectives 

1. Build simple web components
1. Define custom tags that encapsulate functionality
1. Use attributes to configure components
1. Reflect properties and attributes 
1. Use Web Component Lifecycle methods

Continue the Web Component example challenges: 

https://github.com/Make-School-Labs/simple-component

When you complete the challenges above your job is to create a component that will be included in your framework. You can use one of the challenge examples as a starting point. 

If you completed the challenges and you want to try something more challenging for your framework here are few ideas: 

- Make a custom component for the navbar. 
- Here are a couple tutorials that create a tab navigation component:
  - https://developers.google.com/web/fundamentals/web-components/examples/howto-tabs
  - https://piccalil.li/tutorial/solution-005-tabs/

### Apply best practice

When making your components they must use a hyphen. Best practice would have you use a prefix any tag names with the name of your framework. For example if you framework was named Corgi custom tag names might: 

- `<corgi-tabs></corgi-tabs>
- `<corgi-navbar></corgi-navbar>`
- `<corgi-carousel><corgi-carousel>` 

If the name of your framework is long use the initials. For example, imagine the name of your framework was "Stylin Styles" You might abbreviate to:

- `<ss-tabs></ss-tabs>`
- `<ss-navbar></ss-navbar>`
- `<ss-carousel><ss-carousel>` 

## Web Components vs Custom Element

Any time time you create a new custom element with `customElements.define()` define you are creating a new custom element. Your custom element may or may not use the Shadow root. 

Let's call Custom Elements that use the shadow root "Web Components" and custom elements that don't use the shadow root "Custom elements". 

What's the difference? 

Using the Shadow root: 

- Pros
  - Encapsulation - elements and styles are totally separated from the DOM
  - Can't be accidentally affected from outside
- Cons 
  - Can't share styles from outside
  - It's a little more complex to program

Without the Shadow Root: 

- Pros
  - Easier to program
  - Can share styles from outside
- Cons
  - May not be as predictable 
  - Can be accidentally affected by the outside

It's up to you whether you use the shadowroot or not for this assignment. 

Your web components/Custom elements don't have to be huge and complex. If you can make a useful element that has practical application that's goal. If you can make something fun and interesting that's okay also!

