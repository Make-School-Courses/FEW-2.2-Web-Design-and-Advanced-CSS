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

## 6 Ticker Tape 

Create a web component that animates the text inside with a ticker tape effect. Use the ticker tape component at the top of the page for the 
