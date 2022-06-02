# <u>Java</u>

### Datatypes
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

### _DateTime API_
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
