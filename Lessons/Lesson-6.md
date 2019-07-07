# FEW 2.2 - Advanced CSS - CSS Custom Properties Scope and Styling Controls

Styling controls like buttons and form elements provides some extra challenges and opportunities.

## Why you should know this?

Form elements and controls are points of interaction in your applications. These need to be extra engaging. Hard to use and confusing forms risk losing potential users for application and customers for your business. 

## Learning Objectives

1. Use scope to control custom proeprties
1. Create Form elements that use custom proeprties
1. Use fallback values 

## CSS Custom Properties: Fallback Values 

`var(--variable, fallback-value)`

## Scope and Custom properties

Custom properties are used in the scope where they are defined. This local scope is defined by the selector where a custom property is defined. 

```CSS
button {
  --button-color: #47b6e9;
  ...
  background-color: var(--button-color);
}
```

Custom properties are inherited. A variable that exists on the scope of an ancestor is available to descendents. 

```CSS
body {
  --button-color: #47b6e9;
  ...
}

button {
  background-color: var(--button-color);
}
```

The `:root` selector represents the root of the document. This 

## Media Query

Use `@media` to target a platform with features. 

Custom properties and @media for mobile styles

examples........

## Form element strategies 


Setting custom proeprties via the style property. 

Sharing a custom property through scope. 

Button Example .........

Input Example ..........

## Interview Questions 

You need to have flexible UI elements. The default colors work but in some cases you need to be able to easily redefine the color of a button. 

You need to define a range of font sizes. Imagine you need 4 sizes each larger than the previous. All of the sizes should relative to a base size. 

On mobile devices your range of font sizes need to be different from the sizes you are using on the desktop. 

## Wrap Up (5 min)

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

1. Links to additional readings and videos

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
