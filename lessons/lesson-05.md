# FEW 2.2 Lesson 5 - CSS Grid

## Review 



## What is a Grid? 

In design a a grid is used to create a system that arranges things on a page.

The first thing that comes to mind when you talk about a grid is a graph paper. A grid in design looks a little different. Vertically the grid the space between each line is based on the font size. Horizontally the grid is based on the column width. 

Here is a good article describing grid systems: 

https://www.oozlemedia.com/advantages-of-grid-systems-in-web-design/

## CSS Grid 

In the past the deveoper community provided CSS frameworks that had grid built in. You have probably used one of these. 

- https://getbootstrap.com/docs/4.0/layout/grid/
- https://material-ui.com/components/grid/

These systems were built before CSS supported a built in grid system. The CSS grid now makes these grid systems obsolete (in my opinion, I'm sure there is an argument to keep them.)

- Q: What does CSS grid do? 
- A: CSS Grid arranges element in rows and columns.

- Q: How is this different from Flex? 
- A: Flex is a on dimensional arrangement. When using flex you choose an axis either horizontal or vertical. CSS grid on the other hand arranges element on both the horizontal and vertical axis. 

- Q: Why use CSS grid over one of the CSS grid systems like Bootstrap?
- A: CSS Grid is simple enough it doesn't need an abstraction. It's more flexible and doesn't require all of the extra markup needed by a grid system like the one used in Bootstrap. 

- Q: Can you use CSS Grid and Flex together? 
- A: Yes! They both work together. You can use flex to arrange elements on a grid cell or use grid inside an element arranged with flex. 

### Using CSS Grid

CSS Grid works similar to Flex, when you set an elements display property to grid all of that element's children will be arranged in a grid. 

Grid is also different from Flex. It's got two axis and allows you to define cells that make up the grid. It's more complex than Flex. 



Make a basic grid 


Make a complex grid with different size cells 

Map elements to cells

Add some responsive layout



Challenges 

Recreate the example grids















## After Class 

- Use CSS Grid in your Zen Garden Page
- Complete the challenegs from this week

## Resources 

- [Complete Guide to CSS Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [CSS Grid Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
- [Grid Systems](https://www.designsystems.com/space-grids-and-layouts/)
