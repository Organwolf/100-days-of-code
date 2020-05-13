# 100 Days Of Code - Log

Context API in short. First we create the context object, then we provide it, and finally we consume it.

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/context%20api.png" width="484" height="202">
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/context%20provide.png" width="422" height="95">
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/context%20consume.png" width="469" height="84">

### Day 71: May 12, 2020

**Today's Progress**: Getting a grip on fetching data asynchronous. Focusing on async/await, promises and to a small degree the axios library.

**Thoughts**: So whay is asyc/await? If we start with _asyc_ it can be placed before a function. The word _async_ before a function means that the function returns a promise. The second keyword, _await_, that works only inside async functions, makes JavaScript wait until that promise settles and returns its results.

**Experimented with**: async/await, promises and other stuff. According to the developer pages on [mozillas webpage](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise):

> The Promise object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/promise.png" height="285" width="545">

[source](https://javascript.info/promise-basics)

**Link(s) to work**: [async/await in Users component](https://github.com/Organwolf/advanced-react/tree/b9e3811029da50072a926e7fd6592392308ecd6b)

### Day 70: May 11, 2020

**Today's Progress**: Learnt how to use the _useEffect_ hook.

**Thoughts**: It's kind of strange learning front-end development because things change fast. Tutorials, blog and forum posts made two years ago are most likely outdated, at least to some extent. That has been the case for me when trying to learn React. I've read, and heard from others, that I shouldn't use the [lifecycle methods](https://reactjs.org/docs/state-and-lifecycle.html). Only if it was an emergency. I hadn't learnt how hooks worked either so I was kind of stuck between two ways of dealing with the lifecycle of a component not knowing how to use either one. Well, now I've been introduced to the _useEffect_ hook and below I've tried to demonstrate how it works.

**Experimented with**:

```javascript
import React, { useState, useEffect, Fragment } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);
  const [name, setName] = useState("");

  useEffect(() => {
    document.title = `${name} har clicked ${count} times`;

    return () => {
      console.log("cleanup");
    };
  }, [count, name]);

  return (
    <Fragment>
      <input type="text" onChange={(e) => setName(e.target.value)} />
      <div>
        {name} has clicked {count} times
      </div>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </Fragment>
  );
}
```

**useEffect** is triggered everytime a component _mounts_, _updates_ or _unmounts_. So each time a component is triggered, appears on screen or is changed in any way, a cycle occurs. What _useEffect_ replaces is the three lifecycle methods responsible for listening to the mounting, updating and unmounting of a component, namely _componentDidMount_, _componentDidUpdate_, _componentWillUnmount_. **useEffect** takes a function as its first parameter. Optionally one can add an array as a second parameter which specifies the dependencies. In the example above the function inside of useEffect only triggers when either count or name change. Additionally, if a return is added to the useEffect function that will be triggered during the unmounting cycle.

**Link(s) to work**: [Counter using useEffect](https://github.com/Organwolf/advanced-react)

### Day 69: May 10, 2020

**Today's Progress**: Learning more about hooks in React. Specifically useState and useEffect.

**Thoughts**: This has been a recap. I've sort of used hooks before. It just helps a lot to refresh and also relearn the core concepts.

**Experimented with**: Before 16.8 React separated stateful and stateless components. Class components were generally stateful, i.e could keep track of a local state, and functions were statless. Since 16.8 that changed with the introduction of hooks. What is a hook? According to the react documentation

> A Hook is a special function that lets you “hook into” React features. For example, useState is a Hook that lets you add React state to function components.

The most common hook provided by the React, _useState_, enables functional component to add stateful behaviour.

The reasons for adding hooks were many. Mainly it was due to the fact that classes add unwanted complexity to the code with wide use of the **this** keyword. Compared to using hooks class based components also require more boilerplate code which effects readability.

The documentation shows an example of creating a counter app using _useState_. I did the same to wrap my head around the concepts.

The useState can be set up like this:

```javascript
const array = useState(0);
const count = array[0]; // this.state.count
const setState = array[1]; // this.setState()
```

Refactored using array destructuring it looks even better:

```javascript
const [count, setState] = useState(0);
```

The **0** ins _useState(0)_ is just the initial value of count. It could be set to anything really.

**Link(s) to work**: [Counter using useState](https://github.com/Organwolf/advanced-react)

### Day 68: May 9, 2020

**Today's Progress**: Worked with HOC (higher-order components) and did a recap on some basic git.

**Thoughts**: I'm glad that I took the time to recap how to connect a local repo to github. For some reason I feel like I should know that by heart. Thoughts/feelings like that hinder me more than help me. I'm also glad that I took the time to learn more about HOCs. Read through the [react documentation](https://reactjs.org/docs/higher-order-components.html) but didn't delve deep into their examples as they still use lifecycle hooks. I'm trying to avoid using lifecycle hooks if I can.

**Experimented with**: Higher-Order Components (HOC) - A design pattern which enforces DRY (don't repeat yourself). It is more or less a wrapper. A HOC takes a component as an argument and returns a component. Usually it adds some data to the component. I've created an example where a tooltip is added by using a HOC. Check it out. A HOC is a type of heigher-order function. A function that accepts and/or returns another function is called a higher-order function.
[map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) and [filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) are higher-order functions because they take a **callback** function as an argument.

`A Higher Order Component (HOC) is a function that takes a component and returns a component.`

I also experimented with pushing a local git repository to github

> git init.  
>  git add .  
>  git commit -m "first commit"  
>  git remote add origin "remote repository URL"  
>  git push origin master.

**Link(s) to work**: [Simple HOC example](https://github.com/Organwolf/advanced-react)

### Day 67: May 8, 2020

**Today's Progress**: Deployment to Heroku and using their continuous integration. Problem solving on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) as well as setting up and reading the database connection string from a Heroku environment variable.

**Thoughts**: Honest, I should hate trying to solve the breaking updates that have been made since this guy made his tutorial but I actually find it ok. It's really pleasing when you manage to find your way to where you need to go (sort of on your own).

**Experimented with**: Continuous integration with heroku by commiting my changes locally then push it to the heroku, which in turn builds the latest source code, and (assuming that it is runnable) shows it at an address provided by Heroku.

Some commands worth remembering:  
`heroku create`  
`git push heroku master`  
`heroku open`  
`heroku logs`

**Link(s) to work**: None today

### Day 66: May 7, 2020

**Today's Progress**: Registering and setting up environments on [Heroku](www.heroku.com) and [mLab](https://mlab.com/).

**Thoughts**: For some reason my email adress is in use on mLab but I have no memory of hearing about mLab before let along registering. Had to use another email to register

**Experimented with**: Setting up the necesary environment to deploy my react app to the cloud. Deployment and getting an optimized production build using `npm run build`. If I'd want to test my app in the future I can to this with `npm test`which uses test environment variables. I also installed the heroku CLI `brew tap heroku/brew && brew install heroku` and double checked that it was installed with `heroku -v` as well as logged in via the command line using `heroku login`.

**Link(s) to work**: None today

### Day 65: May 6, 2020

**Today's Progress**: Wrote a guide for building Unity 2018 projects to iOS and verified that my guide works on my iPhone.

**Thoughts**: I've been putting this off for ages so it feels amazing to actually get it out of the way.

**Experimented with**: Xcode, Unity 2018.4.22f1, my patience and various preference settings.

**Link(s) to work**: [Build Guide](https://github.com/Organwolf/100-days-of-code/blob/master/text/Building%20to%20iOS%20in%20Unity%202018.txt)

### Day 64: March 5, 2020

**Today's Progress**: Started using environment variables in React, finished the article on composition vs inheritance, started reading an article about [5 React Best Practices To Learn In 2020](https://programmingwithmosh.com/react/5-react-best-practices-to-learn-in-2020/) and drank two cups of tea.

**Thoughts**: Although I've been pouring hours into react I still feel like I'm late to the party. Not being up to date with how hooks work, PropTypes, using higher order functions and the like. Truth is, or at least I hope this is the truth, I'm laying the groundwork for deeper understanding of programming further down the line. Sometimes you can't see the forest for the trees. Learning in itself has inherit value.

**Experimented with**: Thinking in react by following [this](https://reactjs.org/docs/thinking-in-react.html). I also set some environment variable in `.env.development` by prefixing them with `REACT_APP_`. Ending up with something like this

`REACT_APP_NAME=Vidly in Dev`  
`REACT_APP_VERSION=1`

I also restricted the removal of movies to admins of the vidly app.

**Link(s) to work**: [Vidly](https://github.com/Organwolf/ReactJS/tree/react-bootstrap/vidly)

### Day 63: May 4, 2020

**Today's Progress**: Started reading about _Composition vs Inheritancs_ in an effort to be able to create re-usable components in react. I also completed the pokemon hooks app as well as fixed two bugs left by the developer that wrote the tutorial.

**Thoughts**: Still just wrapping my head around the concepts but some of it is pretty straight forward.

**Experimented with**: [This](https://codepen.io/gaearon/pen/ozqNOV?editors=0010) codepen on [reactjs.org](https://reactjs.org/docs/composition-vs-inheritance.html) that is used to explain how you can create a general functional component without knowing the exact type of props that will be passed to it. Esentially you can create a container component such as _FancyBorder_ below and assume that the children passed to is will want to be passed directly to its output.

```javascript
function FancyBorder(props) {
  return (
    <div className={"FancyBorder FancyBorder-" + props.color}>
      {props.children}
    </div>
  );
}
```

This lets other components pass arbitrary children to them by nesting the JSX:

```javascript
function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">Welcome</h1>
      <p className="Dialog-message">Thank you for visiting our spacecraft!</p>
    </FancyBorder>
  );
}
```

<hr />

As for the pokemon app I solved an issue caused by the useEffect's dependency array. I read a little about it in [this](https://medium.com/better-programming/understanding-the-useeffect-dependency-array-2913da504c44) medium post. I don't get everything though but previouse to the bug fix the app kept rendering infinitely.

**Link(s) to work**: [Pokemon context hook app](https://github.com/Organwolf/ReactJS/tree/hooks/pokemon)

### Day 62: May 3, 2020

**Today's Progress**: Worked with the context API for the first time.

**Thoughts**: Fairly straightforward. After working with Redux all sorts of "global" state handlers in react feel manageble. However, I'd like to learn more about [component composition](https://reactjs.org/docs/composition-vs-inheritance.html) and [thinking in React](https://reactjs.org/docs/thinking-in-react.html). I plan on reading up on these topics as well as refactoring my todo-app to use hooks instead of Redux.

**Experimented with**: Adding and removing objects from a **Provider** which looks like this:

```javascript
import React, { createContext, useState } from "react";

export const PokemonContext = createContext();

export const PokemonProvider = (props) => {
  const [pokemons, setPokemons] = useState([
    { id: 1, name: "Bulbasaur" },
    { id: 2, name: "Charmander" },
    { id: 3, name: "Squirtle" },
  ]);

  const [capturedPokemons, setCapturedPokemons] = useState([]);

  const providerValue = {
    pokemons,
    setPokemons,
    capturedPokemons,
    setCapturedPokemons,
  };

  return (
    <PokemonContext.Provider value={providerValue}>
      {props.children}
    </PokemonContext.Provider>
  );
};
```

This provider _provides_ other components with data and functions to manipulate/use that data. The current four provider values give components access to the _current pokemons_, the ability to _manipulate_ the array of pokemons, a list of _captured pokemons_ and yet another functions that allows the component to _set captured pokemons_.

**Link(s) to work**: [Pokemon thing using the context API](https://github.com/Organwolf/ReactJS/tree/hooks/pokemon)

### Day 61: May 2, 2020

**Today's Progress**: Worked with the **Route** component from react-router-dom and moreover I added some functionality to my zsh terminal.

**Thoughts**: I actually feel more comfortable with Routes. I'd used them before in other projects. I'd even used/created/copied from StackOverflow some ProtectedRoute code similar to the code I wrote today. Difference is that I understand (most) of what I'm doing now.

**Experimented with**: Worked with protected routes as well as basic authentication. At first the logic for checking if the user was logged in or not was done in the **App.js** directory. By replacing the **component** with a **render** function this could be accomplished.

Before

```javascript
<Route path="/movies/:id" component={Logout}></Route>
```

After

```javascript
<Route
  path="/movies/:id"
  render={(props) => {
    if (!user) return <Redirect to="/login" />;
    return <MovieForm {...props} />;
  }}
></Route>
```

Further, to make this a reusable component I made it more general. I created a protectedRoute component in my common folder which holds all reusables. Then I extract the **path** from **props** as well as the component to render if the user is logged in. The **render** method is also passed to the protected route as a safeguard if the component is null. **rest** is also passed to ensure that the rest of the properies (if any) are passed along.

```javascript
const ProtectedRoute = ({ path, component: Component, render, ...rest }) => {
  return (
    <Route
      path={path}
      {...rest}
      render={(props) => {
        if (!auth.getCurrentUser) return <Redirect to="/login" />;
        return Component ? <Component {...props} /> : render(props);
      }}
    ></Route>
  );
};
```

You could go further and remove the **path={path}** because the **{...rest}** would actually solve that for us. However, for readabilities sake I chose to keep it as is.

In **App.js** it ended up looking like this when all was said and done.

```javascript
<ProtectedRoute path="/movies/:id" component={MovieForm} />
```

<hr>

As for the configuration of my zsh terminal I did the following:

- opened the config file with vim
- added unsetopt share_history
- saved the changes
  Funny thing is i had to read one of my previouse log posts from day 28 about how to edit the config file. I'm not that used to **vim** either. I accessed the config file by typing `vi ~/. zshrc`, then pressed **i** to to insert new stuff into the file, then hit **esc** followed by typing `:wp` to save and quit vim.

Read these two resources ([1](https://github.com/ohmyzsh/ohmyzsh/issues/2537), [2](https://medium.com/@smile2gether/how-to-customize-your-mac-os-terminal-880c4097b18b)) to solve my zsh problems.

**Link(s) to work**: [Vidly](https://github.com/Organwolf/ReactJS/tree/react-bootstrap/vidly)

### Day 60: May 1, 2020

**Today's Progress**: Yet anohter day solely focused on refactoring. Ok, I didn't just refactor my code, I searched the web for ways to determine if an object is a string or not in JS, as well as worked with JWT (JSON Web Tokens).

**Thoughts**: [This](https://jwt.io/) site helped me understand the different parts of a JWT. You can copy a JWT and paste it into their decypherer. That was helpful. I also appreciate working with refactoring. DRY (don't repeat yourself) is easy to understand but takes tons of practise to master. Todays refactoring focused on moving all of the code that dealt with the JWT token to one place called authService. authService in turn contains a couple of constants, that keep track of the api endpoint as well as the name of the token, and functions that deal with login/loginWithJwt/logout/getCurrentUser. I'm not at the point where this kind of achitecture feels "natural" but at least I'm moving away from putting everything in one big file.

**Experimented with**: Localstorage to store the JWT. I also worked with the axios library to set the x-auth-token header for all http requests which looks like this:

```javascript
axios.defaults.headers.common["x-auth-token"] = auth.getJwt();
```

I also learnt that this was bad because it creates a bi-directional dependency. Apparently they are bad, and I leant how to solve them.

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/bi1.png" width="450" height="210">
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/bi2.png" width="450" height="210">
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/bi3.png" width="450" height="210">

As the images show both the httpService and the authService are dependent on each other. One way to solve this is to set the token from the authService. And _voila_ that removes https dependency to the authService.

The code looks something like this:

```javascript
// authService
http.setJwt(getJwt());

export function getJwt() {
  return localStorage.getItem(tokenKey);
}

// httpService
function setJwt(jwt) {
  axios.defaults.headers.common["x-auth-token"] = jwt;
}
```

**Link(s) to work**: [Vidly](https://github.com/Organwolf/ReactJS/tree/40fc6d9236e8bf210dcf4fa806f3d43e21959b30/vidly)

### Day 59: April 30, 2020

**Today's Progress**: Worked with finding/editing/removing key-value pairs in objects. I also started working on the registration of the Vidly app.

**Thoughts**: I really want to understand the error handling. It was interesting to learn that _hasOwnProperty_ was the better option of the two below because it doesn't look through the entile prototype chain.

**Experimented with**:

`if ('key' in myObj)`  
searches the whole prototype chain.

`myObj.hasOwnProperty('key')`  
check an object's own keys and will only return true if key is available on myObj directly [source](https://stackoverflow.com/questions/455338/how-do-i-check-if-an-object-has-a-key-in-javascript).

```javascript
register = async () => {
  try {
    await userService.register(this.state.data);
  } catch (ex) {
    if (ex.response && ex.response.status === 400) {
      const errors = { ...this.state.errors };
      errors.username = ex.response.data;
      this.setState({ errors });
    }
  }
};
```

Error handling while registering a user.

**Link(s) to work**: [Vidly w registration](https://github.com/Organwolf/ReactJS/tree/8fcbcaf4e12aff8401e84189be7e95888553a464)

### Day 58: April 29, 2020

**Today's Progress**: Started using git stash, used mongodb together with react, moved the api url used for API requests into a config.json file and watched [The art of code](https://www.youtube.com/watch?v=6avJHaC3C2U), a talk given by Dylan Beattie at NDC 2020.

**Thoughts**: I am really glad that I tried using git stash. I also managed to find a way to compare the stash towards a commit which is useful if something has gone wrong and you want to check what you've changed sense the last working commit! I solved a problem I had using git stash, the internet and some patience! <3

**Experimented with**:

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/git_stash.png" width="290" height="174">

`git stash`  
`git diff stash@{0} master`  
`git stash pop`

**Usefull Link(s)**:  
https://www.quora.com/My-Git-is-stashed-How-do-I-unstash-it-and-access-my-original-project  
https://stackoverflow.com/questions/7677736/git-diff-against-a-stash

### Day 57: April 28, 2020

**Today's Progress**: Installed mongoDB, firgured out how to add backticks inside of a code block in markdown, worked with some CS fundamentals such as how to loop though objects in JS as well as check if an object is an array.

**Thoughts**: Today I spent my time installing mongodb on macOS Catalina. It was surprisingly hard for me to do this. Partly due to the fact that macOS [Catalina](https://support.apple.com/en-us/HT210650) runs in a read-only system volume, separate from other files on my mac.
[This](https://zellwk.com/blog/install-mongodb/) article saved the day. By adding double backticks `` before and after a code block I was able to add backticks inside of the code block.

**Experimented with**:

`sudo mkdir -p /System/Volumes/Data/data/db`  
`` sudo chown -R `id -un` /System/Volumes/Data/data/db ``  
`brew services run mongodb-community`  
`brew services list`

```javascript
// Check if adn object is an array
Array.isArray(obj)

// Delete a key value pair from and object
delete errors[action.id];

// Loop through and object
Object.keys(data).forEach((item) => {
  // data[item] is the value
  // item is the key
}
```

**Link(s) to resources**:

[Loop through objects](https://gomakethings.com/the-es6-way-to-loop-through-objects-with-vanilla-javascript/)  
[Check if object is an array](https://stackoverflow.com/questions/4775722/how-to-check-if-an-object-is-an-array)

### Day 56: April 27, 2020

**Today's Progress**: Added toast messages to my application

**Thoughts**: I've heard that you should keep the dependencies to a minimum. So I'm not sure where you should draw the line. I could make my own toast messages. Then again I don't want to re-invent the wheel.

**Experimented with**: npm react-toastify

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/toastify.png" width="365" height="162">

**Link(s) to work**: [http-app w toast messages](https://github.com/Organwolf/ReactJS/tree/5023cf1c2c72ee854fbca155dd2125609b9e7d50)

### Day 55: April 26, 2020

**Today's Progress**: Error handling and some refactoring of axios error handling.

**Thoughts**: Encountered CORS again today. Can't say that I'm totaly comfortable with it at this point. I'll have to read or watch a video about it. At least I sort of know what it is know. I like the refactoring that I'm learning. It's good stuff!

**Experimented with**:
So I'm working on CRUD operations and wanted to add error handling. Apparently you can roughly divide errors into expected and unexpected errors. In my case an expected error is a 404: not found or a 400: bad request. Everything else, from network/server/database errors fall into the unexpected category.

```javascript
handleDelete = async post => {
  const originalPosts = this.state.posts;

  const posts = this.state.posts.filter(p => p.id !== post.id);
  this.setState({ posts });

  try {
    await axios.delete('s' + apiEndpoint + '/999' + post.id);
  } catch (ex) {
    console.log('HANDLE DELETE CATCH BLOCK');
    if (ex.response && ex.response.status === 404)
      alert('This post has already been deleted');
    else {
      console.log('Logging the error', ex);
      alert('An unexpected error occurred');
    }

    this.setState({ posts: originalPosts });
  }
```

All unexpected errors are "logged" do allow the delevoper(s) to understand what happened or didnt' happen while the error occurred. With some refactoring the code can be moved outside of the handler and made more general. By doing so it can handle/intercept requests and responses and check for errors globally.

```javascript
axios.interceptors.response.use(null, (error) => {
  const expectedError =
    error.response &&
    error.response.status >= 400 &&
    error.response.status < 500;

  if (!expectedError) {
    console.log("Logging the error", error);
    alert("An unexpected error occurred");
  }

  return Promise.reject(error);
});
```

Refactoring this even further I moved the _axios.interceptors_ into it's own service module which ended up looking like this:

```javascript
import axios from "axios";

axios.interceptors.response.use(null, (error) => {
  const expectedError =
    error.response &&
    error.response.status >= 400 &&
    error.response.status < 500;

  if (!expectedError) {
    console.log("Logging the error", error);
    alert("An unexpected error occurred");
  }

  return Promise.reject(error);
});

export default {
  get: axios.get,
  post: axios.post,
  put: axios.put,
  delete: axios.delete,
};
```

By exporting an object that is mapped to what axios object looks like we can access its methods outside of the module. Working in this way it is easy to switch axios for another promise-based HTTP client without having to change too much code in the process!

**Link(s) to work**: [http-app simple CRUD in JS](https://github.com/Organwolf/ReactJS/tree/react-bootstrap/http-app)

### Day 54: April 25, 2020

**Today's Progress**: Read about CORS and worked on search functionality in my Vidly app. I also started looking at making API requests to endpoints outside of my application. More specifically I also learnt how to throw an error within a try catch block to test my error handling.

**Thoughts**: I really appriciate learning more about async and await. I use fetch a lot and in this project axios takes that APIs place. It's always interesting to learn more about similar tools and how they tackle stuff. I learnt about optimistic (and pesimistic updates). I tried using optimistic updates in the app I'm currently working on and it really does give the illusion of the app being faster than it actually is.

**Experimented with**: Web contents _origin_ in the context on CORS is defined by the _scheme_ (protocol), _host_ (domain), and _port_ of the URL used to access it.

_http_ and _https_ are are examples of different protocols  
_example.com_ and _otherexample.se_ are examples of different domains  
and numbers like _:8080_ att the end of a domain specifies the port.

On Cross-Origin Resource Sharing (CORS) Mozillas developer pages say the following:

> For security reasons, browsers restrict cross-origin HTTP requests initiated from scripts. For example, XMLHttpRequest and the Fetch API follow the same-origin policy. This means that a web application using those APIs can only request resources from the same origin the application was loaded from, unless the response from other origins includes the right CORS headers.
> [source](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

A promise is an object that holds the result of an asynchronous operation.  
It can either resolve (which leads to a success) OR be rejected (which lead to a failure).

According to the resources I'm following the _then()_ is the old way of working with async operations.  
Below is an example of the "new" way of dealing with async stuff.

```javascript
const response = await axios.get("https://jsonplaceholder.typicode.com/posts");
```

Example of testing the error handling while doing an async call in my app:

```javascript
handleDelete = async (post) => {
  const originalPosts = this.state.posts;

  const posts = this.state.posts.filter((p) => p.id !== post.id);
  this.setState({ posts });

  try {
    await axios.delete(apiEndpoint + "/" + post.id);
    throw new Error("");
  } catch (ex) {
    alert("Failed man failed");
    this.setState({ posts: originalPosts });
  }
};
```

**Link(s) to work**: None today

### Day 53: April 24, 2020

**Today's Progress**: General refactoring as well as refactoring of the validation into its own re-usable class component called Form which loginForm, movieForm and registerForm now extend. I added a generalized dropdown component to the project called _select_, used {...rest} for the first time and read and wrote about immutability.

**Thoughts**: Used a Link element instead of a regular button. Not sure if that is bad practise or not. I'm still not comfortable with using `this.props.history` and `this.props.match` which are props "injecten" into the component that is passed through a Route. I really like the `mapToViewModel(movie)` which is triggered inside of movieForm.jsx if the user has clicked on the hyperlink for a movie. It's pretty "simple", the way that is uses setState to populate the 4 different fields in the movieForm component, but I still like it.

**Experimented with**:
Immutability in react:
keywords: immutability, pure functions, side effects and referential equality in JS

Immutability is the opposite of _mutable_ which means _changeable_.
A pure function must follow two rules:

> It must always return the same value when given the same inputs
> It can't contain/create any side effects

A side effect occurs when modifying things outside the scope of that immediate function. Some examples of side effects include using console.log() or running API calls inside a function.

React prefers immutability
For react to notice the changes, and by doing so re-rendeing the component, the state must change. It appears that mutable changes to the same object, although assigned to a new object with another name, will be referentially equal and nor trigger a re-rendering.

Referential equality works like this

```javascript
// This creates a variable, `crayon`, that points to a box (unnamed),
// which holds the object `{ color: 'red' }`
let crayon = { color: "red" };

// Changing a property of `crayon` does NOT change the box it points to
crayon.color = "blue";

// Assigning an object or array to another variable merely points
// that new variable at the old variable's box in memory
let crayon2 = crayon;
console.log(crayon2 === crayon); // true. both point to the same box.

// Niw, any further changes to `crayon2` will also affect `crayon1`
crayon2.color = "green";
console.log(crayon.color); // changed to green!
console.log(crayon2.color); // also green!

// ...because these two variables refer to the same object in memory
console.log(crayon2 === crayon);
```

The reason referential equality is used instead of checking equality deeply (traversing through the entire object) is largly due to performance gains from using referential equality. Reference equality checks take constant time O(1).

For further reading on this topic I recommend checking out thi [article about immutability in React and Redux](https://daveceddia.com/react-redux-immutability-guide/).

**Link(s) to work**: [Vidly app](https://github.com/Organwolf/ReactJS/tree/1f8c1429fdee362819386a81a1dbbc6cf217d994)

### Day 52: April 23, 2020

**Today's Progress**: Refactoring, form validation, computed properties and custom css for bootstrap.

**Thoughts**: When I take the time to look at what I'm working with I notice that something has happened over the past month or so. I'm not sure if it's the continuity, the coding a little every day, or if it's something else. I can sense the progress I'm making. I'd like to take a closer look at git and get more familiar with merging branches, creating and resolving pull requests, stashing data and so on. Right now I don't feel like I have the time.

**Experimented with**:  
adding `.DS_Store` to my gitignore. It always feels powerful when I can make improvements to my git workflow.

cmd + b toggles the explorer in vscode (mac). I'll be using that a lot moving forward.

[oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Cheatsheet) literalliy has tons of aliases for git out of the box today I found this alias `ggp` which pushes the commit to the current branch.

I also modified the gutters between bootstrap columns using custom css:

```css
.custom-gutter > [class*="col-"] {
  padding-right: 8px;
  padding-left: 8px;
}

.custom-gutter > [class*="col-"]:first-child {
  padding-left: 16px;
}

.custom-gutter > [class*="col-"]:last-child {
  padding-right: 16px;
}
```

and worked with ES6 Computed Property Names while working on form validation in react.  
Where \[name\] is the computed property in the code below.

```javascript
handleChange = (event) => {
  const { name, value } = event.target;
  this.setState({ [name]: value });
};
```

**Link(s) to work**: [Vidly app](https://github.com/Organwolf/ReactJS/tree/34b60b890d3a2888d643328c3e6363f3ac58a04c)

### Day 51: April 22, 2020

**Today's Progress**: Refactoring, working with forms in React as well as pimple validation.

**Thoughts**: Have had som problems with gulp and building my projects today. Going to ask a friend about it tomorrow.

**Experimented with**:

Select text/code, press cmd + shift + P and search for wrap, then type what you want to wrap the selected peice of text/code with. Zen coding can be used here as well.

Vanilla JS

```javascript
const username = document.getElementById("username").value;
```

The whole point of React is to abstract away the DOM. Which makes react apps easier to maintan and unit test. But how do you access the DOM in React? You use Refs

```javascript
// Creating the Ref
username = React.createRef();

// Accessing the Ref
const username = this.username.current.value;

//Assigning the Ref
<input
  ref={this.username}
  id="username"
  type="text"
  className="form-control"
/>;
```

But Refs should not be overused. In the case of forms it is usually good to use controlled components. Controlled components don't have their own state. They get all their data via props and they notify changes to the data by raising events.

A handler in such a situation could look like this:

```javascript
handleChange = (e) => {
  const account = { ...this.state.account };
  account[e.currentTarget.name] = e.currentTarget.value;
  this.setState({ account });
};
```

And with some destructuring it looks like this:

```javascript
handleChange = ({ currentTarget: input }) => {
  const account = { ...this.state.account };
  account[input.name] = input.value;
  this.setState({ account });
};
```

I really like destructuring when used like that. It does a lot for the readability.

Today I also build a simple validation function. Inside that function the return looks like this:

```javascript
return Object.keys(errors).length === 0 ? null : errors;
```

Which means, if the errors object has zero keys return null. In other words there are no errors. Else the errors object is returnd from the validation function.

**Link(s) to work**: None today

### Day 50: April 21, 2020

**Today's Progress**: Routing and refactoring in React.

**Thoughts**: I really liked todays coding. If anything, this is what I need right now. I want and need to learn more about structure, reusability and general skills that have to do with webapps.

**Experimented with**:

**Routing**

A regular Route might look something like this

```javascript
<Route path="/products" component={Products} />
```

However, if I'd want to pass any props along with the Product component I'd have to do this:

```javascript
<Route
  path="/products"
  component={(props) => <Products sortBy="newest" {...props} />}
/>
```

the passing of props into the arrow function and the spreading of props `{...props}` passes the history, location and match properties to the Products component.

**Refactoring**

```javascript
const filtered =
  selectedGenre && selectedGenre._id
    ? allMovies.filter((m) => m.genre._id === selectedGenre._id)
    : allMovies;

const sorted = _.orderBy(filtered, [sortColumn.path], [sortColumn.order]);

const movies = paginate(sorted, currentPage, pageSize);
```

`filtered.length` and `movies`are both used in other parts of the component.  
This has to be taken into consideration when refactoring it into a new method

```javascript
getPageData = () => {
  const filtered =
    selectedGenre && selectedGenre._id
      ? allMovies.filter((m) => m.genre._id === selectedGenre._id)
      : allMovies;

  const sorted = _.orderBy(filtered, [sortColumn.path], [sortColumn.order]);

  const movies = paginate(sorted, currentPage, pageSize);

  return { totalCount: filtered.length, data: movies };
};
```

**Link(s) to work**: No links but check the code above if you'd like

### Day 49: April 20, 2020

**Today's Progress**: Generalizing components in React.

**Thoughts**: It's complicated but fun. When I solve stuff at work I start by trying to get things to work. Learning to generalize components usually work the other way around. You have some functionality you want to be able to reuse.

**Experimented with**: Lodash, specifically [\_.get(object, path, \[defaultValue\])](https://lodash.com/docs/#get).

```javascript
import React, { Component } from "react";
import _ from "lodash";

class TableBody extends Component {
  renderCell = (item, column) => {
    if (column.content) return column.content(item);

    return _.get(item, column.path);
  };

  createKey = (item, column) => {
    return item._id + (column.path || column.key);
  };

  render() {
    const { data, columns } = this.props;
    return (
      <tbody>
        {data.map((item) => (
          <tr key={item._id}>
            {columns.map((column) => (
              <td key={this.createKey(item, column)}>
                {this.renderCell(item, column)}
              </td>
            ))}
          </tr>
        ))}
      </tbody>
    );
  }
}

export default TableBody;
```

The above code functions a bit like a for loop in a for loop.  
The below code enables me to reach nested data inside of **item**.  
**renderCell** renders either moviedata, a like or a delete button.  
**createKey**, as the name implies, creates a unique key for each cell.

```javascript
<td>{_.get(item, column.path)}</td>
```

**Link(s) to work**: [Vidly w generalized table header and table body](https://github.com/Organwolf/ReactJS/tree/a5c565d649369c4fa989ef7cbb0450cfe0b44003/vidly)

### Day 48: April 19, 2020

**Today's Progress**: Stateless functional components in React.

**Thoughts**: I re-arranged and reworked this component

```javascript
import React from "react";

const ListGroup = (props) => {
  const { items } = props;

  return (
    <ul className="list-group">
      {items.map((item) => (
        <li key={item._id} className="list-group-item">
          {item.name}
        </li>
      ))}
    </ul>
  );
};

export default ListGroup;
```

to become more general

```javascript
import React from "react";

const ListGroup = (props) => {
  const { items, textProperty, valueProperty } = props;

  return (
    <ul className="list-group">
      {items.map((item) => (
        <li key={item[valueProperty]} className="list-group-item">
          {item[textProperty]}
        </li>
      ))}
    </ul>
  );
};

export default ListGroup;
```

by forcing the programmer to pass the valueProperty and textProperty as props instead of assuming that
`_id` or `name` exist. Although the changes are minimal codewise the code has become way more re-usable!

**Experimented with**:  
Worked more with stateless functional components in React. Specifically how one can make them as general as possible.

**Link(s) to work**: [Vidly commit with changes in listGroup component](https://github.com/Organwolf/ReactJS/tree/82e1bf4c490d12a935a9692bda5789fe11f83332/vidly)
https://gist.github.com/rxaviers/7360908

### Day 47: April 18, 2020

**Today's Progress**: I've worked more with react today. Thinking more about how a component should be used before implementing it. Worked a little on the Vidly apps filter by genre functionality as well.

**Thoughts**: It's good for me ti focus on the interface of components, what events they might raise and what they might or might not output before I start to code.

**Experimented with**:

Some shortcuts

```
div.col-2+div.col
```

with a simple tab turns into

```html
<div className="col-2"></div>
<div className="col"></div>
```

I also found this cool sight which displays different easing  
functions rate of change. It can be really helpful when writing  
custom animations in css. By modifying the [animation-timing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function)  
you can achieve different easing styles.

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/easOut-easIn.png" width="435" height="450">

**Link(s) to work**: None today

### Day 46: April 17, 2020

**Today's Progress**: I mainly made progress with css but I also touched on [PropTypes](https://reactjs.org/docs/typechecking-with-proptypes.html) and how it can be added to components to require certain data as input. I also learnt about `python -m SimpleHTTPServer`  
which, as the name applies, is a [simple server](https://docs.python.org/2/library/simplehttpserver.html) that serves files from the current directory and below, directly mapping the directory structure to HTTP requests.

**Experimented with**: The lodash library, css wildcard selectors, animation, SimpleHTTPServer and PropTypes in reactjs.

**Thoughts**:
Worked with the wildcard selector **\*** in css. Wildcard selectors are used to select multiple elements simultaniously.  
The **>** in the css below means _select all of what is to the right of **\>** within what is to the left of **\>**._

```css
/* 1 */
hp-chooser.chosen > *.chosen {
  max-width: 30%;
}

/* 2 */
hp-chooser.chosen > *:not(.chosen) {
  max-width: 16.6%;
}
```

The second peice of css applies a max-width of 16.6% to all elements within the hp-chooser with a class of chosen that don't have the class of chosen. A mouthful I know. If I'd seen this css a couple of weeks back I would have shut down. Today it feel manageble and I'm greatful for that.

I also learnt some best practices while working with css such as the css shown below. It allows the body to take up the entire area of the available screen.

```css
html,
body {
  margin: 0;
  padding: 0;
}
```

I've also touched css animations today. Learning more about animating with css was one of my goals during my 100 days. The syntax is pretty straigh forward but still a bit unfamiliar. Here is the code for my animation of the unchosen elements:

```css
hp-chooser.chosen > *:not(.chosen) {
  max-width: 16.6%;
  animation-name: unchosen;
  animation-duration: 0.5s;
}

@keyframes unchosen {
  from {
    max-width: 20%;
  }
  to {
    max-width: 16.6%;
  }
}
```

**Link(s) to work**: [CSS animations](https://github.com/Organwolf/VanillaJS/tree/master/InteractionAnimations/Ch3/03_01%20-%20MODIFIED/begin)  
If you want to run this particular code and have python installed just run `python -m SimpleHTTPServer`  
inside the directory and navigate to http://localhost:8000/.

### Day 45: April 16, 2020

**Today's Progress**: Added a like component to the vidley app (an app that displays movies). The component can be found here: `src > components > common > like.jsx` ([link](https://github.com/Organwolf/ReactJS/tree/react-bootstrap/vidly/src/components/common)).

Like Component architecture  
Input: liked (boolean), onClick (event handler).  
Output: onClick.

I also started working on pagination for the app.

##### Pagination - Interface

Goal: decoupled from movies, re-usable and as general as possible.
Input to component: itemsCount, pageSize, onPageChange.

##### Pagination - Displaying pages

Goal: use the total amount of item and the pageSize (which represents the max amount of items per page) to calculate the total amount of pages. If the page count is 1 or less don't display any pagination.

```javasript
const pagesCount = Math.ceil(itemsCount / pageSize);
if (pagesCount === 1) return null;
```

**Thoughts**: The like component is my first real stand alone component. I binded an onClick event to an **i** tag that displayed a font awesome [heart](https://fontawesome.com/icons/heart?style=solid).

Pagination exercise. Solving the interface, the data and events that the pagination should recieve. It was easy just copying and pasting code from [getbootstrap.com](https://getbootstrap.com/docs/4.0/components/pagination/). So far I could work things out on my own. The rest, refactoring the pagination logic into its own component and knowing what events it should raise was harder. The component should know something about which page it's on. That much I know.

**Experimented with**: Pagination, stateless functional components, stand-alone components, component design, lodash naming a property while destructuring and component re-usability.

I also experimented with this:

```javascript
const { length: count } = this.state.movies;
```

**Link(s) to work**: [Vidly app](https://github.com/Organwolf/ReactJS/tree/40cc9554f68f9824c65bc253ec47a24c8a62c010)

### Day 44: April 15, 2020

**Today's Progress**: Worked with stateless functional components. A stateless functional component returns a react element. A React Element is what gets returned from components. It's an object that virtually describes the DOM nodes that a component represents. With a function component, this element is the object that the function returns. [source](https://stackoverflow.com/questions/30971395/difference-between-react-component-and-react-element)  
<br>
I have also worked with lifecycle hooks:  
mount > update > unmount. Mount -> constructor/render/componentDidMount.  
Update -> whenever state or props of a component changes, componentDidUpdate(), prevProps, prevState.

**Thoughts**:
I've used the turnary operator tons of times before in the past couple of months. However, I still had a hard time wrapping my head around how to apply an attribute dynamically while working with react. Turns out it's as easy as the code on line 4 below.

```r
  <button
    onClick={() => this.props.onDecrement(this.props.counter)}
    className="btn btn-secondary btn-sm m-2"
    disabled={this.props.counter.value === 0 ? "disabled" : ""}
  >
    -
  </button>
```

**Experimented with**: Ternary operator, lifecycle hooks, functional statelsss components and react elemnts.

**Link(s) to work**: [Amazing stetless functional components](https://www.youtube.com/watch?v=oHg5SJYRHA0)

### Day 43: April 14, 2020

**Today's Progress**: Repeating the basics of react. Props = recieved data and read-only. State = private/local data. `The component that owns a piece of the state, should be the one modifying it.` Sending the entire component as props to minimize the amount of separate props sent to a component works well for accessing prosp like id, value etc. Having a single source of truth is important. By removing the local state and only relying on the props a component becomes a controlled component. It is controlled by some parent higher up the the tree. I've also started using some new functionality from the extension "Simple React Snippets". See the pictures below.

<div>
<p>Before tabing</p>
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/before.png" width="420" height="90">
<p>After tabing</p>
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/after.png" width="420" height="90">
<br>
<br>
</div>

**Thoughts**: I've used Redux before to solve the need of a single source of truth. From what I could take away from my work today you can achive the same effect by having all statefull data at the top. I'm looking forward to learning more about hooks. How hooks solve this problem and how one should use them properly. For now I'll have to make do with setState and the like.

**Experimented with**: Event handlers, usages of props and ways to design an app to have a single source of truth.

**Link(s) to work**: None today

props = given data, read-only, state = private data/local data. Sending the entire component as props to be able to minimize the amount of separate props sent to the component. Works well for accessing prosp like id, value etc. Single source of truth. By removing the local state and only rely on the props. Controlled components follow these rules. Controlled by parent.

### Day 42: April 13, 2020

**Today's Progress**: Composing components, props.children and debugging react apps. I'm 21% into a React course. I'd like to complete the _Composing Components_ section I'm in by tomorrow. All of the lectures about lifecycle hooks feel a bit outdated but it's good that I have an understanding of how they work none the less.

**Thoughts**: Looking forward to learning how to debug React apps. Debugging in general feel more and more important the more I program.

**Experimented with**: F2 for refactoring which I will try to remember to use moving forward.

**Link(s) to work**: [Multiple counters app](https://github.com/Organwolf/ReactJS/tree/react-bootstrap/counter-app)

### Day 41: April 12, 2020

**Today's Progress**: Worked a little with the default bootstrap templates. On their starting page > _Examples_ > _Framework_ > _Starter template_ > right click and pick _View Page Source_. ctrl + shift + R enables refactoring in vs code and can be used to extract a method to a class. I also touched on some css basics by reading some of mozillas [Getting started with the Web](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics). I mainly focused on padding, border and margin.

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/padding-border-margin.png" width="500" height="420">

**Thoughts**: I need a lot of repetition when it comes to css. Or let me re-frame that, I haven't worked with css before and I'm new to frontend development so this takes time. I want to cover [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals), more JS basics such as the filter and reduce method as well as some more composing of components in react.

**Link(s) to work**: None today

### Day 40: April 11, 2020

**Today's Progress**: Recaps on recaps on recaps. Used the filter and map methods, learnt more about styling components and completed an exercise where I had to create a table of movies.

**Thoughts**: I got a subscription to programming with Mosh yesterday. I'm 20% into learning react. It's slightly out of date but I appriciate being able to repeat the core concepts of react. While using the map function I actually had some issues. For some reason I thought that the method was used like this:

```javascript
dataStructure.map((data) => {
  // this will not work
});
```

but that caused a parsing error. It should be done like this:

```javascript
dataStructure.map(data => (
  // this will work
))
```

I also worked a little with inline styles/styling

```javascript
<span style={{ fontSize: 30 }} className="badge badge-primary m-2">
```

**Experimented with**:  
The map and filter method. I also completed an exercise where I had to create a table of movies. Good stuff.

**Link(s) to work**:
[Movie app](https://github.com/Organwolf/ReactJS/tree/react-bootstrap/vidly)

### Day 39: April 10, 2020

**Today's Progress**: Learnt more about ES6, general JavaScript, reactjs and regular functions as well as arrow functions. Added the Prettier extension to VS Code I also added `"editor.formatOnSave": true,` to my _settings.json_. I also learnt that after Github converts Markdown to HTML it sanitizes it which removes things that could cause harm- such as script tags and inline-styles [source](https://stackoverflow.com/questions/44831505/which-inline-html-styles-does-github-markdown-accept), the ruby [sanitization_filter](https://github.com/jch/html-pipeline/blob/master/lib/html/pipeline/sanitization_filter.rb).

**Thoughts**:
The disappointments of not understanding Postgres and not being able to complete the corona dashboard app is all part of my process towards becomming a better programmer. That's why I'd like to share these images:
<br>
<br>

<div style="border: 1px solid red;">
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/psql-blog-app.png" width="451" height="286">
<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/corona-dashboard.png" width="451" height="286">
</div>
<br>
So far I havn't dared to ask any questions on stackoverflow. I might write about it on 100xdays slack channel and see what other developers think about it.
<br>
<br>
It's good to recap at certain points and this weekend I will set aside to recapping. Learnt more about the this keyword. The value of this is aparently determined by how a function is called. Something about returing a reference to the window object. If [strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) is enabled it eliminates some of JavaScripts silent errors by changing them to throw errors. It also fixes mistakes that make it difficult for JavaScript engines to perform optimizations. Functions in JS are objects. A common method used on function objects is bind which sets the value of _this_ permanently.

**Experimented with**:

⌘ + p, search for settings.json inside of vs code.

Different ways to create functions.

```javascript
// Arrow functions

// Example 1

// Regular function
const square = function (number) {
  return number * number;
};

// Arron function
const square = (number) => {
  return number * number;
};

// One line arrow function
const square = (number) => number * number;

// Example 2

const jobs = [
  { id: 1, isActive: true },
  { id: 2, isActive: true },
  { id: 3, isActive: false },
];

// Regular function inside of the filter method
const activeJobs = jobs.filter(function (job) {
  return job.isActive;
});

// Arrow function inside of the filter method
const activeJobs = jobs.filter((job) => job.isActive);

// Arrow functions and the this keyword

// Doesn't inherit the this keyword
const coolObject2 = {
  talk() {
    setTimeout(function () {
      console.log("this", this);
    }, 1000);
  },
};

coolObject2.talk();

// Arrow functions don't rebind this keyword
const coolObject = {
  talk() {
    setTimeout(() => {
      console.log("this", this);
    }, 1000);
  },
};

coolObject.talk();
```

**Link(s) to work**: None today

### Day 38: April 9, 2020

**Today's Progress**: More [electron](https://www.electronjs.org/) programming.

**Thoughts**: The first link I followed was well paced and well explained. However it is more than 2 years old. Turns out some of the info was outdated and I coudn't get the menu inside of the electron app to work. Moved on to the second tutorial, which was much more high paced, and completed a screen recording app. I appriciate the boilerplate code you get when running npx create-electron-app. Just the .gitignore is enough value.

**Keywords/commands**: node, process.platform = 'darwin', npx create-electron-app screen-recorder, npx create-electron-app screen-recorder, typing rs while electron app is running restarts the app and shows new changes. IPC (inter-process communication).

**Link(s) to work**:  
Started [here](https://www.youtube.com/watch?v=kN1Czs0m1SU)
Ended up [here](https://www.youtube.com/watch?v=3yqDxhR2XxE)
Produced [this](https://github.com/Organwolf/Electron/tree/b5e5667f43f1ec6e08222abd34aa0dba120503a8)

### Day 37: April 8, 2020

**Today's Progress**: Learnt new zsh shortcuts for git see **keywords/commands** below. Created a boilerplate project with Electron. You can find a link to the project under **links**. I did run the blog app in admin mode as well. Also had to read up on ignorefiles. Learns how to <ins>underline</ins> text in markdown today too.

**Thoughts**: I was going to install a git plugin for zsh but it turns out I already had one by default. Not sure how useful the commands will be or if i'll remember them. In the admin app of the blog app I tried out the calendar functionality. Although that particular project feels like a bit too much for me at the moment it has boosted my self-confidence.

**Keywords/commands**:  
<ins>zsh commands for git</ins>
<br>
`gst git status`<br>
`gaa git add --all`<br>
`gcmsg git commit -m`<br>
`gf git fetch`<br>
`gp git push`<br>
<ins>.gitignore</ins>
<br>
`**` is used for a recursive call in the whole project  
`**/node_modules` inside .gitignore recursively ignores the node_modules folder

**Link(s) to work**:
[Electron boilerplate](https://github.com/Organwolf/Electron/tree/336ce061619b05ac2a5ca224684a13d1534ff764)

### Day 36: April 7, 2020

**Today's Progress**: Read about [System Design](https://www.freecodecamp.org/news/systems-design-for-interviews/) and particularly in the context of job interviews. While doing that I stumbled upon [spaced learning](https://www.freecodecamp.org/news/use-spaced-repetition-with-anki-to-learn-to-code-faster-7c334d448c3c/) and in particular supervised spaced learning using Anki.

Finished the blog app. The tutorial/article I followed was extensive and the app complex but I wish that the author had added parts where he walked me through using the application. I sort of got it to work but once I added a post to the database the backend threw an error.  
`error: column "search_vector" of relation "posts" does not exist`  
Turns out the tsvector doesn't exist in the database. I checked by running `\c posts` and couldn't see the search_vector column either. I might have to either add the column or drop the table and re-add it. Tbh I'm in over my head. I have no idea what a tsvector is. I found and article explaining it's usage. In the [article](https://forestry.io/blog/full-text-searching-with-postgres/) the auther explains that the tsvector is used to full text search.

**Thoughts**: I'm at the point where I need to encorporate better error handling. The Facebook team behind react link to [this](https://reactjs.org/docs/error-boundaries.html) article about error boundaries and I'm planning on reading it later on this week. I would also like to learn how to add toast messages in apps. Something similar to a [modal window](https://en.wikipedia.org/wiki/Modal_window) where I can inform the user about stuff. I'd also like to dig into [Electron](https://www.electronjs.org/) and use it to build a cross-platform desktop app.

I'm feeling a bit overwhelmed right now. I believe that it's good to experiment and do things you don't really know how to do. However I am having a hard time debugging an app I don't really understand. I'll try circling back to this tomorrow and see if I can't add the missing peices to the server side. If that doesn't work I'll leave the app as is and possibly return once I know more about fullstack development with react and postgres.

**Link(s) to work**: [Current state of the blog app](https://github.com/Organwolf/ReactJS/tree/c450117123265d79d13e7e90d75df3e138b50452)

### Day 35: April 6, 2020

**Today's Progress**: Completed a small interactive [VIM tutorial](https://www.openvim.com/) and spent 45 mins on the fullstack blog tutorial.

**Thoughts**: I'm starting to fear that I won't be able to get this app to run. So far I have identified 2 things that might cause problems. 1) That I've copied some of the code from the freeCodeCamp post and some from the authors github repo. The repo contains some additional code not mentioned in the tutorial :triangular_flag_on_post:. 2) the db.js could be set up wrong. Although that is an easier fix.

**Experimented with**: Copy pasting and looking for new resourses. Found [this](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts) which I plan to check out tomorrow.

**Link(s) to work**:
[The latest from the blog](https://github.com/Organwolf/ReactJS/tree/d2d7b6722cd1b8d3c1ce877bc9ae075bcd5cdcc4)

### Day 34: April 5, 2020

**Today's Progress**: Learnt that you don't use '-' in database names. At least that isn't the convention. I created a postgres database for the fullstack app I'm working on. I also learnt that fetching descending dates from a database gives you the most recent date first.

**Thoughts**: It feels really powerful to be able to do things via the command line interface (CLI). Learning how to display the dependencies via the CLI, although you can find them by clicking your way into the package.json, was empowering!

**Experimented with**: Postgresql, Express, React, Context and stuff.

**Keywords/commands**: `\dt to list tables, \d table_name to list the table, npm ls --depth=0` [npm commands](https://docs.npmjs.com/cli/ls)

**Link(s) to work**:
[The latest from the blog](https://github.com/Organwolf/ReactJS/tree/80359873a27b4fa2c56b0a5952aed674bcb5a043)

### Day 33: April 4, 2020

<img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/computer-glitch.png" alt="cool computer" width="241" height="133"/>

**Today's Progress**: Learnt something new about git today. Apparently a `git pull` is shorthand for `git fetch` followed by `git merge FETCH_HEAD`. I was having a hard time accessing a remote branch on my local machine. So I performed a git pull and was confused about my local content merging with the remote branch. Now I know why that happened. [This](https://www.freecodecamp.org/forum/t/push-a-new-local-branch-to-a-remote-git-repository-and-track-it-too/13222) article was a big help when trying to understand the difference between local and remote branches.

I was also having problems with Postgresql. The solution was restarting postgres through homebrew. Not 100% sure why it didn't work to begin with but I'm glad I managed to solve it.

I also managed to set up some fullstack boilerplate code following [this](https://www.freecodecamp.org/news/fullstack-react-blog-app-with-express-and-psql/) tutorial. The commit with with boilerplate code can be found [here](https://github.com/Organwolf/ReactJS/tree/e8783fa33f6d892b6d6535474de80e3b4872b38b). The tutorial has some kinks and some missing information but it has still been of great help. On the client-side useReducer, useState and useContext are used to solve the same tasks. That way I got to see the similarities and differences between them. What made me happy was the fact that useContext and Redux have a lot in common.

**Thoughts**: I've learnt a lot today. Not sure if I'll do more coding until tomorrow but I'm looking forward to setting up the database. I'm also looking forward to learning more about styling applications but that's another chapter entirely :trollface:.

**Experimented with**:  
`brew services restart postgresql, git fetch, \l, \c, \dt, \du,`  
`postgres -V, psql postgres, pg library, axios, useContext`

**Link(s) to work**:
[Fullstack boilerplate code for a blog](https://github.com/Organwolf/ReactJS/tree/e8783fa33f6d892b6d6535474de80e3b4872b38b)

### Day 32: April 3, 2020

**Today's Progress**: I was introduced to Gatsby CLI, Leaflet, Yarn, React Helmet, Resolve Src. Followed [this](https://www.freecodecamp.org/news/how-to-create-a-coronavirus-covid-19-dashboard-map-app-in-react-with-gatsby-and-leaflet/).

**Thoughts**: I didn't quite manage to bring it all together. I started by following the video and managed to do everything up until the custom badges. When I added the new css to \_map.scss nothing changed. I mean, so something broke, I didn't solve whatever the application was missing to function properly. However, I've spent +1 hour debugging, learning more about the file structure of this project, working with yarn and gatsby. Although I'm a little disappointed I still did a good enough job today.

**Experimented with**: Gatsby, which is a React-based, GraphQL powered, static site genereator, some sass, Leaflet, an open-source JS library for interactive maps. I also encountered some destructuring that I liked `const { data = [] } = response`. I like that the data is explicitly set to an array. It looks like I imagine TypeScript functions. It's very easy to understand what datastructure is used for storing the response.

**Links I followed**:  
https://www.freecodecamp.org/news/how-to-create-a-coronavirus-covid-19-dashboard-map-app-in-react-with-gatsby-and-leaflet/
https://github.com/colbyfayock/coronavirus-map-dashboard

**Link(s) to work**: None today

### Day 31: April 2, 2020

**Today's Progress**: Started my research into refactoring a react app using redux for state management to using hooks instead. Found out that I most likely have to use the context reducer _useContext_. I found a list of the available hooks [here](https://reactjs.org/docs/hooks-reference.html). Created a new hooks branch in my todo app and learnt how to push the branch up-stream.

**Thoughts**: Not much coding today. Atleast not yet. I need to wrap my head around useState, useContexr and useReducer first. I'd also like to read more about refactoring from redux code to hooks code. Git and the different commands to deal with branches feel more familiar. Finding answers to problems regarding git has also become easier. The current todo app consists of 3 components

- Add new todo
- List of todos
- Complete todos

I could complete the _Add new todo_ with hooks seperately to get an idea of using hooks. That might help me along the way.

**Experimented with**:  
`git branch -r, ls -a, git checkout --track origin/redux, git checkout -b hooks, git push -u origin.`

**Links I followed**:  
https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#_tracking_branches  
https://www.freecodecamp.org/news/how-to-convert-from-react-redux-classes-to-react-hooks-the-easy-way-eca2233e0e7a/  
https://reactjs.org/docs/hooks-reference.html

**Link(s) to work**: [Todo - hooks](https://github.com/Organwolf/ReactJS/tree/hooks/hooks/todo)

### Day 30: April 1, 2020

**Today's Progress**: Focused on react hooks today which is a new addition in React 16.8. Hooks allow you to use state and other React features without writing a class. They let you "hook" into lifecycle features in function component. The two most common hooks are useState and useEffect. The state hook is called _useState_ because it enables the re-use of stateful behaviour between different components. The effect hook, adds the ability to perform side effects from a function component. API calls can be defined as mutations outside of your own code. By performing such mutations you create side effects. The effect hook is designed to deal with code that creates side effect.

**Thoughts**: Tomorrow I am going to start using hooks in my todo application.

**Experimented with**: React hooks, how to migrate code from Codepen to my local environment, deleting a local branch using git branch -d branch_name, configured vs code to open the current directory using "code .",

**Links I followed**:  
https://code.visualstudio.com/docs/setup/mac  
https://reactjs.org/docs/hooks-overview.html  
https://www.reddit.com/r/javascript/comments/6cm7gd/pure_functions_when_working_with_dom_manipulation/

### Day 29: March 31, 2020

**Today's Progress**: Yesterday I started working with python. A friend of mine had adviced me to take a look at ["Automating the Boring Stuff with Python"](https://www.google.com/search?client=firefox-b-d&q=automating+the+boring+stuff+with+python). Yesterday I opened the pdf, skipped the first 140 pages that deal with python programming basics, and jumped to automating tasks. First of was Regex. Regex is usually used by string searching algorithms to find or validate strings. [Regexpal](https://www.regexpal.com/) can be used to test your regular expressions on a certain text.

**Thoughts**: The syntax can be a real pain. I'm not planning on learning any of this by heart. It just feels like this is a good revamp of my python skills. I've used python mainly for backend tasks before. Mainly when using the Flask framework.

**Experimented with**: Importing re which is the python regex library. Using re.compile(r'Things|To|Find') where r before the first quote marks the string as a _raw string_ which does not excape characters such as backslash. The search method takes a string as input and checks it against the created regex. It returns a _Match_ object. The Match objects have a _group()_ method that will return the matched text fro mthe searched string. I also learnt that by using parentheses inside of my regular expression I can create groups in the regex. These groups can later be "destructured", to use a term from JavaScript, into multiple values like so:

```python
areaCode, mainNumber = mo.groups()
```

Matching One or More is done with a **+** after the group. To match 0 or more use an **\***. Specific repetitions with {} and findall() to... find all. There are character classes that represent digits, any character that is not a digit and so on. The caret symbol (^) at the start of a regex indicated that a match must occur at the beghinning of the searched text. The dollar sign (\$) that it should occur at the end. The dot (.) is a wild card and combining dot and star (.\*) can stant in for anything.

```python
>>> nameRegex = re.compile(r'First Name: (.*) Last Name: (.*)') >>> mo = nameRegex.search('First Name: Al Last Name: Sweigart') >>> mo.group(1)
'Al'
>>> mo.group(2)
'Sweigart'
```

A review of regex symbols can be found on page 186 of the book.

**Link(s) to work**: None yet

### Day 28: March 30, 2020

**Today's Progress**: Installed Oh-My-Zsh and worked my way through several blog posts about customization. Learnt a little about vim but mostly I picked up commands that are mac specific such as pressing cmd + shift + h while in the finder to be redirected to the home directory.

<div>
  <img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/old-terminal.png" width="451" height="300"/>
  <img src="https://github.com/Organwolf/100-days-of-code/blob/master/images/new-terminal.png" width="451" height="300"/>
</div>

**Thoughts**: Finding the Terminal > Preferences > Profiles to be a bit confusing. After a bunch of trial and error I managed to set up the terminal in the particular color I wanted. I had a hard time understanding how to set the chosen background color. There is a "default" button at the bottom left that I had to press.

**Keywords/commands**:  
`zsh --version, cmd + shift + ., cmd + shift + h, .zshrc, source ~/.zshrc, alias myip=\"curl http://ipecho.net/plain; echo\", exit, sh -c \"$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)\", cmd + , , vi file, ls -a, touch .hushlogin`

**Links I followed**:  
https://medium.com/@Zwenza/functional-vs-class-components-in-react-231e3fbd7108  
https://medium.com/@smile2gether/how-to-customize-your-mac-os-terminal-880c4097b18b  
https://hackernoon.com/react-stateless-functional-components-nine-wins-you-might-have-overlooked-997b0d933dbc

### Day 27: March 29, 2020

**Today's Progress**: Continued to revise my CountdownTimer code. Now I've added logic to pause/start the timer once it's active.

I wanted to:

- [x] Show the button once the timer started ticking
- [x] Give the button the same size as the previously added buttons
- [x] Learn how to place two elements next to each other
- [x] Be able to pause/resume the timer
- [x] Count the hours
- [x] Trigger a sound once the timer was done

**Thoughts**: Not loving that I used a global variable to keep track of the remaining time but all in all I'm proud with the over all outcome. As mentioned previously it is way harder adding made up features than following someone else.

**Experimented with**:  
`text-shadow: 4px 4px 0 rgba(0,0,0,0.05); visibility: hidden; as well as the built in Audio API`

**Link(s) to work**: [Count down timer with added features](https://github.com/Organwolf/VanillaJS/tree/master/CountdownTimer)

### Day 26: March 28, 2020

**Today's Progress**: Moving away from tutorials and working on my own. Adding custom :hover and :focus effects via css as well as trying to add my own features to previously finished projects.

**Thoughts**: Worked more independently today. Didn't rely on any tutorial or blog post of any kind and it was hard! I will definitely have to focus more on how much time I spend programming rather than what I program. Atleast for the next 7 days.

**Experimented with**: Hiding/displaying a button, pausing and restarting a setInterval that runs behind the scenes keeping track of time.

**Link(s) to work**: None today

### Day 25: March 27, 2020

**Today's Progress**: Worked with setting up virtualenvwrapper on my mac. Had problems with configurating the \$PATH and had to create a ~/.profile for my zsh shell. Inside of the profile file I added the correct path to my python3 interpreter. Below is some of what I've learnt about virual environments.

#### Virtual environments

**why**:

Virual environment resolve dependency issues, make a project self-contained and reproducible and enables the installation of packages on a host on which you do not have admin privlages.
I also learnt that virtual environment and conda environment are different things.

**what**:

A virtual environment is a python tool for **dependency management** and **project isolation**.
It is just a directory with three important components:

- site-packages
- Symlinks
- Scripts

site-packages -> a folder where third party libraries are installed
Symlinks -> are links to Python executables installed on your system
Scripts -> ensures that executed Python code uses the Python interpreter
and site packages installed inside the given virtual environment.

Don't include the virtual environment to your teams repo.
Create your own vintual environment inside of the proj root directory.
And then pip install -r requirements.txt.

**how**:

It comes down to PATH. In particular echo \$PATH which tells the shell
what instance of Python to use and where to look for packages.
Still a bit confused on the how but that's ok.

**virtualenvironment specific commands**:

% source venv/bin/activate
(venv) % deactivate

(venv) % pip freeze > requirements.txt

**Thoughts**: It's a lot of work yet few lines of code when it comes to configuring stuff like this. I had to read multiple forum posts and guides. Patchworking my way towards a working solution.

**Experimented with**: zsh interactive shell, touch, open, ~/.profile, virtualenvwrapper, docker-compose up, docker-compose down as well as testing http requests using postman.

**Link(s) to work**: [Virtual environments info](https://towardsdatascience.com/virtual-environments-104c62d48c54)

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
if (remainingSeconds < 10) {
  const displaySeconds = "0" + `${remainingSeconds}`;
}
// However
const display = `${minutes}:${
  remainingSeconds < 10 ? "0" : ""
}${remainingSeconds}`;
// Is arguably a more elegant solution
```

**Experimented with**:  
Template literals/template strings and terniery logic but also how to select all elements that share a certain attribute!

```javascript
const buttons = document.querySelectorAll("[data-time]");
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
const height = Math.round(percent * 100) + "%";
bar.style.height = height;
const playbackRate = percent * (max - min) + min;
bar.textContent = playbackRate.toFixed(2) + "x";
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

options.forEach((option) => option.addEventListener("change", setOption));

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
const sortedBands = bands.sort(function (a, b) {
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
**Link(s) to work**:
https://gist.github.com/rxaviers/7360908
 -->
