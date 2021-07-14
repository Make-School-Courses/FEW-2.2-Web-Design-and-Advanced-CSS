# FEW 2.2 Final Assessment 

Your job is to style the color.com web site. Do your best. Use your CSS framework as starting point. You don't have to write all of the styles from scratch! 

Feel free to modify the HTML markup on the page in anyway that you wish. You must not break the fucntionality! There are two things that happening here: 

1. Color swatches are generated in `div.swatches`. 
2. Clicking swatches adds colors to the cart. 

Use your CSS framework! Your framework styles should cover much of the problems here. You will have to write some CSS to fill in some details.

Problems 5 and 7 will not be covered by your framework. You'll need to solve these from scratch. 

## 1 Typography

Set the font style for text and headings. All fonts on the page should styled. I should not see the default Times New Roman anywhere! 

**What do to:** Style the text including the headings. 

## 2 Style The Navbar 

Style the navbar and links. The navbar should include the links and the page title.

**What to do:** Create a navbar along the top of the page. It should be a horizontal bar with containng the links in `section#nav`

**Extra credit:** Make the navbar sticky. A sticky navbar always stays at the top of the page even when the page scrolls. 

## 3 Style cards 

These cards have an image and text. **The cards should sit in a horizontal row.** 

**What to do:** In `section#popular` there are three divs each containing an image and a paragraph. Style these so that look like cards. The cards should be arranged in a horizontal row, use flex. 

## 4 Style Colors

To make the swatches visible I added width, height, and border. You should change these to fit your ideas. You need to present the colors in a grid. We have to be able to click these divs so they need to be big enough to click. Each div also needs to keep the class name: add-to-cart and the data-color and data-price attributes.

### 5 Genereate 100 colors

There are 100 color swatches but there are no colors. You need to generate 100 unique colors and display them in the swatches. You can do this anyway you like. 

Note that all colors have an inline style set to a custom property named: --color-0 to --color-99. Generating 100 colors programatically might be a good solution. 

Possible solutions for this problem would be to use JS or SASS. 

1) JS solution would need to assign an inline color to each color swatch. 

2) The SASS solution would require using a loop to generate style rules for all 100 color properties. The output should look like this: 

```CSS
--color-0: hsl(0, 100%, 50%);
--color-1: hsl(3, 100%, 50%);
--color-2: hsl(6, 100%, 50%);
--color-3: hsl(9, 100%, 50%);
...
```

## 6 Shopping cart 

Clicking a color swatch adds it to the shopping cart. The cart is a list and each row is made up of some text, buttons, and an input. **You should style these.**

In this step your goal is to style the form elements that show up in the shopping cart. 

## 7 Style the contact form

At the bottom of the page is a contact form. Your goal is style this. 

None of the elemenets should use the default styles and all element should look the same. 

## 8 Ticker Tape 

Create a web component that animates the text inside with a ticker tape effect. Use the ticker tape component at the top of the page to animate the text: `<h1>...Color.com is awesome...</h1>`. 

The ticker tape should moves the text across the screen. You can take one of two approaches. 

1) Manipulate the string content. Use a timer to take the first character of the string and move it to the end of the string. Doing this over time you'll end up with: 

- Hello
- elloH
- lloHe
- loHel
- oHell
- Hello

2) Create an inner element containing the the text. Transform this element from right to left. At the end of the animation Move it back to the right and start over again.

Taking this approach it would be easiest to use `@keyframes`. To do this in a web component you'll want to define this in a template. See the example [here](https://github.com/Make-School-Labs/simple-component/blob/master/simple-components-templates/01-counter-template/fancy-counter.js). Note the styles are in a string in a `<style>` tag. You could define your `@keyframes` block here along with other animation styles.

Notice that all of the styles here are defined in a template and the template is used in the component. 

```js
const tempNode = template.content.cloneNode(true)
this._shadowRoot = this.attachShadow({ mode: 'open' });
this._shadowRoot.appendChild(tempNode)
```

## Thanks! 

Thanks for class please fill out the course evaluation if you haven't already: 

https://make.sc/few_2.2_survey
