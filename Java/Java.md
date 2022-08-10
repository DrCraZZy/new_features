# <u>Java</u>

### JDK
![JDK](../img/JDK.png)

### JRE
![JRE](../img/JRE.png)


Abstraction

Incapsulation

Polymorphism - mehrere Formen. Ist eine Fähigkeit mithilfe eines Interfaces

Inheritance - ist ein Prozess bei dem ein Objekt bekommt Eigenschaften eines anderen Objektes. 

## Datatypes
|Type|Value|
|---|---|
|byte| min: -128|
|    | max:127
|short| min: -32 768
|     | max: 32 767
|int | min: -2 147 483 648
|     | max: 2 147 483 647
|long | min: -9 223 372 036 854 775 808
|     | max: 9 223 372 036 854 775 807
|float | min: -3.4E+38
|     | max: 3.4E+38
|double| min: -1.7E+308
|      | max: 1.7E+308
|char| min: 0
|     | max: 65536
|boolean| min: false
|       | max: true

### _if statement_
```java
if(statement) {

} else if (statement) {

} else {

}
```

### _switch statement_
```java
switch(statement) {
    case [check value]:
        ...
        break;
    case [check value]
        ...
        break;
    case[]:
    case[]:
    case[]:
        ...
        break;
    defautl:
        ...
        break;
}
```

## OOP (Modul 6)

### Vererbung (Inheritance)
Dies ist eine Eigenschaft des Systems, mit der Sie eine neue Klasse basierend auf einer vorhandenen Klasse mit teilweise oder vollständig geliehener Funktionalität beschreiben können.
### Verkapselung (Encapsulation)
Es ist eine Eigenschaft des Systems, mit der Sie Daten in einer Klasse kombinieren und Implementierungsdetails vor dem Benutzer verbergen können.
### Polymorphismus (Polymorphism)
Es ist eine Möglichkeit, verschiedene Formen anzunehmen. In der Programmierung bedeutet dies, dass derselbe Code je nach Bedingungen unterschiedlich ausgeführt werden kann. Polymorphismus ist statisch und dynamisch.

## Abstrakte-Klassen und Interfaces


## Classes (Inner/Nested/Anonymous)


## Input- / OutputStream


## Exception


## Multithreading


## Datenstrukturen
__Datenstruktur__ - Daten werden in einer bestimmten Art und Weise angeordnet. Es gibt dabei verschiedene Datenstrukturen, jede hat Vor-und Nachteile. Eine bekannte Datenstruktur ist zum Beispiel das Array. Dort werden die Daten quasi in einer Tabelle hinterlegt. Zugriff auf die Daten erfolgt über den Index.

__Algorithmus__ - Ein Algorithmus ist eine Kette von Anweisungen um ein Problem zu lösen. Zum Beispiel, sobald man etwas bei google suchst, sucht ein Algorithmus die Informationen. Im Grunde ist ein Algorithmus eine Funktion / Methode, welches ein bestimmtes Problem löst.

__O-Notation__ - Die O-Notation sagt etwas über die Performance eines Algorithmus aus. Die Performance gibt Auskunft darüber wie lange ein Algorithmus braucht um ein bestimmtes Problem / Aufgabe zu lösen.

__BubbleSort__
Beim Bubblesort Algorithmus wird ein Array – also eine Eingabe-Liste – immer paarweise von links nach rechts in einer sogenannten Bubble-Phase durchlaufen. Man startet also mit der ersten Zahl und vergleicht diese dann mit ihrem direkten Nachbarn nach dem Sortierkriterium. Sollten beide Elemente nicht in der richtigen Reihenfolge sein, werden sie ganz einfach miteinander vertauscht. Danach wird direkt das nächste Paar miteinander verglichen, bis die gesamte Liste einmal durchlaufen wurde. Die Phase wird so oft wiederholt, bis der gesamte Array vollständig sortiert ist.

__Rekursion__
Eine Methode, die sich selbst aufruft.

### Komplexität O-Notation
 - O(1) Konstant
 - O(n) Linear
 - O(log_2 n) Logarithmisch
 - O(n^2) Quadratisch
 - O(n^3) Kubisch
 - Ο(n log n) n log n

![complexity](../img/JAVA_15_GRAPH.jpg)

### Collection Übersicht
![collection](../img/Collection-framework-hierarchy.png)

### __List__
__ArrayList__
ArrayList ist im Inneren ein Array. Der Unteschied von Array lieg daran, dass ArrayList das Array intern erweitert, wenn wir mehr Platz für neue Elemente benötigen. Bei dem ausruf
```java
List<String> list = new ArrayList<>();
```
wird intern ein Array mit der Größe 10 erstellt. Wenn man die Größe beeinflußen möchte, kann man eine Überladung des Konstruktors aufrufen.
```java
List<String> list = new ArrayList<>(25);
```
Außer dem ist es auch möglich bei der Initialisierung gleich eine Collection zu übergeben
```java
Queue<String> queue = new LinkedList<>();

queue.add(“John”);
queue.add(“Sam”);
queue.add(“Mary”);
queue.add(“Smith”);
queue.add(“Adam”);

List<String> list = new ArrayList<>(queue);
```
Bei der Arbeit kann man nicht auf inneres Array zugreifen. Man arbeitet nur mit den Daten die in ArrayList hinzugefügt wurden. Wenn innere Array volle größe erreicht hat, vergrößert sich das Array automatisch. Normalerweise verdoppelt sich die Größe.

__LinkedList__
LinkedList ist eine Datenstruktur, die gleich zwei Interfaces implementiert: Queue und List. Im Inneren ist es keine Array sondern eine Kette der Objekte der Klasse Node.
```java 
private static class Node<E> {
   E item;        // Referenz zum Objekt in dem Node
   Node<E> next;  // Referenz zum nächsten Objekt der Klasse Node
   Node<E> prev;  // Referenz zum vorherigen Objekt der Klasse Node

   Node(Node<E> prev, E element, Node<E> next) {
       this.item = element;
       this.next = next;
       this.prev = prev;
   }
}
```

![LinkedList_Organisation](../img/JAVA_15_LINKEDLIST.png)

Wenn wir ein Element in LinkedList einfügen, prüfen wir, ob die Liste leer ist. Wenn die Liste leer ist, wird ein Node-Objekt erstellt, das keine Verknüpfungen zu den vorherigen und nächsten Node hat. Bei der nächsten Hinzufügung wird jeder vorhandene NOde überprüft, um zu sehen, ob es einen Link zum nächsten Node gibt. Wenn also ein solcher Link für einen bestimmten Node null ist, dann ist der Knoten der letzte in der Sammlung, und das hinzugefügte Element kann daran „angehängt“ werden. Dasselbe passiert mit der Suche, nur vergleichen wir jetzt das gewünschte Element mit dem Element im Knoten und folgen bei Ungleichheit dem Link zum nächsten Knoten.

__Vergleich ArrayList и LinkedList__

|Operation|ArrayList|LinkedList|
|---|---|---|
|Anfügen/Löschen am Anfang|O(n)|O(1)|
|Anfügen/Löschen am Ende|O(1)|O(n)|
|Element per Index|O(1)|O(n)|
|Contains|O(n)|O(n)|

Wenn man Elemente häufig am Anfang ändern möchten, verwendet man LinkedList.
In anderen Fällen ist es besser, ArrayList den Vorzug zu geben.

### Set
Das Hauptmerkmal der Set-Interfaces ist das Fehlen von Duplikaten in dieser Sammlung. Ein einzigartiger Satz von Elementen ist das Hauptmerkmal dieser Datenstruktur. Schnelles Hinzufügen, Entfernen und Finden im Set ist ein ebenso wichtiges „Feature“. Vorteil dieser Struktur besteht darin, schnell zu überprüfen, ob ein Objekt in der Menge vorhanden ist, schnell ein Objekt zu diesert Menge hinzuzufügen und zu entfernen. Die Einzigartigkeit der Elemente hilft uns, alle oben genannten Operationen in einer __konstanten  Zeit__ auszuführen.

![hash_function](../img/JAVA_15_HASHTABLE.png)

Eine Hash-Tabelle ist ein Java-Array. Darin liegen die Elemente des HashSets. Aber unter welchem Index. Um den Index des Objektes zu berechnen wird __hash-function__ benutzt. Sie wird benötigt, um die Objekte  möglichst gleichmäßig über das interne Array zu verteilen. Die __hash-function__ benutzt das Objekt um den Index zu berechnen. Die __hash-function__ kann in jeder Klasse überschrieben werden (geerbt von Object-Klasse -> hashCode). 

 Bei der Generierungs des Indexes für Hash-Table müssen in der __hash-function__ nicht veränderbare Felder eines Objektes benutzt werden. Innerhalb desselben Programms darf sich das Ergebnis eines hashCode()-Aufrufs nicht ändern. Wenn die Methode equals() true zurückgibt, müssen Aufrufe von hashCode() für diese beiden gleichen Objekte dasselbe Ergebnis zurückgeben. Dies bedeutet, dass hashCode() entweder alle oder weniger der in equals() verwendeten Variablen zum Vergleich verwenden kann. Wenn equals() false zurückgibt, sind hashCode()-Aufrufe nicht erforderlich, um unterschiedliche Ergebnisse zurückzugeben.

__Kollisionen in einer Hash-Tabelle__

In dem Fall, wenn zwei verschiedene Objekte zufällig gleichen _hash code_ liefern, kann es zu einer Kollision kommen. Das erste Element passt problemlos in die Tabelle, aber das zweite geht am selben Index vorbei und sieht, dass die Zelle bereits belegt ist. In diesem Fall vergleicht Java das Objekt in der Tabelle am Index mit dem Objekt, das wir einfügen möchten. Wenn die Elemente gleich waren, ist alles einfach - Sie müssen nichts eingeben.

![hash_collision](../img/JAVA_15_COLLISION.png)

In dieser Abbildung sehen wir, dass hashCode() für John Smith und Sandra Dee gleich berechnet wurde. Dies sind verschiedene Objekte, und jetzt muss die Implementierung der Hash-Tabelle selbst bestimmen, wo das neue Element platziert werden soll. In diesem Beispiel sehen wir, dass wir den nächsten Index der Reihe nach genommen und dort platziert haben. Wenn in diesem Fall der nächste Index bereits ein Objekt enthält, wird die Operation wiederholt (Vergleich und Auswahl des nächsten Index). Als Ergebnis stellt sich heraus, dass wir bei einer Kollision in der Tabelle beim Füllen und Suchen iterativ vorgehen müssen, was die Laufzeit des Algorithmus verschlechtert.

Daher ist eine gute Hash-Tabelle eine, die ein gutes Verhältnis zwischen gefüllten Zellen und leeren Zellen aufweist, die Verteilung der Elemente gleichmäßig ist und keine langen Gruppen benachbarter Indizes gibt, in denen keine freien Zellen vorhanden sind.

Wie korreliert die berechnete Hash-Funktion mit dem Index der Hash-Tabelle? Schließlich kann das Ergebnis der Funktion beispielsweise die Zahl 725 sein, und die Größe der Tabelle ist auf 50 Elemente begrenzt.

In diesem Fall kann __%__ benutzt werden, dabei wird das Ergebnis auf die Länge geteilt mit __%__.

Es gibt mehrere Möglichkeiten, die Anzahl der Kollisionen zu reduzieren. Eine davon besteht darin, die berechnete Funktion mit einer Primzahl (z. B. 7 oder 13) zu multiplizieren. Eine andere besteht darin, einen anderen Tabelleniterationsschritt zu verwenden, wenn eine Kollision auftritt (z. B. nicht 1, sondern 5).

__HashSet__

HashSet ist die am häufigsten verwendete Implementierung der Set-Schnittstelle, es arbeitet mit einer internen HashMap (es unterscheidet sich von einer Hash-Tabelle durch die Möglichkeit, Null hinzuzufügen, und durch fehlende Synchronisation). Aus diesem Grund ist es nicht garantiert, dass die Reihenfolge beibehalten wird, in der die Elemente hinzugefügt wurden (aufgrund derselben Hash-Tabelle).

```java
//Ein leerer Satz wird erstellt, und darin wird ein hashMap-Objekt mit einer Anfangsgröße von 16 und einem standardmäßigen (Standard-)Füllfaktor von 0,75 erstellt. Wenn 75% der Größe belegt ist verdoppelt sich die Größe
Set<String> set = new HashSet<>();

//Eine leere Menge wird mit einer Anfangsgröße gleich dem übergebenen Argument erstellt.
Set<String> set = new HashSet<>(25);

//Ein leerer Satz wird mit der anfänglichen Größe und dem Füllfaktor gleich den übergebenen Argumenten erstellt.
Set<String> set = new HashSet<>(25, 0.9);

//Mit anderen Collection
List<String> list = new ArrayList<>();
list.add("John");
list.add("Sam");
list.add("Mary");
list.add("Smith");
list.add("Adam");

Set<String> set = new HashSet<>(list);
```

__LinkedHashSet__

LinkedHashSet — Implementierung einer Hash-Tabelle und einer LinkedList zur gleichen Zeit bewahrt dieses Objekt zusätzlich zu Funktionen wie in HashSet die Reihenfolge der hinzugefügten Elemente.

__TreeSet__

TreeSet — Implementierung von NavigableSet, ermöglicht es Ihnen, die Elemente in der Reihenfolge zu speichern, die der "normalen Sortierung" entspricht. Was sehr wichtig zu wissen ist: nicht alle Objekte können dem Set dieser Implementierung hinzugefügt werden, sondern nur Objekte der Klassen, die das Interface __java.lang.Comparable__ implementieren.

![hash_function](../img/JAVA_15_hashset.svg)

<hr><hr>

### Map
Map - speichert Key-Value - Paar

__HashMap__

Meist benutzte Implementierung der Map ist HashMap.
![hash_map](../img/JAVA_15_HASHMAP.png)

Links (table[]) ist die Hash-Tabelle. Beim Hinzufügen eines Schlüssel-Wert-Paares zur Map wird der HashCode für den Schlüssel berechnet, daraus der Index des internen Arrays berechnet und das Node-Objekt dort platziert:
<hr><hr>

## DateTime API
_java.util.Date_ ist Deprecated dafür muss man jetzt _java.time_ benutzen. 

|Typ|Beschreibung|
|---|---|
|LocalDate| Objekt des Types enthält nur Datum (ohne Uhrzeit)|
|LocalTime| Objekt des Types enthält nur Uhrzeit (ohne Datum)|
|LocalDateTime| Objekt des Types enthält Datum und Uhrzeit|
|ZonedDateTime| Objekt des Types enthält Datum, Uhrzeit und Zeitzone|

Für das erstellen der Objekt der Klassen werden _static_ - Methonden benutzt:

|Estellen|Beispiel|
|---|---|
|LocalDate.now()|2007-12-03|
|LocalTime.now()|10:15:30|
|LocalDateTime.now()|2007-12-03T10:15:30|
|ZonedDateTime.now()|2007-12-03T10:15:30+01:00 Europe/Paris|

Andere Konstruktoren der Klassen:

|Konstruktor|Beispiel|
|---|---|
|public static LocalDate of(int year, int month, int dayOfMonth)|LocalDate.of(2013, 2, 22)|
|public static LocalDate of(int year, Month month, int dayOfMonth)|LocalDate.of(2013, Month.February, 22)|
|public static LocalTime of(int hour, int minute)|LocalTime.of(6, 15)|
|public static LocalTime of(int hour, int minute, int second)|LocalTime.of(6, 15, 54)|
|public static LocalDateTime of(int year, int month, int dayOfMonth, int hour, int minute)|LocalDateTime.of(2013, 2, 22, 6, 15)|
|public static LocalDateTime of(int year, int month, int dayOfMonth, int hour, int minute, int second)|LocalDateTime.of(2013, 2, 22, 6, 15, 54)|
|public static ZonedDateTime of(LocalDate date, LocalTime time, ZoneId zone|ZonedDateTime.of(LocalDate.of(2013, 2, 22), LocalTime.of(6, 15), ZoneId.of("US/Eastern"))|
|public static ZonedDateTime of(LocalDateTime localDateTime, ZoneId zone)|ZonedDateTime.of(LocalDateTime.of(2013, 2, 22, 6, 15), ZoneId.of("US/Eastern"))|

Für alle verfügbare TimeZones - _ZoneId.getAvailableZoneIds()_

|Methonden für mathematische Operationen mit der Zeit (gibt auch mit _minus_):|
|---|
|LocalDate plusDays(long days)|
|LocalDate plusMonths(long months)|
|LocalDate plusWeeks(long weeks)|
|LocalDate plusYears(long years)|
|LocalTime plusHours(long hours)|
|LocalTime plusMinutes(long minutes)|
|LocalTime plusSeconds(long seconds)|
|LocalTime plusNanos(long nanos)|
|LocalDateTime plusYears(long years)|
|LocalDateTime plusNanos(long nanos)|
|ZonedDateTime plusYears(long years)|
|ZonedDateTime plusNanos(long nanos)|

|Methoden für das Setzen der einzelne Werte:|
|---|
|LocalDate withDayOfMonth(int day)|
|LocalDate withDayOfYear(int day)|
|LocalDate withMonth(int month)|
|LocalDate withYear(int year)|
|LocalTime withHour(int hour)|
|LocalTime withMinute(int minute)|
|LocalTime withSecond(int second)|
|LocalTime withNano(int nano)|
|LocalDateTime withYear(int year)|
|LocalDateTime withNano(int nano)|
|ZonedDateTime withYear(int year)|
|ZonedDateTime withNano(int nano)|

Objekte der Typen sind Immutable - alle Änderungen müssen einer neuen Variable zugebwiesen werden.

### _Period und Duration_
_java.time.Period_ 
|Konstruktoren|Beispiel|
|---|---|
|public static Period ofYears(int years)|Period.ofYears(1) - 1 Jahr|
|public static Period ofMonths(int months)|Period.ofMonths(10) — 10 Monate|
|public static Period ofWeeks(int weeks)|Period.ofWeeks(3) — 3 Wochen|
|public static Period ofDays(int days)|Period.ofDays(11) — 11 Tage|
|public static Period of(int years, int months, int days)|Period.of(3, 4, 16) — 3 Jahre, 4 Monata und 16 Tage|

_java.time.Duration_
|Konstruktoren|Beispiel|
|---|---|
|public static Duration ofHours(long hours)|Duration.ofHours(21) — 21 Stunden|
|public static Duration ofMinutes(long minutes)|Duration.ofMinutes(30) — 30 Minuten|
|public static Duration ofSeconds(long seconds)|Duration.ofSeconds(45) — 45 Sekunden|

Diese Klasse werden für das Ändern der Objekte der Klassen _LocalDate_, _LocalTime_, _LocalDateTime_, _ZonedDateTime_ verwendet.

_Konvertierung zwischen alten und neuen API_

Dafür wurde in der neuen API ein klasse _java.time.Instant_ implementiert

|Konstruktor|Beschreibung|
|---|---|
|public static Instant now()|Instant now = Instant.now(); Estellt ein Objekt mit aktueller Zeit|
|public ZonedDateTime atZone(ZoneId object)|Instant -> ZoneDateTime|
|Instant toInstant()| ZonedDateTime -> Instant|
|Instant toInstant()| Date -> Instant|

Convert Date to LocalDateTime:
```java
public LocalDateTime convertToLocalDateTimeViaInstant(Date dateToConvert) {
    return dateToConvert.toInstant()
      .atZone(ZoneId.systemDefault())
      .toLocalDateTime();
}
```

## Lambda-Function
 
Lambda-Funktionen bauen auf _Functional-Intefaces_ auf. _Functional-Inteface_ ist ein Interface, das nur eine abstrakte Methode enthält.

### Lambda syntax 
```java
//Concise
n -> System.out.print(n);
//Expanded
(String n) -> System.out.print(n);
//Verbose
(String n) -> { System.out.print(n); }
```
Link sind Parameter des _Functional-Interface_, Rechts ist die Logik.

|Fall|Regel|Beispiel|
|---|---|---|
|Keine Parameter|Immer Klammer|() -> new Integer(12)|
|Eine Variable ohne Typ|mit oder ohne Klammern| s -> s.contains("m");|
|||(s) -> s.contains("m")|
|Variable mit Typ|immer Klammern|(String s) -> s.length()|
|mehrere Parameter (gleicher Typ)|immer klammern|(s, t) -> s + t|
|mehrere Parameter mit Typ|immer Klammern|(String a, int b) -> a.substring(b)|
|Eine Code Zeile|Kann vereinfacht werden|(int b) -> b + 12|
|||(int b) -> System.out.print(b)|
|||(int b) -> {return b + 12;}|
|Mehrere Zeilen|Nur im Block|(String s) -> {return s.length();}
|||(String s) -> {
|||    System.out.print(s); 
|||    return s;
|||}

!Wichtig:
- Parameter (links) dürfen nicht neudefiniert werden
- Lambda hat zugang zu den Variablen und Parameter der Funktion, in der diese definiert ist. Aber die müssen faktisch _final_ sein. Also man könnte die Variablen/Parameter _final_ setzen und es kommt kein Fehler.

### Standart _functional-intefaces_ (java.util.function)
|Name|Parameter|Return|Methode|Beschreibung|
|---|---|---|---|---|
|Supplier<T>|0|T|get|Liefert Werte. 
|Consumer<T>|1 (T)|void|accept|Consumer, In 1 return 0
|BiConsumer<T, U>|2 (T, U)|void|accept|
|Predicate<T>|1 (T)|boolean|test| 1 параметр и возвращает true-false («проверяльщик»)
|BiPredicate<T, U>|2 (T, U)|boolean|test|принимает 2 параметра и возвращает true-false («двойной проверяльщик»)
|Function<T, R>|1 (T)|R|apply| 1 параметр и возвращает результат другого типа («функция»)
|BiFunction<T, U, R>|2 (T, U)|R|apply|	принимает 2 параметр и возвращает результат другого типа («двойная функция»)
|UnaryOperator<T>|1 (T)|T|apply|	принимает 1 параметр и возвращает результат такого же типа («оператор»)
|BinaryOperator<T>|2 (T, T)|T|apply|	принимает 2 параметра и возвращает результат такого же типа («двойной оператор»)

Method reference - Vereinfachter Lambdaausdruck.

## Interface Default und static-Methoden

Default - Methode ist normale Methode. Die Befindet sich im Interface und hat Schlüsselwort _default_. _Default_ Methoden sind für alle Objekte der Klassen (die dierekt oder indierekt das Interface implementi) verfügbar. Die Methoden könn überschrieben werden und die Methode muss nicht implementiert werden. Wie jede _static_ Methode werden diese über _Interface.methode_ aufgerufen. Wie jede Statische-Methode kann die nicht geerbt werden.

## _Optional< T >_
Ein Optional ist eine Objekt, das man sich als Datenbehälter vorstellen kann, der entweder einen Wert enthält oder leer (empty) ist. Leer ist hier auch nicht gleichbedeutend mit null!

```java
Optional<String> oe = Optional.empty();              // leeres Optional
Optional<String> os = Optional.of("Hallo Welt!");    // enthält den String "Hallo Welt!"

Optional<String> on = Optional.of(null);             // NullPointerException
Optional<String> onb = Optional.ofNullable(null);    // leeres Optional

Optional<Double> optional = Optional.of(22.4d);      // erstellt Optional ohne null Möglichkeit
Optional<Double> optional = Optional.ofNullable(22.4d);  //erstellt Optional mit null Möglichkeit
Optional<Double> optional = Optional.ofNullable(null);
Double nullDouble = null;
Optional<Double> optional = Optional.ofNullable(nullDouble);

// Beispiel
import java.util.Optional;

public class Main {
   public static Optional<Double> average(int... scores) {
       if (scores.length == 0) {
           return Optional.empty();
       }
       int sum = 0;
       for (int score : scores) {
           sum += score;
       }
       return Optional.of((double) sum / scores.length);
   }
}
```

|Methoden|Wenn Optional.empty()|Wenn Optional.of(value)|
|---|---|---|
|get()|throw Runtime| return value|
|ifPresent(Consumer c)||call Consumer with value|
|isPresent()|return false|return true|
|orElse(T other)|return other| return value|
|orElseGet(Supplier s)|return call Supplier|return value|
|orElseThrow(Supplier s)|throw exception of Supplier|return value|

## Stream API

Streams sind aufeinander folgende Bearbeitung einer Collection.
Stream pipeline besteht aus 3 Operationen:
- Source
- Intermediate operations
- Terminal operation

Stream kann nur 1 MAL benutzt werden. Wenn Terminal operation abgeschlossen ist, kann stream nicht noch mal gestartet werden. 

Stream verfolgt lazy Prinzip. Intermediat operations werden nur dann ausgeführt, wenn Terminal operation definiert ist.

### Stream erstellen
```java
Stream<String> empty = Stream.empty(); // leerer Stream
Stream<Integer> singleElement = Stream.of(1); 
Stream<Integer> anyElements = Stream.of(1, 2, 3); 
Stream<Integer> fromArray = Arrays.stream(new Integer[] {1, 2, 3});
Stream<Integer> fromCollection = collection.stream();

List<String> list = Arrays.asList("a", "b", "c");
Stream<String> listStream = list.stream();
```

### Source
Source kann beliebige Collection sein.

### Intermediate operations
```java
// gibt Element zurück, die dem Predicate entsprechen
Stream<T> filter(Predicate<? super T> predicate);

// liefert Stream mit uniq Werten zurück
Stream<T> distinct();

// verkürzt den Stream
Stream<T> limit(long maxSize);
Stream<T> skip(long n);     //überspring die ersten n Elemente

// transformiert die Stream-Elemente
<R> Stream<R> map(Function<? super T, ? extends R> mapper);
<R> Stream<R> flatMap(Function<? super T, ? extends Stream<? extends R>> mapper);

// Stream sortieren
Stream<T> sorted();
Stream<T> sorted(Comparator<? super T> comparator);
```

### Terminal operations
```java
// prüft ob alle Elemente dem Predicate entsprechen
boolean allMatch(Predicate<? super T> predicate);

// prüft ob ein Element dem Predicate entspricht
boolean anyMatch(Predicate<? super T> predicate);

// prüft ob alle Elemente dem Predicate nicht entsprechen
boolean noneMatch(Predicate<? super T> predicate);

// kombiniert alle stream-Elemente in mutable-Objekt
<R, A> R collect(Collector<? super T, A, R> collector);

// gibt Anzahl der Elemente in Stream
long count();

// gibt ein Element aus dem Stream zur+ck
Optional<T> findAny();
Optional<T> findFirst();

// macht etwas mit jedem Stream-Element
void forEach(Consumer<? super T> action);

// gibt min/max Stream-Element
Optional<T> min(Comparator<? super T> comparator);
Optional<T> max(Comparator<? super T> comparator);

// Kombiniert alle Elemente zu einem Primitiv oder Objekt
<R> R collect(Supplier<R> supplier, BiConsumer<R, ? super T> accumulator,  BiConsumer<R, R> combiner);

// reduce Kombiniert alle Elemente
int[] numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

// 1st argument, init value = 0
int sum = Arrays.stream(numbers).reduce(0, (a, b) -> a + b);

System.out.println("sum : " + sum);

// toArray()
Erstellt einen Array aus dem Ergebenis
```

- IntStream - arbeitet mit int, short, byte, char
- LongStream - arbeitet mit long
- DoubleStream - arbeitet mit double

```java 
// erstellt ein Stream von ... bis ... obere Grenze nicht eingeschlossen
public static IntStream range(int startInclusive, int endExclusive)

public static LongStream range(long startInclusive, final long endExclusive)

// Stream, obere Grenze mit eingeschlossen
public static IntStream rangeClosed(int startInclusive, int endInclusive)

public static LongStream rangeClosed(long startInclusive, final long endInclusive)

// erstellt Stream nach Builder-Prinzip
public static Builder builder()

DoubleStream ds = DoubleStream.builder()
.add(3d)
.add(5.6d)
.add(8d)
.build(); // 3 5.6 8

// erstellt eine Summe von allen Streamelementen
int sum();
long sum();
double sum();

IntStream range = IntStream.range(1, 5);
range.sum(); // 10

// erstellt einen Type ähnlich wie Optional
OptionalDouble average();
DoubleStream ds = DoubleStream.of(2d, 4d, 6d);
ds.average().orElse(Double.NaN); // 4
```

```java
//Collectors
Stream<String> ohMy = Stream.of("lions", "tigers", "bears");
String result = ohMy.collect(Collectors.joining(", ")); // lions, tigers, bears

Stream<String> ohMy = Stream.of("lions", "tigers", "bears");
Double result = ohMy.collect(Collectors.averagingInt(String::length)); // 5.33333333333333333

Stream<String> ohMy = Stream.of("lions", "tigers", "bears");
TreeSet<String> result = ohMy
       .filter(s -> s.startsWith("t"))
       .collect(Collectors.toCollection(TreeSet::new)); // [tigers]

Stream<String> ohMy = Stream.of("lions", "tigers", "bears");
Map<String, Integer> map = ohMy.collect(Collectors.toMap(
       s -> s, String::length
)); // {lions = 5, bears = 5, tigers = 6}
```

## NIO.2 - Non-bloking I/O

- Java 1.4 -> NIO
- Java 1.7 -> NIO.2

### Path
Neu Path alt File
```java
// erstellt relativ Pfad
Path path1 = Paths.get("pandas/cuddly.png");

// erstellt absolut Pfad
Path path2 = Paths.get("c:\\zooinfo\\November\\employees.txt");

// erstellt absolut Pfad bei UNIX
Path path3 = Paths.get("/home/zoodirector");
```

```java
//URI
Path path1 = Paths.get(new URI("file:///c:/zooinfo/November/employees.txt"));
Path path2 = Paths.get(new URI("http://www.wiley.com"));
```

Alt in neu konvertieren
```java
File file = new File("pandas/cuddly.png");
Path path = file.toPath(); // in Path

Path path2 = Paths.get("cuddly.png");
File file2 = path2.toFile(); // in File
```

### Files
```java
// prüfet ob File existiert
boolean exists1 = Files.exists(Paths.get("/ostrich/feathers.png"));
boolean exists2 = Files.exists(Paths.get("/ostrich"));

// prüft ob Filelink stimmt
try {
   Files.isSameFile(Paths.get("/user/home/cobra"), Paths.get("/user/home/snake")); // true
   Files.isSameFile(Paths.get("/user/tree/../monkey"), Paths.get("user/monkey")); // true
} catch (IOException e) {
   // Handle file I/O exception
}

// create directory
try {
   Files.createDirectory(Paths.get("bison/field"));
   Files.createDirectories(Paths.get("bison/field/pasture/green"));
} catch (IOException e) {
   // Handle file I/O exception
}

// copy files
try {
   Files.copy(Paths.get("/panda"), Paths.get("/panda-save"));
   Files.copy(Paths.get("panda/bamboo.txt"), Paths.get("panda-save/bamboo.txt"));
} catch (IOException e) {
   // Handle file I/O exception
}

// verschieben der Files/Ordner
try {
   Files.move(Paths.get("c:\\zoo"), Paths.get("c:\\zoo-new"));
   Files.move(Paths.get("c:\\zoo\\addresses.txt"), Paths.get("c:\\zoo-new\\addresses.txt"));
} catch (IOException e) {
   // Handle file I/O exception
}

// löschen
try {
   Files.delete(Paths.get("vulture/feathers.txt"));
   Files.deleteIfExists(Paths.get("pigeon"));
} catch (IOException e) {
   // Handle file I/O exception
} 

// Files lesen und schreiben
Path path = Paths.get("/animals/gopher.txt");
try (BufferedReader reader = Files.newBufferedReader(path, StandardCharsets.US_ASCII)) { // Выбираем кодировку файла
   // читаем со стрима
   String currentLine = null;
   while ((currentLine = reader.readLine()) != null) {
       System.out.println(currentLine);
   }
} catch (IOException e) {
   // Handle file I/O exception
}

// File lesen
Path path2 = Paths.get("/animals/gorilla");
List<String> data = new ArrayList<>();
try (BufferedWriter writer = Files.newBufferedWriter(path2, Charset.defaultCharset())) {
   writer.write("Hello World");
} catch (IOException e) {
   // Handle file I/O exception
}

// file lesen allLines
Path path = Paths.get("fish/sharks.log");
try {
   List<String> lines = Files.readAllLines(path); // сохраняем строки из файла в лист
   for (String line : lines) {
       System.out.println(line); // выводим содержимое на консоль
   }
} catch (IOException exception) {
   // Handle file I/O exception
}
```

<hr><hr>

## Memory model und Garbage Collection
Speicher einer Anwendung, welche mit _JVM_ gestartet wurde, wird als _native memory_ bezeichnet. Die besteht aus verschiedenen Bereichen. Zwei davon sind __heap__ und __stack__.

__Heap__ ist für Objekte und Klassen vorgesehen:
- alle Threads haben den globalen Zugang zu _heap_ - jeder Thread kann auf jeden Objekt im _heap_ bekommen
- _heap_ wird mit dem Start einer Anwendung erstellt und mit dem Beenden der Anwendung gelöscht
- _heap_ Größe kann sich wehrend der Laufzeit ändern

__Stack__ wird für das Speichern der Ausführungsreihenfolge der Threads benutzt. Jeder _stack_ funktioniert nach dem __LIFO__ Prinzip .
- _stack_ wird bei Thread initialisierung erstellt
- vor jeder Aufruf einer Methode wird ein _stack frame_ erstellt, dieser wird für das Speichern der lokalen Variablen/Parameter (Primitiv) und Links auf Objekt in _heap_
- nach dem Beenden einer Methode wird _stack frame_ gelöscht und Speicher kann für andere Methoden benutzt werden
- nach dem Beenden eines Threads wird auch sein _stack_ gelöscht

__stack__ und __heap__ manuel angeben:
- -Xms{size}, -Xmx{size} - min bis max Größe für _heap_, wenn zuwenig Speicher _java.lang.OutOfMemoryError_
- -Xss{size} - max Größe für _stack_, wenn zuwenig Speicher _java.lang.StackOverflowError_
- size kann in Gigabyte (G/g) oder Megabyte (M/m) oder Kilobyte (K/k) angegeben werden (Beispiel: -Xmx3g / -Xmx3072m /-Xmx3145728)

Beispiel:
```java
//heap
import java.util.*;

public class OOMExample {
   public static void main(String[] args) {
       List<Object> objects = new LinkedList<>();
       for (int i = 0; i < 100; i++) {
           objects.add(new byte[1024 * 1024]);
       }
       System.out.println("Success!");
   }
}

//stack
public class SOExample {
   public static void main(String[] args) {
       // рекурсивный вызов глубиной в
       // 50 тысяч фреймов
       loop(50_000);
       System.out.println("Success!");
   }

   public static void loop(int repeats) {
       if (repeats > 0) {
           loop(repeats - 1);
       }
   }
}
```
```shell
% javac OOMExample.java
% java -Xmx100m OOMExample
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
       at OOMExample.main(OOMExample.java:7)
% java -Xmx200m OOMExample
Success!

% javac SOExample.java
% java -Xss1m SOExample    
Exception in thread "main" java.lang.StackOverflowError
       at SOExample.loop(SOExample.java:8)
       at SOExample.loop(SOExample.java:8)
       at SOExample.loop(SOExample.java:8)
       ...
% java -Xss3m SOExample
Success!
```

## Native Memory
__Native Memory Tracking ([NMT](https://docs.oracle.com/en/java/javase/14/troubleshoot/diagnostic-tools.html#GUID-1F53A50E-86FF-491D-A023-8EC4F1D1AC77))__ - Tool für das Beobachten des Speicherverbrauchs
-XX:NativeMemoryTracking={mode} (mode - ditalisierung der Ausgabe, _off_, _summary_ und _detail_)
Mit dem Tool _jps_ kann man Prozessindentifikator erfahren. Dieser wird für den Tool [_jcmd_](https://docs.oracle.com/en/java/javase/14/docs/specs/man/jcmd.html) benötigt um damit einen Bericht für den Prozess aufzurufen.

```cmd
Prozess kompilieren und starten mit NTM
% javac NMTExample.java
% java -XX:NativeMemoryTracking=detail NMTExample

Prozess ID abrufen
% jps
19248 NMTExample
22225 Jps

Bericht für NMTExample ansehen
% jcmd 19248 VM.native_memory

9248:

Native Memory Tracking:

Total: reserved=5620109KB, committed=667801KB
-                 Java Heap (reserved=4061184KB, committed=561152KB)
                           (mmap: reserved=4061184KB, committed=561152KB)  
 
-                     Class (reserved=1056879KB, committed=4975KB)
                           (classes #474)
                           (  instance classes #401, array classes #73)
                           (malloc=111KB #574)  
                           (mmap: reserved=1056768KB, committed=4864KB)  
                           (  Metadata:   )
                           (    reserved=8192KB, committed=4352KB)
                           (    used=141KB)
                           (    free=4211KB)
                           (    waste=0KB =0.00%)
                           (  Class space:)
                           (    reserved=1048576KB, committed=512KB)
                           (    used=8KB)
                           (    free=504KB)
                           (    waste=0KB =0.00%)
 
-                    Thread (reserved=31947KB, committed=1599KB)
                           (thread #31)
                           (stack: reserved=31808KB, committed=1460KB)
                           (malloc=105KB #188)  
                           (arena=34KB #60)
 
-                      Code (reserved=247725KB, committed=7585KB)
                           (malloc=37KB #398)  
                           (mmap: reserved=247688KB, committed=7548KB)  
 
-                        GC (reserved=208309KB, committed=78425KB)
                           (malloc=23809KB #14174)  
                           (mmap: reserved=184500KB, committed=54616KB)  
 
-                  Compiler (reserved=239KB, committed=239KB)
                           (malloc=74KB #66)  
                           (arena=165KB #5)
 
-                  Internal (reserved=578KB, committed=578KB)
                           (malloc=542KB #998)  
                           (mmap: reserved=36KB, committed=36KB)  

-    Native Memory Tracking (reserved=502KB, committed=502KB)
                           (malloc=176KB #2497)  
                           (tracking overhead=326KB)
```
- _reserved_ - reservierter Speicher
- _committed_ - benutzter Speicher

## Garbage Collector
Solange ein Thread am Leben ist, alle Objekte, die in seinem _stack frame_ verlinkt sind, werden nicht gelöscht. In dem Kontext werden Threads und deren _stack frames_ als __gc roots__.

Codeblock ist Code, der von geschweiften Klammern umgeben ist. Sobald der Thread die Ausführung im verschachtelten Block beendet hat, stehen die Variablen dem äußeren Block nicht mehr zur Verfügung. Wenn die lokale Variable Referenztyp ist, hat die JVM nachdem die Variable den Gültigkeitsbereich verlassen hat, das Recht, die Referenz zu löschen (aber nicht das Objekt, auf das sie zeigt).

Ein Objekt, das den Root-Status hat, wird automatisch als erreichbar betrachtet, und der Garbage Collector hat nur dann das Recht, es zu löschen, wenn dieser Status verloren geht.
Die vollständige Liste der __gc roots__ lautet wie folgt:
- Aktive Threads und Referenzen, die auf ihrem _stack frame_ liegen (sowohl lokale Variablen als auch Methodenparameter).
- Vom Systemklassenloader geladene Klassen.
- Objekte, auf die von Low-Level-Code verwiesen wird, der mit nativer Schnittstelle (JNI) geschrieben oder von der virtuellen Maschine selbst verwendet wird (implementierungsspezifisch).

Der Garbage-Collection-Prozess kann in zwei Phasen unterteilt werden:
- Erstellen eines Erreichbarkeitsdiagramms, ausgehend von den Wurzeln, mit dem Markieren von Objekten als erreichbar (Mark) 
- Das Löschen aller Objekte, die nicht in diesem Diagramm enthalten sind (Sweep).

![GC-Prozess](../img/JAVA_18.2_mark_sweep.gif/)

### Stop The World
Eine der häufigsten Nebenwirkungen der Garbage Collection ist das Anhalten der Welt (Stop The World oder stw-pause). In verschiedenen Phasen der Arbeit des Sammlers muss er die Anwendung möglicherweise unterbrochen werden. Die Pausen selbst sind nicht notwendig, aber sie vereinfachen das Leeren des _heaps_ erheblich. Die meisten Java Virtual Machines können keine Pausen verarbeiten. Der Grund für Pausen ist die Dynamik des Erreichbarkeitsgraphen. Während seiner Durchquerung können zuvor markierte Objekte unzugänglich werden, und der Garbage Collector entfernt möglicherweise nicht, was gerade zu Garbage wurde. Oder umgekehrt – die Wurzel kann auf ein neues Objekt verweisen und der Garbage Collector muss dies berücksichtigen, um die verwendeten Objekte nicht versehentlich zu löschen.

__Generationshypothese__
Der einfachster Weg die Zeit zu sparen ist weniger sinnlose Arbeit zu erledigen. Im Falle der Garbage Collection kann nutzlose Arbeit als unnötiges Durchlaufen von Objekten angesehen werden, die höchstwahrscheinlich kein Garbage sind. Basierend auf empirischen Beobachtungen für objektorientierte Sprachen wurde die sogenannte Generationshypothese formuliert. Im Allgemeinen enthält diese Hypothese zwei Axiome:
- Die Lebensdauer der meisten Objekte ist extrem kurz und sie „sterben jung“.
- Die Zahl der Verweise auf „junge“ Objekte von „alten“ ist gering.

![GC-Prozess](../img/JAVA_18.2_survival.png/)

__Der Algorithmus der Arbeit von Garbage Collectors, der auf der Hypothese von Generationen basiert, kann wie folgt beschrieben werden:__

- Alle Objekte sind Eden zugeordnet.
- Wenn in Eden nicht genügend Speicherplatz vorhanden ist, wird der Garbage Collector ausgelöst. Alle verbleibenden Live-Objekte werden auf S0 kopiert. Das gesamte Eden-Gebiet wird geräumt.
- Wenn in S0 nicht genügend Speicherplatz vorhanden ist, findet ein Garbage Collector unter den verbleibenden Objekten statt. Alle verbleibenden Objekte von S0 werden nach S1 verschoben, S0 wird gelöscht und diese Bereiche werden umgekehrt.
- Wenn Objekte im Survivor Space genügend Bauzyklen durchlaufen haben, um als alt zu gelten, werden sie in die alte Generation verschoben.
- Wenn in der alten Generation nicht genügend Speicherplatz vorhanden ist, findet dort ein Garbage Collector statt. Zusätzlich zum Löschen von Objekten können sie komprimiert werden, um die Speicherfragmentierung zu beseitigen.
- Wenn keine Objekte mehr in die alte Generation platziert werden können, tritt ein Speicherfehler (java.lang.OutOfMemoryError) auf. Denken Sie daran, dass dieser Fehler bei Threads auftritt, die versucht haben, ein Objekt zuzuweisen.

_Es ist erwähnenswert, dass es Situationen gibt, in denen junge Objekte vorzeitig in die alte Generation fallen können. Wenn beispielsweise die Größe eines Objekts die Größe von Eden überschreitet, kann es sofort in der alten Generation zugewiesen werden. Dasselbe gilt für Survival._

Bei einigen Garbage Collectors kann ein Speichermangel nicht nur dann auftreten, wenn es physikalisch unmöglich ist, ein Objekt zuzuordnen, sondern auch, wenn der Garbage Collector die meiste Zeit der Anwendung in Anspruch nimmt, wenn die Anzahl der zu löschenden Objekte gering ist . Diese Situation wird _gc overlimit_ genannt und tritt normalerweise auf, wenn der Garbage Collector mehr als 98 % der Zeit in Anspruch nimmt und nicht mehr als 2 % des Heapspeichers durch der Garbage Collector freigegeben werden.

## Memory leak. Heapdump
Ein Speicherleck ist eine Situation, in der sich Objekte auf dem Heap befinden, die nicht mehr verwendet werden, der Garbage Collector sie jedoch nicht entfernen kann, was zu einer Verschwendung von Speicher führt.

Lecks sind Probleme, da sie Speicherressourcen sperren, was mit der Zeit zu einer Verschlechterung der Performance führt. Und wenn es nicht behoben wird, erschöpft die Anwendung ihre Ressourcen und wird mit einem __java.lang.OutOfMemoryError__-Fehler beendet.

Es gibt zwei Arten von Heap-basierten Objekten: solche, die aktive Referenzen in der Anwendung haben, und solche, auf die von keiner Variablen des Referenztyps verwiesen wird.
Der Garbage Collector entfernt regelmäßig Objekte, die keine aktiven Verweise mehr haben, entfernt jedoch niemals Objekte, auf die verwiesen wird.

### Memory leak durch Inner-Class

None static inner Klassen (anonym) erfordern immer eine Instanz der äußeren Klasse, um initialisiert zu werden. Jede nichtstatische innere Klasse hat standardmäßig einen impliziten (verborgenen) Verweis auf die Klasse, in der sie sich befindet. Wenn wir dieses Objekt der inneren Klasse in unserer Anwendung verwenden, wird es auch nach Abschluss der Arbeit des Objekts der äußeren Klasse nicht vom Garbage Collector zurückgefordert.

### Memory leak durch Static-Fields

Systemloader/Classloader ist __root__ für GC und initialisierte static fields der geladenen Klassen sind aus dem Classloader erreichbar, also darf der GC die nicht entsorgen, weil es immer noch ein Link auf die Felder existiert.

### Memory leak durch nicht geschloßen Resource

Immer wenn men eine neue Verbindung erstellt oder einen Thread öffnet, weist die JVM Speicher für diese Ressourcen zu. Dies können Datenbankverbindungen, eingehende Streams oder Sitzungsobjekte sein. Indem man vergisst, diese Ressourcen zu schließen, kann man Speicher sperren, wodurch sie für den Garbage Collector nicht verfügbar sind. Dies kann selbst dann passieren, wenn eine Ausnahme auftritt, die das Programm daran hindert, den Code auszuführen, der für das Schließen der Ressourcen verantwortlich ist.

# Modul 21 ([Maven](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference))
![](../img/JAVA_25.1_maven.png)

Apache Maven, ein deklaratives Build-Automatisierungssystem, ist weit verbreitet. Auch Maven nutzt das XML-Format, aber pom.xml (die Hauptdatei für Maven) enthält keine einzelnen Befehle, sondern eine Beschreibung des Projekts. Auf den Aufbau der pom-Datei gehen wir später noch genauer ein.

Die Vorteile von Maven gegenüber Ant sind:

- automatisches Abhängigkeitsmanagement;
- gut strukturierte Projekte;
- eine einfachere Montagebeschreibung.

Maven lässt sich auch gut in alle wichtigen Entwicklungsumgebungen integrieren. Um im Fall von Ant ein Projekt ohne IDE zu erstellen, müssen Build-Skripte unterstützt werden. Das Erstellen von Maven kann über die Befehlszeile erfolgen.

Die Nachteile dieses Systems sind normalerweise die Lernschwierigkeiten und die Schwierigkeit, Montageprobleme zu diagnostizieren. Zu beachten ist auch, dass es schwierig ist, die richtigen Plugins zu finden und zu konfigurieren.

Die Übersichtstabelle zeigt die wichtigsten Vor- und Nachteile von Maven:

|Vorteile | Nachteile|
|---|---|
|Abhängigkeitsmanagement|Lernschwierigkeiten|
|Build aus der Befehlszeile|Schwierigkeiten beim Diagnostizieren von Problemen|
|Gute Integration mit vielen IDEs| Schwierigkeiten beim Auffinden von Plugins und Anpassungen|
|Aussagekräftige Beschreibung||
|Erweiterung der Funktionalität mit Plugins||

## Anweisungen zur Installation von Maven unter Windows
1. Laden Sie die Datei bin.zip mit der neuesten Version von der offiziellen Website herunter.
1. Entpacken Sie den Ordner in ein beliebiges Verzeichnis, in dem Sie Maven haben möchten.
1. Fügen Sie M2_HOME=your_maven_path zu Ihren Umgebungsvariablen hinzu (genauso wie Sie JAVA_HOME hinzugefügt haben).
1. Fügen Sie %M2_HOME%\bin zu PATH hinzu, damit Sie Maven-Befehle von überall ausführen können.
1. Führen Sie den Befehl aus:
   ```cmd
   mvn-Version
   ```
1. Wenn alles richtig gemacht wurde, wird die Maven-Version angezeigt.

### Maven-Integration mit Intellij Idea
Als einen der Vorteile von Maven haben wir die gute Integration mit der IDE hervorgehoben. Im Video sehen wir uns an, was so großartig an der Arbeit mit Maven in Intellij Idea ist.

## pom.xml-Struktur. Archetypen
POM (Project Object Model) ist die Hauptdatei für Maven. Die Datei pom.xml enthält Projektinformationen und Konfigurationsdetails, die Maven zum Erstellen des Projekts benötigt. Die Datei pom.xml muss sich im Projektverzeichnis befinden.

Die folgenden Elemente können in pom.xml eingebunden werden:

- Abhängigkeiten;
- Plugins;
- Aufgaben;
- Profile;
- Projektversion;
- weitere Informationen zum Projekt.

Pom-Struktur
Schauen wir uns noch einmal die Struktur der Pom-Datei an, die Idea in der letzten Einheit für uns erstellt hat (die Werte der einzelnen Elemente sind in der folgenden Tabelle aufgeführt):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>org.example</groupId>
    <artifactId>greeting</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</project>
```
Eine solche Struktur ist die minimal erforderliche Pom-Dateistruktur. Betrachten Sie die Werte der einzelnen Elemente in der Tabelle.

|Element|Beschreibung|
|---|---|
|```<Projekt>```| Das Stammelement der Pom-Datei. Wenn Sie es manuell erstellen, müssen Sie hier die grundlegenden XML-Schemaeinstellungen angeben, z. B. das Apache-Schema und die w3.org-Spezifikation. Wenn Sie in IntelliJ IDEA erstellen, werden alle Schemas automatisch angegeben.|
|```<modelVersion>``` |Gibt die aktuelle POM-Version an. Derzeit wird nur 4.0.0 unterstützt, daher wird immer nur diese Version aufgeführt.|
|```<groupId>```| Gibt die Gruppen-ID des Projekts an. Beispielsweise ist org.springframework die ID einer Gruppe von Projekten, die sich auf das Spring Framework beziehen.|
|```<artifactId>```| Gibt den Namen des Projekts an. Zum Beispiel Gruß oder Federkern.|
|```<Version>```| Gibt die Version des Projekts an. Im Beispiel wird -SNAPSHOT auch zur Projektversion hinzugefügt, was bedeutet, dass die Version nicht endgültig ist, sie befindet sich in der Entwicklung.|

Jede erstellte _Pom_-Datei erbt die Konfiguration, die im sogenannten _Super-POM_ definiert ist, das in Maven definiert ist. Tags, die nicht in der für unser Projekt generierten pom.xml definiert sind, verwenden den Standardwert aus dem _Super-POM_.

Sie können das kombinierte Pom (Werte, die in der pom.xml des Projekts angegeben sind, + nicht angegebene Werte, die aus dem _Super-POM_ stammen) anzeigen, das vom Projekt verwendet wird, Sie können den Befehl verwenden:

```cmd
mvn help:effective-pom
```
Beispiel für pom.xml:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <properties>
      <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
      <maven.compiler.source>1.8</maven.compiler.source>
      <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <groupId>org.example</groupId>
    <artifactId>greeting</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>

    <name>Greeting application</name>  
    <url>http://example.org</url>  
    <description>Greeting application</description>  
    <dependencies>
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-lang3</artifactId>
            <version>3.11</version>
        </dependency>
    </dependencies>

    <build>
        <sourceDirectory>src</sourceDirectory>
        <resources>
            <resource>
                <directory>resources</directory>
            </resource>
        </resources>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```
Betrachten wir die zusätzlichen Elemente, die im Beispiel aufgetreten sind.

|Element|Beschreibung|
|```<packaging>```| Gibt den Dateityp an, der vom Build generiert wird. Mögliche Optionen: JAR, WAR, EAR. Das Tag ist optional. Wenn nicht vorhanden, ist der Standardwert JAR.|
|```<properties>```| Dieser Block spezifiziert Einstellungen wie die Dateicodierung und die Version des verwendeten Compilers.|
|```<name>```| Gibt einen beschreibenden Namen für das Projekt an.|
|```<url>```| Enthält die URL des Projekts.|
|```<Beschreibung>```| Kurze Beschreibung des Projekts. Die Tags <name>, <url>, <description> werden häufig beim Erstellen von Dokumentationen verwendet.|
|```<dependencies>```| Enthält eine Liste aller Abhängigkeiten, die im Projekt verwendet werden. Jede Abhängigkeit enthält dieselben Tags wie das Projekt: Gruppen-ID, Artefakt-ID, Version.|
|```<build>```| Enthält Build-Informationen.|
|```<sourceDirectory>```| Gibt den Pfad zum Quellcode an. Der Standardwert ist: src/main/java. Denken Sie daran, dass wir im Tutorial beim Erstellen des Maven-Projekts genau eine solche Struktur erstellt haben.|
|```<resources>```| Gibt Pfade zu Ressourcendateien an. Standardverzeichnis: src/main/resources.|
|```<outputDirectory>```| Gibt das Verzeichnis an, in dem die kompilierten Dateien gespeichert werden. Standardwert: Ziel/Klassen.|
|```<finalName>```| Der Name der resultierenden Assemblydatei. Standardwert: artifactId-version.|
|```<plugins>```| Der Abschnitt definiert die Verwendung von Plugins von Drittanbietern.|

### Archetyp
Neben den bereits besprochenen Erstellungsmethoden (von Hand und mit der IDE) kann die Datei pom.xml auch mit dem Archetyp erstellt werden.

Ein Archetyp ist eine Art Projektvorlage, die die Struktur und Stubs von Quell- und Konfigurationsdateien enthält. Der Archetyp wird verwendet, um die Projektstruktur zu standardisieren und schnell ein Projekt aus einer bestehenden Vorlage zu erstellen.
Ein Archetyp ist ein reguläres Maven-Projekt, das eine zusätzliche Datei archetype-metadata.xml enthält, die sich im Ordner META-INF/maven befindet und eine Beschreibung enthält, wie die Projektstruktur aussehen wird.

Beispiel für die Datei archetype-metadata.xml:
```xml
<archetype-descriptor
... name="example-archetype">
  <fileSets>
    <fileSet packaged="true">
        <directory>src/main/java</directory>
    </fileSet>
    <fileSet packaged="true">
        <directory>src/test/java</directory>
    </fileSet>
  </fileSets>
</archetype-descriptor>
```

Das fileSet gibt die zu erstellende Struktur und die zu kopierenden Dateien an. Das heißt, in unserem Fall wird die Ordnerstruktur src/main/java für das erste fileSet erstellt.

Die Eigenschaft packaged=true gibt an, dass die Dateien dem durch den Paketparameter angegebenen Ordner hinzugefügt werden.

Für die Erstellung der Projektstruktur und der pom.xml gibt es eine Vielzahl vorgefertigter Archetypen. Beispielsweise generiert maven-archetype-webapp eine Projektstruktur für Webanwendungen. Das Ergebnis ist folgende Struktur:

![](..\img\JAVA_25.3_1.png)

Und maven-archetype-simple erstellt die Struktur eines regulären Maven-Projekts:

![](..\img\JAVA_25.3_2.png)

Führen Sie dazu einfach den Befehl aus:

```cmd
mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-plugin -DarchetypeVersion=1.4
```
wo

- in -DarchetypeGroupId müssen Sie die groupId des Archetyps angeben,
- -DarchetypeArtifactId gibt die Artefakt-ID des Archetyps an,
- in -DarchetypeVersion ist seine Version.

Die _ArtifactId_ der offiziellen Maven-Archetypen finden Sie in der Tabelle. Sie beziehen sich alle auf die ```gruppen-gd org.apache.maven.archetypes```.

Die auf diese Weise erstellte Projektstruktur ähnelt der, __Idea__ in der letzten Einheit für uns erstellt hat, als wir mit __Idea__ ein Maven-Projekt erstellt haben.

Sie können einen Archetyp auch manuell erstellen, indem Sie eine Projektdeskriptordatei archetype-metadata.xml oder aus einem vorgefertigten Projekt erstellen. Um einen Archetyp aus einem Projekt zu erstellen, müssen Sie den folgenden Befehl ausführen:

```cmd
mvn archetype:create-from-project
```

Der generierte Archetyp befindet sich in target/generated-sources/archetype.

## Erstellen Sie Ihren eigenen Archetyp.

1. Verwenden Sie dazu den vorgefertigten Archetyp des Archetyps. Führen Sie den Befehl aus, um ein Projekt basierend auf einem Archetyp aus der Theorie zu erstellen, und geben Sie den Archetyp -DarchetypeArtifactId=maven-archetype-archetype an.
Als Ergebnis erhalten Sie mit der Deskriptordatei die Struktur des fertigen Archetyps.

1. Ändern Sie in archetype-metadata.xml den Namen des generierten Archetyps in Ihren eigenen und ersetzen Sie die generierte Projektstruktur. Fügen Sie zum Beispiel die Ordner src/main/java/db hinzu (für eine hypothetische Datenbankverbindung werden wir keine Verbindung herstellen, erstellen Sie einfach einen Archetyp für Projekte, wo es benötigt wird) und src/main/java/entity (für eine hypothetische Entitätssatz). Die Struktur wird im Tag ```<fileSets>``` angegeben.
1. Erstellen Sie den erstellten Archetyp und fügen Sie ihn dem lokalen Repository hinzu, indem Sie den folgenden Befehl ausführen:
```cmd
mvn clean install
```
Stellen Sie sicher, dass Ihr Archetyp in .m2/repository/archetype-catalog.xml erscheint.

Erstellen Sie ein Projekt mit dem soeben erstellten Archetyp. Dazu können Sie den Befehl zum Erstellen eines Projekts aus einem Archetyp aus der Theorie verwenden, indem Sie den Namen Ihres Archetyps angeben.

## Abhängigkeitsmanagement. Eigenschaften
Eines der Hauptmerkmale von Maven ist das Abhängigkeitsmanagement. In dieser Einheit sehen wir uns an, wie Abhängigkeiten in Maven definiert werden, welche Eigenschaften Abhängigkeiten haben und wie Konflikte mit Versionen gelöst werden.

Alle Abhängigkeiten sind in der pom-Datei im Abschnitt <dependencies/> definiert.

Zum Beispiel:
```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-core</artifactId>
    <version>5.2.9.RELEASE</version>
</dependency>
```
Für Artefakte, die zur selben Gruppe gehören, ist es praktisch, Variablen zu verwenden. Anstatt beispielsweise für jede Bibliothek aus Spring eine Version definieren zu müssen, können Sie eine Variable definieren und diese in allen Spring-spezifischen Abhängigkeiten verwenden.

```xml
<properties>
    <spring.version>5.2.9.RELEASE</spring.version>
</properties>

<dependencies>
     
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-data</artifactId>
        <version>${spring.version}</version>
        <scope>test</scope>
    </dependency>
         
    <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-core</artifactId>
       <version>${spring.version}</version>
    </dependency>
         
 </dependencies>
 ```

Wenn Sie einen Maven-Befehl ausführen, versucht Maven, alle Abhängigkeiten zu installieren, indem es sie aus dem lokalen Repository herunterlädt, und wenn sie nicht im lokalen Repository gefunden werden, werden sie aus dem zentralen Repository heruntergeladen und im lokalen gespeichert.

Mit Maven können Sie eine Bibliothek verwenden, die sich weder im zentralen noch im lokalen Repository befindet. Dies sind beispielsweise proprietäre Bibliotheken. Geben Sie dazu im Tag <systemPath> einfach den Pfad zur Bibliothek des Drittanbieters an und definieren Sie den Geltungsbereich <scope> als system.

Zum Beispiel:
```xml
<dependency>
  <groupId>myDependency</groupId>
  <artifactId>myDependency</artifactId>
  <scope>system</scope>
  <version>1.0</version>
  <systemPath>${basedir}\libs\myDependency.jar</systemPath>
</dependency>
```
Die Abhängigkeit hat Eigenschaften: GroupId, ArtifactId und Version, ähnlich den Eigenschaften des Projekts, die wir bereits in der letzten Einheit betrachtet haben. Überlegen Sie, welche zusätzlichen Eigenschaften eine Abhängigkeit haben kann.

### Scope
Insgesamt gibt es sechs Arten von _scope_ oder _Sichtbarkeitsbereiche_. Sie bestimmen, in welchen Phasen des Builds oder der Programmausführung die Abhängigkeit sichtbar wird.

|||
|---|---|
|compile | Der Standardbereich. Die Abhängigkeit ist in allen Phasen des Builds verfügbar und wird in den Build eingeschlossen. |
|provided | Gibt eine Abhängigkeit an, die zur Laufzeit vom JDK oder Container bereitgestellt wird. Eine solche Abhängigkeit ist nur zur Kompilierzeit verfügbar. Die Abhängigkeit gelangt nicht in die Assembly. |
|runtime | Eine Abhängigkeit mit diesem Umfang wird zur Kompilierzeit nicht benötigt, sondern nur zur Laufzeit. |
|test | Gibt eine Abhängigkeit an, die beim Kompilieren und Ausführen von Tests sichtbar ist. |
|system | Maven sucht solche Abhängigkeiten nicht im Repository, sie sind im System vorhanden. |
|import | Dieser Bereich ist nur für den Abhängigkeitstyp pom verfügbar. Wird verwendet, um Abhängigkeiten von anderen pom zu importieren.|

### Classifier
Es gibt Fälle, in denen das Teilen durch groupId, artifactId und Version nicht ausreicht und dann der Classifier <classifier> verwendet wird. Classifier kann in Fällen verwendet werden, in denen Artefakte für die Verwendung in unterschiedlichen Umgebungen (Entwicklung, Test, Produktion) auf unterschiedlichen Betriebssystemen erstellt werden oder wenn Artefakte für unterschiedliche JDKs funktionieren sollen.

Zum Beispiel gibt es dieselbe Bibliothek, die mit verschiedenen JDKs funktionieren soll: JDK 8 und JDK 11. Diese Bibliothek hat dieselbe Artefakt-ID, aber der Klassifikator ist unterschiedlich.

Ein Beispiel für die Verwendung der Bibliothek zum Arbeiten mit JDK 8:

```xml
<dependency>
    <groupId>org.example</groupId>
    <artifactId>greeting</greeting>
    <version>1.0.0</version>
    <classifier>jdk8</classifier>
</dependency>
```

Wenn für das Projekt ein Klassifizierer angegeben ist, wird sein Wert zum Assemblynamen hinzugefügt. In diesem Fall erhält das Artefakt den Namen Greeting.1.0.0-jdk8.jar.

### Optional
Eine Abhängigkeit kann als optional deklariert werden. Fügen Sie dazu einfach das Tag ```<optional>``` mit dem Wert true hinzu. Dies wird verwendet, wenn eine Abhängigkeit nur für bestimmte Funktionen benötigt wird, und ist optional, wenn der Rest des Projekts verwendet wird. Beispielsweise gibt es Projekt A mit Abhängigkeit B. Abhängigkeit B ist als optional deklariert. In meinem C-Projekt füge ich Abhängigkeit A hinzu, aber Abhängigkeit B wird nicht automatisch geladen. Wenn ich in Projekt C Funktionen benötige, die Abhängigkeit B verwenden, muss ich sie als direkte Abhängigkeit zum pom hinzufügen.

Ein Beispiel für das Deklarieren einer Abhängigkeit als optional:

```xml
<dependency>
    <groupId>org.example</groupId>
    <artifactId>greeting</artifactId>
    <version>1.0.0</version>
    <optional>true</optional>
</dependency>
```

### Abhängigkeitsbaum

Um eine Liste aller Abhängigkeiten im Projekt anzuzeigen, einschließlich der transitiven, führen Sie einfach den folgenden Befehl aus:

```xml
mvn dependency: tree 
```

Ein Beispiel für ein Fragment des konstruierten Abhängigkeitsbaums:
![](../img/JAVA_25.3_3.png)

Hier sehen wir zwei transitive Abhängigkeiten: hibernate-validator und jackson-databind. Hibernate-Validator enthält wiederum Abhängigkeiten: Validation-Api, JBoss-Logging, FasterXml und Jackson-Databind enthält Jackson-Anmerkungen.

### Abhängigkeiten beseitigen

Es gibt zwei Arten von Abhängigkeiten in Maven: direkt und transitiv.

Direkte Abhängigkeiten sind diejenigen, die wir explizit in den Abschnitt ```<dependencies>``` schreiben.
Transitive Abhängigkeiten sind Abhängigkeiten, die die Abhängigkeiten verwenden, die wir in das Projekt aufnehmen.

Transitive Abhängigkeiten Maven lädt auch automatisch.

Dabei können wir auf das Problem von Versionskonflikten stoßen. Sie besteht darin, dass eine bestimmte Abhängigkeit als transitiv dargestellt wird und die Version 1.0.0 hat, und wir im Projekt die neuere Version 2.0.0 verwenden wollen. Maven kann nur eine Abhängigkeit mit derselben Gruppen- und Artefakt-ID in ein Projekt aufnehmen. Um einen solchen Konflikt zu vermeiden, können wir die Abhängigkeit mit dem Tag ```<exclusion>``` ausschließen und als direkte Abhängigkeit hinzufügen.

```xml
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>${junit.version}</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.dbunit</groupId>
    <artifactId>dbunit</artifactId>
    <version>${dbunit.version}</version>
    <scope>test</scope>
    <exclusions>
        <!--Exclude transitive dependency to JUnit-3.8.2 -->
        <exclusion>
            <artifactId>junit</artifactId>
            <groupId>junit</groupId>
         </exclusion>
    </exclusions>
</dependency>
```

## Assembly-Lebenszyklus

In früheren Einheiten haben wir häufig den Befehl zum Erstellen des Projekts verwendet:

```cmd
mvn clean install 
```

Es ist Zeit herauszufinden, was genau dahinter steckt. Überlegen Sie, was der Baugruppenlebenszyklus ist und was sie sind.

Es gibt 3 Lebenszyklen in Maven:

- default – erstellt die Anwendung und stellt sie bereit.
- clean - entfernt alle seit dem letzten Build generierten Dateien.
- site - erstellt Dokumentation für das Projekt.

Der Lebenszyklus wird durch das Lösen einer Kette von Aufgaben erreicht. In diesem Fall hat der Lebenszyklus keine abzurufenden Befehle. Wie wird es dann durchgeführt?

Jede Aufgabe wird innerhalb einer Phase (Phase) durchgeführt. Somit ist der Lebenszyklus eine logische Vereinigung von Phasen.

Der Befehl mvn clean install fordert Sie auf, die Bereinigungs- und Installationsphasen auszuführen.

Der Lebenszyklus von Default besteht aus 23 Phasen, Clean - von 3, Site umfasst 4 Phasen. Jede Phase ist für eine bestimmte Aufgabe verantwortlich.

![](../img/JAVA_25.5_1.png)

Die Reihenfolge der Phasen im Zyklus ist nicht zufällig, in dieser Reihenfolge werden die Phasen ausgeführt. Wenn eine Phase beginnt, werden alle Phasen vor der gestarteten Phase ausgeführt. 

Zum Beispiel, wenn Sie den Befehl aufrufen:

```cmd
mvn clean install
```
Nennt man zunächst den __Clean__-Lebenszyklus, der von Anfang an bis zur __Clean__-Phase läuft, es gibt also nur zwei Phasen: __Pre-Clean__ und __Clean__. Dann ruft derselbe Befehl die Installationsphase aus dem Standardlebenszyklus auf, was dazu führt, dass alle Phasen dieses Zyklus von der Überprüfung bis zur Installation ausgeführt werden und die Bereitstellungsphase nicht ausgeführt wird, da sie nach der Installationsphase kommt.

### Default
Werfen wir einen Blick auf die beliebtesten und nützlichsten Phasen der Standardschleife.

|||
|---|---|
|validate| Überprüft, ob die Projektkonfiguration korrekt ist, und stellt sicher, dass die erforderlichen Abhängigkeiten verfügbar sind.|
|compile| Verantwortlich für das Kompilieren der Quelldateien des Projekts.|
|test-compile| Verantwortlich für das Kompilieren von Testquelldateien.|
|test| Führt Komponententests aus.|
|package| Setzt kompilierte Dateien in Abhängigkeit vom angegebenen Build-Typ (JAR, WAR, EAR) zu einem Archiv zusammen.|
|integration-test| Führt Integrationstests aus.|
|install| Kopiert das erstellte Artefakt in das lokale Repository. Es wird für den Bau anderer lokaler Projekte verfügbar.|
|deploy| Kopiert ein Artefakt in ein Remote-Repository zur Verwendung in anderen Projekten.|

Die Reihenfolge der Phasen in der Tabelle ist nicht zufällig, in dieser Reihenfolge werden die Phasen ausgeführt. Wenn eine Phase beginnt, werden alle Phasen vor der gestarteten Phase ausgeführt. Zum Beispiel, wenn wir den Befehl ausführen

```cmd
mvn package
```
Die folgenden Phasen werden ausgeführt: _validate, compile, test-compile, test_, das heißt, bevor das Projekt erstellt wird, validiert Maven zuerst das Projekt, kompiliert die Projekt- und Testdateien, führt die Tests aus und erstellt erst dann das Projekt.

### Clean

Der Bereinigungszyklus löscht alle Dateien, die während des vorherigen Builds erstellt wurden: .CLASS, .JAR usw. Im Allgemeinen ist dies das Entfernen des Zielordners

Der Zyklus umfasst 3 Phasen:

|||
|---|---|
|pre-clean|Vorbereiten zur Entnahme. Standardmäßig enthält die Phase keine Ziele (das Konzept eines Ziels wird weiter unten besprochen).|
|clean|Eigentlich die Entfernung selbst.|
|post-clean|Es impliziert die Ausführung einiger Aufgaben nach dem Löschen. Standardmäßig enthält eine Phase keine Ziele.|

Es wird empfohlen, vor einem neuen Projektaufbau immer zu bereinigen, um die Verwendung von Dateien aus einem früheren Build zu vermeiden.

### Site
Die Site-Schleife dient zum Erstellen von Dokumentationen. Besteht aus 4 Phasen:

|||
|---|---|
|Pre-Site| Vorbereitung für die Erstellung.|
|site| Direktes Erstellen von Dokumentationen.|
|Post-Site| Vorbereitung für die Bereitstellung.|
|site-deploy| Stellt die Dokumentation auf einem Webserver bereit.|

### Goals 
Jede Phase wiederum ist eine Reihe von Zielen (Zielen).

![](../img/JAVA_25.5_2.png)

GoalS sind Aufgaben, die ausgeführt werden, um eine bestimmte Phase abzuschließen. Ein Ziel kann zu mehreren Phasen gehören oder zu keiner.

Ein Beispiel, bei dem sich das Ziel in keiner Phase befindet, ist der Befehl mvndependency:tree, den wir in der vorherigen Einheit ausgeführt haben, um den Abhängigkeitsbaum anzuzeigen. Der Zweck vondependency:tree bezieht sich nicht auf irgendeine Phase.

Ein Beispiel für ein Ziel, das sich über mehrere Phasen erstreckt:

```cmd
mvn compiler: compile
```

Es kann sowohl in der Testphase (test) als auch in der Kompilierphase (compile) ausgeführt werden.

Die Besonderheit des Ziels besteht darin, dass bei Erfüllung eines bestimmten Ziels nur dieses Ziel erfüllt wird, im Gegensatz zu der Phase, in der zusätzlich alle vorherigen Phasen durchgeführt werden.
Wenn Sie beispielsweise ein JAR-Ziel ausführen, das kompilierte Dateien in eine JAR-Datei kompiliert, und Sie die Dateien vorher nicht kompiliert haben, den Kompilierungsbefehl nicht ausgeführt haben, tritt ein Fehler auf, das Ziel wird nicht ausgeführt – die JAR-Datei target wird einfach keine kompilierten Dateien haben, um sie zu erstellen.

Ziele werden dank Plugins erfüllt. Das Maven-Plugin ist grob gesagt eine Reihe von Zielen. Beispielsweise können Sie in den Standardzielen und ihrer Bindung an Phasen sehen, dass in der Clean-Phase das Clean-Ziel vom Clean-Plugin ausgeführt wird.

Das Ziel kann über die Befehlszeile ausgeführt werden, indem der Befehl wie folgt zusammengesetzt wird:

```cmd
mvn plugin:goal
```
Um eine Liste von Zielen und Plugins anzuzeigen, die sich auf ein bestimmtes Ziel beziehen, müssen Sie den Befehl help:describe mit einer Phase ausführen. Wie zum Beispiel für die Compile-Phase:

```cmd
mvn help:describe -Dcmd=compile
```

![](../img/JAVA_25.5_3.png)

Wie wir sehen können, werden für einige Phasen keine Ziele definiert. Dies bedeutet, dass dieser Phase standardmäßig kein Ziel zugeordnet ist, Sie können das Ziel jedoch selbst binden.

## Häufig verwendete Plugins

Das Thema Plugins haben wir bereits kurz angesprochen. Lassen Sie uns nun genauer untersuchen, was es ist, wie es in Maven verwendet wird, und die beliebtesten betrachten.

In der vorherigen Einheit haben wir gesagt, dass ein Plugin eine Reihe von Zielen ist. In einem Maven-Plugin ist das Ziel ein Mojo (Main Plain Old Java Object), das eine Java-Klasse sein kann. Mojo stellt alle notwendigen Informationen über das Ziel bereit: den Namen des Ziels, die Phase, in der es ausgeführt wird, und Konfigurationsoptionen. Ein Plugin besteht aus einem oder mehreren Mojos.

Mojo-Beispiel, das einen Bericht generiert:

```java
public class ReportExampleMojo extends AbstractMojo {

   @Parameter(property = "reportName", required = false, defaultValue = "Report")
   private String reportName;
 
   @Parameter(property = "targetPath", required = true)
   private String targetPath;
 
   @Parameter(property = "locales")
   private String[] locales;
 
   public void execute() throws MojoExecutionException {
       ...
   }
}
```
Diesem Plugin können 3 Parameter gegeben werden (@Parameter): reportName (Berichtsname), targetPath (Pfad, wo der Bericht generiert wird), locales (Sprachen, in denen der Bericht generiert wird). Erforderliche Parameter haben das Flag required = true. Für optional können Sie den Standardwert setzen, wie im Beispiel: defaultValue = "Report".

Sie können zusätzliche Parameter für das Plugin im Tag <configuration> in pom.xml festlegen. Die so eingestellten Parameter werden den Feldwerten in Mojo hinzugefügt.

Die oben beschriebene Beispiel-POM-Datei für Mojo würde folgendermaßen aussehen:

```xml
<project>
 ...
 <build>
   <plugins>
     <plugin>
      <groupId>org.example</groupId>
       <artifactId>maven-reportexample-plugin</artifactId>
       <version>1.0</version>
       <configuration>
         <reportName>my_report</reportName>
         <targetPath>${basedir}/target/reports</targetPath>
              <locales>
                <locale>ru</locale>
                <locale>en</locale>
                <locale>de</locale>
                <locale>fr</locale>
              </locales>
       </configuration>
     </plugin>
   </plugins>
 </build>
 ...
</project>
```

Im Allgemeinen gibt es zwei Arten von Plugins in Maven:

Assembly-Plugins. Plug-ins werden während des Projekterstellungsprozesses ausgeführt und müssen innerhalb des <build>-Blocks angegeben werden.
Plugins melden. Sie werden während des Dokumentationsgenerierungsprozesses durchgeführt und müssen innerhalb des <reporting>-Blocks angegeben werden.
Plugins werden in der Datei pom.xml innerhalb des Blocks <plugins></plugins> angegeben, wie im obigen Beispiel.

Sie werden auf ähnliche Weise wie Abhängigkeiten deklariert. Erforderliche Informationen für Plugins auch: Gruppen-ID, Artefakt-ID und Version.

Wenn Sie ein Plugin deklarieren, können Sie es an eine bestimmte Phase binden und Ziele angeben.

Zum Beispiel:

```xml
<plugin>
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-compiler-plugin</artifactId>
   <version>3.8.0</version>
   <executions>
      <execution>
         <id>default-compile</id>
         <phase>compile</phase>
         <goals>
            <goal>compile</goal>
         </goals>
      </execution>
      <execution>
         <id>default-testCompile</id>
         <phase>test-compile</phase>
         <goals>
            <goal>testCompile</goal>
         </goals>
      </execution>
   </executions>
</plugin>
```

Das maven-compiler-plugin enthält zwei Ziele: „compile“, das an die „compile“-Phase gebunden ist, und „test-compile“, das an die „test-compile“-Phase gebunden ist.

Sie können das Plugin aus dem obigen Beispiel mit der Befehlszeile ausführen:
```cmd
mvn compiler:compile 
rem oder
mvn compiler:testCompile
```
Im Allgemeinen sieht der Plugin-Ausführungsbefehl wie folgt aus:
```cmd
mvn groupId:artifactId:version:goal 
```
n diesem Fall kann die Version normalerweise weggelassen werden, dann wird die neueste Version des Plugins ausgewählt.

Hinweis: Gemäß der Namenskonvention sollten generierte Plugins ```<yourpluginname>```-maven-plugin heißen. Namen wie maven-```<pluginname>```-plugin beziehen sich nur auf offizielle Maven-Plugins.

Rufen Sie das Ziel „compiler:compile“ mit dem vollständig qualifizierten Plug-in-Namen auf.
```cmd
mvn org.apache.maven.plugins:maven-compiler-plugin:3.8.1:compile 
```

Die Liste der auf dem Computer installierten Maven-Plugins kann im Verzeichnis eingesehen werden
```${M2_HOME}/repository/org/apache/maven/plugins.```

Und die Liste der Plugins, die standardmäßig mit dem Projekt verbunden sind, mit dem Befehl:
```Cmd
mvn help:effective-pom
```
Betrachten Sie einige Maven-Plugins
|Plugin|Beschreibung|
|---|---|
|maven-clean-plugin|Entfernt generierte Dateien beim Erstellen des Projekts.|
|maven-compiler-plugin|Kompiliert Projekt- und Testquelldateien.|
|maven-surefire-plugin|Führt Tests durch und generiert Berichte über die Ergebnisse ihrer Ausführung.|
|maven-jar-plugin|Erstellt ein JAR-Archiv für das Projekt.|
|maven-war-plugin|Erstellt ein WAR-Archiv für das Projekt.|
|maven-javadoc-plugin|Entwickelt, um eine Dokumentation zum Quellcode des Projekts mit dem Standard-Javadoc-Dienstprogramm zu erstellen.|

[Weitere Plugins](https://maven.apache.org/plugins/index.html#supported-by-the-maven-project)

## Profile verwenden

Maven bietet die Funktionalität zum Erstellen mehrerer Konfigurationssätze, die zum Festlegen oder Überschreiben der standardmäßigen Maven-Build-Werte verwendet werden können. Dadurch können Sie verschiedene Builds erstellen, die jeweils darauf abzielen, einige spezielle Probleme zu lösen, beispielsweise für verschiedene Umgebungen (development  [lit. „Entwicklung“], training  [lit. „Training“, „Testen“], production  [ lit. "Produktion"]).

Diese Funktionalität wird als __Maven-Profil__ bezeichnet.

Es gibt 3 Profiltypen in Maven:

- Projektprofile. Definiert in pom.xml.
- Benutzerprofil. Definiert in der Datei settings.xml. ```(%USER_HOME%/.m2/settings.xml)```
- globale Profile. Definiert in der globalen settings.xml-Datei.

Sehen wir uns an, wie Profile in pom.xml erstellt werden. Das Profil wird durch das Tag <profile> im Abschnitt <profiles> definiert. Das Hauptelement des Profils ist die Profilkennung <id>. Sie können mehrere Profile erstellen, indem Sie verschiedene IDs angeben.

```xml
<profiles>
    <profile>
        <id>local</id>
    </profile>
    <profile>
        <id>production</id>
    </profile>
</profiles>
```

Innerhalb jedes Profils können Sie Abhängigkeiten, Plugins, Ressourcen usw. angeben und so das Profil für bestimmte Aufgaben anpassen.

Profilaktivierung
Um ein Profil verwenden zu können, muss es aktiviert werden. Ein Maven-Build-Profil kann auf folgende Weise als aktiv angegeben werden:

- das Standardprofil ist angegeben;
- Parameter auf der Kommandozeile;
- das Vorhandensein/Fehlen/Wert einer Umgebungsvariablen;
- JDK-Version
- Version oder Typ des Betriebssystems;
- das Vorhandensein oder Fehlen einer bestimmten Datei.

Alle diese Verfahren werden der Reihe nach unten besprochen. Um eine Aktivierungsmethode auszuwählen, geben wir das Tag ```<aktivierung>``` direkt im Profil an und geben darin die Aktivierungsmethode an.

Es gibt Profile, die nicht gleichzeitig verbunden werden sollten, da sie miteinander in Konflikt geraten, z. B. Profile für die Testumgebung und für die lokale Umgebung. Es ist, als würde man im selben Raum versuchen, die Wände in einer schönen Farbe zu streichen und gleichzeitig die Tapete zu kleben – eine sinnlose Übung. Nur bei Test- und lokalen Umgebungsprofilen werden sie höchstwahrscheinlich einfach nicht gestartet oder funktionieren nicht richtig.

Es gibt Profile, die gleichzeitig verbunden werden können, da sie auf unterschiedliche Aufgabengruppen ausgerichtet sind. Es ist, als würde man gleichzeitig einen Elektriker und einen Klempner anrufen – beide arbeiten an Heimwerkerarbeiten, aber sie werden keine Konflikte über Arbeitsprobleme haben.

### Standard Profil 
Im Pom können Sie ein Profil definieren, das standardmäßig aktiv ist, indem Sie das Tag ```<activeByDefault>``` im Abschnitt ```<activation>``` verwenden, das auf __true__ gesetzt sein muss.

```xml
<profile>
    <id>integration-tests</id>
    <activation>
        <activeByDefault>true</activeByDefault>
    </activation>
</profile>
```

Danach können Sie den Profilparameter während des Builds nicht mehr in der Befehlszeile angeben. Wenn wir aber ein anderes Profil als das Standardprofil aktivieren wollen, muss dieses Profil im Parameter angegeben werden, und dann wird das angegebene Profil anstelle des Standardprofils verwendet. Dazu später mehr.

### Build Parameter
Sie können ein Profil aktivieren, indem Sie es während des Builds als Parameter angeben:
```cmd
mvn package -P dev
rem -P bedeutet, dass dies ein Profilparameter ist, 
rem dev ist der Name unseres Profils.
```
Sie können mehrere Profile aktivieren. Dazu genügt es, sie durch Kommas getrennt anzugeben:
```cmd
mvn package -P integration-tests,test
```

### Abhängig von der Systemvariable
Ein Profil kann auch abhängig vom Vorhandensein einer Systemvariablen aktiviert werden. Beispielsweise wird ein Profil aktiv, wenn es eine Systemvariable (die wir im Tag ```<property>``` angeben) mit dem Namen local (die wir im Tag ```<name>``` angeben) gibt:

```xml
<profile>
    <id>example</id>
    <activation>
        <property>
            <name>local</name>
        </property>
    </activation>
</profile>
```
Ein solches Profil kann durch Ausführen des Befehls aktiviert werden, wobei -D den Namen der Systemvariablen angibt:

```cmd
mvn package -Dlocal
```
Im Gegenteil, Sie können angeben, dass das Profil aktiv wird, wenn die Variable nicht angegeben ist.

```xml
<property>
    <name>!local</name>
</property>
```

Oder geben Sie den Wert an, den die Variable annehmen soll (im Beispiel haben wir die Umgebungsvariable angegeben, der der Wert local zugewiesen wurde):

```xml
<property>
    <name>environment</name>
    <value>local</value>
</property>
```
Ein solches Profil kann durch Ausführen des folgenden Befehls aktiviert werden:

```Cmd
mvn package -Denvironment=test
```

*In diesem Fall ist der Namenstest nur ein Beispiel. Eine solche Umgebung ist jedoch standardmäßig vorhanden, sie wird zum Ausführen von Tests benötigt (wir werden später ausführlich auf Tests eingehen).

Sie können auch einen Wert angeben, den die Variable nicht annehmen darf, damit das Profil aktiv wird:

```xml
<property>
    <name>environment</name>
    <value>!local</value>
</property>
```

### Abhängig von der JDK-Version
Das Profil kann abhängig von der angegebenen JDK-Version aktiv werden.
```xml
<profile>
    <id>active-on-jdk-11</id>
    <activation>
        <jdk>11</jdk>
    </activation>
</profile>
```

### Abhängig vom Betriebssystem
Oder je nach Betriebssystem. Sie können ein Profil erstellen, das nur auf einem bestimmten Betriebssystem aktiv ist.
```xml
<profile>
    <id>active-on-windows-10</id>
    <activation>
        <os>
            <family>Windows</family>
            <name>windows 7</name>
            <version>7.0</version>
        </os>
    </activation>
</profile>
```

### Abhängig vom Vorhandensein/Fehlen der Datei
Die letzte Option ist die Aktivierung, wenn die Datei im System vorhanden/nicht vorhanden ist. Das folgende Beispiel demonstriert die Aktivierung eines Profils, wenn keine Datei test.xml im Zielverzeichnis vorhanden ist:

```xml
<activation>
    <file>
        <missing>target/test.xml</missing>
    </file>
</activation>
```
Das Tag ```<exists>``` wird verwendet, um zu aktivieren, wenn die Datei existiert.

### Deaktivierung des Profils

Zum Beispiel durch Ausführen des Befehls:
```cmd
mvn compile -P -active-on-jdk-8
```
Um zu sehen, welche Profile aktiv sind, können Sie den Befehl verwenden:
```cmd
mvn help:active-profiles
```

# Modul 22 (JDBC)

## Взаимодействие с БД из прикладных программ
В большинстве случаев работы прикладных программ нам требуется _сохранять их данные_. Как мы знаем, лучше всего на данную роль подходят БД. Запись и чтение в них из прикладных программ обычно не видны пользователю, и могут не иметь никакого графического интерфейса.