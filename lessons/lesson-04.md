# FEW 2.2 - Advanced CSS - Typography

This lesson will take a look at Typography and CSS. 

## Why you should know this or industry application

A majority of the content on the internet is text. Making good looking text that is easy to read will make your websites stand apart from the rest. 

## Learning Objectives

1. Identify features of typography
1. Use CSS styles to style type
1. Implement custom fonts

## Features of typography

- Kearning
- Leading
- Baseline

## Styling type

In CSS we use the following properties to style type.

- font-family
- font-size
- font-weight
- color
- line-height

## Native Fonts 

In the old days there was: 

- Arial
- Helvetica
- Verdana
- Times
- Times New Roman
- Courier New
- Courier
- Georgia
- Palatino
- Garamond
- BookmanComic Sans
- Trebuchet MS
- Arial Black
- Impact

These don't work on all systems. The Mac includes some of these and Windows includes others. Linux probably has it's own subset. 

The list of fonts that are very likely to exist across all operating systems is shorter: 

- Arial
- Courier New
- Georgia
- Times New Roman
- Trebuchet MS
- Verdana

Looking at the list the fonts fall into two categories:

- Serif - Courier New, Georgia, Times New Roman
- San Serif - Arial, Verdana, Trebuchet MS

For any web site you are probably Using either serif or a San serif as your base font.

## UI System Fonts 

These UI specific fonts. These are newer and more up to date than the standard system fonts. These work especially good for mobile since mobile devices tend to not use the same fonts available on the desktop. 

You should include these in your font stack. 

| OS       | Version      | Font name     |
|:---------|:-------------|:--------------|
| Mac OS X | El Capitan	  | San Francisco |
| Mac OS X | Yosemite     | Helvetica Neue |
| Mac OS X | Mavericks    | Lucida Grande  |
| Windows  | Vista        | Segoe UI       |
| Windows  | XP |         | Tahoma         | 
| Windows  | 3.1 to ME    | Microsoft Sans Serif |
| Android  | Ice Cream Sandwich (4.0)+ | Roboto |
| Android  | Cupcake (1.5) to Honeycomb (3.2.6) | Droid Sans |
| Ubuntu   | All versions | Ubuntu |

It's hard to support everyone, and you never know which system is viewing your site. You'll need a large font stack. 

Here is what the pros are doing: 

**GitHub**

```CSS
/* System Fonts as used by GitHub */
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```

**Medium** and **Wordpress**

```CSS
/* System Fonts as used by Medium and WordPress */
body {
  font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen-Sans,Ubuntu,Cantarell,"Helvetica Neue",sans-serif;
}
```

Using the the methods above is quick and easy but forces the system to check the font stack each time fonts are applied. Alternatively you can use `@font-face` to declare a font in advance and reference that choice by name. 

```CSS
/* Define the "system" font family */
@font-face {
  font-family: system; /* Name of your font family */
  font-style: normal;
  font-weight: 300;
  /* Font stack: Uses the first available font in this list */
  src: local(".SFNSText-Light"), local(".HelveticaNeueDeskInterface-Light"), local(".LucidaGrandeUI"), local("Ubuntu Light"), local("Segoe UI Light"), local("Roboto-Light"), local("DroidSans"), local("Tahoma");
}

/* Now, let's apply it on an element */
body {
  font-family: "system"; /* Use your named family here */
}
```

Read more about this here: https://css-tricks.com/snippets/css/system-font-stack/

Which should you use? For now your choice. The first is easier to manage. The second might have better performance. 

Speaking of `@font-face` what does this do? 

## Custom Fonts 

Load a custom font using `@font-face`. You'll need to host your font files and have license to the serve them. 

[Yes you must have a license to use a font on your website](https://designshack.net/articles/typography/what-is-a-font-license-and-do-i-need-one/)

Google provides a wide range of free fonts, and they serve them from the google servers. We will use these for this class. 

Google Fonts has hundereds of fonts. You can borwse them all at the link below. 

[Google Fonts](https://fonts.google.com)

Custom fonts have the downside that they take longer load. System fonts are already installed. 

## Font Strategies 

Choosing fonts 

- Pick a family 
- Set the base font style for all tags by setting styles on the html tag
  - Set the font size on the html tag
  - Set the line height

## Defining your Font Stack

There is room for optimism. When defining `font-family` you can provide a list of fonts. The browser picks the first available font in the list.

```CSS
html {
  font-family: Helvetica, "Trebuchet MS", Verdana, sans-serif;
}
```

## Take a look at how fonts are used

Explore some good font styles.

Medium: https://fontsinuse.com/uses/18899/medium-com-2017

Bootstrap: https://getbootstrap.com/docs/4.0/content/typography/

Why Do font choices matter: https://themeisle.com/blog/wordpress-fonts/

## Font Units: em vs rem

The **`em`** is a unit that represents a multiple of the inherited font size. Think of this as a number that multiplies the font size an element would inherit. 

The **`rem`** is root em. It represents a multiple of the root font size. This is the font size set on the html element, or body if you haven't set the font size on html. 

## Wrap Up 

- Review objectives 

## Additional Resources

1. https://blog.prototypr.io/top-10-ui-fonts-for-web-mobile-a8488e561ce3
1. https://uxplanet.org/5-universal-fonts-for-web-mobile-design-7b491df0ea16
1. https://css-tricks.com/snippets/css/system-font-stack/

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
