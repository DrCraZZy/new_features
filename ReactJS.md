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