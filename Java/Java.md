# <u>Java</u>

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

### List
Array -> Suche -> O(1)

LinkedList -> Suche -> O(n)


### Set


### Map



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

List<String> list = Arrays.asList("a", "b", "c");
Stream<String> listStream = list.stream();
```

### Source
Source kann beliebige Collection sein.

### Intermediate operations
```java
// gibt Element zurück, die dem Predicate entsprächen
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
// prüft ob alle Elemente dem Predicate entsprächen
boolean allMatch(Predicate<? super T> predicate);

// prüft ob ein Element dem Predicate entspricht
boolean anyMatch(Predicate<? super T> predicate);

// prüft ob alle Elemente dem Predicate nicht entsprächen
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

