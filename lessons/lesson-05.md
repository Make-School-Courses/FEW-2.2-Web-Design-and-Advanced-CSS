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

Vocabulary

**Columns**

Columbs are the horzontal divisions of the grid. Picture these as vertical bars that define the horizontal space. These are the most important measurement! 

![Columns](./images/01-columns.png)

**Gap/Gutter**

The grid gap or gutter is the space between the the columns. 

**Rows**

These are the vertical divisions. Picture these as the horizontal bars that are stacked vertically. 

![Rows](./images/02-rows.png)

When you put the two gether you get a **grid**,

![Grid](./images/03-grids.png)

**Grid Cell**

A grid cell is rectangular area that maps across any number of rows and columns. It has to be a rectangle! The edges must stop at the borders defined by the rows and columns. Notice that a cell doesn't fall into the gap between rows and columns! 

![Cells](./images/04-cells.png)

Generally speaking you can ignore the height of rows since the row height will be set by the height of the content, though sometimes you will set this. 

### Making a Grid with CSS

Imagine you have the following markup: 

```HTML
<div class="container">
	<div class="box a">One</div>
	<div class="box b">Two</div>
	<div class="box c">Three</div>
	<div class="box d">Four</div>
	<div class="box a">Five</div>
	<div class="box b">Six</div>
	<div class="box c">Seven</div>
	<div class="box d">Eight</div>

</div>
```

With this arrangement you can use `div.container` to arrange all of the `div.box` in a grid. The following would arrange these elements into three columns with a `1em` gap. 

```CSS
.container {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr;
	grid-gap: 1em;
}
```

Let's take that apart. 

```CSS
.container {
	display: grid; /* .container arranges its children on a grid */
	...
}
```


```CSS
.container {
	...
	/* Creates three columns, which are each one fraction */
	grid-template-columns: 1fr 1fr 1fr;
	...
}
```

The `fr` is a unit that is one fraction. A fractional unit takes up a fraction of the available space. In this each we have three fractions they should each be 1/3 or 33.333% of the space. 

If you had `1fr 1fr 1fr 1fr` each fraction would be 1/4 or 25%. 

You can mix and match fraction for example: `1fr 1fr 2fr` is a total of 4 fractions and would give us: 1/4, 1/4, and 1/2 or 25%, 25%, and 50%.

The code above is all you need for a simple grid where each cell is the same size. 

### Creating complex grids

CSS Grid provides more tools for creating more complex grids. One of the best tools is `grid-areas`. This property allows you to define cells that span rows and columns and map elements to those cells. 

This time start with four divs. 

```HTML
<div class="container">
	<div class="box header">Header</div>
	<div class="box side">Sidebar</div>
	<div class="box main">main</div>
	<div class="box footer">Footer</div>
</div>
```

These elements represent the areas of the page and will mapped to the grid. 

```CSS
.container {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr 1fr;
	grid-template-areas:  "h h h h" 
                        "s m m m" 
												"s m m m"
												"f f f f";
```

This time we have 4 columns each one fraction. 

The `grid-areas` property is where you will define your grid areas. The letters assign a name and the space used for a cell. 

![Grid Areas](./images/Grid-Areas.png)

The cells will map like this. Imagine `h` represents the header, `s` is the sidebar, `m` is the main content, and `f` is the footer. 

![Grid Areas](./images/Grid-Areas-2.png)









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
- [CSS Grid in 5 mins](https://www.freecodecamp.org/news/learn-css-grid-in-5-minutes-f582e87b1228/)