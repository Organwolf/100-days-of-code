# 100 Days Of Code - Log

### Day 16: March 18, 2020

**Today's Progress**: Finished a video about APIs called [APIs for Beginners - How to use an API (Full Course)](https://www.youtube.com/watch?v=GZvSYJDk-us) by Craig Dennis. I've worked a little with flask, express, nodeJs and javascript completing 2 webapps I cloned from [Craig's github](https://github.com/craigsdennis/intro-to-apis-course/blob/master/course-notes.md). 

**Thoughts**: This has nothing to do with programming but I love the aestetics of [Glitch](https://glitch.com).

### Day 15: March 17, 2020

**Today's Progress**: Learnt more about event bubbling and event capturing as well as *once* in the context of using event listeners. Also used *transform: scare( x )* to create a subtle popping effect.

```javascript
// the scale of the text while at the top of the page
transform: scale(0.98);

// the space of the text while you've scrolled down a bit
transform: scale(1);
```

**Thoughts**: The stuff I learnt about event bubbling and capturing further drove home the point of the DOM being a graph. You traverse the graph/tree to modify content etc.

**Experimented with**: Google fonts as well as the custom background image used in the SpeechSynthesis web app. 

**Link(s) to work**: [Sticky navigation bar](https://github.com/Organwolf/VanillaJS/tree/master/StickyNav)

### Day 14: March 16, 2020

**Today's Progress**: I personally really like the JavaScript below. First you fetch all of the elements with the type of *range* or *text* and store them in an *options* array. Then a forEach is used on that options array adding an eventlistener to each of the elements. The eventlistener triggers on the *'change'* event calling *setOption()*. *msg* is an instance of *SpeechSynthesisUtterance*. `The SpeechSynthesisUtterance interface of the Web Speech API represents a speech request. It contains the content the speech service should read and information about how to read it (e.g. language, pitch and volume.)` Because the retrieved elements' name attributes are the same as the attributes on the msg object that we want to change it is possible to use the *this.name*. The *toggle()* function then runs the speech service with the current text, pitch and range that the user has specified.

```javascript
  const options = document.querySelectorAll('[type="range"], [name="text"]');

  options.forEach(option => option.addEventListener('change', setOption));

  function setOption() {
    msg[this.name] = this.value;
    toggle();
  }
```

**Thoughts**: Had an absolute hell with my firefox browser. It didn't load the voices and I spent +1 hour reading the Mozilla documentation and trying stuff out. In the end it was a really good experience. I've had a similar problem before when using Flask together with JavaScript. I didn't know that you had to hard reflesh the browser to se the changes. So I spent tons of time trying to fix something without seing anything change in the browser.

**Experimented with**: The Mozilla documentation and loading the voices into the dropdown. I'd love to change the font, the background, moving around the labels and stuff like that.

**Link(s) to work**: [SpeechSynthesis](https://github.com/Organwolf/VanillaJS/tree/master/SpeechSynthesis)

### Day 13: March 15, 2020

**Today's Progress**: Today has been a really mixed bag of stuff. I added a jumbotron to my todoapp, worked with APIs to understand them better, read about and worked with virtual environments in python and tried to complete day 23 of Wesbos JavaScript30 which deals with speach synthesis in the browser (robot voices reading stuff). I usually make physical todo notes when programming. Here is a taste:

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/Todos1-15:3:20.png" alt="without" width="600" height="400"/>

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/Todos2-15:3:20.png" alt="without" width="600" height="400"/>

I was also introduced to [Glitch](https://glitch.com/) trough the APIs for beginners course linked below.  
This site might be a real gem, we'll see.

**Thoughts**: 2 weeks completed at this point and it feels good! I really appriciate the [APIs for Beginners - How to use an API (Full Course)](https://www.youtube.com/watch?v=GZvSYJDk-us). As for day 23 of the 30 days of JavaScript challange I'm a bit confused. Had to read up on speech synthesis on [mozillas developer pages](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis). I'll have to solve the last issues I have with that tomorrow. Python is really fun. Working in the console, writing bash commands and just doing (fairly basic) stuff like that makes you feel like a hacker (or something). I appreciate it, that's what I'm trying to get at, and I'm looking forward to automating stuff with it further down the line.

**Experimented with:** SpeechSynthesis in the browser, twillo API calls using both JavaScript and python, virtual environments and there file structures and environment variables!

**Link(s) to work**: [Work in progress](https://giphy.com/gifs/character-lemon-wip-3o7qE4iwtQb9PSYsE0)

### Day 12: March 14, 2020

**Today's Progress**: Created a highlight that adjusts to the size of whatever has a anchor tag around itself. First step was creating a span element, adding the highlight class to the span and then appending that span to the body of the document. To trigger the dynamic highlighting of the current anchor tag under the mouse cureser event listeners where added to each a-tag. Each time the 'mouseenter' event was triggered a functions was called that got the bounding rectangle of the current element. The [Element.getBoundingClientRect()](https://developer.mozilla.org/en-US/docs/Web/API/Element/getBoundingClientRect) method returns the size of an element and its position relative to the viewport. I could use the position information to retrieve the width, height, top and left coords and set the highlights width, height and transform accordingly.

**Thoughts**: Yet again I used a web API. This time the most general of them all, the Element web API. The MDN web [docs](https://developer.mozilla.org/en-US/docs/Web/API/Element) state that the *Element is the most general base class from which all element objects (i.e. objects that represent elements) in a Document inherit. It only has methods and properties common to all kinds of elements*.

**Experimented with:** Experimented a lot with the css this time. Font size in the menu, width of the wrapper, the linear-gradient colors in the background and so on. Also added some [random text](https://www.blindtextgenerator.com/) instead of the lorem ipsum.

**Link(s) to work**: [Link highlighter](https://github.com/Organwolf/VanillaJS/tree/master/LinkHighlighter)

### Day 11: March 13, 2020

**Today's Progress**: A mixed bag of canvas drawing context, chart.js (in another project not added here), pixel manipulation in plain JS, using the video stream from my webcam, working with fetch to load csv data (in another project). This is part of Wesbos [JavaScript30](https://javascript30.com/) -> day 19

**Thoughts**: It turns out the term API is way broader then I initially thought. Today I used one without even knowing it at first. There are a lot of [web APIs](https://developer.mozilla.org/en-US/docs/Web/API). I used the [navigator](https://developer.mozilla.org/en-US/docs/Web/API/Navigator) web API to access the webcams [localMediaStream](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia).

**Experimented with:**

~~~~
const ctx = canvas.getContext('2d');
~~~~

Using the [setInterval](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval) function to draw a frame each 16ms.

~~~~
function paintToCanvas() {
    const width = video.videoWidth;
    const height = video.videoHeight;
    canvas.width = width;
    canvas.height = height;

    console.log(width, height);
    return setInterval(() => {
        // draw the image starting in the top left corner
        ctx.drawImage(video, 0, 0, width, height);
        // take pixels out
        let pixels = ctx.getImageData(0, 0, width, height);
        // add effect
        ctx.globalAlpha = 0.1;
        // pixels = redEffect(pixels);
        pixels = rgbSplit(pixels);
        // put pixels back
        ctx.putImageData(pixels, 0, 0);
    }, 16);
}
~~~~

**Link(s) to work**: [Webcam Photobooth](https://github.com/Organwolf/VanillaJS/tree/master/Webcam-PhotoBooth)

### Day 10: March 12, 2020

**Today's Progress**: Added a navbar to the site, used styled components to add color and a hover effect to the navbar, learnt more about the difference between [named export and default export in ES6](https://medium.com/@etherealm/named-export-vs-default-export-in-es6-affb483a0910). 

**Thoughts**: Html and JSX doesn't feel as unfamiliar any more. Reading documentation also seems to be more manageable. Once I've refactored the entire page to work with react-bootstrap and styled components I'll upload pictures.
 
**Experimented with:** git reflog and hard reseting to the previouse commit. Without knowing what would happen I tryed to pull down a branch I'd created on another computer. This lead to a local merge with the current branch I was on. Always nice when you manage to solve stuff like this. 

**Link(s) to work**: [Todo w navbar](https://github.com/Organwolf/ReactJS/tree/a1a3da343d1038179a1e61b9ad24599137980114)

### Day 9: March 11, 2020

**Today's Progress**: Added react-bootstrap to my app. I also threw in styled-components and some components from react-router-dom. 

**Thoughts**: I planned to replace the buttons, inputfield and change the font today. In retrospect that was a bit too much to hope for. 
Instead I managed to complete the setup from the routing and installed all of the appropriate packages. I also pushed the new code to it's own branch. I'll see if I can't complete this tomorrow.

**Experimented with:** Routing. If someone tries to access a route I havn't implemented I rerout to a NoMatch component.

**Link(s) to work**: [Todo with react-bootstrap](https://github.com/Organwolf/ReactJS/tree/react-bootstrap)

### Day 8: March 10, 2020

**Today's Progress**: Used the voice recognition that is built into Edge and Chrome to render a unicorn whenever the user says "unicorn". The site will register what the user says and display it one screen. The core functionalities are taken from JavaScript30 by Wesbos. This is day 20 "Speech Detection". 

**Thoughts**: If I'm not way of this is actually an API. At least is says so in the [documentation](https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition/SpeechRecognition). The browser compatability is quite limited. It doesn't work in my browser of choice which is Firefox. 

**Experimented with:** The idea of controlling something using ones voice. Now I just check if the user says 'Unicorn' but I'd like to expand this to an app that takes a picture once a user says say 'Take a picture'.

**Link(s) to work**: [Speach detection in the browser](https://github.com/Organwolf/VanillaJS/tree/master/SpeachRecognition)

### Day 7: March 9, 2020

**Today's Progress**: Learnt how to add pictures to my markdown as well as basic styling using css. Giving the buttons a *border-radius* did a lot. Changing the font also did a lot.

###### Todo app without css

<img src="https://github.com/Organwolf/ReactJS/blob/redux/images/todo-no-css.png" alt="without" width="400" height="400"/>

###### Todo app with css

<img src="https://github.com/Organwolf/ReactJS/blob/redux/images/todo-plain-css.png" alt="with" width="400" height="400"/>

**Thoughts**: CSS feels a bit more manageable. I try to encurage myself to try before being 100% what a certain peice of code does. Encouraging experimentation and exploration baby! :baby: 

**Experimented with:** CSS - *border-radius*, using a container class, using *display: block* to place elements on seperate lines, removing text-decoration as well as using *em* for font-size, padding and margin.

**Link(s) to work**: [Todo app plain css](https://github.com/Organwolf/ReactJS/tree/cc375aa561ddb746eec3ba8becbe7d496d988b68)

### Day 6: March 8, 2020

**Today's Progress**: Refactored my log. Reversed the order of log entries to make it easier for myself in the long run. Added a new feature to the todo app. You can now add notes about a completed chore.

**Thoughts**: I still get confused when it comes to redux. A lot of the concepts are still really new and I suspect that the loose typing is one of the reasons for confusion. 

**Experimented with:** How a user can add a note to a completed todo using react and redux

**Link(s) to work**: [Todo with notes](https://github.com/Organwolf/ReactJS/tree/2284186d6cc2b49373584046f9d000cec1b9eb19)

### Day 5: March 7, 2020

**Today's Progress**: Final refactoring of Todo.

**Thoughts**: I feel way more comfortable with the refactoring from 'regular' react code to react-redux code. The single source of truth etc. Tomorrow I'll start to add 
more functionality!

**Experimented with:** Naming the actions and action creators something else than CJ did in the videos. 

**Link(s) to work**: [Redux Refactored Todo](https://github.com/Organwolf/ReactJS/tree/db7e74f04aa8213caf7cc6d872b4087a652ff824)


**Link(s) to work**: No link today

### Day 4: March 6, 2020

**Today's Progress**: I have refactored more than half of the Todo app to work with Redux.

**Thoughts**: Redux is confusing. 

**Experimented with:** I have new ideas of addons I can do to this app. For example I'd like to add the opportunity to write a note once a chore is finished.

**Link(s) to work**: [Todo app with redux](https://github.com/Organwolf/ReactJS/tree/redux)

### Day 3: March 5, 2020

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

**Link(s) to work**: [TODO-list](https://github.com/Organwolf/VanillaJS/tree/master/TODO-list)

### Day 2: March 4, 2020

**Today's Progress**: By making this todoapp I got the opportunity to repeat some of ReactJS core concepts such as separating the data from the view components.

**Thoughts**: The app is far from beautiful. It litterally has minimal styling. All of the binding of functions can be a bit confusing. On the other hand this was
a good opportunity to practise. I could definitely revisit this and work on the visuals. Both with different css frameworks and plain css!

**Experimented with:** Removing the list style type on list elements by setting the list type style to none. I also experimented with different fonts
~~~~
font-family: sans-serif;
list-style-type: none;
~~~~

**Link(s) to work**: [Todo App](https://github.com/Organwolf/ReactJS/tree/master/intro-react)

### Day 1: March 3, 2020

**Today's Progress**: Made a TODO app in combination with localStorage so that the information persests even if you reload the page

**Thoughts**: Still working on wesbos JavaScript 30. Used event delegates in this one. I subscribe to the click event on the itemsList. Inside the function I determine which element I want to add logic to. 

**Experimented with:** SVG icons. Found an icon that fitted the theme. I actually had to fiddle around with the viewBox attribute to make the icon look ok.

~~~~
viewBox="-2.35 -0.5 23 23"
~~~~

### Day 0: March 2, 2020

**Today's Progress**: Learnt more about debouncing, window events, using scroll events in vanilla JS.

**Thoughts:** Had to debug my code for 10+ minutes because I had forgot the punctuation **.** while using querySelectorAll to select the elements of a certain class. 

~~~~
const sliderImages = document.querySelectorAll('.slide-in');
~~~~

Debouncing is problably the most advanced part of this code and from what I understand it enables me to trigger a particular function a fixed amount of times instead of it triggering unnecessarily often.

**Link to work:** [Slide in on scroll](https://github.com/Organwolf/VanillaJS/tree/master/SlideInOnScroll)