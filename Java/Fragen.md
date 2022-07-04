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

<hr>

## Назвать методы Object. (*)
- toString()
- equals()
- hashCode()
- wait()
- notify()
- notifyAll()
- finalize() — deprecated в Java 9+
- getClass()

Про toString(), equals(), hashCode() и их контракт знать нужно обязательно

<hr>

## Что такое string-pool? В чем отличие cоздания строки через new от литерала? Что такое String.intern()? 
string-pool — структура в памяти, хранящая массив всех строк-литералов программы.
String.intern(), соответственно, вернет строку из пула, при наличии таковой. Полезно при сравнениях вида:

```java
new String("hello").intern() == new String("hello").intern()
```
Т.к без интернирования пришлось бы сравнивать строки через equals, что может быть медленнее при наличии длинных строк. В данном случае возвращается ссылка на один и тот же объект строки из пула, и проверка проходит с true.

<hr>

## Привести пример плохой реализации hashCode() 
Метод, возвращающий константу, или значения хэшкодов с неравномерным распределением, приводящим к коллизиям

<hr>

## Примитивы, врапперы. Package/unpackage (boxing/unboxing). 
Типы примитивы не создаются в куче, их жизненный цикл ограничен жизненным циклом стек-фрейма
Package — создание типа-обертки в хипе для аналогичного типа-примитива, например при объявлении аргумента как Integer, и при передаче int в качестве аргумента. Unpackage — обратная операция

<hr>

## Сравнение по == и по equals
Сравнение по "==" — сравнение по ссылкам
Сравнение по «equals» — если переопределен equals, то это сравнение эквивалентности объектов по их полям, если нет — по ссылкам на объекты

<hr>

## Свойства, которым должен удовлетворять equals
Рефлексивность: a==a
Симметричность: a==b, b==a
Транзитивность: a==b, b==c, a==c
Консистентность: Множественные вызовы equals должны возвращать один и тот же результат

<hr>

## Отличия String/StringBuilder/StringBuffer
String — иммутабельный байтовый массив
StringBuilder — helper-класс для построения строк, не предоставляет гарантий синхронизации
StringBuffer — то же, что и StringBuilder, с synchronized методами

<hr>

## Приведите пример нарушения симметрии equals
1. Создать класс Point2D c полями x,y: double
1. Унаследовать от него класс ColoredPoint2D c доп. полем color
1. a: Point2D
1. b: ColoredPoint2D
1. a.equals(b), !b.equals(a)

<hr>

## Interface vs Abstract Class.
- Интерфейс есть средство наследования API, абстрактный класс — средство наследования реализации
- Через интерфейсы возможно осуществлять множественное наследование, абстрактный класс можно наследовать в одном экземпляре.
- В интерфейсе нет возможности определить поля и конструкторы
-

<hr>

## override vs overload
- override — возможность переопределениия поведения метода в типах-потомках
- overload — возможность переопределять метод с одним именем, но разным набором аргументов

<hr>

## Как в Java сделать утечку памяти?
- Используя самописный класс стека, при выполнении операции pop() не присваивать предыдущей ссылке значение null.
- Также можно неверно использовать HashMap вместо WeakHashMap для кэширования чего-нибудь большого, например картинок ваших товаров, пользователей и.т.д в. Т.к ссылки на ключи сильные (strong references), значения по этим ключам будут висеть в хипе до морковкиного заговенья следующей перезагрузки jvm процесса или удаления ключа из мапы и обнуления ссылки на него. Вообще, кэширование — тема для отдельного разговора
- Также, [статья](https://www.toptal.com/java/hunting-memory-leaks-in-java) (но староватая)

<hr>

## Как вернуть псевдо-случайную последовательность целых чисел/чисел с плавающей запятой
- java.util.Random

<hr>

## В чем проблемы Random?
Random возвращает псевдо-случайную числовую последовательность, основанную на линейном конгруэнтном методе и seed'е, основанном на timestamp'е создания j.u.Random.
Соотвественно, зная время создания, можно предсказать такую последовательность. Такой генератор является детерминированным, и криптографически нестойким. Для исправления этого лучше использовать SecureRandom

<hr>

## GC и различные его виды в JVM. Какой объект считать достижимым. Как происходит сборка мусора (своими словами).
Виды GC:
- Serial Stop the World
- Parallel
- CMS (В чем недостаток по сравнению с Parallel?)
- G1 (Назвать отличие от CMS)
- Shenandoah

<hr>

## Java 8: стримы, функциональные интерфейсы, Optional
Stream — интерфейс, предоставляющий функциональные возможности обработки коллекций (filter, map, reduce, peek)
Операции на стримах делятся на терминальные и нетерминальные. Нетерминальные операции модифицируют pipeline операций над коллекцией, при этом не изменяя саму коллекцию, терминальные (например, collect) — проводят действия pipeline'а, возвращают результат и закрывают Stream.

FunctionalInterface — аннотация, предоставляющая возможность использовать лямбды на месте интерфейсов (например, при передаче лямбды в качестве аргумента в метод)

Optional — интерфейс, предохраняющий пользовательский код от nullable ссылок. Оборачивает исходный nullable объект, и предоставляет возможность понять, хранит ли non-nullable объект или нет.

<hr>

## Java 8: Что такое capturing/non-capturing lambda
- capturing lambda захватывает локальные переменные/аргументы/поля объекта из внешнего скоупа
- non-capturing lambda — не захватывает контекст внешнего скоупа, не инстанцируется каждый раз при использовании

<hr>

## Новые возможности Java 9 — 11
- Новые методы в String
- Java 9: Модульность
- Java 9: Методы в Objects: requireNonNullElse() и requireNonNullElseGet()
- Java 9: List.of(), Set.of(), Map.of(), Map.ofEntries()
- Java 9: Optional.ifPresentOrElse(), Optional.stream()
- Java 10: var type-inference
- Java 11: Files.readString(), Files.writeString()
- Java 11: Local-Variable Syntax for Lambda Parameters — выведение типов у var-аргументов в лямбда-параметрах
- Java 11: JEP 321: HTTP Client


Можно как бонус назвать какие-нибудь:
- JEP 328: Flight Recorder
- JEP 335: Deprecate the Nashorn JavaScript Engine
- JEP 320: Remove the Java EE and CORBA Modules


но это совершенно необязательно, покажет лишь вашу въедливость при чтении JDK'шных Release Notes :)

<hr>

## Swing: рассказать про EDT, как им пользоваться
EDT — тред в котором производится обработка пользовательских действий на UI: движение курсора, нажатие клавиш, скролл, drag'n'drop и.т.д. Соотвественно, все «тяжелые» по времени и ресурсам операции нужно выносить в отдельный worker-тред (SwingUtils.invokeLater(...)), чтобы не фризить EDT.

<hr>

## Swing: перечислить все виды Layout, которые знаете
- FlowLayout
- GridLayout
- BoxLayout
- BorderLayout

<hr>

## Generics: В чем преимущество, как работают? Что такое type-erasure? В чем отличие от шаблонов C++?
- Типы дженерики обеспечивают параметрический полиморфизм, т.е выполнение идентичного кода для различных типов. Типичный пример — коллекции, итераторы
- type-erasure — это стирание информации о типе-параметре в runtime. Таким образом, в байт-коде мы увидим List, Set вместо List<Integer>, Set<Integer>, ну и type-cast'ы при необходимости
- В отличие от дженериков в Java, в С++ шаблоны в итоге приводят к компиляции метода или типа для каждого специфицированного типа параметра (специализация шаблона). Да простят меня здесь адепты С++.

<hr>

## Generics: Метод принимает ссылку на List<Parent>. Child наследуется от Parent. Можно ли в метод передать List<Child>?
В типе аргумента нужно указать List<? extends Parent>

<hr>

## Generics: Ковариантность/контравариантность. Спросить про принцип PECS как бонус
- Ковариантность — List<? extends T>, если B extends T, то и List<B> extends List<T>
- Контраваринтность — List<? super T>, если B super T, то и List<B> super List<T>
- PECS — Producer-Extends-Consumer-Super, метод отдаёт ковариантный тип, принимает контравариантный (прим. автора — последнее интуитивно не очень понятно)

<hr>

## Регионы памяти в JVM
Java 8: Metaspace, Old Generation, Young Generation (Eden Space/Survivor Space), Stack, Constant Pool, Code Cache, GC Area.

<hr>

## Hard-references, weak references, soft-references, phantom-references
- Hard-references — стандартные ссылки на объекты, которые становится eligible for collection после недостижимости из root set
- Weak-references — объекты могут быть удалены при наличии слабой ссылки на него в любое время
- Soft-references — объекты могут удалятся GC при недостатке памяти
- Phantom-references — объекты не доступны напрямую по ссылкам, перед удалением помещаются в очередь на удаление. Нужны для более безопасной финализации ссылок (вместо finalize)

<hr>

## Рассказать про classloader'ы и их иерархию. Из за чего, например, может возникать NoClassDefFoundError, NoSuchMethodError?
Иерархия classloader'ов
1. Bootstrap
1. System
1. Application

- NoClassDefFoundError может возникнуть, если нужной библиотеки с этим классом нет в classpath
- NoSuchMethodError может возникнуть из-за несовместимости ваших библиотек, если зависимая библиотека A вызывает метод из старой версии библиотеки B, но в classpath есть более новая версия библиотеки B, c другой сигнатурой этого метода

<hr>

## Какими способами можно сконструировать объект в Java?
- Через конструктор
- Через статический factory-method
- Через паттерн Builder

<hr>

## Как идентифицируется класс в Java?
По его FQDN и classloader'у
<hr>

## Bytecode: назовите какие-нибудь инструкции и опишите их
Здесь только краткий список команд:
- aload
- aconst
- astore


* Попросить описать принцип действия стековой машины, как бонус. Допустим, на примере вызова метода.
<hr>

## Bytecode: invokevirtual, invokestatic, invokespecial — когда используются?
- invokevirtual — вызовы методов (в Java все методы виртуальные)
- invokestatic — вызовы статических методов
- invokespecial — вызовы конструкторов и приватных методов

