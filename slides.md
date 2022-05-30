# React v18 for Beginners

Max Foo

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

#### HyperText Markup Language (HTML)

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

#### Cascading Style Sheets (CSS)

<div style="display: flex;">
<div style="flex: 1">
Example HTML

```html
<div class="example1_container">
  <img
    class="example1_avatar"
    src="img/pikachu.png"
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
    src="img/pikachu.png"
  />
  <span>Pikachu</span>
</div>
</div>

----

#### JavaScript (JS)

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

#### Document Object Model (DOM)

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

- [codepen.io - React Hello World](https://codepen.io/xamfoo/pen/rNJGMma)
- [replit.com - React template](https://replit.com/@replit/Reactjs)
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
6. Download and install a code editor if you want to try it

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

----

### Function Components

<div style="font-size: 0.7em">

The simplest React component is a function

```javascript
const Welcome = props => <h1>Hello, {props.name}</h1>;
```

- Must <!-- .element class="fragment" --> accept a **props** object
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

- The <!-- .element class="fragment" -->  **render** method is expected to
  return a value like a function component 
- Use <!-- .element class="fragment" --> for specific APIs offered by the class
  such as **componentDidCatch** or **getSnapshotBeforeUpdate**
- Supports <!-- .element class="fragment" --> **state** via `this.state` and
  `this.setState`
- Refer <!-- .element class="fragment" --> to `React.Component` docs for a
  detailed API reference

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
- Use <!-- .element class="fragment" --> **StrictMode** for additional checks
  and warnings during development
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

- A React app is composed of multiple components <!-- .element class="fragment"
  -->

----

### Exercise 2 - Creating Components

<div style="font-size: 0.7em">

1. Find a random web page you would like to make a copy of
2. Use browser dev tools to view the source code and styles of the page elements
3. Ensure your React app from the previous exercise is running. The page should
   reload automatically when code is saved.
```shell
$ npm start
```
4. Modify and save **`src/App.js`** with an editor
5. Modify and save **`src/App.css`** to update styling
6. Define and use multiple components
7. Move components into separate files when there is too much code in one file
   (observe how **`App`** is exported then imported by **`src/index.js`**)

Note: Instructor should choose to demonstrate a small change on App.js

</div>

---

## Lists and Fragments

---

## State and Effect

---

## Events and Forms

---

## Context and Composition
