# 100 Days Of Code - Log

### Day 27: March 28, 2020
**Today's Progress**: Continued to revise my CountdownTimer code. Now I've added logic to my pause/start button.  

I wanted to:
 - [x] Show the button once the timer started ticking
 - [x] Give the button the same size as the previously added buttons
 - [x] Learn how to place two elements next to each other
 - [x] Be able to pause/resume the timer
 - [x] Count the hours
 - [x] Trigger a sound once the timer was done  

**Thoughts**: Not loving that I used a global variable to keep track of the remaining time but all in all I'm proud with the over all outcome. As mentioned previously it is way harder adding made up features than following someone else.

**Experimented with**: `text-shadow: 4px 4px 0 rgba(0,0,0,0.05); visibility: hidden; as well as the built in Audio API`

**Link(s) to work**: [Count down timer with added features](https://github.com/Organwolf/VanillaJS/tree/master/CountdownTimer)

### Day 26: March 28, 2020

**Today's Progress**: Moving away from tutorials and working on my own. Adding custom :hover and :focus effects via css as well as trying to add my own features to previously finished projects.

**Thoughts**: Worked more independently today. Didn't rely on any tutorial or blog post of any kind and it was hard! I will definitely have to focus more on how much time I spend programming rather than what I program. Atleast for the next 7 days. 

**Experimented with**: Hiding/displaying a button, pausing and restarting a setInterval that runs behind the scenes keeping track of time.

**Link(s) to work**: None today

### Day 25: March 27, 2020

**Today's Progress**: Worked with setting up virtualenvwrapper on my mac. Had problems with configurating the $PATH and had to create a ~/.profile for my zsh shell. Inside of the profile file I added the correct path to my python3 interpreter. 

**Thoughts**: It's a lot of work yet few lines of code when it comes to configuring stuff like this. I had to read multiple forum posts and guides. Patchworking my way towards a working solution. 

**Experimented with**: zsh interactive shell, touch, open, ~/.profile, virtualenvwrapper, docker-compose up, docker-compose down as well as testing http requests using postman.

**Link(s) to work**: None today

### Day 24: March 26, 2020

**Today's Progress**: Completed [Javascript30](https://javascript30.com/) today! :birthday:

**Thoughts**: I really feel like revisiting some of the vanilla js projects I've completed. I feel like I've leant a lot the past 3-4 weeks. It would be great to recap and also add new features to some projects. Repetition, experimentation and perseverance! 

**Experimented with**: WindowOrWorkerGlobalScope.setTimeout.setTimeout() which according to [MDN](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) is a method of the WindowOrWorkerGlobalScope mixin thats purpose is to start a timer and execute a function or specified piece of code once the timer expires.

**Link(s) to work**: [Whack A Mole](https://github.com/Organwolf/VanillaJS/tree/master/WhackAMole)

### Day 23: March 25, 2020

**Today's Progress**: Made an old fasioned timer. Actually I use timer quite a lot. It's great to break down tasks in 5 min parts as well as take regular breaks from whatever you're trying to solve/work on/learn. The timer has a couple of buttons for presets pause times as well as an input for any amount of minutes you'd like to enter. When I revise the work i've done while working with Javascript30 I will consider adding more functionality. For now I'm really glad with the result.

**Thoughts**: Came across yet another example of writing "if/else logic" with a ternary operator. Apparantly the ternary is the only JavaScript operator that takes three operands [source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator).  

```javascript
    // Intuitively I still want to solve if-else logic like this
    if(remainingSeconds < 10){
        const displaySeconds = '0' + `${remainingSeconds}`;
    }
    // However
    const display = `${minutes}:${remainingSeconds < 10 ? '0' : ''}${remainingSeconds}`;
    // Is arguably a more elegant solution
```

**Experimented with**:  
Template literals/template strings and terniery logic but also how to select all elements that share a certain attribute!  

```javascript 
const buttons = document.querySelectorAll('[data-time]'); 
```  

**Link(s) to work**: [Countdown thing](https://github.com/Organwolf/VanillaJS/tree/master/CountdownTimer)

### Day 22: March 24, 2020

**Today's Progress**: Worked with the playback rate of video together with a controller for the playback. The controller is a slider that is next to the video. When you hover over the controller the playback speed with increase or decrease depending on where the cursor is. Nothing ground breaking but still good repetition of css, html and vanilla js. 

**Thoughts**: For this exercise I started by going over both the css file and the html file before watching the video. It's easy to say that I should have done that from the very beginning with these exercises. Hindsight is 20/20 and all that. I would actually like to frame this differently when I think about it. It's more like this -> now that I've gained more confidence when it comes to css/html/js I'm ok with browsing the code before being told what it's about. Hey, that's exactly what I wanted to accomplish with these 100xCode.

**Experimented with**: toFixed() was new to me.  
```javascript
    const y = e.pageY - this.offsetTop;
    const percent = y / this.offsetHeight;
    const min = 0.5;
    const max = 4;
    const height = Math.round(percent * 100) + '%'
    bar.style.height = height;
    const playbackRate = percent * (max-min) + min;
    bar.textContent = playbackRate.toFixed(2) + 'x';
    video.playbackRate = playbackRate;
```

**Link(s) to work**: [Video speed controller](https://github.com/Organwolf/VanillaJS/tree/master/VideoSpeedController)

### Day 21: March 23, 2020

**Today's Progress**: Created "click and drag" functionality using vanilla javascript. I also delved deep into css while trying to style the images that are show to the user. I learnt how to fetch random images from unsplash as well.

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/chuttersnap-leaves.jpg" width="300" height="400"/>  
Photo by [chuttersnap](https://unsplash.com/@chuttersnap/) on [Unsplash](https://unsplash.com/).

**Thoughts**: I'm still a bit afraid of experimenting but today I experimented with css. Especially the aligning of particular object, resizing, attatching and detatching classes and the like. But it's still a bit confusing. I will most likely add a **styling** label to my goals. I feel like a need to learn more about styling in general. I will read through this [post](https://vanseodesign.com/css/vertical-centering/) tomorrow (or later). It should help me understand basic alignment using css.

**Experimented with**: css, unsplash images, adding and removing css classes using javascript and I also read up on virtual environments in Python. I will publish what I've learnt about that tomorrow.

**Link(s) to work**: [Drag and scroll](https://github.com/Organwolf/VanillaJS/tree/master/DragAndScroll)

### Day 20: March 22, 2020

**Today's Progress**: Finished PERN todo app which includes adding, editing and deleting todos. It has a RESTFUL api with crud functionality. The frontend is created w ReactJS and Bootstrap 4 for styling.

**Thoughts**: I will most likely be adding an additional feature to the app just to wrap my head around the app. Creating one or more columns in the database, one or more buttons to each todo or just working a little on the styling of the application. I actually got good use of [w3Schools Bootstrap 4 modal examples](https://www.w3schools.com/bootstrap4/bootstrap_modal.asp). I just had to replace the "class" attribute with "className" instead to adjust the code to ReactJS standards. I also used their table examples as guidelines.

**Experimented with**: Using the id of data from the backend as the id inside of the modal.

**Keywords/commands**:

> data-target={\`#id\${todo.todo_id}\`}, id = {\`id\${todo.todo_id}\`}, const editTodo = async (e) => {};, className="text-centered", className="d-flex", adding [] as the second argument to useEffect so it only triggers once.

**Link(s) to work**: [PERS stack todo app](https://github.com/Organwolf/ReactJS/tree/react-bootstrap/PERN-stack)

### Day 19: March 21, 2020

**Today's Progress**: Work with the PERN stack (Postgresql, Express, ReactJS, Node) following along [this tutorial](https://www.youtube.com/watch?v=ldYcgPKEZC8&list=PLDYvKtwxa9g39626F5PhHborthRAKaI6v&index=2&t=0s).

**Thoughts**: So this was it for the backend. Next up is the react front-end and I'll complete that tomorrow. I've completed some of the JavaScript, CSS and HTML stuff on [freeCodeCamp](https://www.freecodecamp.org/) before. This PERN turorial is something I found on freeCodeCamps youtube channel.

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/freecodecamp_logo.png" width="" height=""/>

**Experimented with**: The password needed to work with postgresq. I'd forgotten mine and tried all kind of hacks. I tried resetting the password following [this](https://dev.to/theoklitosbam7/how-to-reset-your-forgotten-password-in-postgresql-4a7g) dev article. Problem was I didn't know how to handle GNU nano. I also tried uninstalling -> reinstalling which didn't work. I reverted to trying to guess what my password was and managed to hack myself :sweat_smile:. I also experimented with adding requests in Postman to a collection dedicated to this PERN app.

**Keywords/commands**:  
`mkdir, npm init, npm i express pg cors, touch index.js,`  
`npm i -g nodemon, nodemon index, \l, \c, \dt, trycatch + tab,`  
`POST body raw JSON, (\$1), RETURNING \*, req.params, :id, psql -U postgres.`

**Link(s) to work**: [Work in progress](https://www.kindpng.com/imgv/JibJhR_sadcat-meme-memes-sad-cat-crying-cat-meme/)

### Day 18: March 20, 2020

**Today's Progress**: Worked with getBoundingClientRect again today. This time I used it to be able to find the coordinates of the rectangle around elements in dropdowns. I also worked with the offset of the nav element to make the code more flexible.

**Thoughts**: I feel like I'm more used to using template literals as well as adding eventlisteners using _forEach_. Definitely looking forward to wrapping up JavaScript30.

**Experimented with**: getBoundingClientRect as well as the dropdownbackground transition.

```css
transition: all 0.3s, opacity 0.1s, transform 0.2s;
```

**Link(s) to work**: [Stripe Follow Along Nav](https://github.com/Organwolf/VanillaJS/tree/master/StripeFollowAlongNav)

### Day 17: March 19, 2020

**Today's Progress**: A bit of a mixed bag today. I took a detour into the world of key/value pairs in JavaScript. Read a [post](https://stackoverflow.com/questions/1168807/how-can-i-add-a-key-value-pair-to-a-javascript-object) from 10 years ago about adding a key/value pair to a JS object. Also started working on day 26/30 of Wesbos JavaScript30.

**Thoughts**: I really liked the querySelector selecting something inside a class. At first I didn't really understad the syntax but after playing around with it a bit I was able to wrap my head around it.

```javascript
// Adds all list elements inside of the cool class to a nodeList called triggers
const triggers = document.querySelectorAll(".cool > li");
```

**Experimented with**: Query selecting elements inside a particular class, mouseenter and mouseleave events to trigger hover effects, adding and removing css classes to achive cool effects. In another project I experimented with redux and in particular how to change the state of input components depending on the value of other input components.

**Link(s) to work**: [Work in progress](https://www.kindpng.com/imgv/JibJhR_sadcat-meme-memes-sad-cat-crying-cat-meme/)

### Day 16: March 18, 2020

**Today's Progress**: Finished a video about APIs called [APIs for Beginners - How to use an API (Full Course)](https://www.youtube.com/watch?v=GZvSYJDk-us) by Craig Dennis. I've worked a little with flask, express, nodeJs and javascript completing 2 webapps I cloned from [Craig's github](https://github.com/craigsdennis/intro-to-apis-course/blob/master/course-notes.md). I had a look at the Spotify API and got the chance to admire their documentation. They even have a [web console](https://developer.spotify.com/console/) which enables you to do requests in the browser. I've also used Postman to do Http requests to the Twilio API. I also fixed a couple security alerts that I got from Github concerning depricated dependencies in an older VanillaJS project.

**Thoughts**: This has nothing to do with programming but I love the aestetics of [Glitch](https://glitch.com).  
Found this image of a dog on their page:

<br />
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/new%20stuff%20doggo%20glitch.png" alt="without" width="120" height="122"/>
<br />

**Experimented with/Links to todays work**:  
Javascript full stack complimentr app - [Glitch link](https://glitch.com/edit/#!/complimentr-javascript?path=README.md:1:0)  
Python/Javascript full stack complimentr app - [Glitch link](https://glitch.com/edit/#!/complimentr-javascript?path=README.md:1:0)  
A "scraper" that scrapes the table with the id "#main*table_countries" from \_Worldometers* [coronavirus data](https://www.worldometers.info/coronavirus/#countries) and then prints out the JSON data that was scraped. - [Github link](https://github.com/Organwolf/VanillaJS/tree/master/ScrapeTable)  
I've also used the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) together with temperature data from NASA and plotted the curve - [Github link](https://github.com/Organwolf/VanillaJS/tree/master/FetchCsv)

### Day 15: March 17, 2020

**Today's Progress**: Learnt more about event bubbling and event capturing as well as _once_ in the context of using event listeners. Also used _transform: scare( x )_ to create a subtle popping effect.

```css
/* the scale of the text while at the top of the page */
transform: scale(0.98);

/* the space of the text while you've scrolled down a bit */
transform: scale(1);
```

**Thoughts**: The stuff I learnt about event bubbling and capturing further drove home the point of the DOM being a graph. You traverse the graph/tree to modify content etc.

**Experimented with**: Google fonts as well as the custom background image used in the SpeechSynthesis web app.

**Link(s) to work**: [Sticky navigation bar](https://github.com/Organwolf/VanillaJS/tree/master/StickyNav)

### Day 14: March 16, 2020

**Today's Progress**: I personally really like the JavaScript below. First you fetch all of the elements with the type of _range_ or _text_ and store them in an _options_ array. Then a forEach is used on that options array adding an eventlistener to each of the elements. The eventlistener triggers on the _'change'_ event calling _setOption()_. _msg_ is an instance of _SpeechSynthesisUtterance_. `The SpeechSynthesisUtterance interface of the Web Speech API represents a speech request. It contains the content the speech service should read and information about how to read it (e.g. language, pitch and volume.)` Because the retrieved elements' name attributes are the same as the attributes on the msg object that we want to change it is possible to use the _this.name_. The _toggle()_ function then runs the speech service with the current text, pitch and range that the user has specified.

```javascript
const options = document.querySelectorAll('[type="range"], [name="text"]');

options.forEach(option => option.addEventListener("change", setOption));

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

**Thoughts**: Yet again I used a web API. This time the most general of them all, the Element web API. The MDN web [docs](https://developer.mozilla.org/en-US/docs/Web/API/Element) state that the _Element is the most general base class from which all element objects (i.e. objects that represent elements) in a Document inherit. It only has methods and properties common to all kinds of elements_.

**Experimented with:** Experimented a lot with the css this time. Font size in the menu, width of the wrapper, the linear-gradient colors in the background and so on. Also added some [random text](https://www.blindtextgenerator.com/) instead of the lorem ipsum.

**Link(s) to work**: [Link highlighter](https://github.com/Organwolf/VanillaJS/tree/master/LinkHighlighter)

### Day 11: March 13, 2020

**Today's Progress**: A mixed bag of canvas drawing context, chart.js (in another project not added here), pixel manipulation in plain JS, using the video stream from my webcam, working with fetch to load csv data (in another project). This is part of Wesbos [JavaScript30](https://javascript30.com/) -> day 19

**Thoughts**: It turns out the term API is way broader then I initially thought. Today I used one without even knowing it at first. There are a lot of [web APIs](https://developer.mozilla.org/en-US/docs/Web/API). I used the [navigator](https://developer.mozilla.org/en-US/docs/Web/API/Navigator) web API to access the webcams [localMediaStream](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia).

**Experimented with:**

```javascript
const ctx = canvas.getContext("2d");
```

Using the [setInterval](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval) function to draw a frame each 16ms.

```javascript
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
```

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

**Today's Progress**: Learnt how to add pictures to my markdown as well as basic styling using css. Giving the buttons a _border-radius_ did a lot. Changing the font also did a lot.

#### Todo app without css

<img src="https://github.com/Organwolf/ReactJS/blob/redux/images/todo-no-css.png" alt="without" width="500" height="500"/>

#### Todo app with css

<img src="https://github.com/Organwolf/ReactJS/blob/redux/images/todo-plain-css.png" alt="with" width="501" height="500"/>

**Thoughts**: CSS feels a bit more manageable. I try to encurage myself to try before being 100% what a certain peice of code does. Encouraging experimentation and exploration baby! :baby:

**Experimented with:** CSS - _border-radius_, using a container class, using _display: block_ to place elements on seperate lines, removing text-decoration as well as using _em_ for font-size, padding and margin.

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

```javascript
// 1 & 2 are equivalent to each other.

// 1
str.replace(/^(a |the |an )/i, "").trim();

// 2
str.replace(/the/gi, "");
str.replace(/an/gi, "");
str.replace(/a/gi, "");
str.trim();
```

```javascript
// 1 & 2 are equivalent to each other.

// 1
const sortedBands = bands.sort(function(a, b) {
  if (strip(a) > strip(b)) {
    return 1;
  } else {
    return -1;
  }
});

// 2
const sortedBands = bands.sort((a, b) => (strip(a) > strip(b) ? 1 : -1));
```

**Link(s) to work**: [TODO-list](https://github.com/Organwolf/VanillaJS/tree/master/TODO-list)

### Day 2: March 4, 2020

**Today's Progress**: By making this todoapp I got the opportunity to repeat some of ReactJS core concepts such as separating the data from the view components.

**Thoughts**: The app is far from beautiful. It litterally has minimal styling. All of the binding of functions can be a bit confusing. On the other hand this was
a good opportunity to practise. I could definitely revisit this and work on the visuals. Both with different css frameworks and plain css!

**Experimented with:** Removing the list style type on list elements by setting the list type style to none. I also experimented with different fonts

```css
font-family: sans-serif;
list-style-type: none;
```

**Link(s) to work**: [Todo App](https://github.com/Organwolf/ReactJS/tree/master/intro-react)

### Day 1: March 3, 2020

**Today's Progress**: Made a TODO app in combination with localStorage so that the information persests even if you reload the page

**Thoughts**: Still working on wesbos JavaScript 30. Used event delegates in this one. I subscribe to the click event on the itemsList. Inside the function I determine which element I want to add logic to.

**Experimented with:** SVG icons. Found an icon that fitted the theme. I actually had to fiddle around with the viewBox attribute to make the icon look ok.

```javascript
viewBox = "-2.35 -0.5 23 23";
```

### Day 0: March 2, 2020

**Today's Progress**: Learnt more about debouncing, window events, using scroll events in vanilla JS.

**Thoughts:** Had to debug my code for 10+ minutes because I had forgot the punctuation **.** while using querySelectorAll to select the elements of a certain class.

```javascript
const sliderImages = document.querySelectorAll(".slide-in");
```

Debouncing is problably the most advanced part of this code and from what I understand it enables me to trigger a particular function a fixed amount of times instead of it triggering unnecessarily often.

**Link to work:** [Slide in on scroll](https://github.com/Organwolf/VanillaJS/tree/master/SlideInOnScroll)


<!-- ### Day 22: March 24, 2020

**Today's Progress**:
**Thoughts**: 
**Experimented with**:
**Link(s) to work**: -->