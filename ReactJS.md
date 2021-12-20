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