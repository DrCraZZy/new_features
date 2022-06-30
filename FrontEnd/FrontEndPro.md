# Modul 6

### Selektoren kombinieren

|Selektorkombinator|Bedeutung|
|---|---|
|,|wählt alle passenden Knoten aus|
|Leerzeichen|wählt Elemente aus, die sich innerhalb des angegebenen Elements befinden (unabhängig von der Verschachtelungsebene)|
|>|wählt im Gegensatz zu Leerzeichen nur untergeordnete Elemente aus|
|~|wählt Elemente aus, die sich auf derselben Verschachtelungsebene nach dem angegebenen Element mit demselben übergeordneten Element befinden|
|+|wählt das Element unmittelbar nach dem angegebenen Element innerhalb desselben übergeordneten Elements aus|

### Selektorgewichtung

![selektorgewichtung](../img/frpro_m6_priority.svg)

Mithilfe _!important_ kann man Gewichtung eines Selektors anheben. (Ist verboten zu benutzen).

### Maßen in CSS
|Einheiten|Beschreibung|
|---|---|
|px|Pixel|
|in|Zoll|
|cm|Centimetr|
|mm|Millimetr|
|pt|Punkt = 1/72 Zoll|
|pc|Pika = 12 Punkt|

__relative größen__
|Einheiten|Beschreibung|
|---|---|
|em|Schriftgröße des aktuellen Elements|
|ex|Zeichenhöhe x|
|ch|Zeichenbreite 0 des aktuellen Elements|
|rem|Schriftgröße des Stammelements|

|Einheiten|Beschreibung|
|---|---|
|vw|1% der Breite viewport|
|vh|1% der Höhe viewport|
|vmin|1% der min Änderung viewport|
|vmax|1% der max Änderung viewport|

### Block-Modell der CSS
![css_block-modell](../img/Margin-Padding-1.jpeg)

### Position
Position - eine der Eigenschaften, mit der man Elemente in einer anderen Reihenfolge als im klassischen Dokumentenfluss anordnen kann.

Zusätzliche Eigenschaften, die die Position des Elements bestimmen:
- top
- right
- bottom
- left

Zusätzliche Eigenschaften funktionieren jedoch nur, wenn _position_ festgelegt ist.

|Wert der _position_|Bedeutung|
|---|---|
|position: static;|Das Element befindet sich in seinem normalen Zustand an seiner Stelle im Dokument. Die Eigenschaften _top_, _right_, _bottom_, _left_ und _z-index_ gelten nicht für ein solches Element. Dies ist der Standardwert.|
|position: relative;|Ein Element mit diesem Wert wird __relativ__ zu seiner normalen Position positioniert, indem die Eigenschaften _top_, _right_, _bottom_ und _left_ verwendet werden.|
|position: fixed;|Das Element wird relativ zum Ansichtsfenster positioniert, dh seine Position bleibt beim Scrollen immer gleich.|
|position: absolute;|Das Element wird relativ zu seinem nächsten Vorfahren positioniert (anstatt wie fixiert relativ zum Ansichtsfenster positioniert zu werden). Wenn ein absolut positioniertes Element keine positionierten Vorfahren hat, verwendet es den Hauptteil des Dokuments und bewegt sich mit dem Scrollen der Seite.|
|position: sticky;|Ein Element ist "klebrig", wenn der Darstellungsbereich der Seite eine bestimmte Position erreicht. Kann als "klebrige" Positionierung übersetzt werden.|

# Modul 7

## _display_-Property

Die _display_-Property steuert, wie ein HTML-Element angezeigt wird. 

- display: block;
- display: inline;
- display: inline-block;
- display: none;
- display: flex;
- display: grid;

![diplay-property](../img/frpro_display.png)

___Blockelemente___ (\<div>, \<h1>-\<h6>, \<header>, \<p>) sind ein rechteckiger Bereich, der die gesamte mögliche Breite einnimmt. 

___Inline-Elemente___ (\<img>, \<span>, \<a>, \<q>, \<code>) sind ein direkter Teil einer Zeile und werden verwendet, um das Erscheinungsbild von Text logisch hervorzuheben oder zu ändern. Daher entspricht ihre Breite in einer normalen Situation dem Inhalt plus Rahmen und Polsterung, und die Eigenschaften in Bezug auf Größen gelten nicht für sie.

### block
Bildschirmsperre; ändert die Situation für Inline-Elemente vollständig. Wie Sie im folgenden Beispiel sehen können, nimmt span, das normalerweise verwendet wird, um den Stil eines bestimmten Textelements zu ändern, jetzt die volle bereitgestellte Breite ein, und es kann eine Höhe angegeben werden. Ein Element, dessen Anzeigeeigenschaft auf Block eingestellt ist, verhält sich wie ein Blockelement, unabhängig davon, ob es tatsächlich ein Blockelement ist oder nicht.

### inline
Eigenschaftsanzeige: Inline; Stattdessen verhalten sich Elemente auf Blockebene wie Inline-Elemente. Wenn ein Element diesen Wert hat, verhält es sich wie ein Inline-Element (solche Elemente werden nacheinander in derselben Zeile platziert). Breite und Höhe eines Elements werden durch den Inhalt bestimmt und können nicht verändert werden. Sie können beliebige Größenwerte für ein leeres Element mithilfe von Padding und Rändern festlegen, wie dies im Beispiel unten getan wird.

### none
Ein Element mit __display: none;__ vollständig aus dem Layout der Seite verschwinden. Es wird kein Platz dafür reserviert, seine Anwesenheit kann nur aus der Dateistruktur erkannt werden. Diese Eigenschaft wird häufig verwendet, um Dropdown-Menüs auf Seiten zu organisieren. Es sollte nur sichtbar sein, wenn der Benutzer die Maus über ein Listenelement bewegt, ansonsten erscheint das Menü in keiner Weise. Das heißt, allen seinen Elementen wird die Eigenschaft __display: none;__ zugewiesen.

### inline-block
Eigenschaftsanzeige: Inline-Block; ermöglicht es dem Element, innerhalb der Linie zu bleiben, behält aber gleichzeitig eine Reihe von Blockeigenschaften bei, von denen die wichtigsten die Abmessungen sind.

### flex
Die Eigenschaft _display: flex_ wird nicht dem Element, der Positioniert werden soll, eingegeben. Sondern dem Container in dem Elemente plaziert werden müssen.

Es gibt 2 Achsen, Hauptachse:
![flex-main](../img/FR-A3-flex1.gif)

und zusätzlich Achse:
![flex-not-main](../img/FR-A3-flex2.gif)

Nach dem Hinzugüfen der Eigenschaft _display: flex;_ dem Container werden alle darin enthaltene Element entlang der Hauptachse ausgerichtet. Mit _flex-direction_ Position und Reihnfolge der Elemente bestimmen.

_flex-direction_ Element ausrichten _row_, _row-reverse_, _column_, _column-reverse_

_flex-wrap_ - Artikel in die nächste Reihe umbrechen (gilt nur, wenn die kombinierte Breite der Artikel größer ist als die des Containers)

_align-content_ - gilt nur, wenn es mehrere Reihen da sind ( flex-wrapper )

_justify-content_
_flex-start_ — Anfang der Flexbox-Zeile
_flex-end_ — Ende der Flexbox-Zeile
_center_ — Zentrum der Zeile
_space-between_ — vom Anfang bis Ende mit gleichmäßengen Abständen zwischen den Elementen
_space-around_ — ordnet alle Elemente auf die Breite/Höhe mit gleichmäßigen Abständen

_align-items_ - ausrichten nach auf der zusatz Achse
_stretch_ — Element streching, wenn Höhe nicht fixiert
_flex-start_ — Anfang der Zusatzachse
_flex-end_ — Ende der Zusatzachse
_center_ - Zentral

_align-self_ - richtet Flex-Element auf der Zusatzachse aus. Wird dem bestimmten Element zugeordnet
_align-self_ - auto;
_align-self_ - center; /* Put the item around the center */
_align-self_ - flex-start; /* Put the flex item at the start */
_align-self_ - flex-end; /* Put the flex item at the end */
_align-self_ - baseline; /* Baseline alignment */
_align-self_ - stretch; /* Stretch 'auto'-sized items to fit the container */

_order_ - Damit kann man die Reihenfolge der Element eingeben. (Default: _order: 0_) Kann sowohl positiv als auch negativ sein.

### grid

Mithilfe von _grid_ können Spalten erstellt werden. 
```html
<div class="grid-wrapper">
    <div class="grid-item item-1"></div>
    <div class="grid-item item-2"></div>
    <div class="grid-item item-3"></div>
    <div class="grid-item item-4"></div>
    <div class="grid-item item-5"></div>
</div>
```

```css
.item-1 {
    background-color: rgb(161, 48, 48);
}

.item-2 {
    background-color: rgb(49, 163, 68);
}

.item-3 {
    background-color: rgb(34, 32, 180);
}

.item-4 {
    background-color: rgb(207, 219, 29);
}

.item-5 {
    background-color: rgb(175, 52, 165);
}

.grid-wrapper {
    display: grid; /* 1 */
    grid-template-columns: 200px 200px; /* 2 */
    grid-template-rows: 100px 100px 100px; /* 3 */
}

/* oder */

.grid-wrapper {
    display: grid;
    grid-template-columns: 500px 200px;
    grid-template-rows: 100px 300px 100px;
} 
```

Es muss nicht jede Spalte/Zeile aufgeschrieben werden, wenn die Größen gleich sind, kann auch _repeat()_ benutzt werden.

```css
.grid-wrapper {
    display: grid;
    grid-template-columns: repeat(2, 200px);
    grid-template-rows: repeat(3, 100px);
}
```

Damit die Größen (Breite) der Spalten sich flexibel verhält werden "Verhältnisseinheiten" __fr__ verwendet.

```css
grid-template-columns: 1fr 1fr; /* zwei Spalten 1 zu 1*/

grid-template-columns: 2fr 1fr; /* zwei Spalten 2 zu 1*/
```

Damit die Anzahl der Zellen pro Reihe sich anpasst, können kann __auto-fit__ anstatt Anzahl der spalten benutzt werden.

```css
.grid-wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fit, 200px);
    grid-template-rows: auto;
}

.grid-item {
    min-height: 100px;
}
```

Damit der Inhalt des Grides immer gut aussieht:

```css
.grid-wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    /* auto-fit - Anzahl der Spalten wird automatisch angepasst */
    /* minmax(200px, 1fr) - min-Größe 200px; max-Größe die komplette Breite, die zur verfügung steht */
    grid-template-rows: auto;
    /* anzahl der Zeilen hängt von der Breite des Fensters ab */
    grid-gap: 2vw;
    /* grid-gap - macht Abstände zwischen den Zellen möglich */
}
```

# Modul 8

## Transition

Animationen macht Design schöner, kann aber Performance beeinflussen.

Transition - ist eine CSS Eigenschaft für einfache Übergänge.

_transition_
```css
transition: background-color 1s ease 0.5s, padding 1s ease-out 0s;

/*background-color - Zeigt was verändert wird*/
/*1s - Zeit für die Animation*/
/*ease - Szenarium der Animation*/
/*0.5s - Zeit verzögerung, wann beginnt die Animation*/
```

_transition-duration_`
```css
/*Zeit für Animationsdauer*/
transition-duration: 1s;
```

_transition-property_
```css
/*Properties, die Animiert werden*/
transition-property: background-color, box-shadow;
```

_transition-delay_
```css
/*Verzögerung der Animation*/
transition-delay: 1s;
```

_transition-timing-function: ease-in-out_
```css
/*Wie die Animation verläuft, bei mehreren properties kann man mehrere Funktionen angeben*/
transition-timing-function: ease-in-out;
```

|Funktion|Bedeutung|
|---|---|
|ease|Функция по умолчанию, переход начинается медленно, разгоняется быстро и замедляется в конце. Соответствует cubic-bezier(0.25,0.1,0.25,1).|
|linear|Переход происходит равномерно на протяжении всего времени, без колебаний в скорости. Соответствует cubic-bezier(0,0,1,1).|
|ease-in|Переход начинается медленно, а затем плавно ускоряется в конце. Соответствует cubic-bezier(0.42,0,1,1).|
|ease-out|Переход начинается быстро и плавно замедляется в конце. Соответствует cubic-bezier(0,0,0.58,1).|
|ease-in-out|Переход медленно начинается и медленно заканчивается. Соответствует cubic-bezier(0.42,0,0.58,1).|
|cubic-bezier(x1, y1, x2, y2)|Позволяет вручную установить значения от 0 до 1 для кривой ускорения. Подробнее о cubic-bezier.|
|initial|Устанавливает значение свойства в значение по умолчанию.|
|inherit|Наследует значение свойства от родительского элемента.|

![Animation](img/frpro_m8_u1_1_new.png)

## CSS animation & @keyframes

@keyframes - ermöglicht eine Animation sehr komplex zu gestalten. Hiermit kann man verschieden Werte der CSS-Props in den verschiedenen Punkten/Fasen der Animation anzugeben. 
```css
@keyframes myAnimation {
    from {
        text-shadow: 0 0 3px black;
    }
    50% {
        text-shadow: 0 0 30px black;
    }
    to {
        text-shadow: 0 0 3px black;
    }
}
```

_animation-name_ - 
```css
<div class="myAnimation"></div>

body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation: pulsing;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}
```

_animation-duration_ - Dauer der Animation
```css
body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation: pulsing 2s;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}
```

_animation-iteration-count_ - Anzahl der Wiederhollungen der Animatin
```css
body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-name: pulsing;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}

/*Kurzschreibweise*/
animation: pulsing 2s infinite;
```

_animation-play-state_ - Animationssteuerung _running_ und _paused_
```css
body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-name: pulsing;
}
.myAnimation:hover {
  animation-play-state: paused;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}
``` 

_animation-fill-mode_ - was passiert mit dem Objekt nach der Animation
|||
|---|---|
|__none__|Objekt kehrt wieder zum Ursprungszustand|
|forwards|Objekt bleibt in dem Zustand der Animation bei 100%|
|backwards|Zustand bis zur Animation|
|both|


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