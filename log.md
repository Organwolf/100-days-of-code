# 100 Days Of Code - Log

### Day 0: March 2, 2020

**Today's Progress**: Learnt more about debouncing, window events, using scroll events in vanilla JS.

**Thoughts:** Had to debug my code for 10+ minutes because I had forgot the punctuation **.** while using querySelectorAll to select the elements of a certain class. 

~~~~
const sliderImages = document.querySelectorAll('.slide-in');
~~~~

Debouncing is problably the most advanced part of this code and from what I understand it enables me to trigger a particular function a fixed amount of times instead of it triggering unnecessarily often.

**Link to work:** [Slide in on scroll](https://github.com/Organwolf/VanillaJS/tree/master/SlideInOnScroll)

### Day 1: March 2, 2020

**Today's Progress**: Made a TODO app in combination with localStorage so that the information persests even if you reload the page

**Thoughts**: Still working on wesbos JavaScript 30. Used event delegates in this one. I subscribe to the click event on the itemsList. Inside the function I determine which element I want to add logic to. 

**Experimented with:** SVG icons. Found an icon that fitted the theme. I actually had to fiddle around with the viewBox attribute to make the icon look ok.

~~~~
viewBox="-2.35 -0.5 23 23"
~~~~

**Link(s) to work**: [TODO-list](https://github.com/Organwolf/VanillaJS/tree/master/TODO-list)

### Day 2: March y, 2020

**Today's Progress**: By making this todoapp I got the opportunity to repeat some of ReactJS core concepts such as separating the data from the view components.

**Thoughts**: The app is far from beautiful. It litterally has minimal styling. All of the binding of functions can be a bit confusing. On the other hand this was
a good opportunity to practise. I could definitely revisit this and work on the visuals. Both with different css frameworks and plain css!

**Experimented with:** Removing the list style type on list elements by setting the list type style to none. I also experimented with different fonts
~~~~
font-family: sans-serif;
list-style-type: none;
~~~~

**Link(s) to work**: [Todo App](https://github.com/Organwolf/ReactJS/tree/master/intro-react)


### Day 3: March y, 2020

**Today's Progress**: Worked on Javascript30 by Wesbos. Day 17: Sort Without articles. Learnt more about using map, regex and "compressing" functions by using fat arrows and turnary functions. Also learnt how I can parse a nodeList to an array using Array.from().

**Thoughts**: It is good if I try to solve the Javascript30 problems on my own first before the solution is shown.


**Experimented with:** Regex and turnary functions

~~~~
// 1 & 2 are equivalent to each other.

// 1
str.replace(/^(a |the |an )/i, '').trim();

// 2
str.replace(/the/gi, "")
str.replace(/an/gi, "")
str.replace(/a/gi, "")
str.trim()
~~~~

~~~~
// 1 & 2 are equivalent to each other.

// 1
const sortedBands = bands.sort(function (a,b) {
  if(strip(a) > strip(b)){
      return 1;
  } 
  else {
      return -1;
  }
});

// 2
const sortedBands = bands.sort((a, b) => strip(a) > strip(b) ? 1 : -1);
~~~~

**Link(s) to work**: No link today
<!--
### Day x: March y, 2020

**Today's Progress**: 

**Thoughts**:

**Experimented with:**

**Link(s) to work**: [Todays thing](http://www.example.com)
-->
