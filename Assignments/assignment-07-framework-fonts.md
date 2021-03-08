# FEW 2.2 - Custom CSS Framework - Typography

This is the first part of a larger assignment to create a CSS framework. 

**What is a CSS framework?** A framework is a library of code that has opinion about how things should be done. Your CSS framework should supply basic styles and take an opinion about what looks good on the web and how styles should be applied. 

## Description

Your goal is create a framework that can be used to build better looking web pages. 

Your framework will have the following features which you will implement across separate assignments from now until the end of the term. 

The first step of this assignment is to define some font styles.

### Why this assignment?

Understand how type works and the features of typography will make your projects look better and be more engaging. 

## Project requirements
### Getting Started
- [ ] Create a new repo to host your CSS framework.
- [ ] Name your CSS framework.  
  - Seriously, it needs a name, it's a product. No, really it is and like any other product it needs a name. 
    - Frmwrk
    - Framwërk
    - Ninja CSS
    - Chonky CSS
    - CSSS - Chonky Styles Solidly Served
    - CSSSS - CSS Served with Solid Sagacious Style 
    - CSSSSS - Colorful Simple Seamless and Safely Served Styles 
  Seriously, your CSS framework needs a name. Make up a name. 

- [ ] Name your CSS file after your framework. **The framework CSS should not be named: style.css!**
  - Your CSS framework will be a CSS file. Yep, it will be a single CSS file. 
    - You can build your CSS file from SASS, break this up into several `.scss` files but it should compile to a single .css file. 
  - Anyone who wants to use your CSS framework should only have to download the `.css` file and link to it in their HTML document. 
- [ ] Find two sample files to test your work against.
  1. One of your or any existing webpage. 
      - Find a past project or other web page you can test your framework against. This can be any HTML page. 
      - Remove any styles this page previouly used. 
  2. The sample markup here: https://github.com/Make-School-Labs/css-framework-starter
- [ ] Copy your sample HTML files into the folder with your framework css repo and link your CSS files in the head of each HTML document. 
- [ ] Add some styles! What will your CSS framework look like? 

### Styling Type

Start by styling type. Set a default font style for your framework. Follow these steps: 

- [ ] Choose a font 
  - It's probably best to use a system font. See the notes in [lesson 4](../lessons/lesson-04.md). 
  - The big decision here is choose between a serif or sans-serif font family. 
- [ ] Set a default font style on the body element. 
  - [ ] Define your default font style in your `body` tag 
  - [ ] Set the `font-family`
  - [ ] Set the `font-size`
  - [ ] Set the `line-height`
  - [ ] Set `color` and `background-color`  
    - Check contrast meets the Web Accessibility [guide lines](https://webaim.org/resources/contrastchecker/)
    - Don't let choosing colors block you from the rest of the task.  You can always change them later.
      - PROTIP: Use custom properties
      - http://colormind.io/
- [ ] Set a style for the headings `h1-h6`.  Consider: 
    - `margin`
    - `color` 
    - `font-weight`
    - `letter-spacing`
- [ ] Style other text elements 
  - [ ] `strong`
  - [ ] `em`
  - [ ] `a`
  - [ ] `abbr`
  - [ ] `code` (use a fixed width font)

Every single element may not need to be uniquely defined/styled, but you should still consider the styles for each of these and then make that call. 

### Stretch Goals
- Create color palettes for both dark/light mode 
  - https://css-tricks.com/dark-modes-with-css/
- Explore and use a CSS naming convention
  - https://hackernoon.com/best-practice-in-css-organisation-and-naming-conventions-4d103ujy
  - https://www.keycdn.com/blog/oocss
  - https://en.bem.info/methodology/naming-convention/
  - http://smacss.com/book/categorizing
   

## Deliverable

A link to the branch of your project with the improved typography. 

### Due date

- Monday June 28 

## Assessing the assignment

| Expectations | Does not meet              | Meets                 | Exceeds                          |
|:-------------|:---------------------------|:----------------------|:---------------------------------|
| Completion   | You have not styled all of the elemnts listed. | Everything listed above looks styled. | You have paid close attention to the properties styled and adjusted them to refine their appearance further. |
| Quality      | The style of the work doesn't look too much different from the default html styles. | You're work looks better than the default HTML styles. | People can't help but offer comments about how amazing and professional your work looks. |
| Comprehension | Can't explain the the styles that you have used. | You could explain the styles you've used. | You can explain the styles and provide deeper insight into the properties. |
| Work ethic   | few massive commits | Commits outline progress | Clearly show progression of the work |
| Code | You're code is sloppy and unformatted | You're code is well formatted and uses best coding prctices. | You've used CSS custom properties. |
