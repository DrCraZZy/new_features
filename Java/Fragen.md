```
https://habr.com/ru/post/485678/

https://github.com/enhorse/java-interview#%D0%9E%D0%9E%D0%9F

https://javastudy.ru/interview/collections/
```


## Erklären Sie, was OOP ist, und definieren Sie eine Klasse.

Die objektorientierte Programmierung (OOP) ist eine Programmiermethodik, die darauf basiert, ein Programm als eine Sammlung von Objekten darzustellen, von denen jedes eine Instanz einer bestimmten Klasse ist, und Klassen eine Vererbungshierarchie bilden.

Grundprinzipien von OOP: Abstraktion, Kapselung, Vererbung, Polymorphie.

```
Inkapsulierung - Verbergen der Implementierung.
Vererbung - Erstellen einer neuen Entität auf der Grundlage einer bestehenden.
Polymorphismus - Fähigkeit, verschiedene Formen für dieselbe Entität zu haben.
Abstraktion - eine Reihe gemeinsamer Merkmale.
```

Eine Klasse ist eine Vorlage, die die allgemeinen Eigenschaften einer Gruppe von Objekten beschreibt. Diese Eigenschaften können sowohl Eigenschaften von Objekten (Größe, Gewicht, Farbe usw.) als auch Verhaltensweisen, Rollen usw. sein.

<hr>

## Was ist der Unterschied zwischen einer abstrakten Klasse und einer Schnittstelle, in welchen Fällen würden Sie beide verwenden?

Abstrakte Klassen werden nur verwendet, wenn es einen Beziehungstyp __is a__ gibt; Schnittstellen können durch Klassen implementiert werden, die nicht miteinander verwandt sind.

Eine abstrakte Klasse kann Methoden implementieren; Eine Schnittstelle kann ab Java 8 statische Methoden implementieren.

Eine Schnittstelle kann Konstanten und Methoden beschreiben. Alle Schnittstellenmethoden sind standardmäßig öffentlich (öffentlich) und abstrakt (abstrakt), und Felder sind öffentlich statisch final. Seit Java 8 können Schnittstellen Standard- und statische Methoden implementieren.

In Java kann eine Klasse viele Interfaces erben (implementieren), aber nur eine abstrakte Klasse.

Bei abstrakten Klassen verlieren Sie die Identität der Klasse, die sie erbt; Mit Schnittstellen erweitern Sie lediglich die Funktionalität jeder Klasse.

<hr>

## Что разного/общего у классов ArrayList и LinkedList? Когда лучше использовать ArrayList, а когда — LinkedList?

ArrayList ist als reguläres Array implementiert. Daher müssen Sie beim Einfügen eines Elements in die Mitte zuerst alle Elemente danach um eins verschieben und erst dann ein neues Element in den frei gewordenen Raum einfügen. Aber es implementiert schnell das Nehmen und Ändern eines Elements - die Get- und Set-Operationen, da wir uns in ihnen einfach auf das entsprechende Element des Arrays beziehen.
LinkedList ist intern anders implementiert. Es ist als verkettete Liste implementiert: ein Satz einzelner Elemente, von denen jedes einen Link zum nächsten und vorherigen Element speichert. Um ein Element mitten in eine solche Liste einzufügen, genügt es, die Links seiner zukünftigen Nachbarn zu ändern. Aber um das Element mit der Nummer 130 zu erhalten, müssen Sie alle Objekte von 0 bis 130 nacheinander durchgehen.
Wenn Sie viele Elemente in der Mitte der Sammlung einfügen (oder entfernen) müssen, ist es besser, LinkedList zu verwenden. In allen anderen Fällen - ArrayList.

LinkedList benötigt mehr Speicher, um die gleiche Anzahl von Elementen zu speichern, da es neben dem Element selbst auch Zeiger auf die nächsten und vorherigen Elemente der Liste gibt, während in ArrayList die Elemente einfach der Reihe nach gehen.

<hr>

## Was ist die Besonderheit der Methoden _hashCode_ und _equals_? Wie werden die hashCode- und equals-Methoden in der Object-Klasse implementiert? Welche Regeln und Konventionen gibt es für die Umsetzung dieser Methoden? Wann gelten sie?

Dies ist eine in __Object__ definierte Methode, die zum Vergleichen von Objekten verwendet wird. Beim Vergleichen von Objekten mit __==__ erfolgt der Vergleich durch Referenz. Beim Vergleich durch __equals()__ wird ein Vergleich anhand der Zustände von Objekten durchgeführt (die Implementierung der equals-Methode für eine neu erstellte Klasse fällt auf die Schultern der Entwickler). Mathematisch bezeichnet __equals()__ eine Objektäquivalenzbeziehung. Eine äquivalente Relation ist eine, die symmetrisch, transitiv und reflexiv ist.

```
Reflexivität: Für jedes Nicht-Null-x gibt x.equals(x) true zurück;

Transitivität: Wenn x.equals(y) und y.equals(z) für x, y und z ungleich Null zurückgeben, gibt x.equals(z) ebenfalls true zurück;

Symmetrie: Für x und y ungleich Null muss x.equals(y) genau dann wahr zurückgeben, wenn y.equals(x) wahr zurückgibt.

Auch für alle Nicht-Null-x sollte x.equals(null) false zurückgeben.
```

Achten Sie beim Überschreiben von __equals()__ darauf, die Methode __hashCode()__ zu überschreiben. Gleiche Objekte müssen dieselben Hashcodes zurückgeben.

Der Hashcode ist eine Zahl. Genauer gesagt handelt es sich um eine Bitkette fester Länge, die aus einem Array beliebiger Länge erhalten wird. In Java-Begriffen ist ein Hashcode das ganzzahlige Ergebnis einer Methode, der ein Objekt als Eingabeparameter übergeben wird.

Diese Methode ist so implementiert, dass der Hashcode für dasselbe Eingabeobjekt immer gleich ist. Es versteht sich, dass die Menge möglicher Hash-Codes durch den primitiven Typ int begrenzt ist und die Menge der Objekte nur durch unsere Vorstellungskraft begrenzt ist. Dies impliziert die Aussage: "Eine Menge von Objekten ist mächtiger als eine Menge von Hash-Codes." Aufgrund dieser Einschränkung ist es durchaus möglich, dass die Hash-Codes verschiedener Objekte übereinstimmen.

```
Das Wichtigste hier ist, Folgendes zu verstehen:

Wenn die Hash-Codes unterschiedlich sind, dann sind die Eingabeobjekte garantiert unterschiedlich.

Wenn die Hash-Codes gleich sind, sind die Eingabemerkmale nicht immer gleich.

Die Situation, wenn verschiedene Objekte die gleichen Hash-Codes haben, wird als Kollision bezeichnet. Die Wahrscheinlichkeit einer Kollision hängt vom verwendeten Hashcode-Erzeugungsalgorithmus ab.
```

<hr>

## Warum ist es besser, das Passwort in char[]/byte[] statt in String zu speichern?

Ein Literal-String gibt sofort das Passwort preis, außerdem wird es immer im String-Pool gespeichert
byte[]/char[] kann nach Gebrauch zurückgesetzt werden und alle Verweise darauf entfernen