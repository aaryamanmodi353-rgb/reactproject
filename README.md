🧠 Core Concepts Implemented

1. Virtual DOM

JSX is not HTML. It compiles to function calls that return virtual DOM objects.

Example (conceptually):

<div>Hello</div>

becomes:

createElement("div", null, "Hello");

Your implementation produces objects like:

{
  type: "div",
  props: {
    children: ["Hello"]
  }
}


---

2. Components as Functions

React components are simply functions that return UI elements.

function Header() {
  return <h1>Welcome</h1>;
}

In this project:

function Header() {
  return createElement("h1", null, "Welcome");
}


---

3. JSX-like Children & Expressions

Example JSX:

<h1>Score: {points}</h1>

This becomes two children:

"Score: " — text node

points — evaluated expression


Your implementation mirrors this behavior.


---

4. Rendering Engine

The renderer walks the virtual DOM tree and converts it into actual DOM nodes using:

document.createElement

document.createTextNode

setAttribute

appendChild


This is a simplified version of React’s “reconciliation” + “commit” phases.


---

📁 Project Structure

mini-react/
│── src/
│   ├── createElement.js     # Virtual DOM creation
│   ├── render.js            # Render virtual DOM → real DOM
│   ├── component.js         # Functional component handler
│   └── index.js             # Example usage / entry point
│
│── README.md                # Documentation
│── package.json             # (Optional) Package metadata


---

📝 Example

import { createElement } from "./createElement.js";
import { render } from "./render.js";

function App() {
  return createElement(
    "div",
    { id: "root-container" },
    createElement("h1", null, "Hello Mini React"),
    createElement("p", null, "This is a custom React-like renderer.")
  );
}

const root = document.getElementById("root");
render(createElement(App), root);
