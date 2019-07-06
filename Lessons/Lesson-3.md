# FEW 2.2 - Advanced CSS - SASS

CSS Preprocessors SASS: Syntactically Awesome StyleSheets. 

## Why you should know this?

CSS preprocessors are common in industry and provide some valuable functionality. Expect to see them in the work flow of companies large and small.

## Learning Objectives

1. Define CSS preprocessor functionality and uses
1. Write SASS code
1. Compile code writte in SASS to vanilla CSS

## What is SASS? 

Q: What is SASS? 
A: SASS is an alternative language that compiles to vanilla CSS. 

Q: Why use SASS? 
A: SASS provides a way to generate CSS from higher level code that inlcudes variables, if then logic, for loops, and more, that doesn't exist in vanilla CSS. 

Q: Can I use SASS in web projects?
A: No, you must compile SASS to CSS and use CSS in your projects. 

Q: How do you compile SASS? 
A: Use preprocessor, there are a few to choose from. 

## Install SASS

There are several tools you can use to compile SASS. There are desktop apps like: 

- http://koala-app.com
- http://compass-style.org

There are a couple command line tools also. We will use Node JS version since we have been using Node for projects. 

Install Node SASS. 

`npm install -g sass`

## Compiling SASS

Compile SASS.

1. Make a new folder
1. Create `index.html`
1. Create `style.scss`
1. `sass --watch style.scss style.css`

The last line above runs SASS. The `--watch` flag tells SASS to watch for changes and update when it sees them. The last two parameters: `style.scss style.css` define the input (`style.scss`) and output (`style.css`) files. 

Try it. 

## Getting started with SASS

SASS supports variables. Use to 

- Share values for DRY code
- Calculate relative values for DRY code 
- And more!

Variables in SASS always beginw with the `$`

```CSS
$bg-color: #eee;
$font-color: #333;
$font-size: 16px;
```

Use these where you like: 

```CSS
body {
  background-color: $bg-color;
  color: $font-color;
  font-size: $font-size;
}
```

There is a lot you can do with this it extends CSS in new ways. _Keep in mind that SASS is always rendered to vanilla CSS!_

## In Class Activity 

Pair up with someone you haven't paired with before. You'll be assigned a topic from the list below. You and your pair are repsonsible for studying and **making an example that explains the concept**. Do you best to think of a practical use for your topic and code sample. 

https://sass-lang.com/documentation

- [Variables](https://sass-lang.com/documentation/variables)
- [Nested Rules](https://sass-lang.com/documentation/style-rules#nesting)
- [Mixins](https://sass-lang.com/documentation/at-rules/mixin)
- [Functions](https://sass-lang.com/documentation/functions)
- [If else](https://sass-lang.com/documentation/at-rules/control/if)
- [For](https://sass-lang.com/documentation/at-rules/control/for)
- [Extend](https://sass-lang.com/documentation/at-rules/extend)

## Homework 

To really get an understanding for SASS you have to use it. Your goal is to apply SASS to one of your past projects. 



## Wrap Up (5 min)

- Continue working on your current tutorial
- Complete reading
- Complete challenges

## Additional Resources

1. https://sass-lang.com

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
