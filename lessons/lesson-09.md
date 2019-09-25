# FEW 2.2 - Advanced CSS - Exploring Web Components

Continuing the discussion of Web Components from lesson 8. 

## Why you should know this?

Web Components are probably the most important new and emerging web technology. They will take some practice to master.  

## Learning Objectives 

1. Identify major features of Web Components
1. Use refelction with attributes 
1. Build Web Components

## Review CSS Frameworks 

- Show your framework
- Hacktober
  - https://hacktoberfest.digitalocean.com
  - Try some of these 
    - https://github.com/soggybag/tetris-redux-app
    - https://github.com/soggybag/simple-journal
    - https://github.com/soggybag/course-book-react
    - https://github.com/soggybag/sf-public-spaces
- Review the homework
- Publish your Framework to GitHub Pages

## Web Components Activity 

To solve the challenges below we need to do a little prework. 

- Add a script to a page
- Select an element in the DOM
- Get the text contents of that element
- Create a new element
- Append that new element as a child to another element 

Try these challenges. Walk through the first, collaborate, on the second, solve the third in pairs. 

- Copyright Component - Component displays a copyright message
  - Make a new custom element
  - Make a shadow root
  - Use the date object to generate the year
  - Override the year
  - Display a message before and after the copyright
- Blink - Lets bring back the Blink tag!
  - Make a custom component named 'blink-text'
  - Make a new shadow root
  - Use `this.innerText` to get the inner text content of the tag
  - Make the text 50% transparent using a style
  - Animate the opactity using `setInterval()`
  - Add a transition
  - Use an attribute `time` to set the timing of the blinks
  - Listen for chnages to the `time` attribute
  - Remove the intverval when the component is removed
- Rainbow text - The goal is to make a component that colors all of it's in a rainbow of colors. Imagine each word is a different color. 
  - Make a new custom element `rainbow-text`
  - Get the text from the host element
  - Split the text on the space to get an array of words
  - Transform the array of words into an array of spans
  - Append these spans to the shadow root
  - Assign each span a color style 

## Homework: Continue working on your framework

Take the feedback collected in class today to improve your framework. Continue working on your framework

- [Assignment 9](../Assignments/assignment-09.md)

## Wrap Up

- 

## Additional Resources

1. 

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
