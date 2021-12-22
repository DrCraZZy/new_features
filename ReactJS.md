#  ReactJS

## JSX
React nutzt JSX-Files, hiermit kann man in einem JS-File HTML benutzen.

```javascript
// dieser Javascript-Syntax wird vom BABLE-Compiler in javascript-code übersetzt, 
// welcher von allen browser unterstützt https://babeljs.io/
import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(<h1>Hello World!</h1>, document.getElementById("root"));
```

`render` der von ReactDOM nimmt ein Element (wenn es mehrere sind einfach in __div__ verpacken). Und als zweites wird einfach ein id von dem Element übergeben, wo dieser Inhalt in HTML-File plaziert werden soll (standard ist "root")

## Javascript-Variablen in HTML

Hierfür wir in dem JS-File(JSX-File) die Variable deklariert und um in HTML-Teil auf den Wert dieser zugreifen zu können, wird die Variable einfach in `{ }` genommen. Hier können beliebige Ausdrücke (Expression) stehen aber keine Anweisung (Statements)

```javascript
const name = "Maxim";

ReactDOM.render(<h1>Hello {name}!</h1>, document.getElementById("root"));
```

## Create new Componing

Zu erstellen eines neuen Komponeneten wird eine Datei erstellt (__DateiName.jsx__). In diese Datei soll als erstes __React__ importiert werden.

```javascript
import React from "react";
```

Dies ermöglicht uns den HTML/JSX Syntax zu schreiben.

Als nächstes wird eine `function` erstellt und anschließend exportiert.

```javascript
//step 1
import React from "react";

//step 2
function Hearding() {
  return <h1>My Favourite Foods</h1>;
}

//step3
export default Hearding;
```

Zum Schluß wird das Component in die index.js Datei importiert:

```javascript
import Hearding from "./Hearding.jsx";
```

Component wird mit den Namen der Funktioni angesprochen:

```javascript
<Heading />
```

```javascript
import React from "react";
import ReactDOM from "react-dom";

import Hearding from "./Hearding.jsx";
import Listing from "./Listing.jsx";

ReactDOM.render(
  <div>
    //anfügen des Components
    <Hearding /> 
    <Listing />
  </div>,
  document.getElementById("root")
);
```

## Project structure

index.js:
```javascript
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

App.jsx:
```javascript
import React from "react";
import Hearding from "./Hearding.jsx";
import Listing from "./Listing.jsx";

function App() {
  return (
    <div>
      <Hearding />
      <Listing />
    </div>
  );
}

export default App;
```

Component.jsx as example:
```javascript
import React from "react";

function Listing() {
  return (
    <ul>
      <li>Bacon</li>
      <li>Jamon</li>
      <li>Noodles</li>
    </ul>
  );
}

export default Listing;
```

## Setup local environment

1. Install Node.js
2. VS Code + Erweiterungen:
    - vscode-icons
    - babel-javascript
3. [Create React App](https://reactjs.org/docs/create-a-new-react-app.html)
    - npx create-react-app [app name]
    - cd my-app
    - npm start
    
## React props

Mithilfe von `props` können Parameter (Eingenschaften) an die Funktionen (Components) weitergegeben werden. In der Funktion landen die Parameter in `props`

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Card(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <img src={props.imageUrl} alt="avatar_img" />
      <p>{props.phone}</p>
      <p>{props.email}</p>
    </div>
  );
}

ReactDOM.render(
  <div>
    <h1>My Contacts</h1>
    <Card
      
      name="Beyonce"
      imageUrl="https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg"
      phone="+123 456 789"
      email="b@beyonce.com"
    />
    <Card
      name="Jack Bauer"
      imageUrl="https://pbs.twimg.com/profile_images/625247595825246208/X3XLea04_400x400.jpg"
      phone="+987 654 321"
      email="jack@nowhere.com"
    />
    <Card
      name="Chuck Norris"
      imageUrl="https://i.pinimg.com/originals/e3/94/47/e39447de921955826b1e498ccf9a39af.png"
      phone="+918 372 574"
      email="gmail@chucknorris.com"
    />
  </div>,
  document.getElementById("root")
);
```

## React - Mapping Data to Components
Wir haben ein Dataset (Array)

```javascript
const emojipedia = [
  {
    id: 1,
    emoji: "💪",
    name: "Tense Biceps",
    meaning:
      "“You can do that!” or “I feel strong!” Arm with tense biceps. Also used in connection with doing sports, e.g. at the gym."
  },
  {
    id: 2,
    emoji: "🙏",
    name: "Person With Folded Hands",
    meaning:
      "Two hands pressed together. Is currently very introverted, saying a prayer, or hoping for enlightenment. Is also used as a “high five” or to say thank you."
  },
  {
    id: 3,
    emoji: "🤣",
    name: "Rolling On The Floor, Laughing",
    meaning:
      "This is funny! A smiley face, rolling on the floor, laughing. The face is laughing boundlessly. The emoji version of “rofl“. Stands for „rolling on the floor, laughing“."
  }
];

export default emojipedia;
```

Es wird ein Component erstellt:
```javascript
import React from "react";

function Entry(props) {
  return(
    <div className="term">
      <dt>
        <span className="emoji" role="img" aria-label="Tense Biceps">
          {props.emoji}
        </span>
        <span>{props.name}</span>
      </dt>
      <dd>
        {props.meaning}
      </dd>
    </div>
  );
}

export default Entry;
```

In der App.jsx werden die Components dynamisch erstellt:
```javascript
import React from "react";
import Head from "./Head";

import emojipedia from "../emojipedia";
import Entry from "./Entry";

function createEntry(item) {
  return <Entry
    key={item.id} //key property wird ist wichtig und wird vom React erwartet
    emoji={item.emoji}
    name={item.name}
    meaning={item.meaning}
  />
}

function App() {
  return (
    <div>
      <Head />
      <dl className="dictionary">
        // Es wird einfach map() - Funktion auf Dataset benutzt mit eine Funktion, 
        // die für uns das Component erstellt und zurückgibt
        {emojipedia.map(createEntry)}
      </dl>
    </div>
  );
}

export default App;
```

## Help-Functions
```javascript
var numbers = [3, 56, 2, 48, 5];

//Map -Create a new array by doing something with each item in an array.
const newNumbersMap = numbers.map(function (x) {
  return x * 2;
});
console.log(newNumbersMap);

//Filter - Create a new array by keeping the items that return true.
const newNumbersFilter = numbers.filter(function(num){
  return num > 10;
});
console.log(newNumbersFilter);

//Reduce - Accumulate a value by doing something to each item in an array.
const newNumbersReduce = numbers.reduce(function(accumulater, currentNumber){
  return accumulater + currentNumber;
});
console.log(newNumbersReduce);

//Find - find the first item that matches from an array.
const newNumbersFind = numbers.find(function(num){
  return num > 10;
});
console.log(newNumbersFind);

//FindIndex - find the index of the first item that matches.
const newNumbersFindIndex = numbers.findIndex(function(num){
  return num > 10;
});
console.log(newNumbersFindIndex);
```

## Conditional Rendering

```javascript
import React from "react";
import Login from "./Login";

let isLoggedIn = true;

function App() {
  return (
    <div className="container">
      // Terneri operator
      {isLoggedIn === true ? <h1>Hello</h1> : <Login />}
    </div>
  );
}

export default App;
```

## React Hooks - useState
[documentation](https://reactjs.org/docs/hooks-reference.html#usestate)

```javascript
// useState returns stateful value and function to update this value
import React, {useState} from "react";

function App () {
  // unboxing the returns
  // count is a stateful value
  // setCount is a function to change this value
  const [count, setCount] = useState(0); //0 is hier an initiale value of count

  function increase(){
    setCount(count + 1);
  }

  function decrease(){
    setCount(count - 1);
  }

  return (
    <div className="container">
      <h1>{count}</h1>
      <button onClick={increase}>+</button>
      <button onClick={decrease}>-</button>
    </div>
  );
}

export default App;
```

## Destructuring (ES6)
```javascript
const cars = [
  {
    model: "Honda Civic",
    //The top colour refers to the first item in the array below:
    //i.e. hondaTopColour = "black"
    coloursByPopularity: ["black", "silver"],
    speedStats: {
      topSpeed: 140,
      zeroToSixty: 8.5
    }
  },
  {
    model: "Tesla Model 3",
    coloursByPopularity: ["red", "white"],
    speedStats: {
      topSpeed: 150,
      zeroToSixty: 3.2
    }
  }
];

export default cars;
```

```javascript
import React from "react";
import ReactDOM from "react-dom";

import cars from "./practice";

const [honda, tesla] = cars;

const {speedStats: { topSpeed: teslaTopSpeed }} = tesla;
const {speedStats: { topSpeed: hondaTopSpeed }} = honda;

const {coloursByPopularity: [teslaTopColour]} = tesla;
const {coloursByPopularity: [hondaTopColour]} = honda;

ReactDOM.render(
  <table>
    <tr>
      <th>Brand</th>
      <th>Top Speed</th>
    </tr>
    <tr>
      <td>{tesla.model}</td>
      <td>{teslaTopSpeed}</td>
      <td>{teslaTopColour}</td>
    </tr>
    <tr>
      <td>{honda.model}</td>
      <td>{hondaTopSpeed}</td>
      <td>{hondaTopColour}</td>
    </tr>
  </table>,
  document.getElementById("root")
);
```

## Event Handling
```javascript
import React, { useState } from "react";

function App() {
  const [headingText, setHeadingText] = useState("Hello");
  const [isMousedOver, setMouseOver] = useState(false);

  function handleClick() {
    setHeadingText("Submitted");
  }

  function handleMouseOver() {
    setMouseOver(true);
  }

  function handleMouseOut() {
    setMouseOver(false);
  }

  return (
    <div className="container">
      <h1>{headingText}</h1>
      <input type="text" placeholder="What's your name?" />
      <button
        style={{ backgroundColor: isMousedOver ? "black" : "white" }}
        onClick={handleClick}
        onMouseOver={handleMouseOver}
        onMouseOut={handleMouseOut}
      >
        Submit
      </button>
    </div>
  );
}

export default App;
```