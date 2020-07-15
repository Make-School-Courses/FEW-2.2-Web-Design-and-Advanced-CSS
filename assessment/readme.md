# FEW 2.2 Final Assessment 

Your job is to style the color.com web site. It's lacking in style. Do your best. Use your CSS framework as starting point. 

Feeel free to modify the HTML markup on thepage in anyway that yu wish. You must not break the fucntionality! There are two things that happening here: 

1. Color swatches are generated in `div.swatches`. 
2. Clicking swatches adds colors to the cart. 

## 1 Type 

Set the font style for text and headings.

## 2 Style The Navbar 

Style the navbar and links.

## 3 Style cards 

These cards have an image and text. **The cards should sit in a horizontal row.**

## 4 Style Colors 

To make the swatches visible I added width, height, and border. You should change these to fit your ideas. You need to present the colors in a rows or a grid. Remember we have to be able to click them and these divs so they need to be big enough to click. Each div also needs to keep the class name: add-to-cart and the data-color and data-price attributes.

### 5 Genereate 100 colors

There are 100 color swatches but there are no colors. You need to generate 100 unique colors and display them in the swatches. You can do this anyway you like. 

Note that all colors have an inline style set to a custom property named: --color-0 to --color-99. Generating 100 colors programatically might be a good solution. 

## 6 Shopping cart 

Clicking a color swatch adds it to the shopping cart. The cart is a list and each row is made up of some text, buttons, and an input. You should style these. 

## 7 Ticker Tape 

Create a web component that animates the text inside with a ticker tape effect. Use the ticker tape component at the top of the page to animate the text: `<h1>...Color.com is awesome...</h1>`. 

The ticker tape should moves the text across the screen. You can take one of two approaches. 

1) Manipulate the string content. Use a timer to take the first character of the string and move it to the end of the string. Doing this over time you'll end up with: 

- Hello
- elloH
- lloHe
- loHel
- oHell

2) Create an inner element containing the the text. Transform this element from right to left. At the end of the animation Move it back to the right and start over again. 

Taking this approach it would be easiest to use `@keyframes`. To do this in a web component you'll want to define this in a template. See the example [here](https://github.com/Make-School-Labs/simple-component/blob/master/simple-components-templates/01-counter-template/fancy-counter.js). Note the styles are in a string in a `<style>` tag. You could define your `@keyframes` block here along with other animation styles.

Notice that all of the styles here are defined in a template and the template is used in the component. 

```js
const tempNode = template.content.cloneNode(true)
this._shadowRoot = this.attachShadow({ mode: 'open' });
this._shadowRoot.appendChild(tempNode)
```