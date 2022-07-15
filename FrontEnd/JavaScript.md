# Modul 10 (JavaScript)

## Arrays
```javascript
// type of array
typeof [];
"object"

// length
const arr =  [1, 2];
console.log(arr.length);
2

// Array.isArray()
const arr =  [1, 2];
console.log(Array.isArray(arr));
true
```

### Array-Methoden
_.push(...items), .unshift(...items)_ - Elemente am Ende / am Anfang des Arrys anfügen
_.pop(), .shift()_ - Elemente am Ende / am Anfang des Arrys löschen
_.splice(index[, deleteCount, elem1, ..., elemN])_ - Elemente löschen / anfügen
_.concat()_ - Arrays konkatenieren

```javascript
let arr = [ "orange"];
arr.unshift("apple");// arr = ["apple", "orange"];
arr.push("strawberry");// arr = ["apple", "orange", "strawberry"];
arr.shift(); //arr =  ["orange", "strawberry"];
arr.pop();// arr =  ["orange"];
```

_.map(function)_ - geht durch Array durch und bearbeitet die Elemente entsprechend der funktion (es entsteht eine neues Array)

```javascript
let result = arr.map(function(item, index, array) {

  // gibt eine neues Element zurück
  // item — aktueller Element des Arrays
  // index — Index des aktuellen Elements
  // array — Array

});
```

_.reduce(cb) или reduceRight(cb)_ - akkumuliert die Elemente des Arrays

```javascript
let result = arr.reduce(function(previousValue, item, index, array) {

  // ...
  // item — aktueller Element des Arrays
  // index — Index des aktuellen Elements
  // array — Array

}, [initial]);
```

## Schleifen

```javascript
for(let i = 0; i < 10; i++) {...}

for(let i in object) {...}

while(){...}

do {...} while()

arr.forEach(function(item, index, array) {
  ...
});
```

## Map
```javascript
// Kann beliebigen Typ als Schlüssel benutzen
let map = new Map(); // Map anlegen

map.set("1", "string"); // Wert anfügen

map.get(1); // Wert auslesen 

map.size; // größe erfahren

// schleife über map
for (let name of fruits.keys()) { // .keys() - gibt Schlüssel zurück
  console.log(name); // apple, strawberry, blueberry
}

for (let color of fruits.values()) { // .values() - gibt Werte zurück
  console.log(color); // green, red, blue
}

for (let elem of fruits) { // gibt Schlüssel Wert nach einander
   console.log(elem); // apple, green, strawberry, red, blueberry, blue
}
```

# Modul 11 (Funktionen und Objekte)

### Function Declaration (FD)
__Function Declaration__ Funktionen werden vom Interpreter erstellt, bevor der Code ausgeführt wird, sodass sie aufgerufen werden können, bevor sie deklariert werden.
```javascript
function sum() {
  const result = 1 + 2;
  console.log(result);
};
```

### Function Expression (FE)
__Function Expression__ Funktionen verhalten sich je nach verwendetem Operator unterschiedlich. Über FD deklarierte Funktionen verhalten sich immer gleich.
```javascript
const sum = function() {
  const result = 1 + 2;
  console.log(result);
};
```

Deklaration der Funktionen (Priorität)
1. Function Declaration
2. Function Expression mit __const__


### Parameter und Argumente
Die Funktionsparameter ist eine Liste von Bezeichnern, die zum Zeitpunkt der Deklaration angegeben werden, dh im folgenden Beispiel sind die Parameter a und b. Parameter werden durch Kommas getrennt aufgelistet. Wenn eine Funktion aufgerufen wird, wird ihr eine Liste von Werten übergeben, die als Argumente der Funktion bezeichnet werden.

Das __arguments__ Pseudo-Array kann auch verwendet werden, um auf Argumente zuzugreifen. Es enthält eine nummerierte Liste von Argumenten: arguments[0], arguments[1] usw. sowie eine _length_-Eigenschaft. In der Praxis wird es verwendet, wenn mehr Argumente als Parameter angegeben werden. Es ist wichtig, sich daran zu erinnern, dass, wenn ein Parameter angegeben ist, aber kein Argument an die Funktion übergeben wird, diese standardmäßig auf __undefined__ gesetzt wird.

### Funktion und Prozedur
Sowohl eine Prozedur als auch eine Funktion sind eine Reihe von Anweisungen, die in einer bestimmten Reihenfolge ausgeführt werden können. Der Unterschied besteht darin, dass eine Funktion immer einen Wert zurückgeben muss (eine strengere Definition erfordert auch, dass die Funktion immer eine Eingabe hat). Der Standardrückgabewert ist __undefined__.

### Higher-order function
_Higher-order function_ - Funktionen, die andere Funktionen als Argument annehmen und Funktionen als Wert zurückgeben können. In __JS__ sind alle Funktionen Objekte.

### Closure
Es ist eine Kombination aus der Funktion und allen lexikalisch erhaltenen übergeordneten Gültigkeitsbereichen. Durch diese gespeicherten Bereichsobjekte kann die Funktion jedoch freie Variablen verwenden. Mit anderen Worten, eine Closure ist eine Funktion zusammen mit allen ihr zur Verfügung stehenden externen Variablen. Theoretisch sind alle Funktionen in JavaScript Closures.

Wenn eine Funktion erstellt wird, erhält sie eine versteckte __[[Environment]]__-Eigenschaft, die sich auf den Geltungsbereich bezieht, in dem sie erstellt wurde. Wenn eine Funktion aufgerufen wird, wo immer sie im Code übergeben wird, sucht sie zuerst in sich selbst nach Variablen und dann in externen Gültigkeitsbereichen, die aus __[[Environment]]__ stammen.

### Callback-Function
Wenn nach dem _function_ ein Name steht, wird die Funktion benannt, andernfalls ist sie anonym. Wenn eine Funktion die als _Function Expression_ deklariert wurde einen Namen hat, kann man diesen Namen __nur__ im Falle einer _Rekurtion_ verwenden. 

Anonyme Funktionen werden als __Callback-Function__ verwendet, wenn eine Funktion über  _Function Expression_ und __IIFE__ (immediately invoked function expression) definiert wird.

__IIFE__ - Es wird eine Funktion als  _Function Expression_ deklariert und sofort aufgerufen.

```javascript
const func = function () {
  // ...
}();

(function () {
  // ...
}());

(function () {
  // ...
})();
```

__Wofür werden IIFE benutzt?__
1. Erstellen eines lokalen Geltungsbereichs (_scope_)

    Die erste, auf der alle anderen aufbauen, ist die Schaffung eines lokalen _scope_.
    ```javascript
    (function () {
      const local = 123;
      console.log(local);  // 123
    }());
    console.log(local);  // Uncaught ReferenceError: local is not defined
    ```
    Das Erstellen eines solchen Bereichs hält den globalen Bereich sauber: Wenn mehrere Skripte (z. B. Bibliotheken von Drittanbietern) den globalen Bereich verwenden, verwenden sie möglicherweise versehentlich denselben Namen für eine Variable, und aus diesem Grund funktionieren beide möglicherweise nicht mehr , weil erwartet wird, dass nur sie mit dieser Variable arbeiten können.

    Zweitens kann die JS-Engine solchen Code besser optimieren – ungenutzte lokale Variablen entfernen (z. B. die lokale Variable im obigen Beispiel).

    Drittens ermöglicht Ihnen der lokale Geltungsbereich Folgendes:
    ```javascript
    const count = function() {
      let counter = 1;
      function count() {
        console.log(counter);
        counter++;
      }
      return count;
    }();

    count();  // 1
    count();  // 2
    counter = 1;
    count();  // 3

    // Nach dem counter = 1 außerhalb der Funktion gesetzt wurde, hat es keine Einfluß auf der count() genommen, weil die Funktion und global verschiedene scopes haben.
    ```

2. Lösen der Konflikten der Variablen aus Bibliotheken
    Der zweite Anwendungsfall für IIFE besteht darin, Konflikte zwischen Variablen aus Bibliotheken zu lösen. Beispielsweise exportieren sowohl jQuery als auch Cash die $-Variable in den globalen Gültigkeitsbereich, sodass nicht klar ist, auf welche Bibliothek Sie sich im Skript beziehen. Dies lässt sich leicht beheben, wenn Sie IIFE mit Parametern als Wrapper verwenden:
    ```javascript
    (function ($) {
      // nutzen $ und wissen, dass es jQuery ist.
    })(jQuery);
    ```

3. Modulmuster
    Und die dritte Option haben wir im Wesentlichen schon erfunden – das Modulmuster in JavaScript. Lassen Sie uns ein einfaches Modul schreiben, das die Variable MAX_COUNT aus dem globalen Bereich importiert und mehrere Zählfunktionen exportiert:
    ```javascript
    MAX_COUNT = 3;

    const counter = (function (max) {
      let current = 0;

      return {
        getCurrent() {
          return current;
        },

        increment() {
          if (current === max) {
            return;
          }
          current++;
        },

        decrement() {
          if (current === 0) {
            return;
          }
          current--;
        },
      };
    })(MAX_COUNT);

    counter.getCurrent();  // 0
    counter.decrement();
    counter.getCurrent();  // 0
    counter.increment();
    counter.getCurrent();  // 1
    counter.increment();
    counter.getCurrent();  // 1
    counter.increment();
    counter.getCurrent();  // 3
    counter.increment();
    counter.getCurrent();  // 3
    counter.decrement();
    counter.getCurrent();  // 2
    ```
    Wie inkapsulierung in OOP.

__Callback__ - eine Funktion, die am Ende der Operation ausgeführt wird, wenn alle anderen Operationen bereits abgeschlossen sind. Normalerweise wird eine Rückruffunktion als letztes Argument an die Funktion übergeben. Callbacks sind normale Javascript-Funktionen. Häufig wird eine Callback-Funktion als anonyme Funktion definiert.

__Usage der Callback__
1. Wenn Sie nach Abschluss einer asynchronen Aktion (z. B. Laden von Informationen aus einer Datenbank) Code ausführen müssen.
    ```javascript
    function loadData(url, cb) {
      let result = doSomethingAndGetResult(url)

      // onload wird ausgelöst, wenn result vollständig geladen ist und der Callback aufgerufen wird
      result.onload = function () {
        cb();
      }
    }

      loadData('url', function(){
      // code
      })
    ```

    Mit einem Rückruf steuern wir die Aktion.

2. Als Argument in vielen Array-Methoden.
    ```javascript
    const arr = [1, 2, 3]
    arr.forEach(function(item){
      console.log(item+1)
    })
    ```

3. Als Argument in __setTimeout__, __setInterval__ und anderen Methoden.

### Arrow funtion

Mit Hilfe von Function Expression können wir auch eine Pfeilfunktion deklarieren - Arrow Function. Es ist also nicht nötig, das Funktionsschlüsselwort zu schreiben. Wenn es nur einen Parameter gibt, werden keine geschweiften Klammern {} benötigt:
```javascript
const logText = text => console.log(text);

const sayHelloWorld = () => console.log('Hello, world!');

const sum = (a, b) => a + b;
```

Besonderheiten:
- Kurze Syntax.
- Keine Bindung dazu (dazu später mehr).
- Kann nicht als Konstruktor verwendet werden (dazu später mehr).
- Pseudo-Array ohne Argumente.

### Object

Ein Objekt ist eine ungeordnete Sammlung von Eigenschaften, wobei jede Eigenschaft aus einem Namen (Schlüssel) und einem zugeordneten Wert besteht. Objekte in JavaScript können als assoziative Arrays bezeichnet werden, da sie aus einem Schlüssel-Wert-Paar bestehen. Sie sind darauf ausgelegt, komplexe Datenstrukturen zu speichern.

Ein Objekt wird mit geschweiften Klammern {...} mit einer optionalen Liste von Eigenschaften erstellt. Eigenschaften werden als 'Schlüssel:Wert'-Paar geschrieben, wobei der Schlüssel eine Zeichenfolge ist und der Wert beliebig sein kann.

```javascript
// leer
const obj = {};

// zwei key:value - Paare
const obj2 = {
    a: 'hello',
    b: 123,
};

// mit new
const obj = new Object();
```

Wenn der Wert der Eigenschaft eines Objekts eine Funktion ist, wird diese Eigenschaft als Methode bezeichnet. Eine Methode ist eine Eigenschaft, die aufgerufen werden kann.

```javascript
const obj = {
    a: 1,
    f: function() {
        console.log(1);
    },
};
```
Aufrufe der Properties
1. dot notation
2. bracket notation

Mit der Klammernotation können Sie auch auf eine Eigenschaft verweisen, deren Name in einer Variablen gespeichert ist. Dies wird als berechnete Eigenschaft bezeichnet.

```javascript
const lang = prompt("Geben Sie den Namen der Programmiersprache ein", "javascript");
const collection = {
    [lang]: 'Die beste Programmiersprache!', // der Eigenschaftsname wird aus der Variablen übernommen lang
};
alert(collection.javascript);
```

__Arbeiten mit dem Objekten__
```javascript
// Objekt erstellen
const obj = {a: 1};

obj.a; // 1 – Wert erhalten

obj.a = 9; // neuen Wert zuweisen

console.log(obj.a); // 9

obj.b = 100; // neue Propertie b hinzufügen mit dem Wert 100

// obj['b'] = 100; new Propertie in bracket notation

// löschen der Propertie
const obj1 = {a: 1};
delete obj1.a; 
console.log(obj1) // {}

// Vergleich der Objekte wird nach der Referenz gemacht

// existiert Propertie in Object
const obj = {a: 1, c: undefined}; 
console.log('a'  in obj);
'a' in obj; // true
'b' in obj; // false
'c' in obj; // true

// durch Objekt iterieren mit for in
const obj = {a: 1, b: 2};
for (let key in obj) {
    // zeigt alle Properties/keys
    console.log(key);
}

// a
// b

for (let key in obj) {
    // zeigt alle Werte
    console.log(obj[key]);
}

// 1
// 2
```

# Modul 12 (DOM)
JavaScript wurde ursprünglich für Webbrowser entwickelt. Aber seitdem hat es sich erheblich weiterentwickelt und sich zu einer plattformübergreifenden Programmiersprache zur Lösung einer Vielzahl von Problemen entwickelt.

Heute kann JavaScript in einem Browser, auf einem Webserver oder in einer anderen Umgebung verwendet werden, sogar in einer Kaffeemaschine. Jede Umgebung stellt ihre eigene Funktionalität bereit, die die JavaScript-Spezifikation Umgebung nennt.

Die Umgebung stellt neben der Basissprache eigene Objekte und zusätzliche Funktionen zur Verfügung. Browser bieten beispielsweise die Möglichkeit, Webseiten zu verwalten. Node.js stellt einige serverseitige Funktionen zur Verfügung und so weiter.

Das folgende Bild zeigt allgemein, was für JavaScript in der Browserumgebung verfügbar ist:

![js](../img/m13_browser_environment.png)

Wobei __window__ ein globales Objekt ist, das alle verfügbaren Funktionen speichert. Es wird verwendet, wenn der Entwickler Methoden verwenden möchte, die vom Browser bereitgestellt werden.

__Window__ tritt sowohl als _Global Object_ für _JS_, als auch Browserfenster.

__Window__ enthält __DOM__, __BOM__ und __JS__.

__DOM__ (Document Object Model) ist das Dokumentobjektmodell. Ist eine Web-API, wie sie vom Browser bereitgestellt wird. Das DOM verwaltet eine objektorientierte Darstellung einer Webseite, wodurch es möglich ist, sie beispielsweise mit JavaScript zu ändern. Das Arbeiten mit dem _html_-Dokument wir über das Objekt _document_ ermöglicht. _Document_ enthält den Inhalt einer Webseite (den gesamten DOM-Baum) und bietet außerdem Funktionen, die für das _Document_ global sind (z. B. das Erstellen neuer Elemente). Von dort aus können Sie auf jeden Knoten (HTML-Element) zugreifen.

__BOM__ (Browser Object Model) ist eine Browserumgebung. Es bietet Funktionalität (Objekte und Funktionen), die JavaScript verwenden kann, zum Beispiel enthält BOM häufig verwendete Dinge wie:
- Location – gibt ein Location-Objekt mit Informationen über den aktuellen Ort des Dokuments zurück.
- Verlauf - bietet eine Schnittstelle zum Bearbeiten des Verlaufs der Browsersitzung (z. B. besuchte Seiten im aktuellen Tab).
- XMLHttpRequest - wird verwendet, um Anfragen an den Server zu erstellen.

## Nodes
Nodes sind einzelne Bestandteile des DOMs. Elemente sind HTML-Tags. Non-Elemente sind Texte, Kommentare...

### ParentNodes
Nodes werden in _ParentNodes_, _neighborNodes_ und _ChildrenNodes_. Für die Elements in dem __DOM__ gibt es zwei verschiedene Referenzen für alle Elemente (Texte und andere) und Elemente (HTML-Tags). Für das Arbeiten mit _Parents_ gibt es zwei Methoden _parentNode_ und _parentElement_.

### ChildrenNodes
Diese Kategorie wird in zwei Typen unterteilt:
- childNodes - beinhaltet, die Elemente, die in dem Element liegen, welcher angesprochen wird (Text, Kommentare...)
- children - beinhaltet alle Tag-Elemente in dem jeweiligen Tag

Für alle Nodes: _childNode, firstChild, lastChild_
Nur für Elemente: _children, firstElementChild, lastElementChild_

Parent-Nodes sind eindeutig. Um auf die zuzugreifen kann man _parentElement_ oder _parentNode_ benutzen, beide geben Parent-Node zurück. Wobei _parentElement_ gibt Node-Element zurück und _parentNode_ gibt einen beliebigen Parent zurück.

### firstChild & lastChild
- Mit den beiden Methoden kann man den ersten und den letzten Element aus dem _childNodes_-Pseudoarray holen.

- Mit der Methode _elem.hasChildNodes()_ kann man abfragen ob ein Element _childNodes_ beinhaltet.

- _childNodes_ ist ein Pseudoarray und kann mit _for ... of_ durchlaufen. (mit _for...in_ wird es nicht funktionieren)

- Array-Methoden für _childNodes_ funktionieren nicht. Aber _childNodes_ kann in ein Array mit __Array.from()__ umgewandelt werden.

### Siblings
- Siblings sind Nodes, die den selben Parent haben

- _nextSibling_, _previousSibling_ (_parentNode_) - für alle Nodes

- _previousElementSibling, nextElementSibling_ - nur für Elemente

## Suche der Elementen in DOM
|Funktion|Was|Erklärung|
|---|---|---|
|document.getElementById(id)|ID|Akzeptiert die _ID_ als Zeichenfolge. Gibt Element - Objekt zurück
|document.getElementsByTagName(tagName)|Tag|Akzeptiert den Tag-Namen als Zeichenfolge. Gibt ein Array von Elementen zurück.
|document.getElementsByClassName(className)|Class|Akzeptiert den Klassennamen als Zeichenfolge. Gibt ein Array von Elementen zurück.
|document.querySelector(selector)|CSS-Selector|Akzeptiert einen Selektor als Zeichenfolge, das erste Zeichen oder dessen Abwesenheit gibt den Selektor an (. (Punkt) - Klasse, # - ID, Abwesenheit - Tag-Name). Gibt das erste Element zurück.
|document.querySelectorAll(selector)|all CSS-Selectoren|Akzeptiert einen Selektor als Zeichenfolge, das erste Zeichen oder seine Abwesenheit gibt den Selektor an (. - Klasse, # - ID, Abwesenheit - Tag-Name). Gibt ein Array von Elementen zurück.

## Ändern der Elemente

|Funktion|Was|Erklärung|
|---|---|---|
|elem.innerHTML = "content"|Fügt Content an|Bevor Sie Inhalte einfügen, müssen Sie das Element mit speziellen Funktionen finden.|
|elem.setAttribute(attr, value)|Anfügt/Ändern des Attributs|Akzeptiert den Attributnamen als Zeichenfolge und den Wert für dieses Attribut als Zeichenfolge. Bevor Sie ein Attribut hinzufügen, müssen Sie das Element mithilfe spezieller Funktionen finden.|
|elem.style.property = "style"|Style anfügen|Bevor Sie einen Stil einfügen, müssen Sie das Element mit speziellen Funktionen finden.|

## Anfügen/Löschen der Elemente 
|Funktion|Was|Erklärung|
|---|---|---|
|document.createElement(elem)|Element anfügen|Akzeptiert den Tag-Namen und -Wert für dieses Attribut als Zeichenfolge.|
|elem.removeChild(child)|Element löschen|Akzeptiert _child_, das zu entfernende Element. _elem_ ist das übergeordnete Element, aus dem das _child_ entfernt wird.|

```javascript
// Element erstellen
const customDiv = document.createElement("div");
// mit Content füllen
customDiv.innerHTML = "<span id=\"custom\">Привет!</span>";
// suchen der Parentelement für den neuen Element
const parent = document.getElementById("id");

document.body.insertBefore(customDiv, parent);
```

_innerHTML_ kann auch Tags als Text in Tag bringen. 
```javascript
const content = "Hello!"
const parent = document.getElementById("id");
parent.innerHTML = `<div><span id="custom"> ${content}</span></div>`;
```

_insertAdjacentHTML(__position__, __html__)_ - diese Methode analysiert den angegebenen Text als HTML oder XML und fügt die resultierenden Knoten an der angegebenen Position in den DOM-Baum ein. Diese Funktion überschreibt keine bestehenden Elemente. 

__Position__ sagt wo das Element eingefügt wird.
|Position values|Explanation|
|---|---|
|beforebegin|vor dem Element|
|afterbegin|nach dem öffnenden Tag|
|beforeend|vor dem  schließenden Tag|
|afterend|nach dem Element|

```javascript
// Parentelement suchen und neues Element anfügen
const content = "Hello!"
const parent = document.getElementById("id");

parent.insertAdjacentHTML('afterend', `<div><span id="custom"> ${content}</span></div>`);
```

## Events
Event ist Signal vom Browser, dass etwas passiert ist. (Beispiele für Events: mausclick, pageloading...)

![](../img/M12_DOM_Load_Skillfactor.png)
- __DOMContentLoaded__ - Der DOM-Baum wurde erstellt, aber die Skripte/Stile/Inhalte wurden noch nicht geladen. Feuert auf dem Dokumentobjekt ab, abgefangen mit addEventListener.
- __load__ - Vollständig geladene HTML-Seite. Sie können es verarbeiten, indem Sie auf die Eigenschaft _window.onload_ zugreifen.
- __beforeunload__ - Der Benutzer möchte die _window.beforeunload_-Seite verlassen. Sie können fragen, ob der Benutzer wirklich gehen möchte.
- __unload__ - Der Benutzer hat fast die _window.unload_-Seite verlassen. Sie können Metriken oder Statistiken zur Seitenanalyse senden.

Wenn wir auf ein Ereignis reagieren müssen, weisen wir einen __Handler__ zu. Das heißt, wir stellen eine Funktion ein, die funktioniert, sobald das Ereignis eingetreten ist. Dank Handler ist es möglich, dass JavaScript auf Benutzeraktionen reagieren kann.

### Variante 1
Benutzen eines Attributes eines Elements.
```javascript
// Attribut onclick, hierbei wir ausgeführt das was in "..." steht.
// Also muss Funktion mit () 
<button onclick="alert('Clicked!')">Press</button>

oder 

<script>
  function clickMe() {
    alert('Clicked!')
  }
</script>

<button onclick="clickMe()">Press</button>

// Über onclick property wird eine Referenz einer Funktion übergeben
<button onclick="alert('HTML clicked')" id="btn">Press</button>
<script>
  btn.onclick = function() { // überschreibt den bestehenden Handler
    alert('JS clicked'); 
  };
</script>
```

Den Handler entfernen, indem man _elem.onclick = null_ zuweisen.

### Variante 2 mit addEventListener
Vorteil bei der Benutzung __addEventListener__ ist die Möglichkeit einem Element mehrere Handler zuzuweisen.

_element.addEventListener(event, handler [, phase]);_
-event — Name des Events, für den der Handler ausgeführt wird
-handler — code, Handler-Funktion, die gestartet wird
-phase — Phase (normalerweise nicht verwendet, Standard = false)
-phase true — das Ereignis wird auf dem Weg nach unten abgefangen
-phase false — das Ereignis wird auf dem Weg nach oben abgefangen

```javascript 
<button id="btn">Press</button>

<script>
  function click1() {
    alert('Click1');
  };

  function click2() {
    alert('Click2');
  }

  btn.onclick = () => alert("The native handler");
  btn.addEventListener("click", click1); // Click1
  btn.addEventListener("click", click2); // Click2
</script>
```

## Event Object

Bei der Benutzung der Methode _addEventListener_ kann dem Handler ein _event object_ übergeben werden. Es ist ein Objekt, der vom Browser erstellt wird und wird in der Parameterliste der Funktion in Regel als _event_ oder _e_ bezeichnet. Die Eigenschaften des Objektes können über _event.prop_ oder _event[prop]_ aufgerufen werden. Häufig benutzt werden:
- event.type - Name des Events ('click')
- event.currentTarget - Element für Event eingegeben ist
- event.target - Element-Trigger, Auslöser des Events

Andere Evente:
- eventPhase — Zahl, die Zeigt in welcher Phase Event ist passiert (1-capturing, 2-on target, 3-bubbling)
- timestamp — Datum, wann Event gefeuert wurde
- bubbles — Returnt boolean-Wert, kann diese Event "auftauchen"
- defaultPrevented — prüft ob _preventDefault()_ Methode aufgerufen werden darf
- view — gibt Referenz zum Window-Object zurück, in dem Event aufgerufen wird

Zweiter Argument ist ein Callback, der gefeuert wird, wenn der Event eintritt

Dritter Argument ist ein Objekt/Boolean, der aussagt, wann die Funktion ausgeführt wird _capturing_ oder _bubbling_ (per default ist der Wert auf false eingestellt; entspricht _bubbling_)

Was bedeutet das? Ereignisse können aufgrund der Benutzer- oder Browserinteraktion mit jedem Teil eines Dokuments ausgelöst werden. Sie beginnen und enden nicht einfach am selben Ort; Sie zirkulieren im gesamten Dokument und durchlaufen ihren eigenen Lebenszyklus.

![](../img/m13_eventflow.svg)

1. Wenn der Browser feuert einen Event, Element, auf dem diese Passiert, wird als Ziel markiert -_event.target_
1. Event bewegt sich nach unten von dem Root zu _event.target_ und ruft unterwegs alle Handler, die mit der _addEventListener(..., true)_ auf, wobei true = {capture: true}. Dieser Prozess heißt _capturing_
1. Als nächstes wird der Handler auf dem _event.target_ aufgerufen
1. Und als letztes bewegt sich das Event wieder zu Root und ruft unterwegs alle Handler, die mit der _addEventListener(..., false)_ auf, wobei false = {capture: false}. Dieser Prozess heißt _bubbling_
```
Wichtig!!! Fast alle Events sind _bubbling_ bis auf einige Ausnahmen wie focus
```
Meistens bubbling of Events ist störend. Deshalb existieren Methoden und diese zu unterbinden.
|Funktion|Explanation|
|---|---|
|event.stopPropagation()|stoppt das Bubbling des Events|
|event.stopImmediatePropagation()|Wenn ein Element mehrere Handler besitzt, wird mit der Methode nicht nur Bubbling unterbunden, sondern auch die Restlichen Handler werden nicht ausgeführt|
|event.preventDefault()|Unterbindet standard Benehmen des Events/Browsers|

### Einen Handler vom Element löschen
Dies kann mit der Methode _removeEventListener_ 
```js
element.removeEventListener(event, handler [, phase]);
```
- event - Typ des Events ('click')
- handler - Handler-Funktion, wobei es die selbe Referenz sein soll
- phase - ist meistens Default-Wert _false_

```js
// Richtig
<button onclick="click()" id="btn">Press</button>

<script>
  function click1() {
    alert('Click1');
  };

  btn.addEventListener("click", click1); // Click1
  btn.removeEventListener("click", click1); // 
</script>

// False
<button onclick="click()" id="btn">Press</button>

<script>
  btn.addEventListener("click", function() {
    alert('Click1');
  };); // Click1
  btn.removeEventListener("click", function() {
    alert('Click1');
  };); // 
</script>
```