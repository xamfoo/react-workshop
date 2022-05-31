# React 18 for Beginners

Max Foo

https://xamfoo.github.io/react-workshop

Note:
- Should give you a good foundation to learn about HTML, CSS, JS and React

---

## Introduction to React

- What is React?
  - HTML
  - CSS
  - JS
  - DOM
- Why use React?
- Usage
- Toolchain
- Editors for JS
- Exercise 1 - Create a React project

----

### What is React?

- A JavaScript library for building user interfaces
- Initial release by Facebook in 2015

Note:
- What do you already know about React?

----

#### What is React? - HyperText Markup Language (HTML)

**The source code of a Web page**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example Page</title>
  </head>
  <body>Example text</body>
</html>
```

- Easily parsed by a browser <!-- .element class="fragment" -->
- Snapshot of a web app <!-- .element class="fragment" -->
- Specify presentation with CSS <!-- .element class="fragment" -->
- React is a way to create HTML <!-- .element class="fragment" -->

Note:
- Why do you think HTML looks like this?

----

#### What is React? - Cascading Style Sheets (CSS)

<div style="display: flex; font-size: 0.8em">
<div style="flex: 1">
Example HTML

```html
<div class="example1_container">
  <img
    class="example1_avatar"
    src="assets/img/pikachu.png"
  />
  <span>Pikachu</span>
</div>
```
</div>
<div style="flex: 1">
Example CSS

```css [1-8|10-13|]
.example1_container {
  align-items: center;
  background: #000;
  border: 1px solid #FFF;
  display: flex;
  gap: 10px;
  padding-left: 10px;
}

.example1_avatar {
  border-radius: 50%;
  width: 65px;
}
```
</div>
</div>

<div class="fragment">
<div class="example1_container">
  <img
    class="example1_avatar"
    src="assets/img/pikachu.png"
  />
  <span>Pikachu</span>
</div>
</div>

Note:
- What do you already know about CSS?

----

#### What is React? - JavaScript (JS)

**Scripting language used by browsers**

```javascript
const people = [
  { name: 'Alice', email: 'alice@example.com' },
  { name: 'Bob', email: 'bob@example.com' },
  { name: 'Martin', email: 'martin@example.com' }
];
const extract = (list, key) => list.map(item => item[key]);
const names = extract(people, 'name');
// ['Alice', 'Bob', 'Martin']
```

- JavaScript core: <!-- .element class="fragment" --> `Object`, `Array`, `String` etc. 
- Web APIs: <!-- .element class="fragment" --> `document`, `window` etc.
- Node.js APIs: <!-- .element class="fragment" --> `require` etc.
- React exposes JS APIs <!-- .element class="fragment" -->

Note:
- It is now a good time to have a quick revision on JS

----

#### What is React? - Document Object Model (DOM)

In-memory object of a document

```javascript
document.title = 'Example Page';
document.body.appendChild(document.createTextNode('Example text'));
```

- This is how React interact with DOM under the hood <!-- .element
  class="fragment" -->
- 90% YAGNI when using React <!-- .element class="fragment" -->

Note: See React Fiber Architecture about rendering and the reconcilation process

----

### Why use React?

<div class="fragment">

Pros

- Declarative code is simpler than manipulating DOM <!-- .element
  class="fragment" -->
- Rich ecosystem of libraries and tooling <!-- .element class="fragment" -->
- Knowledge transferable to mobile app development with React Native <!--
  .element class="fragment" -->
</div>
<div class="fragment">

Cons

- Usually requires transpilation (JSX) <!-- .element class="fragment" -->
- react + react-dom are sizable (44.3kB compressed) <!-- .element
  class="fragment" -->
</div>

Note: Declarative (what needs to be done, instead of how it should be done)

----

### Usage

<div class="fragment">

Install React in an existing Node.js project

```shell
$ npm install react react-dom
```
</div>

<div class="fragment">

or add React to an existing HTML page

```html
<script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
```
</div>

<div class="fragment">

or try it in an online editor

- codepen.io - React Hello World
  https://codepen.io/xamfoo/pen/rNJGMma
- replit.com - React template
  https://replit.com/@replit/Reactjs
</div>

----

### Toolchain

- A <!-- .element class="fragment" --> **package manager** for using published packages including React e.g. npm, pnpm, Yarn
- A <!-- .element class="fragment" --> **bundler** lets you write modular code and bundles it for optimal load time e.g. Parcel, Rollup, webpack
- A <!-- .element class="fragment" --> **compiler** lets you use the latest language features which still works in older browsers e.g. Babel, Typescript
- (<!-- .element class="fragment" -->*Optional*) An opinionated **template** for creating a new React App e.g. Create React App, Vite

----

### Editors for JS

- **VS Code** is recommended for beginners with no background
- **Intellij** or **WebStorm** when you want an IDE
- Try **Vim** or **Emacs** at your own time when you want maximum
  configurability and don't mind a steep learning curve

----

### Exercise 1 - Create a React project

<div style="font-size: 0.7em">

1. Ensure node version >=16 is installed (use powershell in windows)
```shell
$ node --version
v16.15.0
```
2. Go to a directory you want to create a project (e.g. home)
```shell
$ cd ~
```
3. Create a project (make sure you have internet access)
```shell
$ npx create-react-app@latest react-exercises
```
4. Follow instructions to run the template
```shell
$ cd react-exercises
$ npm start
```
5. You should be able to access your app in the browser
6. (Optional) Download and install a code editor

</div>

---

## Elements and JSX

- What are React Elements?
- Rendering Elements
- What is JSX?
- Why JSX?

----

### What are React Elements?

Smallest building blocks of React apps

```javascript
const element = React.createElement(
  'h2',          // Component or HTML tag name
  { id: 'tin' }, // Attributes
  'Tin'          // Children
);
```

- Immutable objects <!-- .element class="fragment" -->
- Cheap to create <!-- .element class="fragment" -->
- Snapshot of a component <!-- .element class="fragment" -->

----

### Rendering Elements

<div style="font-size: 0.8em">
<div class="fragment">

To render a React element, include a target node in HTML

```html
<div id="root"></div>
```

</div>
<div class="fragment">

Then, create a root object and pass an element to its render method

```javascript
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(React.createElement('h2', null, 'Lithium'));
```
</div>
<div class="fragment">

Update UI by re-rendering root with a new element

```javascript
root.render(React.createElement('h2', null, 'Gallium'));
```
</div>
</div>

----

### What is JSX?

<div class="fragment">

JSX extends JS syntax to compile markup to React elements

```javascript
React.createElement('h1', { className: 'greeting' }, 'Hello World!');
// is equivalent to
<h1 className="greeting">Hello World!</h1>
```

</div>
<div class="fragment">

JS expressions are valid inside markup when wrapped with curly braces

```javascript
const user = { name: 'Green', avatarUrl: '/img/user/green.png'}
const element = (
  <div>
    <img src={user.avatarUrl} />
    <span>Name: {user.name}</span>
  </div>
);
```
</div>

----

### Why JSX?

- React allows creation of components are units where markup and logic are
  defined together
- Most people find it helpful as a visual aid when working with UI inside JS

---

## Components and Props

- Function Components
- Class Components
- Rendering Components
- Composing Components
- Styling Components
- JS Modules and Components
- Exercise 2 - Creating Components

----

### Function Components

<div style="font-size: 0.7em">

The simplest React component is a function

```javascript
const Welcome = props => <h1>Hello, {props.name}</h1>;
```

- Should only <!-- .element class="fragment" --> accept a **props** argument
- Props <!-- .element class="fragment" --> should NOT be modified
- Should return one of the following <!-- .element class="fragment" -->
  - **React element** Rendered as an element
  - **String or number** Rendered as text node
  - **Booleans or null** Rendered as nothing
  - **Arrays and fragments** Rendered as multiple React elements
  - **Portals** Rendered into a different DOM node
- Only <!-- .element class="fragment" --> function components support **hooks**

</div>

----

### Class Components

<div style="font-size: 0.7em">

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

- <!-- .element class="fragment" -->
  The **render** method is expected to return a value like a function component 
- <!-- .element class="fragment" -->
  Use for specific APIs offered by the class such as **componentDidCatch** or
  **getSnapshotBeforeUpdate**
- <!-- .element class="fragment" -->
  Supports  **state** via `this.state` and `this.setState`
- <!-- .element class="fragment" -->
  Refer  to `React.Component` docs for API details including the state and
  lifecycle methods of a class component

</div>

----

### Rendering Components

<div style="font-size: 0.8em">

User-defined components can be rendered by specifying it as a JSX tag name.

```javascript [1|]
const element = <Welcome name="Spock" />;
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<React.StrictMode>{element}</React.StrictMode>);
```

- Component names should begin with a capital letter to differentiate it from
  HTML tags <!-- .element class="fragment" data-fragment-index="2" -->
- Wrap your root element <!-- .element class="fragment" --> with **StrictMode**
  for additional checks and warnings during development
  - Warnings about using legacy, deprecated and unsafe API
  - Check if state is reusable by re-mounting componoents
  - Help detect unexpected side effects by double-invoking component methods
    which are supposed to be idempotent

</div>

----

### Composing Components

A components can refer to other components

```javascript
function App() {
  return (
    <div>
      <Welcome name="Kirk" />
      <Welcome name="Spock" />
    </div>
  );
}
```

- <!-- .element class="fragment" -->
  A React app is composed of multiple components

----

### Styling Components

Add CSS classes to components by passing the **`className`** prop

```javascript
const Menu = (props) => (
  <span className="menu navigation">
    Menu
  </span>
);
```

Then target them with CSS class selectors

```css
.menu { /*...*/ }
.navigation { /*...*/ }
```

----

### JS Modules and Components

<div style="font-size: 0.8em">

Use **import** and **export** to access variables across files and packages
when working with JS modules

```javascript
// react npm package
export const useState = () => {/*...*/}; // Named export
export default {/*...*/}; // Default export

// ./App.js
export const Provider = () => {/*...*/}; // Named export
export default () => {/*...*/}; // Default export

// ./App.css
.App { /*...*/ }

// ./index.js
import App from './App'; // import from relative path
import { Provider as AppProvider } from './App'; // Rename import
import React, { useState } from 'react'; // import from package
import './App.css'; // import CSS file works only if supported by bundler
```

Ensure **`React`** is imported when using JSX in the file

</div>

----

### Exercise 2 - Creating Components

<div style="font-size: 0.7em">

1. Ensure your React app from the previous exercise is running. The page should
   reload automatically when code is saved.
```shell
$ npm start
```
2. Copy **`src/App.js`** and **`src/App.css`** to new files  
   e.g. **`src/Ex2.js`** and **`src/Ex2.css`**
3. Modify **`src/index.js`** to import the created JS file  
   e.g. **`import App from './Ex2.js'`**
4. Modify **`src/Ex2.js`** to **`import './Ex2.css'`** instead
5. Find a random web page you like and attempt to clone it with components and
   CSS
   - Define and use multiple components
   - Move components into separate files when there is too much code
   - Use browser dev tools to view the source and styles of the page

</div>

---

## Lists and Fragments

- Lists
- Keys
- Fragments
- Keyed Fragments

----

### Lists

```javascript
const users = [
  { id: 'A', name: 'Alice' },
  { id: 'B', name: 'Bob' },
  { id: 'C', name: 'Martin' }
];
const Users = (props) => (
  <ul>
    {props.users.map(user => <li>{user.name}</li>)}
  </ul>
);
const element = <Users users={users} />;
```

<div class="fragment">

- Alice
- Bob
- Martin

</div>

<div class="fragment warning">

```text
Warning: Each child in a list should have a unique 'key' prop.
```

</div>

Note: Why does the warning exist?

----

### Keys

Add keys to help identify addition or removal of an item

```javascript [3]
const Users = (props) => (
  <ul>
    {props.users.map(user => <li key={user.id}>{user.name}</li>)}
  </ul>
);
```

<div class="fragment">

Use array index only if a stable key is unavailable

```javascript [3]
const Users = (props) => (
  <ul>
    {props.users.map((user, index) => <li key={index}>{user.name}</li>)}
  </ul>
);
```

</div>

- Keys need only be unique among siblings <!-- .element class="fragment" -->

Note: Why is using a stable key better than an array index?

----

### Fragments

Returning multiple elements without keys or nesting

```javascript [2-5|]
const Stats = (props) => (
  <>
    <td>{props.user.hp * 100}%</td>
    <td>{props.user.mp * 100}%</td>
  </>
);
const Player = (props) => (
  <tr>
    <td>{props.user.name}</td>
    <Stats user={props.user} />
  </tr>
);
```

- Useful to present disparate groups of information as one <!-- .element
  class="fragment" -->

----

### Keyed Fragments

\<\> is the shorthand for \<React.Fragment\>
```javascript
const Glossary = (props) => (
  <dl>
    {props.items.map(item => (
      // Without the `key`, React will fire a key warning
      <React.Fragment key={item.id}>
        <dt>{item.term}</dt>
        <dd>{item.description}</dd>
      </React.Fragment>
    ))}
  </dl>
);
```

- Only <!-- .element class="fragment" --> **\<React.Fragment\>** supports the
  key attribute

---

## State and Effect

- Introduction to Hooks
  - Component Lifetime
- State Hook
- Effect Hook Without Cleanup
- Effect Hook With Cleanup
- Rule of Hooks
- Data Fetching
- Exercise 3 - Rendering Data

----

### Introduction to Hooks

- <!-- .element class="fragment" -->
  Hooks are functions which can be easily identified by the prefix **"use"**
  e.g. **`useState`**, **`useEffect`**
- <!-- .element class="fragment" -->
  Hooks only works in function components
- <!-- .element class="fragment" -->
  Hooks stores data for the **lifetime** of a component

----

### Introduction to Hooks - Component Lifetime

<div style="font-size: 0.7em">

```javascript [1-2|2-3|3-4|4-5|5-6|6-7|]
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App name="Tom" />); // Mounted: Life begins
root.render(<App name="Jerry" />); // Props change: Life continues
root.render(<span>Loading...</span>); // Unmounted: Life ends
root.render(<main><App name="Spike" /></main>); // Mounted: 2nd life begins
root.render(<div><App name="Tyke" /></div>); // Parent change: 2nd life ends and 3rd life begins
root.render(<div><App name="Tyke" key="1" /></div>); // Key change: 3rd life ends and 4th life begins
```

- <!-- .element class="fragment" -->
  Component life begins when it is **mounted**
- <!-- .element class="fragment" -->
  Component life continues when props change
- <!-- .element class="fragment" -->
  Component life ends when it is **unmounted**
- <!-- .element class="fragment" -->
  A parent or **key** change unmounts a component and mounts a new one

</div>

Note: How does React decide when to mount or unmount a component?

----

### State Hook

<div style="font-size: 0.7em">

```javascript [1-6|1-7|1-8|1-9|]
let testSetCount;
const Counter = () => {
  const [count, setCount] = useState(0);
  testSetCount = setCount; // For demo. Do NOT do this for production!
  return <span>{count}</span>;
};
root.render(<Counter />); // 0
testSetCount(10);         // 10
root.render(<Counter />); // 10
testSetCount(n => n + 1); // 11
```

- <!-- .element class="fragment" -->
  useState accepts an initial value and returns an array `[state, setState]`
- <!-- .element class="fragment" -->
  Assign variable names to `state` and `setState` by array destructuring
- <!-- .element class="fragment" -->
  State is stored for the lifetime of the component and does not change until
  `setState` is called
- <!-- .element class="fragment" -->
  Pass a function to `setState` when the new state depends on the previous one
- <!-- .element class="fragment" -->
  Beware: Calling `setState` unconditionally causes an infinite rendering loop
- <!-- .element class="fragment" -->
  React can sometimes batch state updates and then render the final state

</div>

----

### Effect Hook Without Cleanup

```javascript
const Debugger = (props) => {
  useEffect(() => 
    console.log('Component mounted');
  , []); // [] means run after first render
  useEffect(() => {
    console.log('Component rendered');
  }); // No dependencies means run after every render
  useEffect(() => {
    console.log(`Message received: ${props.message}`);
  }, [props.message]); // Run after printing a new message
  return <span>{props.message}</span>;
};
```

<div style="font-size: 0.7em">

- <!-- .element class="fragment" -->
  Effect Hooks makes a component do something after it renders
- <!-- .element class="fragment" --> 
  `useEffect` accepts a function and an optional list of dependencies
- <!-- .element class="fragment" -->
  Given an empty list of dependencies, the effect is run after the first render
- <!-- .element class="fragment" -->
  Not given a list of dependencies, the effect is run after every render
- <!-- .element class="fragment" -->
  Given a list of dependencies, the effect is run whenever any of the
  dependencies changes

</div>

----

### Effect Hook With Cleanup

```javascript
const Clock = () => {
  const [date, setDate] = useState(new Date());

  useEffect(() => {
    const interval = setInterval(() => setDate(new Date()), 1000);
    return () => clearInterval(interval);
  });

  return <span>{date.toLocaleString()}</span>;
};
```

<div style="font-size: 0.7em">

- <!-- .element class="fragment" -->
  To cleanup, return a function in `useEffect`
- <!-- .element class="fragment" -->
  `setInterval` updates the state every second (1000ms)
- <!-- .element class="fragment" -->
  `clearInterval` stops the update when the component is unmounted

</div>

----

### Rule of Hooks

```javascript
const App = (props) => {
  // Top Level - Call hooks here
  const [state, setState] = userState();
  useEffect(() => {
    // Not top level - Don't call hooks here
  });
  if (/* condition */) {
    // Not top level - Don't call hooks here
  }
  props.list.forEach(item => {
    // Not top level - Don't call hooks here
  });
  return null;
};
```

- Only call hooks at the **top level**
- This preserves the order of hooks so React knows what to return for each hook

----

### Data fetching

<div style="font-size: 0.7em">

```javascript
const IpAddress = () => {
  const [request, setRequest] = useState({ isError: false });
  useEffect(() => {
    fetch('https://api.country.is')
      .then(res =>
        res.status === 200 ? res.json() : undefined
      )
      .then(data => setRequest({ data }))
      .catch(error => {
        console.error(error);
        setRequest({ isError: true });
      });
  }, []);
  return (
    <div>
      {request.isError && 'Error loading IP address'}
      {!request.data && !request.isError && 'Loading...'}
      {request.data && request.data.ip}
    </div>
  );
};
```

Note:
- Learn more about `fetch`
  https://developer.mozilla.org/en-US/docs/Web/API/fetch
- Learn more about `Promise`
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

</div>

----

### Exercise 3 - Rendering Data

<div style="font-size: 0.7em">

1. Develop new components for this exercise (Refer to Exercise 2 steps 1 to 4
   but use a different file name)
2. Choose a data source
   - Real-time SG data from https://data.gov.sg/developer#realtime
   - A Reddit page (add .json?raw_json=1 to any page) e.g.
     https://www.reddit.com/.json?raw_json=1
   - Any other APIs e.g. https://github.com/public-apis/public-apis
3. Write a component to load data with **`useState`**, **`useEffect`** and
   **`fetch`**
4. Write component(s) and CSS to present the loaded data

</div>

Note:
- Example Reddit Page
  https://codepen.io/xamfoo/pen/OJQvaWr

---

## Events and Forms

- Handling Events
- Controlled Components
- `textarea` Tag
- `select` Tag
- Multiple Inputs

----

### Handling Events

<div style="font-size: 0.8em">

```javascript
const Toggle = () => {
  const [isOn, setIsOn] = useState(true);
  return (
    <button onClick={() => setIsOn(prevState => !prevState)}>
      {isOn ? 'ON' : 'OFF'}
    </button>
  );
}
```

- <!-- .element class="fragment" -->
  Event handlers are **camelCase** (`onClick`) rather than lowercase
  (`onclick`) like in HTML
- <!-- .element class="fragment" -->
  Event handlers are **functions** rather than strings like in HTML
- <!-- .element class="fragment" -->
  No need to `addEventListener` to a DOM element

</div>

----

### Controlled Components

<div style="font-size: 0.8em">

```javascript
const NameForm = (props) => {
  const [name, setName] = useState('');
  const handleSubmit = event => {
    event.preventDefault();
    props.submit(name);
  };
  const handleChange = event => setName(event.target.value);
  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
};
```

- <!-- .element class="fragment" -->
  Event handlers receive cross-browser synthetic events
- <!-- .element class="fragment" -->
  Access input value for an event via **`event.target.value`**
- <!-- .element class="fragment" -->
  Call **`event.preventDefault`** explicity to prevent default behavior
- <!-- .element class="fragment" -->
  Defining the **value** of an input makes it a controlled component

</div>

----

### `textarea` Tag

```javascript
const Essay = () => {
  const [text, setText] = useState('Text in an area');
  const handleChange = event => setText(event.target.value);
  return <textarea value={text} onChange={handleChange} />
};
// HTML: <textarea>Text in an area</textarea>
```

- <!-- .element class="fragment" -->
 textarea uses a **value** attribute rather than children

----

### `select` Tag

<div style="font-size: 0.8em">

```javascript
const FlavorPicker = () => {
  const [flavor, setFlavor] = useState('coconut');
  const handleChange = event => setFlavor(event.target.value);
  return (
    <label>
      Pick your flavor:
      <select value={flavor} onChange={handleChange}>
        <option value="coconut">Coconut</option>
        <option value="mango">Mango</option>
      </select>
    </label>
  );
};
// HTML: <option selected value="coconut">Coconut</option>
```

- <!-- .element class="fragment" -->
 `select` uses a **value** rather the option `selected` attribute

</div>

----

### Multiple Inputs

<div style="font-size: 0.8em">

```javascript
const WaitListForm = () => {
  const [formState, setFormState] = useState({ name: '', mobile: '' });
  const handleChange = ({ target }) =>
    setFormState({ [target.name]: target.value });
  return (
    <form>
      <label>
        Name:
        <input type="text" name="name" />
      </label>
      <label>
        Mobile:
        <input type="number" name="mobile" />
      </label>
    </form>
  );
};
```

- <!-- .element class="fragment" -->
  Add a **name** attribute to each input to help a handler differentiate them
  with **`event.target.name`**

</div>

---

## Build Your Own App

- Time to let the creative juices flow!
- Build a React app with what you have learnt today
- Choose one
  - Build your personal website
  - Build something else with APIs
    https://github.com/public-apis/public-apis
  - Expand on the app you have built in Exercise 3
  - Build a simple game like Tic-tac-toe
    https://reactjs.org/tutorial/tutorial.html
- Please share what you have built!

---

## Further Reading

<div style="font-size: 0.8em">

- React API reference **\#react**
  https://reactjs.org/docs/react-api.html
- React Developer Roadmap **\#react**
  https://roadmap.sh/react
- Frontend Developer Roadmap **\#html** **\#css** **\#js**
  https://roadmap.sh/frontend
- Responsive Web Design - freeCodeCamp **\#html** **\#css**
  https://www.freecodecamp.org/learn/2022/responsive-web-design/
- JavaScript Algorithms and Data Structures - freeCodeCamp **#js**
  https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/

</div>
