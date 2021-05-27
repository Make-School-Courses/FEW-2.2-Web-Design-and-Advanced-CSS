# FEW 2.2 - Advanced CSS - Styling form Controls

Styling controls like buttons and form elements provide some extra challenges and opportunities.

## Why you should know this?

Form elements and controls are points of interaction in your applications. These need to be extra engaging. Hard to use and confusing forms risk losing potential users for application and customers for your business. 

## Learning Objectives

1. Style form elements
1. Style elements according to state
1. Use attribute selector
1. Use parent element to control the layout of children

### Form elements 

Form elements are input, textarea, radio button, and checkbox. Your goal today is to style these elements. 

Add the markup below to your style example: 

```HTML
<form>
  <label>Name</label>
  <input type="text" placeholder="enter name" />
  <label>email</label>
  <input type="email" placeholder="enter email" />
  <label>password</label>
  <input type="password" placeholder="enter password" />
  <label>Notes</label>
  <textarea placeholder="enter notes"></textarea>
  <input type="submit">
</form>
```

This is only a few of the input types. There are also input types for: 

- number
- date
- color
- and more...

You'll just style these for now. 

## Styling Inputs

Selectors: 

```CSS
input[type=text], 
input[type=email], 
input[type=password], 
textarea {
  /* Your styles here */
}
```

Use these properties: 

- Typography
  - `font-size`
  - `font-weight` 
  - `color`
- Box 
  - `border-style`
  - `border-width`
  - `border-radius`
  - `border-color`
  - `background-color`
  - `padding`
  - `margin`
  - `box-shadow` (can have multiple, can be inset)

Let's talk about focus. An input has focus when the keyboard is able to enter text. You can style the input in it's focussed state. 

```CSS
input[type=text]:focus, 
input[type=email]:focus, 
input[type=password]:focus, 
textarea:focus {
  /* Your styles here */
}
```

What about that outline? The accessibility outline is very important. 

https://a11yproject.com/posts/never-remove-css-outlines/

`outline: none !important;`

If you don't like this replace it with your own style. Don't remove it!

## Challenge 

Style the form inputs and textarea. Use the properties listed above to make good looking form inputs. 

Think about readability by looking closely at padding and font-size. 

Use the :focus pseudo selector to style form elements in their forcussed state.

Here are a few ideas: 

- Set a consistant border for all elements 
- Use padding to give some space around the text and the border
- Set the font size, the default font is too small

```CSS
input[type=text], 
input[type=email], 
input[type=password], 
textarea {
  padding: 1em;
  font-size: 1em;
  border: 3px solid var(--dark-gray); /* use a custom property! */
  /* Removing the outline! */
  outline: none !important;
  /* Animate changes */
  transition: 300ms;
}
```

If you've removed the outline be sure to Style the :focus state for these elements!

```CSS
input[type=text]:focus, 
input[type=email]:focus, 
input[type=password]:focus, 
textarea:focus {
  border-color: var(--selected-color); /* Use a custom property! */
}
```

## Labels and Selectors

Form elements should always have labels. It's important that a label be associated with it's form input. Why? 

- Used by screen readers and accessibility helpers
- Clicking a label activates the form element

A label can be associated with a form element in one of two ways: 

Using an `id` and `for` attributes:

```HTML
<label for="name">Your name</label>
<input id="name">
```
Or wrap the input in the label: 

```HTML
<label for="name">
  Your name
  <input id="name">
</label>
```

Each of these methods has it's pros and cons. You should choose one style to use for your framework. This is how developers using your framework will need to write markup when using for elements. 

## Challenge 

Style your labels. 

## Forms 

Forms are groups of inputs. Forms are important to your applications. If people aren't willing to enter their information your web sites are not going to go very far. Good looking easy to use forms encourage people to use them. 

By default form elements are inline. This means they line up like words in a paragraph. More often you'll want forms to arrange it self in a column. 

The form element can arrange it's children using flex. Using flex-direction. Here are some styles to get you started: 

```CSS
form {
  display: flex;
  flex-direction: column;
}
```

Style the labels. They might look better with a little margin: 

```CSS
label {
  margin: 1em
}
```

Usually the the submit button will be at the bottom and often on the left. 

```CSS
input[type=submit], button[type=submit] {
  align-self: flex-end;
}
```

## Challenge 

Style your form. You want to set the basic layout without doing everything. The goal is to get enough style to make things look good while not doing so much that your forms can't be customized. 

## Check boxes and radio buttons

Check boxes and radio buttons are special inputs. These do not provide much that you can style. They also appear different in different browsers. 

What can you do? You can style the label! Remember that clicking on the label is the same as clicking on the input it is associated with! 

The label can be styled extensively. 

Follow the example here and create a customized check box and radio button. 

https://www.w3schools.com/howto/howto_css_custom_checkbox.asp

With only the label element to work there is a limit to what you can draw. Luckily CSS provides to special elements: 

- `:before` (adds a first child element)
- `:after` (add a last child element)
- `:checked` (is active when the element is selected)

These can be used to add elements that don't exist in your source markup. You can use them with the check box to add the check mark. 

Use the content property to set what the content of the new pseudo element. 

Follow the custom checkbox example. Here :after is use to add the checkmark. This checkmark is box with a border on two sides, that has been rotated 45 degrees. 

The `:checked` pseudo class applies when a check box or a radio button is currently selected. 

## Homework: Framework - Controls

Define some styles for controls in your CSS Framework. See the home description linked below for more details:

- [Framework: Controls](../Assignments/assignment-09-controls.md)

## Wrap Up (5 min)

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

1. https://css-tricks.com/the-checkbox-hack/

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time** | **Activity** |
| ----------- | --------- | ------------------------- |
| 0:00 | 0:05 | Objectives |
| 0:05 | 0:15 | Overview |
| 0:20 | 0:45 | In Class Activity I |
| 1:05 | 0:10 | BREAK |
| 1:15 | 0:45 | In Class Activity II |
| TOTAL | 2:00 | |

