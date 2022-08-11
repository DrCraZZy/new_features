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

# OOP (Modul 6)

### Vererbung (Inheritance)
Dies ist eine Eigenschaft des Systems, mit der Sie eine neue Klasse basierend auf einer vorhandenen Klasse mit teilweise oder vollständig geliehener Funktionalität beschreiben können.
### Verkapselung (Encapsulation)
Es ist eine Eigenschaft des Systems, mit der Sie Daten in einer Klasse kombinieren und Implementierungsdetails vor dem Benutzer verbergen können.
### Polymorphismus (Polymorphism)
Es ist eine Möglichkeit, verschiedene Formen anzunehmen. In der Programmierung bedeutet dies, dass derselbe Code je nach Bedingungen unterschiedlich ausgeführt werden kann. Polymorphismus ist statisch und dynamisch.

# Абстрактные классы. Интерфейсы (Modul 7)



# Classes (Inner/Nested/Anonymous)


# Input- / OutputStream


# Exception (Modul 11)
## Error и Exception: первый взгляд на Throwable
Исключительные ситуации (исключения) и ошибки возникают в процессе выполнения программы, когда что-то идет не так. Например, попытка обратиться к элементу массива, индекс которого лежит за пределами массива, или же вызов метода у объекта, значение которого равно null. 

В момент возникновения проблемы в приложении создается объект, который описывает это событие. Затем выполнение приложения останавливается, и включается механизм обработки исключений. При этом ссылка на объект-исключение передается обработчику исключений, который пытается решить возникшую проблему и продолжить выполнение программы. 

В своей программе мы можем сами перехватить, обработать исключение, поймать ошибку и сделать что-то, например, сообщить пользователю о возникшей проблеме и попытаться продолжить нормальную работу. 

Все объекты исключительных ситуаций  — наследники класса Throwable. Иерархия сразу делится на две ветви: наследников класса Error (ошибки) и Exception (исключения).

![](../img/JAVA_NEW_10.1_2_bigsize.png)

**Ошибки (Errors)** — это серьёзные проблемы, которые, согласно спецификации Java, не следует пытаться обрабатывать в собственной программе, поскольку они связаны с проблемами уровня JVM.

Исключения такого рода возникают, например, когда заканчивается память, которая доступна виртуальной машине.  Мы не сможем выделить больше памяти, поэтому в любом случае JVM остановит свою работу. Это ошибка OutOfMemoryError. Другая частая ошибка, StackOverFlowError, возникает при бесконечной рекурсии, когда функция многократно вызывает сама себя.

Ошибку перехватывать поздно, программа все равно не сможет «вернуться к нормальной жизни», все совсем плохо. Но можно понять, где именно произошла ошибка, мы научимся делать это в юните про **стек ошибок** (*Stack Trace*).

**Исключения (Exceptions)** происходят в результате возникновения проблем в программе, которые, в принципе, решаемы.

Например, произошло деление на ноль в целых числах.  В этом случае программа может продолжить нормальную работу. Например, если возникла проблема получения данных по сети из-за того, что отвалился Wi-Fi, можно вывести сообщение о том, что связь временно прервалась, дождаться возобновления связи и продолжить загрузку данных.

Exception — это и есть классическое исключение, которое генерируется вследствие неправильной работы программы, которое мы можем обрабатывать. Здесь иерархия тоже делится на две больших ветви: подклассы RuntimeException — ошибки программирования, и остальные, самые главные из которых — IOExceptions — ошибки ввода вывода, мы подробно рассмотрим в этом модуле.

Исключения делятся также на две группы: checked и unchecked (проверяемые и непроверяемые).

![](../img/JAVA_NEW_10.1_4.png)

На диаграмме красным цветом выделены непроверяемые, мы не должны писать никакого дополнительного кода для их обработки. Но можем.

А вот если код может выбросить проверяемое исключение, это нужно обязательно обрабатывать. 

Давайте рассмотрим пример исключений. И нем покажем, как и зачем можно перехватывать исключения.

### IndexOfBoundsException. Программа для гаданий

Это исключение очень часто возникает в программах. Например, в такой:

```java
int[] array = {1, 2, -1, 5, 3};
int s = 0, i;
for (i = 0; i <= array.length; i++);
{
    s += array[i];   
}
System.out.println(s);
```
Этот фрагмент должен выводить сумму элементов массива, но при запуске программа падает с ошибкой:

```cmd
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 5 out of bounds for length 5
	at Main.main(Main.java:16)
```

ArrayIndexOutOfBoundExсeption — это подкласс класса IndexOfBoundsException.

Тут не много строк, но вывод подсказывает, какая ошибка возникла и где. Уверены, вы очень быстро найдете здесь ошибку и после исправления программа начнет работать правильно.

Программа упадет с ошибкой IndexOutOfBoundsException. Исправить ситуацию можно двумя способами: добавить в программу if или перехватить исключение.

В первом случае делаем так:
```java 
int n = in.nextInt();
if (n < lines.size()) {
       System.out.println("Вот предсказание для вас:\n" + lines.get(n));
}
else {
     System.out.println("Вы ввели недопустимый номер..." ); 
}
```

Во втором так:
```java
int n = in.nextInt();
try {
       System.out.println("Вот предсказание для вас:\n" + lines.get(n));
}
catch (Exception e) {
     System.out.println("Вы ввели недопустимый номер..." ); 
}
```

Здесь мы поступаем таким образом: «попробуем взять строку с номером n (блок в скобках после слова try, англ. пытаться) и, если не получится, то … (блок в скобках после слова catch, англ. ловить)».

Какой из способов лучше? Кажется, что первый. Возможно. Но иногда причин того, что программа сработает неверно, бывает несколько, и нужно городить целую батарею из if-ов. И в этих случаях удобно перехватывать исключения.  Кстати, вариант с if-ом всё ещё легко сломать, если ввести отрицательное число, мы эту проверку упустили.

## Класс RuntimeException и его подклассы
Класс RuntimeException и его подклассы относятся к непроверяемым исключениям. Компилятор не проверяет, может ли метод генерировать эти исключения. Исключения типа RuntimeException генерируются при возникновении ошибок во время выполнения приложения. Почему возникла необходимость деления исключений на проверяемые и непроверяемые? 
Посмотрим на конкретные unchecked исключения: 

* деление в целочисленных типах вида a/b при b=0 генерирует исключение ArithmeticException; 
* индексация массивов. Выход за пределы массива приводит к исключению ArrayIndexOutOfBoundException;
* вызов метода на ссылке вида obj.toString(), если obj ссылается на null порождает NullPointerException.

Если бы возможность появления перечисленных исключений проверялась на этапе компиляции или запуска, то любая попытка проверки массива на индекс или каждый вызов метода требовали бы или блока обработки исключения, или оператора проверки всего метода. Такой код был бы практически непригоден для понимания и поддержки. Именно поэтому часть исключений была выделена в группу непроверяемых, и ответственность за защиту приложения от последствий их возникновения возложена на программиста.

Перечислим часто встречаемые unchecked exception:

|Тип исключения|	С чем связана ошибка|
|---|---|
|ArithmeticException|	Выполнение арифметических операций (например, деление на ноль).|
|ArrayIndexOutOfBoundsException|	Индекс массива выходит за допустимые границы.|
|ArrayStoreException|	Присвоение элементу массива значения несовместимого типа.|
|ClassCastException|	Попытка выполнить приведение несовместимых типов.|
|NegativeArraySizeException|	Попытка создать массив отрицательного размера.|
|NullPointerException|	Некорректное использование ссылок (обычно, когда мы вызываем метод объектной переменной, которая содержит пустую ссылку).|
|NumberFormatException|	Преобразование строки к числовому значению (когда в число преобразуется строка, содержащая некорректное текстовое представление числа).|
|StringIndexOutOfBoundsException|	Неверное индексирование при работе с текстовой строкой.|

## Класс IOException и его подклассы
![](../img/JAVA_NEW_10.3_1.png)

Ошибки ввода вывода, возникающие при чтении из сети и из файлов  — это подклассы IOException. Они нуждаются в обработке. 

Пожалуй, самыми частыми здесь являются FileNotFoundException и сам IOException. Так как первый является  подклассом второго, достаточно бывает обработать только IOException, потому что оно практически всегда нуждается в обработке. Ведь, мы открывали файл для чтения или для записи, для чего же еще?!

### Работа с исключениями
Что можно делать с исключениями? С непроверяемыми можно ничего не делать, а проверяемые нужно обязательно обрабатывать, иначе программа не скомпилируется.

Какие у нас варианты?
**throws…  — отказаться от ответственности**

Самый простой способ обработки исключений  — не обрабатывать их. Мы поступали именно так в первой части модуля.

Если в методе может возникнуть исключение какого-то типа, то можно просто добавить в заголовок этого метода throws этого исключения или его подкласса, и все — забота об обработке лежит на вызвавшем методе.

Вернёмся к примеру из первой части модуля.

```java
import java.io.FileOutputStream;
import java.io.IOException;
public class FileOutputStreamEx {

	public static void main(String[] args) throws IOException {
		FileOutputStream fos = new FileOutputStream("test.txt");
		fos.write("Hello FileOutputStream world".getBytes());
        fos.close();    
	}
}
```
Здесь мы можем получить исключения IOException и FileNotFoundException. В throws указывать несколько возможных исключений через запятую. Но в данном случае это не нужно, потому что IOException более общее.

### Обработка try-catch-finally
Но можно и по-честному обработать.

В примерах мы уже видели, что для обработки исключений есть специально зарезервированные ключевые слова: 

try {...}  —  ключевое слово, определяющее участок кода, в котором может произойти исключение (ошибка).
catch (тип_исключения){...} — ключевое слово, определяющее участок кода, который отвечает за обработку исключения. Этот блок может быть использован несколько раз. 
И ещё есть: 

finally {...} — ключевое слово, определяющее дополнительный участок кода, который выполняется в любом случае. Этот блок реализуется после последнего блока catch. Как правило, этот блок используется для освобождения ресурсов, например, закрытия файлов.
Общий алгоритм обработки исключений имеет следующий вид:

![](../img/JAVA_NEW_10.3_3.png)

Сначала определяем потенциально опасный участок кода нашей программы и заключаем его в блок try. Если код все-таки генерирует исключение по какой-то причине, то в дело вступает код, который нацелен на обработку ошибки определенного типа. Далее смотрим на наличие блока finally. Если этот блок присутствует, то выполняется код из него. Обычно в блоке finally размещают код сохранения данных, чтобы, если уж программа упала с ошибкой, в любом случае хотя бы не повредить, то что есть. Если нет, то действия по обработке исключения закончены.

Зачем же вообще блок finally, если мы до него «доезжаем» в любом случае?
Дело в том, что исключение может возникнуть и в блоке catch(), и тогда мы вывалимся с ошибкой, и finally выполнен не будет.

разные варианты этой конструкции:

1. Стандартный блок try{} catch(){} finally{}:
```java
try {
//здесь пишем код, который потенциально может привести к ошибке

} 
catch(SomeException e ) { //в скобках указывается класс конкретной ожидаемой ошибки  //здесь пишем код, направленный на обработку исключений
}
finally {
//выполняется в любом случае ( блок finally не обязателен)
}
```

2. Блок без обработки возможного исключения:
```java
try {
//здесь пишем код, который потенциально может привести к ошибке
} 
finally {
//выполняется в любом случае
}
```
3. Отлавливание исключений с обработкой нескольких исключений:
```java
try {
//здесь пишем код, который потенциально может привести к ошибке
} 
catch(SomeException e ) { //в скобках указывается класс конкретной ожидаемой ошибки  //здесь пишем код, направленный на обработку исключений
} 
catch(AnotherException e ) { //в скобках указывается класс конкретной ожидаемой ошибки 
 //здесь пишем код, направленный на обработку исключений типа AnotherException
}
```

В данном примере мы попытаемся привести строку к числу с помощью класса NumberFormat. Для этого мы заведомо дадим неправильные данные.
```java
try {
   	NumberFormat nf = NumberFormat.getInstance();
   	//специально создаем ситуацию, которая приведет к исключению
   	System.out.println(nf.parse("NOT A NUMBER"));
} 
catch (ParseException e) {
   	System.out.println(e.getMessage());
}
System.out.println("Конец программы!"); 
```

В результате мы получим информацию о том, что была совершена ошибка, которую при желании сможем обработать и вывести ответ пользователю в нужном нам виде. Попробуйте убедиться в этом, запустив код из примера у себя в среде разработки.

Теперь попытаемся получить символ строки по странному индексу:
```java
String string = "123";
try
{
    char chr = string.charAt(10);
}
catch(StringIndexOutOfBoundsException ex)
{
   System.out.println(ex.toString());
}
System.out.println("Конец программы!");
```
В обоих примерах на выводе мы увидим на выводе “Конец программы!”. То есть благодаря обработке исключения программа не упала, а доработала до конца.

### Обработка нескольких исключений
На практике часто складывается такая ситуация, когда в одном блоке try может быть выброшены исключения нескольких типов. В таком случае нам необходимо использовать несколько блоков catch, если мы не отлавливали ошибки по классу Exception (что делать не рекомендуется). Такая конструкция имеет следующий вид (проще посмотреть на примере:
```java
public void doAction() {
   try {
       int a = (int)(Math.random() * 2);
       System.out.println("a = " + a);
       int c[] = { 1/a }; // опасное место #1
       c[a] = 71; // опасное место #2
   } catch(ArithmeticException e) {
       System.err.println("деление на 0" + e);
   } catch(ArrayIndexOutOfBoundsException e) {
       System.err.println("out of bound: " + e);
   } // окончание try-catch блока
   System.out.println("after try-catch");
}
```
В данном примере строка int c[] = { 1/a }; является потенциально опасной потому, что строкой выше а генерируется случайным образом, и может принять значение 0 или 1. Если значение будет равнятся 0, то получим ошибку деления на ноль. Если а=1, то в этой строке c[a] = 71; выйдем за границы массива.

Подклассы исключений, которые используются в блоках catch, должны следовать перед любым из их суперклассов, иначе суперкласс будет перехватывать эти исключения.
Давайте рассмотрим пример: 
```java
try { /* код, который может вызвать исключение */
} catch(IllegalArgumentException e) {...
} catch(PatternSyntaxException e) {... } /* никогда не может быть вызван: ошибка компиляции */
```

В данном примере PatternSyntaxException представляет собой подкласс класса IllegalArgumentException. Правильная конструкция будет иметь следующий вид:

```java
try { /* код, который может вызвать исключение */ 
    } catch (PatternSyntaxException e) { ...
    } catch (IllegalArgumentException e) { ...}
```
То есть в данном примере обязательно нужно было поменять местами блоки catch.

На практике иногда возникают ситуации, когда инструкций catch несколько, и обработка производится идентичная, например, вывод сообщения об исключении в журнал.

```java
try {
// Любые действия, которые могут породить исключения
       } catch (NumberFormatException e) {
           e.printStackTrace();
       } catch (ClassNotFoundException e) {
           e.printStackTrace();
       } catch (InstantiationException e) {
           e.printStackTrace();
       }
```
В седьмой версии Java появилась возможность сокращения кода, избавляя код от избыточности, используя для разделения оператор |.
```java
try {
//Любые действия, которые могут породить исключения
       } catch (NumberFormatException | ClassNotFoundException | InstantiationException e) {
           e.printStackTrace();
       }
```

### try-with-resources  — о закрытии потоков можно не думать!
В Java7 (вот к чему эти постоянные отсылки к истории, кто вообще сейчас программирует на Java до 8-й версии!), так вот, в Java 7 появилась возможность открывать потоки в скобках try, и закрывать их тогда не надо!

Вот такой метод, решающий маленькую задачу чтения единственной строки из файла, приходится писать в миллион строк.
```java
static String readFirstLineFromFileWithFinallyBlock(String path) {
   BufferedReader br = null;
   try {
        br = new BufferedReader(new FileReader(path));   
        return br.readLine();
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if (br != null) {
            // и снова try-catch потому что...
            try {
                br.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        return null;
    }
}
```
А с использованием **try-with-resources** получается вполне компактно:

```java
static String readFirstLineFromFileWithTryWithResources(String path) {
   // открывается прямо на месте, а закрывается само!
   try ( BufferedReader br = new BufferedReader(new FileReader(path))){
           return br.readLine();
       } catch (IOException e) {
           e.printStackTrace();
       }
   return null;
}
```
В этих программах используется метод printStackTrace(). Это очень полезный метод, выводящий много полезной информации о возникшей ошибке. Мы его обсудим в следующем юните.

### Стектрейс. Учимся понимать, что случилось
И все-таки программа сломалась и на экране появилось это:
```cmd
Exception in thread "main" java.lang.NullPointerException at com.example.myproject.Book.getTitle(Book.java:16) at com.example.myproject.Author.getBookTitles(Author.java:25) at com.example.myproject.Bootstrap.main(Bootstrap.java:14)
```
Или это:
```cmd
Exception in thread "main" java.lang.IllegalStateException: A book has a null property at com.example.myproject.Author.getBookIds(Author.java:38) at com.example.myproject.Bootstrap.main(Bootstrap.java:14) Caused by: java.lang.NullPointerException at com.example.myproject.Book.getId(Book.java:22) at com.example.myproject.Author.getBookIds(Author.java:36) ... 1 more
```
И во всем этом можно разобраться?

Нужно!
**Stack Trace** — очень полезный информативный инструмент для отладки приложений. *Stack Trace* указывает место, где было выброшено исключение. Он показывает стек методов, в которых приложение было, когда исключение возникло.

Обычно приложение работает так: одни методы вызывают другие, те, в свою очередь, третьи, третьи вызывают четвертые… 

![](../img/JAVA_NEW_10.4_1.png)

И вот в пятых или в седьмых, или в сотых возникает ошибка. Stack Trace и показывает весь путь до ошибки. 

Рассмотрим модельный пример:
```java
public class ErrorChecking {
    public static void main(String[] args) {
        System.out.println("Метод main() успешно запущен");
        method1();
        System.out.println("Метод main() заканчивает свою работу");
    }

    static void method1() {
        System.out.println("Первый метод передаёт привет!");
        method2();
    }

    static void method2() {
        System.out.println("Второй метод передаёт привет!");
    }
}
```
В нашем классе реализовано три метода: main(), method1() и method2().

Как только приложение было запущено, метод main помещается в стек, становится его вершиной (занимает 1 позицию). В методе Main мы вызываем метод Method1, где затем вызывается метод method2. Как вы уже могли догадаться, метод method2 становится на вершину стека. После выполнения метода method2 начинаем возвращать управление методам. 
На экране мы получим следующий ряд сообщений:
```
Метод Main успешно запущен
Первый метод передаёт привет!
Второй метод передаёт привет!
Метод Main заканчивает свою работу
```
```java
public class ErrorChecking {
    public static void main(String[] args) {
        System.out.println("Метод Main успешно запущен");
        method1();
        System.out.println("Метод Main заканчивает свою работу");
    }

    static void method1() {
        System.out.println("Первый метод передаёт привет!");
        method2();
    }

    static void method2() {
        int x = 10;
        int y = 0;
        double z = x / y;
        System.out.println( z );
        System.out.println("Второй метод");
    }
}
```
Запустите программу и посмотрите, что выдаст вам программа:
```
Метод Main успешно запущен
Первый метод передаёт привет!(method1)
Exception in thread "main" java.lang.ArithmeticException: / by zero

	at errorhandling.errorChecking.method2(<u>errorChecking.java:17</u>)
	at errorhandling.errorChecking.method1(<u>Solution.java:11</u>)
	at errorhandling.errorChecking.main(<u>>Solution.java:5</u>)	
```
Теперь давайте изменим метод method1() так:
```java
try {
    System.out.println("Первый метод передаёт привет!");
    method2();
}
catch (ArithmeticException err) {
    System.out.println(err.getMessage());
}
```
Теперь мы обернули метод method2 в блок try.В блоке catch отловим исключение ArithmeticException.

Запустим код снова. В итоге на выходе получим:
```
Метод Main успешно запущен
Первый метод передаёт привет!
/ by zero
Метод Main заканчивает свою работу
```
Стоит обратить внимание на то, что на экран вывелось лишь: / by zero. Метод method2 не был выполнен полностью, а был остановлен, когда возникла ошибка. После этого контроль был передан обратно методу method1(). Это произошло из-за того, что блок catch сам распознавал ошибку. JVM (Java Virtual Machine) не обращалась к стандартному обработчику ошибок, а вывела сообщение находящееся между фигурными скобками блока catch.

Обратите внимание, что сама программа не была остановлена. Контроль, как обычно перешел к методу main(), откуда method1() был вызван. И последняя строка метода main() смогла вывести на экран: Метод Main заканчивает свою работу.

У всех Throwable есть метод printStackTrace(), который и выводит стек вызовов. Им часто пользуются в блоке catch. Сама среда генерирует этот вызов.

### Собственные исключения, throw
Вам мало стандартных исключений? Можно создать свои и выбрасывать их!

Главный вопрос: Зачем?

Созданное исключение повышает читабельность и восприятие кода. Часто  можно встретить такой код:
```java
public void getBookIds(int id) {
    try { 
    book.getId(id); 
    } catch (NullPointerException e) { 
        throw new CustomException("A book has a null property", e) 
    }
}
```
Мы перехватываем противный NullPointerException и тут же возбуждаем новое, свое, приятное глазу и дополняем его информативным сообщением.

Внимание! Не путать throw (выбросить, возбудить исключение) и throws (здесь мы сообщаем о ненадежности функции, что она может и взбрыкнуть).

Чтобы создать своё собственное исключение, мы должны расширить класс Exceptions или его подклассы. 

Давайте рассмотрим пример создания своего собственного исключения:
```java
public class MyException extends Exception {
   private int detail;
   public MyException(int detail, String message) {
        super(message);
        this.detail = detail;
   }
   @Override
   public String toString() {
        return "MyException{"
               + "detail=" + detail
               + ", message=" + getMessage()
               + "} ";
   }
}
```
При реальном программировании создание собственных классов исключений позволяет разработчику выделить важные аспекты приложения и обратить внимание на детали разработки.

**Что произойдет, если поместить оператор return или System.exit () в блок try/catch?**
Это очень популярный вопрос «на засыпку» по Java. Хитрость его в том, что многие программисты считают, что блок finally выполняется в любом случае. Данный вопрос ставит эту концепцию под сомнение путем помещения оператора return в блок try/catch или вызова из блока try/catch оператора System.exit ().

Ответ на этот каверзный вопрос: блок finally будет выполняться при помещении оператора return в блок try/catch, и не будет выполняться при вызове из блока try/catch оператора System.exit ().

**Предположим, есть блок try-finally. В блоке try возникло исключение и выполнение переместилось в блок finally. В блоке finally тоже возникло исключение. Какое из двух исключений «выпадет» из блока try-finally? Что случится со вторым исключением?**
В данном примере в любом случае отобразится на экране исключение, которое выбрасывается в блоке finally.

**Предположим, есть метод, который может выбросить IOException и FileNotFoundException. В какой последовательности должны идти блоки catch? Сколько блоков catch будет выполнено?**

Общее правило — обрабатывать исключения нужно от «младшего» к старшему. Т.е. нельзя поставить в первый блок catch(Exception e) {}, иначе все дальнейшие блоки catch() уже ничего не смогут обработать, т.к. любое исключение будет попадать под ExceptionName extends Exception.

Таким образом сначала нужно обработать public class FileNotFoundException extends IOException, а затем уже IOException.

**Есть метод, в котором есть блок try-catch-finally. В блоке try возвращается 1, в catch — 2, finally — 3. Какое значение вернется в итоге выполнения метода?**
Правильный ответ:  3. Вернётся то значение, которое находится в блоке finally — 3 .













# Multithreading


# Datenstrukturen
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

Интерфейс обычно обеспечивает само прикладное приложение. Как правило, это окно с набором полей для ввода данных и кнопками для управления ими. Также с помощью приложения мы можем выводить данные с нескольких таблиц или баз, и мы можем скрыть некоторые данные, если они вдруг стали неактуальными. В итоге интерфейс представляет данные пользователю в понятной и информативной форме.

У различных языков программирования обычно разные стандарты для взаимодействия с БД.

Например, в Python используется Python DB-API, благодаря которой можно подключаться к различным БД с примерно одинаковыми конструкциями. Скорее это набор правил, которым должны следовать несколько библиотек.

Ниже показана небольшая таблица о соответствии библиотеки и БД:

|База данных|DB-API модуль|
|---|---|
|SQLite|sqlite3|
|PostgreSQL|psycopg2|
|MySQL|mysql.connector|
|ODBC|pyodbc|

Интерфейс подключения в Java, называется JDBC (Java Database Connectivity). Предоставляется он самой платформой и, также как и в других языках, не привязан к какой-либо конкретной СУБД.  JDBC реализован в виде **пакета java.sql**, входящего в состав Java SE. Но помимо интерфейса нам также потребуются **драйверы баз данных**.

### Немного о драйверах
Драйвер для PostgreSQL можно получить через Maven. Это такое место в интернете — репозиторий, в котором хранятся библиотеки.

В принципе, можно создать пустой Maven-проект и сразу сделать вставку в pom.xml, как показано ниже:

**PostgreSQL:**
```xml
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <version>42.2.18</version>
</dependency>
```

**Oracle:**
```xml
<dependency>
   <groupId>com.oracle</groupId>
   <artifactId>ojdbc6</artifactId>
   <version>11.2.0.3</version>
</dependency>
```

**MSSQL:**
```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.4.1.jre14</version>
</dependency>
```

**MySQL:**
```xml
<dependency>
   <groupId>mysql</groupId>
   <artifactId>mysql-connector-java</artifactId>
   <version>5.1.38</version>
</dependency>
```

Для эффективного решения задач, связанных с базами данных, есть достаточно простой паттерн **DAO** (Data Access Object). Сам по себе **DAO** — это абстрактный класс или интерфейс, в котором обычно описывают методы добавления, обновления, удаления и т.д. в базу данных. Основная его задача — **абстрагировать доступ** к различным БД.

Основное его предназначение — уменьшить количество переписываемого кода в случае, когда нам потребуется сменить базу данных или логику приложения. Данный класс не конечный и может дополняться различными методами в зависимости от нужд реализации. Рассмотрим самый простой пример.

Создаём класс — условную «коробку», в которой будем хранить данные:
```java
public class Box {
    private String boxname;
}
```

```java
//Дальше создаем наш интерфейс DAO:
import java.util.List;
import java.util.Optional;

public interface Dao<T> {
    Optional<T> get(long id);
    List<T> getAll();
    void save(T t);
    void update(T t, String[] params);
    void delete(T t);
}
```

```java
//И теперь реализуем пользовательский интерфейс DAO:
import java.util.List;
import java.util.Optional;

public class BoxDao implements Dao<Box>{

    @Override
    public Optional<Box> get(long id) {
        return Optional.empty();
    }

    @Override
    public List<Box> getAll() {
        return null;
    }

    @Override
    public void save(Box box) {
    }

    @Override
    public void update(Box box, String[] params) {
    }

    @Override
    public void delete(Box box) {
    }
}
```

Понятно, что в методах save, update и delete мы должны описать взаимодействие с БД. Сделаем это в следующих юнитах .

Ну и пример реализации в основном коде программы:
```java
public class Main {
     private static Dao boxdao;
     public static void main(String[] args) {
         boxdao = new BoxDao();
         boxdao.save(new Box("TestNameBox"));
    }
}
```

Как становится ясно, данный паттерн сильно упрощает жизнь программиста, так как при смене типа БД или подключения в БД код не надо будет переписывать. Но для создания более-менее рабочего приложения мы должны также разобраться, как работают драйвера JDBC, и что это такое.

## Архитектура JDBC
### Понятие драйвера

Драйвер — это некоторая сущность, благодаря которой реализуются интерфейсы JDBC. Он позволяет получить соединение с БД по специально описанному URL. Загружаются драйверы обычно динамически во время работы нашего приложения. Вызываются автоматически, когда приложению требуется загрузить URL, при этом в URL’e содержится протокол, за который драйвер отвечает.

Создадим такую строку в коде и попробуем подключиться.

Для того чтобы подключиться, нужно знать некоторые данные о своей установленной PostgreSQL:

* где она установлена;
* имя и пароль пользователя;
* имя базы данных;
* порт (необязательно).

Выполняя ранее известные условия, мы знаем:

* место установки localhost;
* стандартный пользователь БД при первой установке — postgres, пароль тот, что указали при установке (в моём случае это 00000);
* в качестве базы для подключения используем служебную базу с именем postgres;
* порт не указываем, так как скорее всего был выбран порт по умолчанию.

Теперь нам надо преобразовать эти данные в строку для подключения:

```java
private static final String URL = "jdbc:postgresql://localhost/postgres?user=postgres&password=000000";
```

Целиком код будет выглядеть так:

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Main {

    private static final String URL = "jdbc:postgresql://localhost/postgres?user=postgres&password=000000";
  
    private static Connection con;

    public static void main(String[] args) {
        try {
            con = DriverManager.getConnection(URL);
            con.close();
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }
    }
}
```

Результатом выполнения будет :
```
Process finished with exit code 0
```

Если зайти в приложение PgAdmin и посмотреть, что происходит с базой после нескольких запусков программы, то можно увидеть, что есть активность.

![](../img/java_23_1.png)

Программа выполнилась без ошибок. Теперь стоит немного разобраться с тем, что мы сделали, что такое **интерфейс Connection** и как он работает.

### Интерфейс Connection
Интерфейс Connection является элементом JDBC API и необходим нам для взаимодействия с БД. Мы его можем представить как **средство для создания сессий**. Он отвечает за физическое подключение к базе данных.

Улучшим предыдущий пример под PostgreSQL, написав теперь переменную интерфейса нормально, а также перепишем конструкцию *try-catch* как *try-with-resources*:

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Main {

    private static final String URL = "jdbc:postgresql://localhost/postgres?user=postgres&password=0000000";

    private static String conok="Соединение с бд установлено";
    private static String conerr="Произошла ошибка подключения к бд";

    public static void main(String[] args) {
        try (Connection connection = DriverManager.getConnection(URL)){
            System.out.println(String.format("%s",conok));
        } catch (SQLException e) {
            System.out.println(String.format("%s",conerr));
            e.printStackTrace();
        }
    }
}
```

При удачном подключении к БД появится строка в терминале, показывающая, что всё ок. А при неудачном подключении она покажет, что подключение не прошло и в чем возможная причина. Например, если поменять пароль на несуществующий:

```cmd
Произошла ошибка подключения к бд
org.postgresql.util.PSQLException: ВАЖНО: пользователь "postgres" не прошёл проверку подлинности (по паролю) (pgjdbc: autodetected server-encoding to be windows-1251, if the message is not readable, please check database logs and/or host, port, dbname, user, password, pg_hba.conf)
	at org.postgresql.core.v3.ConnectionFactoryImpl.doAuthentication(ConnectionFactoryImpl.java:613)
```

Ну или попытаться подключиться к базе, которой нет:
```cmd
Произошла ошибка подключения к бд
org.postgresql.util.PSQLException: ВАЖНО: база данных "testpostgres" не существует (pgjdbc: autodetected server-encoding to be windows-1251, if the message is not readable, please check database logs and/or host, port, dbname, user, password, pg_hba.conf)
	at org.postgresql.core.v3.QueryExecutorImpl.receiveErrorResponse(QueryExecutorImpl.java:2553)
```

### Интерфейс Statement
После того как мы поняли, как создавать соединение с базой данных, логично было бы узнать, как можно выполнять в ней запросы. Интерфейс **Statement** позволяет делать запросы к БД, которые определены как константы, и не принимают никаких параметров.

Тут следует пояснить, что под константой имеется ввиду заранее определенная строка типа:

```java
String s = "SELECT * from testtable;";
```

Перед тем как использовать данный интерфейс для наших запросов к БД, нам нужно его создать. Для этого используем метод сonnection.createStatement(). Посмотрим, как он будет выглядеть в коде нашей программы:

```java
Statement statement = connection.createStatement();
```

И теперь, как уже говорили ранее — для того чтобы выполнить запрос, мы должны создать его как строковую константу:

```java
String sql = "SELECT * FROM test";
```

Ну и делаем запрос на выполнение:

```java
statement.execute(sql);
```

Но это немного некрасивый код, корректно будет сделать так:
```java
boolean isExecuted=statement.execute(sql);
if (isExecuted){
    System.out.println("SELECT executed");
}
```

Теперь при выполнении кода уже увидим следующее:

```cmd
Соединение с БД установлено корректно
SELECT executed
Process finished with exit code 0 
```

Прежде чем перейти дальше, обратите внимание на один важный момент. После того как мы выполним наш запрос, чтобы данные сохранились в базе, нам нужно использовать метод close().

```java
statement.close();
connection.close();
```

Создадим тестовую БД — testDB, а в ней тестовую таблицу — testTable:

![create test](../img/java_23_2.png)

Добавляем таблицу:

![](../img/java_23_3.png)

Добавляем в неё тестовые данные:
```sql
insert into test(id) values (2),(9),(10);
```

![](../img/java_23_4.png)

У интерфейса Statement для получения результатов существует три метода:
* boolean execute(String s);
* int executeUpdate(String s);
* ResultSet executeQuery(String s).

Первый, *boolean execute(String SQL)*, возвращает логический ответ true, если метод executeQuery может быть выполнен, в результате чего может быть получено значение ResultSet.

Второй, *int executeUpdate(String SQL)*, возвращает число. Это число показывает, на сколько столбцов в таблице повлиял наш запрос. При вызове с SELECT запросом выдаст ошибку:

```cmd
SQLException : Can not issue SELECT via executeUpdate() or executeLargeUpdate().
```

Третий, *ResultSet executeQuery(String SQL)*, возвращает объект **ResultSet** и используется для получения множества результатов, обычно с SELECT запросом.

Пример кода:
```java
ResultSet resultSet = statement.executeQuery(sql);
System.out.println("ID");
System.out.println("||------------||");
while (resultSet.next()){
   System.out.println(resultSet.getInt("ID"));
}
System.out.println("||------------||");

// Select executed
// ID
// ||------------||
// 2
// 9
// 10
// ||------------||
// Process finished with exit code 0
```

Кстати, также как для метода execute(), перед выходом нужно использовать метод close():

```java
statement.close();
resultSet.close();
connection.close();
```

### Интерфейсы PreparedStatement и CallableStatement
В случае, когда нам нужно передать в выражение какие-нибудь значения, и также требуется несколько раз вызывать один и тот же запрос, мы можем использовать метод PreparedStatement. Рассмотрим небольшой пример:

```java
int count = 2;
String SQL = "Select * from test WHERE id = ?;";
try (PreparedStatement preparedStatement = connection.prepareStatement(SQL)); {
    preparedStatement.setInt(1, count);
    ResultSet resultSet = preparedStatement.executeQuery();

    while (resultSet.next()) {
        System.out.println(resultSet.getInt("ID"));
    }
}
```

Знак вопроса **?** называется **маркером** и способен получать значение. Стоит заметить, что нумерация начинается с единицы, а не с нуля, как в обычных массивах.

Ещё один небольшой пример на добавление данных в таблицу (*таблицы не существует в PostgreSQL и пример скорее для того, чтобы посмотреть, как можно использовать маркеры*):

```java
int ourint = 3;
String ourname = "testname";

String sql = "Insert into test (id, name) Values (?, ?)";
PreparedStatement preparedStatement = connection.prepareStatement(sql);
preparedStatement.setInt(1, ourint);
preparedStatement.setSrting(2, ourname);
int rows = preparedStatement.executeUpdate();
System.out.println(rows + "Строк добавлено");
```

**PreparedStatement**, так же как и **Statement**, обладает методами **execute, executeUpdate, executeQuery**. И так же перед завершением работы с интерфейсом или БД нужно вызвать метод его закрытия **preparedStatement.close();**.

Интерфейс CallableStatement позволяет нашему приложению вызвать хранимую на сервере DB процедуру. Так же как и в PreparedStatement, с помощью маркеров мы можем определить операторы, но есть и отличие — мы можем использовать не только порядковое местоположение, но и указание по имени. Звучит, наверное, сложновато, но на примере сейчас станет понятно.

```java
String SQL= "{call ourpostgresqlProc(?,?,?)}"; 
// Создаем подключение
try(CallableStatement callableStatement = connection.prepareCall(SQL)){
// Добавляем три значения
   callableStatement.setInt(1, 123);
   callableStatement.setString(2, "name");
   callableStatement.setString(3, "surname");
// вызываем функцию, которая лежит у нас в базе
   callableStatement.executeUpdate();
}
```

Ну или в случае, когда мы знаем, как в процедуре называются наши переменные, мы можем обратиться к ним по имени:
```java
String SQL= "{call ourProc(?,?,?)}"; 
try (CallableStatement callableStatement = connection.prepareCall(SQL)){
   callableStatement.setInt("ID", 123);
   callableStatement.setString("NAME", "Ivan");
   callableStatement.setString("SURNAME", "Ivanov");
   callableStatement.executeUpdate();
   callableStatement.close();
}
```

В пакете java sql мы используем методы, часть из которых требует закрытия **close()**, а часть — нет.

|Методы|Описание|Требуется закрытие?|
|---|---|---|
|DriverManager|Подключение драйвера|–|
|Connection|Создание сессии|+|
|Statement|Для вызова статических запросов|+|
|PreparedStatement|Для вызова запросов с параметрами|+|
|CallableStatement|Для вызова функций|+|
|ResultSet|Множество ответов после выполнения запроса|–|

Стоит упомянуть, что конструкция *try-with-resources* имеет приоритет перед методом *close*.

### Практикум
В качестве практики мы создадим базу данных и попробуем к ней подключиться. После этого напишем небольшой код программы.

Но для начала надо определить, как мы скачиваем JDBC драйвер:

либо через Maven:
```xml
<dependencies>
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>42.2.18</version>
    </dependency>
</dependencies>
```
либо скачиваем [тут](https://jdbc.postgresql.org/download/postgresql-42.2.18.jar):

![](../img/java_23_5.png)

Создаём в нашем рабочем проекте директорию lib и перекладываем туда JAR-файл драйвера из архива. В директории нажимаем правой клавишей мыши и выбираем пункт Add as Library...

Итоговый код выглядит так в обоих случаях:

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Main {

   private static final String URL = "jdbc:postgresql://localhost/testDB?user=postgres&password=000000";
   private static String conok="Соединение с бд установлено";
   private static String conerr="Произошла ошибка подключения к бд";

   public static void main(String[] args) {
       try (Connection connection = DriverManager.getConnection(URL)){
           System.out.println(String.format("%s",conok));
       } catch (SQLException e) {
           System.out.println(String.format("%s",conerr));
           e.printStackTrace();
       }
   }
}
```
При попытке запустить получаем:

```cmd
Соединение с бд установлено
Process finished with exit code 0
```

## Выполнение запросов средствами JDBC
Давайте попробуем немного углубиться в интерфейс **PreparedStatement**. Мы уже знаем, что маркер **?** позволяет передавать различные переменные в запрос.

На примере мы рассмотрели методы **setInt** и **setString**, но это не все методы, также существуют и другие:

* setBigDecimal — похож на класс float, но имеет более гибкую настройку дробной части и используется для работы с финансами.
* setBoolean;
* setDate — используется для передачи даты, имеет примерно такую конструкцию: setDate(2, new java.sql.Date(System.currentTimeMillis()));
* setDouble;
* setFloat;
* setLong;
* setNull — устанавливает null значение для необходимой нам ячейки, так как если попробовать передать через setInt(1,j), притом ранее мы определим j=null, то возникнет ошибка: s.setNull(10, java.sql.Types.INTEGER);
* setTime — используется как и date, но для передачи времени.

Так как PreparedStatement наследует Statement, он тоже имеет 3 метода для выполнения запроса:

* **boolean execute()**, можно выполнить на любом запросе и он вернёт результат, выполнится ли запрос.
* **ResultSet executeQuery()** выполняет **select** запрос и возвращает искомое множество в виде **resultset** переменной.
* **int executeUpdate()** создан для того, чтобы выполнять **create**, **insert**,**update** и **delete** запросы. Возвращает количество измененных строк.

Стоит сказать, что устанавливать значения параметров не в момент составления запроса, а в момент его выполнения, очень удобно.

```
Интересно знать, что количество маркеров в одном запросе не бесконечно и имеет ограничение в две тысячи.
```
```cmd
Caused by: java.sql.SQLException: Prepared or callable statement has more than 2000 parameter markers.
       at net.sourceforge.jtds.jdbc.SQLParser.parse(SQLParser.java:1139)
       at net.sourceforge.jtds.jdbc.SQLParser.parse(SQLParser.java:156)
       at net.sourceforge.jtds.jdbc.JtdsPreparedStatement.<init>(JtdsPreparedStatement.java:107)
Caused by: java.sql.SQLException: Prepared or callable statement has more than 2000 parameter markers.
```

А теперь немного о том, почему стоит использовать **PreparedStatement** вместо **Statement**.

Метод Statement складывает строки значений и строки запроса. А вот **PreparedStatement** имеет по сути шаблон запроса, и данные в него вставляются с учётом кавычек. Данный метод позволяет защититься от SQL инъекций.

Рассмотрим на простом примере. Есть у нас такая таблица:

```
+-----------+----+--------+
| user      | id |password|
+-----------+----+--------+
| admin     |  1 |  admin |
| user      |  2 |  pass  |
| guest     |  3 |  guest |
+-----------+----+--------+
```

В таблице 3 столбца: имя пользователя, его id и его пароль. Сделаем запрос пользователя в программе.

Значения user.name и user.pass определяем заранее и передаем в нашу программу через консоль:
```
enter user : admin
enter password : admin
```

```java
String query = "SELECT user, id, password FROM users WHERE user='" + user.name + "' AND password = '" + user.pass + "'";
System.out.println(query);
ResultSet resultSet = statement.executeQuery(query);

while (resultSet.next()) {
    System.out.println("User: id=" + resultSet.getInt("id") +
        "name=" + resultSet.getString("user") +
        "password=" + resultSet.getString("password"));

}
```
Ответ программы будет таким:
```java
User: id=1 name=admin pass=admin
```

Итоговый запрос в базу данных будет выглядеть следующим образом:
```sql
select user, id, password 
from users 
where user = 'admin' and password ='admin';
```

Если комбинация логин и пароль не совпадают с теми, что указаны, то и данные о пользователе мы не получим.

Теперь попробуем немного изменить имя и пароль.
```
enter user : admin
enter password : nevermind' or '1' = '1
```

Пробуем запустить программу. Что мы видим в качестве результата?
```java
User: id=1 name=admin password=admin
User: id=2 name=user password=user
User: id=3 name=guest password=guest
```

Несмотря на неверный пароль, запрос выдал результат. Притом выдал вообще все данные по пользователям с паролями. Стоит более детально разобраться в логике нашего запроса, который мы передали на сервер:

```sql
select user, id, password 
from users 
where user = 'admin' and password = 'nevermind' or '1' = '1';
```

Логика итогового запроса подсказывает, что нам нужно выбрать из таблицы users строки, у которых значение поля user равно admin, значение поля password равно nevermind, или если один равно одному. Очевидно, что при переборе всех строк и сравнении значений с условиями, логин и пароль могут не совпадать, а вот один всегда равно одному для каждой строки, поэтому в результирующей выборке будут содержаться все строки таблицы users.

Давайте попробуем теперь заменить в коде метод Statement на PreparedStatement. Код при этом меняется не сильно:

```java
String query = "SELECT user, id, password FROM users WHERE user=? AND password=?";
try(PreparedStatement statement = connect.prepareStatement(query)){
    statement.setString(1, user.name);
    statement.setString(2, user.pass);
    System.out.println(statement);
    ResultSet resultSet = statement.executeQuery();
}
```

А вот результат отличается более чем. Понятно, что при правильном логине и пароле вернутся правильные значения. Давайте лучше рассмотрим пример SQL-инъекции. Передаём в консоли:

```
enter user : admin
enter password : nevermind' or '1' = '1
```

И ответа в консоль не приходит, так как логин и пароль не совпадают. Ну и чтобы понять, что произошло, следует посмотреть на итоговый запрос к базе данных:

```sql
SELECT user, id, pass 
FROM users 
WHERE user=admin
AND password='nevermind\' or\'1\'=\'1';
```

То есть метод setString экранировал кавычки, и пользователя с паролем nevermind\' or\'1\'=\'1 действительно не оказалось. Как подытог можно сказать, что лучше использовать метод PreparedStatement вместо Statement, и крайне внимательно относиться к данным в Statement.

Инициализация метода PreparedStatement крайне простая. Мы уже видели в примерах выше, как это выглядело. Вот минимальная конструкция:

```java
try (Connection connection = DriverManager.getConnection(url, username, password)) {
    String SQL = "Select * from test;";
    try (
        PreparedStatement preparedStatement = connection.prepareStatement(SQL)
    ) {}
}
```

Также можно после выполнения действий переинициализировать интерфейс, вначале закрыв его методом close(), а потом заново создав через connection.prepareStatement(SQL), но до выполнения метода connection.close().

Инициализация параметров (setInt(1,1), например) также была в нескольких примерах выше. Выполняется всегда после connection.prepareStatement(SQL) и перед preparedStatement.executeQuery(), ну или аналогичных методов запуска execute(), executeUpdate().

Интерфейс ResultSet представляет собой итоговый набор данных. Доступ к нему осуществляется построчно. Доступ к данным в нём происходит благодаря набору get методов, а переход к следующей строке происходит через метод next().

**Полученный набор ResultSet можно не закрывать методом close(), это делается родительским элементом preparedStatement, или если начинает использоваться повторно.*

Метод wasNull() возвращает true, если в последнем считанном столбце было SQL NULL значение. Этот момент следует объяснить более детально. Считывание происходит в момент вызова get-метода. Например, есть условная БД:

```sql
select * from test;
+------+
| ID   |
+------+
|    2 |
|    9 |
|   10 |
| NULL |
|    0 |
+------+
5 rows in set (0.00 sec)
```

Перебор классический построчный while (resultSet1.next()){}. Так вот, допустим, стоит такая задача — вывести в консоль результаты БД, а так как resultSet1.getInt("ID"), если наткнется на null, значение станет равным 0 и поменяет флаг в wasNull() на true.

Поэтому логично было в таком случае не сразу выводить System.out.println(resultSet1.getInt("ID"));, а с каким то промежуточным шагом, как показано ниже:

```java
while (resultSet1.next()){
   int i = resultSet1.getInt("ID");
   if (resultSet1.wasNull()){
      System.out.println("NULL");
   } else {
      System.out.println(i);
   }
}
```

Кстати, в различные get-методы возвращают различные null-значения:

* fasle в методе getBoolean;
* 0 в методах getByte, getShort, getInt, getLong, getFloat, и getDouble;
* null — во всех остальных случаях getString, getBigDecimal, getBytes, getDate, getTime, getTimestamp, getAsciiStream, getUnicodeStream, getBinaryStream, getObject.

Также помимо уже известного метода навигации next() существует ещё ряд методов:

|Метод|	Описание|
|---|---|
|beforeFirst()|	Перемещает указатель на место перед первым рядом.|
|afterLast()|	Перемещает указатель на место после крайнего ряда.|
|first()|	Перемещает указатель на первый ряд.|
|last()|	Перемещает указатель на крайний ряд.|
|previous()|	Перемещает указатель на предыдущий ряд. Возвращает false, если предыдущий ряд находится за пределами множества результатов.|
|next()|	Перемещает указатель на следующий ряд. Возвращает false, если следующий ряд находится за пределами множества результатов.|
|absolute (int| row)	Перемещает указатель на указанный ряд.|
|relative (int| row)	Перемещает указатель на указанное количество рядов от текущего.|
|getRow()|	Возвращает номер ряда, на который в данный момент указывает курсор.|
|moveToInsertRow()|	Перемещает указатель на ряд в полученном множестве, который может быть использован для того, чтобы добавить новую запись в БД. Текущее |положение указателя запоминается.
|moveToCurrentRow()|	Возвращает указатель обратно на текущий ряд в случае, если указатель ссылается на ряд, в который в данный момент добавляются данные.|

Когда мы немного разобрались с тем, что и как перемещается по БД средствами JDBC, самое время понять, как правильно формировать список всех сущностей БД.

Тут тоже ничего сложного нет. Так как считывание результатов происходит построчно, то каждая новая сущность — это строка, а каждый столбец в этой строке — это атрибут сущности.

В плане кода это тоже будет выглядеть просто. Создаем перед началом работы лист объектов. ```List<LoadModel> data```, где LoadModel выглядит так:

```java
public class LoadModel {
    int i;
}
```

Итоговый код выглядит так:
```java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class Main
{
    private  final static String  HOST     = "localhost";  // сервер базы данных
    private  final static String  DATABASENAME = "testDB"; // имя базы
    private  final static String  USERNAME = "postgres";   // учетная запись пользователя
    private  final static String  PASSWORD = "000000";     // пароль
    public  static void main(String[] args)
    {
        List<LoadModel> data = new ArrayList<>();
        String url="jdbc:postgresql://"+HOST+"/"+DATABASENAME+"?user="+USERNAME+"&password="+PASSWORD;
        try (Connection connection = DriverManager.getConnection(url, USERNAME, PASSWORD)) {
            if (connection == null)
                System.err.println("Нет соединения с БД!");
            else {
                System.out.println("Соединение с БД установлено корректно");
                String SQL = "Select * from test;";
                //Запрос на получение всех данных
                try (PreparedStatement preparedStatement = connection.prepareStatement(SQL)) {
                    try (ResultSet resultSet = preparedStatement.executeQuery()) {
                        while (resultSet.next()) {
                            int i = resultSet.getInt("ID");
                            if (resultSet.wasNull()) {
                                System.out.println("NULL");
                            } else {
                                System.out.println(i);
                            }
                            //Добавляем каждый полученный элемент в наш лист
                            LoadModel loadModel = new LoadModel();
                            loadModel.i = i;
                            data.add(loadModel);
                        }
                    }
                }
            }
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }
    }
}
```

### Практикум
Создадим простой метод для взаимодействия с БД: 

```java
public static boolean checkvalue(int checkedvalue) {
    String SQL = "Select * from test where ID=?;";
    try (PreparedStatement statement = connection.prepareStatement(SQL)) {
        statement.setInt(1, checkedvalue);
        ResultSet resultSet = statement.executeQuery();
        while (resultSet.next()) {
            return true;
        }
    } catch (SQLException throwables) {
        throwables.printStackTrace();
        return false;
    }
    return false;
}
```

Данный запрос выводит все строки, где есть искомое число с клавиатуры. Весь код будет выглядеть так:
```java
package main.java;

import java.sql.*;
import java.util.Scanner;

public class Main {
    private  final static String  HOST     = "localhost"  ; // сервер базы данных
    private  final static String  DATABASENAME = "testDB"  ;// имя базы
    private  final static String  USERNAME = "postgres"; // учетная запись пользователя
    private  final static String  PASSWORD = "000000"; // пароль пользователя
    static Connection connection;

    public static void main(String[] args){

        //Строка для соединения с бд
        String url="jdbc:postgresql://"+HOST+"/"+DATABASENAME+"?user="+USERNAME+"&password="+PASSWORD;
        try {
            connection = DriverManager.getConnection(url, USERNAME, PASSWORD);
             if (connection == null)
                System.err.println("Нет соединения с БД!");
             else {
                 System.out.println("Соединение с БД установлено корректно");
                 if(checkvalue(new Scanner(System.in).nextInt())){
                     System.out.println("Число есть в таблице");
                 }else{
                     System.out.println("Число отсутствует в таблице");
                 }
             }

        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        }
    }
    public static boolean checkvalue(int checkedvalue){
        String SQL = "Select * from test where ID=?;";
            try(PreparedStatement statement = connection.prepareStatement(SQL)){
            statement.setInt(1, checkedvalue);
            ResultSet resultSet = statement.executeQuery();
            while (resultSet.next()) {
                return true;
            }
            } catch (SQLException throwables) {
                throwables.printStackTrace();
                return false;
            }
        return false;
    }
}
```

```
Соединение с БД установлено корректно
11
Число отсутствует в таблице

Process finished with exit code 0

Соединение с БД установлено корректно
10
Число есть в таблице

Process finished with exit code 0
```

Всё корректно, наш метод работает.


## Изменение данных средствами JDBC
### Вставка и обновление данных

Вставка в БД происходит посредством использования insert запросов. Хм. Ранее мы рассматривали момент вставки через prepareStatement. Рассмотрим теперь случай, когда нам нужно изменить данные в нашей таблице.

Первый случай изменения данных — это изменение структуры таблицы. Имеем всю ту же таблицу. Добавим в неё ещё один столбец:
```java
import java.sql.*;
public class Main 
{
        private final static String HOST = "localhost"; // сервер базы данных
             private final static String DATABASENAME = "testDB"; // имя базы
             private final static String USERNAME = "postgres"; // учетная запись пользователя
             private final static String PASSWORD = "000000"; // пароль
             public static void main(String[] args) 
             {
                String url = "jdbc:postgresql://" + HOST + "/" + DATABASENAME + "?user=" + USERNAME + "&password=" + PASSWORD;
                try (Connection connection = DriverManager.getConnection(url, USERNAME, PASSWORD)) {
                        if (connection == null)
                                System.err.println("Нет соединения с БД!");
                        else {
                                System.out.println("Соединение с БД установлено.");
                                String SQL = "ALTER TABLE test ADD name varchar(255);"; // Добавление столбца name
                                try (PreparedStatement preparedStatement = connection.prepareStatement(SQL)) 
                                {
                                        preparedStatement.executeUpdate();
                                }
                        }
                } catch (SQLException throwables) {
                        throwables.printStackTrace();
                }
        }
}
```

Сам запрос:
```sql
ALTER TABLE test ADD COLUMN name varchar(255);
```

В итоге в таблице видим:

![](../img/java_23_6.png)

Изменим запрос так, чтобы добавить имя пользователя под ID = 9;.
Весь код будет таким же, кроме строки SQL-запроса:

```java
String SQL = "UPDATE test set name='Nick' where ID=9;";
```

![](../img/java_23_7.png)

### Управление транзакцией средствами интерфейса Connection
Когда мы работаем с JDBC в обычном режиме, все SQL-запросы будут выполнены, а результаты выполнения сохранены. Такой режим работы называется **auto-commit**.

Если наше приложение небольшое, то это очень удобная модель. Но если нам нужно увеличить производительность, или требуется использовать бизнес-логику, то такой режим необходимо отключить, **для того чтобы обрабатывать запросы поблочно**. Ну, и по правилам транзакции, если один запрос из блока не пройдёт, то отменяется весь блок.

Доступ к управлению транзакциями JDBC в коде можно получить с помощью команды:

```java
connection.setAutoCommit(false); 
```

Теперь после использования ряда SQL-запросов, чтобы наши данные сохранились, надо использовать метод commit():

```java
connection.commit();
```

Если мы обнаружим, что какой-то из запросов не прошел (нам вернулась ошибка), то нужно откатить транзакцию методом rollback():

```java
connection.rollback();
```

Пример ошибки:
```java
package main.java;

import java.sql.*;

public class Main {
   private  final static String  HOST     = "localhost"  ; // сервер базы данных
    private  final static String  DATABASENAME = "testDB"  ;// имя базы
    private  final static String  USERNAME = "postgres"; // учетная запись пользователя
    private  final static String  PASSWORD = "000000"; // пароль
    static Connection connection;

    public static void main(String[] args) throws SQLException {

        //Строка для соединения с бд
        String url="jdbc:postgresql://"+HOST+"/"+DATABASENAME+"?user="+USERNAME+"&password="+PASSWORD;
        try {
            connection = DriverManager.getConnection ( url, USERNAME, PASSWORD);
            connection.setAutoCommit(false);
            if (connection == null) {
                System.err.println("Нет соединения с БД!");
            }
            else {
                System.out.println("Соединение с БД установлено корректно");
            }

            String SQL = "ALTER TABLE test ADD user varchar(255);";
            //Запрос на получение всех данных
            try (PreparedStatement preparedStatement = connection.prepareStatement(SQL)) {
                preparedStatement.executeUpdate();
                connection.commit();
                System.out.println("Транзакция прошла");
            }
        } catch (ClassNotFoundException | SQLException e) {
            connection.rollback();
            System.err.println("Транзакция не прошла");
            e.printStackTrace();
        }
    }
}
```

Можем увидеть ошибку в терминале.
```cmd
Соединение с БД установлено корректно
Транзакция не прошла
java.sql.SQLSyntaxErrorException: Duplicate column name 'user'
```
Ошибка говорит о том, что нельзя добавить столбец с названием user, так как уже такой есть.

Если мы используем JDBC 3.0 и выше, мы можем использовать сэйвпоинты (savepoint) и откатываться до них, а не целиком откатывать всю транзакцию.

Есть два метода для управления ими:

* Savepoint savePoint = connection.setSavepoint("MysavePoint"); — устанавливает точку сохранения.
* releaseSavepoint(Savepoint savePoint); — удаляет точку сохранения.

Для того чтобы откатить транзакцию до точки сохранения, можно использовать такую конструкцию:

```java
connection.rollback(savePoint);
```

### Batch processing, метод addBatch
**Batch processing**, а именно пакетная обработка, позволяет значительно сократить нагрузку на БД, накапливая SQL и отправляя их в БД одной пачкой (пакетом).

Чтобы включить такую обработку, необходимо использовать метод *DatabaseMetaData.supportBatchUpdates()*. Данный метод возвращает *true*, если наш JDBC драйвер способен так делать

Интерфейсы (*Statement*, *PrepparedStatement* и *CallableStatement*), через которые мы создавали запросы, имеют метод *addBatch()*, который добавляет каждый SQL-запрос в пакет.

После добавления мы используем метод *executeBatch()*, который выполняет все наши запросы. После использования метод возвращает массив с целыми числами, где каждое число сопоставляется с каждым нашим запросом и является показателем изменений.

Также мы можем удалять запросы из пакета методом *clearBatch()*. Стоит учитывать, что отдельные запросы из пакета мы удалить не можем. Всё или ничего.

Есть простой алгоритм создания пакета:

1. Выключить функцию **auto-commit** ```connection.setAutoCommit(false);```.
1. Создать *PreparedStatement*.
1. С помощью метода *addBatch()* добавить все наши запросы.
1. Запустить выполнение запросов методом *executeBatch()*.
1. Сохранить все изменения с помощью метода **connection.commit();**.

Небольшой пример кода.

Есть исходная таблица:
```sql
+------+------+
| ID   | user |
+------+------+
|    2 | NULL |
|    9 | Nick |
|   10 | NULL |
| NULL | NULL |
|    0 | NULL |
|   15 | NULL |
+------+------+
6 rows in set (0.00 sec)
```

Код целиком:
```java
package main.java;
import java.sql.*;
public class Main {
    private final static String HOST = "localhost"; // сервер базы данных
    private final static String DATABASENAME = "testDB"; // имя базы
    private final static String USERNAME = "postgres"; // учетная запись пользователя
    private final static String PASSWORD = "000000"; // пароль
    static Connection connection;
    public static void main(String[] args) throws SQLException {
        //Строка для соединения с бд
        String url = "jdbc:postgresql://" + HOST + "/" + DATABASENAME + "?user=" + USERNAME + "&password=" + PASSWORD;
        connection = DriverManager.getConnection(url, USERNAME, PASSWORD);
        try {
            connection.setAutoCommit(false); //2
            if (connection == null)
                System.err.println("Нет соединения с БД!");
            else {
                System.out.println("Соединение с БД установлено корректно");
            }
            String SQL = "Insert into test(ID,user) VALUES(?,?);";
            //Запрос на получение всех данных
            try (PreparedStatement preparedStatement = connection.prepareStatement(SQL)) { //1
                //Часть кода, в котором мы добавляем несколько запросов для одной отправки данных
                preparedStatement.setInt(1, 10);
                preparedStatement.setString(2, "Olaf");
                preparedStatement.addBatch();   //3

                preparedStatement.setInt(1, 11);
                preparedStatement.setString(2, "Erik");
                preparedStatement.addBatch();   //3

                preparedStatement.setInt(1, 12);
                preparedStatement.setString(2, "Baleog");
                preparedStatement.addBatch();   //3

                int[] count = preparedStatement.executeBatch(); //4
                connection.commit();    //5
                System.out.println("Данные отправлены");
            }
        } catch (ClassNotFoundException | SQLException e) {
            connection.rollback();
            System.err.println("Данные не добавлены");
            e.printStackTrace();
        }
    }
    public static boolean checkvalue(int checkedvalue) {
        String SQL = "Select * from test where ID=?;";
        try (PreparedStatement statement = connection.prepareStatement(SQL)) {
            statement.setInt(1, checkedvalue);
            ResultSet resultSet = statement.executeQuery();
            while (resultSet.next()) {
                return true;
            }
        } catch (SQLException throwables) {
            throwables.printStackTrace();
            return false;
        }
        return false;
    }
    public static boolean insertvalue(int insertedvalue) {
        String SQL = "insert  test(id) values(?)";
        try (PreparedStatement statement = connection.prepareStatement(SQL)) {
            statement.setInt(1, insertedvalue);
            int i = statement.executeUpdate();
            if (i >= 1) {
                return true;
            } else {
                return false;
            }
        } catch (SQLException throwables) {
            throwables.printStackTrace();
            return false;
        }
    }
}
```

Результат:
```cmd
Соединение с БД установлено корректно
Данные отправлены

Process finished with exit code 0
```

```sql
select * from test;
+------+--------+
| ID   | user   |
+------+--------+
|    2 | NULL   |
|    9 | Nick   |
|   10 | NULL   |
| NULL | NULL   |
|    0 | NULL   |
|   15 | NULL   |
|   10 | Olaf   |
|   11 | Erik   |
|   12 | Baleog |
+------+--------+
9 rows in set (0.00 sec)
```

## Эволюционное изменение БД
Основной задачей баз данных является **хранение данных реального мира**. Обычно разработчик старается максимально упорядочить информацию по каким-либо признакам для более удобного поиска. И чтобы поиск был быстрым или, например, можно было производить поиск по нескольким параметрам, БД должна быть очень хорошо *структурирована*.

При интенсивном использовании БД и попутной разработке программы возникает момент, когда какие-либо данные в БД нам уже не нужны, а какие-то наоборот нужно добавить и начать использовать. В ходе этого процесса старые версии приложения могут перестать корректно работать. Возникает вопрос **централизованного управления версией**, и эту проблему версий БД нужно как-то решать.

В принципе, изменение базы данных и является её эволюцией. Есть четыре пункта, отвечающие за ее изменение:

* изменение данных;
* изменение схемы;
* изменение версии программы взаимодействия;
* трансформация модели представления.

Есть такая библиотека — **Flyway**, она нужна для управления миграцией и эволюцией баз данных. Она полностью решает проблему версий любой БД.

Чтобы воспользоваться этой библиотекой, вам нужно создать новый проект под Maven и добавить строчки зависимости в pom.xml файл (файл загрузок всего проекта):

```xml
<dependency>
    <groupId>com.googlecode.flyway</groupId>
    <artifactId>flyway-core</artifactId>
    <version>1.5</version>
</dependency>
```

```xml
<plugin>
   <groupId>org.flywaydb</groupId>
   <artifactId>flyway-maven-plugin</artifactId>
   <version>6.5.5</version>
   <configuration>
      <url>jdbc:postgresql://localhost/flywaytest?autoReconnect=true&amp;useUnicode=true&amp;characterEncoding=UTF-8&amp;connectionCollation=utf8_general_ci&amp;characterSetResults=UTF-8</url>
      <user>root</user>
      <password>root</password>
   </configuration>
</plugin>
```

Далее для поддержания версионности (чтобы библиотека начала работать с нашей базой данных) необходимо запустить строку с консоли:

```cmd
mvn flyway:baseline -Dflyway.baselineVersion=1 -Dflyway.baselineDescription="Base version"
```

В консоли происходит примерно следующее:
![](../img/JAVA_23.5_1.png)

А в базе данных появилась ещё таблица, отвечающая за контроль версий:

```sql
use test;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
show tables;
+----------------+
| Tables_in_test |
+----------------+
| schema_version |
| test           |
+----------------+
2 rows in set (0.00 sec)
```

```sql
select * from schema_version;
+---------+--------------+------+--------------+----------+--------------+---------------------+----------------+---------+-----------------+
| version | description  | type | script       | checksum | installed_by | installed_on        | execution_time | state   | current_version |
+---------+--------------+------+--------------+----------+--------------+---------------------+----------------+---------+-----------------+
| 1       | Base version | INIT | Base version |     NULL | root         | 2020-08-27 11:53:08 |              0 | SUCCESS |               1 |
+---------+--------------+------+--------------+----------+--------------+---------------------+----------------+---------+-----------------+
1 row in set (0.00 sec)
```

Внутри содержатся данные (действия, которые происходили с базой, как-то её изменяя) о версии.

Создадим теперь файл, содержащий данные о схеме таблицы, сама таблица будет создана автоматически. Путь по умолчанию, в котором должны лежать наши скрипты /src/main/resources/db/migration/.

Создадим файл V0_0_00__create_table.sql. Важный момент: начало имени файла V и двойной нижний слэш обязательны, без них Flyway игнорирует файлы.

```sql
CREATE TABLE IF NOT EXISTS second_test_table (
  id INT NOT NULL, 
  name varchar(50) NOT NULL, 
  surname varchar(50) NOT NULL, 
  PRIMARY KEY (id)
);
```

Создадим файл V0_0_00__create_table.sql для заполнения таблицы.
```sql
INSERT INTO second_test_table (id, name, surname) 
VALUES (1, 'Tester', 'Testerov');
```

Теперь нам необходимо перейти в раздел плагина для Maven и запустить миграцию:

* для начала очистим всё;
* используем flyway:clean;
* а потом flyway:migrate.

![](../img/JAVA_23.5_2.png)

После запуска видим сообщения в терминале:
```cmd
[INFO] Scanning for projects...
[INFO] 
[INFO] -----------------------< org.example:FlywayTest >-----------------------
[INFO] Building FlywayTest 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- flyway-maven-plugin:6.5.5:migrate (default-cli) @ FlywayTest ---
[INFO] Flyway Community Edition 6.5.5 by Redgate
[INFO] Database: jdbc:postgresql://localhost:3306/flywaytest
[INFO] Successfully validated 2 migrations (execution time 00:00.021s)
[INFO] Creating Schema History table `flywaytest`.`flyway_schema_history` ...
[INFO] Current version of schema `flywaytest`: << Empty Schema >>
[INFO] Migrating schema `flywaytest` to version 0.0.00 - create table
[INFO] Migrating schema `flywaytest` to version 0.0.01 - insert data
[INFO] Successfully applied 2 migrations to schema `flywaytest` (execution time 00:00.082s)
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.014 s
[INFO] Finished at: 2020-09-16T14:41:02+03:00
[INFO] ------------------------------------------------------------------------
```

Переходим в нашу базу и смотрим, что там появилось:
```sql
select * from second_test_table;
+----+--------+----------+
| id | name   | surname  |
+----+--------+----------+
|  1 | Tester | Testerov |
+----+--------+----------+
1 row in set (0.00 sec)
```

В итоге мы создали базу версии 0.0.01. Стоит отметить, что вначале выполняется файл с именем V0_0_00, а потом уже V0_0_01.

## Прочие средства взаимодействия с БД
### ORM
**ORM** (*Object-Relational Mapping*) — это технология, благодаря которой можно провести связь между базой данных и объектно-ориентированным языком программирования. В итоге получается виртуальная объектная база данных. Со стороны программиста логично, что база данных должна хранить данные, если данные — это объект, то она должна хранить объекты «без лишних заморочек». Также ORM позволяет избежать написания большого куска однообразного кода. В принципе, у такого подхода можно найти свои плюсы и минусы.

**Плюсы**:

* Наличие схемы базы данных в коде программы (ну или другом месте, например, в конфигурационных файлах), благодаря чему она хранится в одном месте и её удобно редактировать.
* Возможно управлять моделями ООП, а не элементами базы данных.
* Наличие автоматических SQL-запросов
* Код, созданный через ORM, написан достаточно оптимально
* Разработка идёт на порядок быстрее.

**Минусы**:

* Достаточно большая нагрузка на программиста, которому помимо ООП и БД нужно знать промежуточный уровень ORM.
* Ошибки, которые крайне трудно исправить, если они допущены в самой ORM.
* ORM рассчитаны на большие системы и использование их в небольших проектах зачастую замедляет работу программ.

### Spring JDBC Template
Главная задача Spring JDBC Template — это упростить логику. В Spring имеется стандартный класс JDBCTemplate для работы. Пример такого упрощения с использованием JDBC Template можно увидеть ниже:

```java
@Configuration
@ComponentScan("com.test.jdbc")
public class SpringJdbcConfig {
    @Bean
    public DataSource postgresqlDataSource() {
        DriverManagerDataSource dataSource = new DriverManagerDataSource();
        dataSource.setUrl("jdbc:postgresql://localhost:3306/test");
        dataSource.setUsername("root");
        dataSource.setPassword("root");
        return dataSource;
    }
}
```

Без Spring JDBC данная конструкция выглядела бы так:
```java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class Main
{
       public  static void main(String[] args)
    {
        List<LoadModel> data = new ArrayList<>();
        String url  = "jdbc:postgresql://localhost/test";
        try ( Connection connection = DriverManager.getConnection(url, "root", "root")) {
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }
    }
}
```

Данный компонент для подключения к нашей БД написан с использованием Spring JDBC:

```java
int result = jdbcTemplate.queryForObject("select count(*) from test", Integer.class);
```

Достаточно простой запрос вернёт количество строк в нашей таблице:
```java
public int addID(int id) {
    return jdbcTemplate.update("insert into test values (?)", id);
}
```

На примере видно, как Spring JDBC позволяет выполнить запрос всего в «три» строчки.

Ещё один простой запрос на добавление данных в таблицу. Знаки ? работают так же маркерами, как и в PrepareStatement.

JdbcTemplate обладает удобными средствами маппирования. И, так же как JDBC, может создавать пакеты SQL- запросов. Более подробная информация по тому, как это можно сделать [тут](https://www.baeldung.com/spring-jdbc-jdbctemplate).

### Hibernate
Также достаточно популярный фреймворк для решения задач ORM. И, как большинство ORM, предоставляет всё те же возможности. Удобный маппинг результатов, быстрая разработка. Hibernate позволяет создавать CRUD (Create,Read,Update,Delete) приложения.

Hibernate обеспечивает отображение классов Java в таблицы баз данных. Кроме того, он предоставляет средства запроса и поиска данных. Это может значительно сократить время разработки, которое в противном случае тратится на ручную обработку данных в SQL и JDBC. Использование Hibernate состоит из двух частей: сохранение объектов в базу и чтение объектов из базы.

Официальная документация [тут](https://hibernate.org/orm/documentation/5.4/).

### Spring Data
**Spring Data JPA** упрощает разработку JPA-приложений.

Реализует слой доступа к данным, который может быть достаточно громоздким. Spring Data JPA призван улучшить реализацию доступа к данным. Как разработчик вы пишете интерфейс репозитория, а также свои собственные методы для поиска, а Spring их автоматически реализует.

Пример документации [тут](https://spring-projects.ru/guides/accessing-data-jpa/).


# Модуль 23. Обзор NoSQL
## NoSQL как подход к разработке систем хранения данных

Из предыдущих занятий мы узнали, что существует два основных подхода к базам данных: реляционные и нереляционные, **SQL** и **NoSQL**. Различия между ними заключаются в том, как они спроектированы, какие типы данных поддерживают, как хранят информацию.

Мы уже знаем что реляционные БД хранят данные, которые представляют объекты реального мира, например, имена и фамилии, банковские счета, перечень продуктов на складе. *Это обычно данные, собранные в виде таблиц*.

А нереляционные БД устроены по другому. Например, в документоориентированных БД информация хранится в виде JSON-моделей. Тут идёт речь о том, что *у одного объекта произвольный набор атрибутов*.

Внутреннее устройство различных систем управления базами данных влияет на особенности работы с ними. Например, нереляционные базы лучше поддаются масштабированию. Ключевым фактором развития нереляционных БД стал планомерный рост объема баз данных, в связи с этим появилась проблема быстрого доступа к ним. И на фоне этого появилась концепция новой модели БД, которая будет больше нацелена на **скорость доступа и масштабируемость**.

В реляционных базах данных разработчики сосредоточились на выполнении по принципам модели **ACID** (**Atomicity** — атомарность, **Consistency** — согласованность, **Isolation** — изолированность, **Durability** — стойкость).

Модель базы данных NoSQL не использует высокоструктурированную модель (подобную той, что используется в реляционных базах данных), а использует *гибкий подход* ключ/хранилище значений. Этот неструктурированный подход к данным требует альтернативы модели ACID: модель BASE. Модель **BASE** не расшифровывается, так как термин был противопоставлен классической системе ACID. С английского ACID — кислота, BASE — щелочь.

**Существует четыре основных принципа модели ACID**

* Атомарность транзакций гарантирует, что каждая транзакция базы данных является единым блоком. Если какой-либо шаг в транзакции не выходит, вся транзакция откатывается.
* Реляционные базы данных также обеспечивают согласованность каждой транзакции с логикой БД. Если элемент транзакции нарушит целостность базы данных, вся транзакция завершится неудачно.
* БД обеспечивает изолированность транзакций, которые выполняются одновременно (на самом деле такие транзакции происходят по очереди). Ни одна транзакция не видит то, что делает другая транзакция.
* Долговечность гарантирует, что после выполнении транзакции в БД, результаты постоянно сохраняются с помощью резервных копий и журналов транзакций. В случае сбоя они используются для восстановления данных через зафиксированные транзакций.

**BASE состоит из трёх принципов:**

* **Базовая доступность**. Подход к базе данных NoSQL фокусируется на доступности данных даже при наличии множества сбоев. Это достигается путем использования распределенного подхода к управлению базами данных: вместо того, чтобы поддерживать одно большое хранилище данных и сосредоточиться на отказоустойчивости этого хранилища, базы данных NoSQL распределяют данные по многим системам хранения с высокой степенью репликации (копирования сегментов или целых кластеров данных). В маловероятном случае, если сбой нарушает доступ к сегменту данных, это необязательно приводит к полному отключению базы данных, потому что данные из этого сегмента дублируются в её других сегментах.
* **Мягкое состояние**. Концепция звучит так: «Согласованность данных является проблемой разработчика и не должна обрабатываться базой данных».
* **Возможная последовательность**. Этот принцип означает, что в какой-то момент в будущем предполагается, что данные конвертировались бы в согласованное состояние. Однако никаких гарантий относительно того, когда это произойдет, не даётся. Это полная противоположность требования немедленной согласованности ACID, которое запрещает выполнение транзакции до тех пор, пока предыдущая транзакция не будет завершена и база данных не приблизится к согласованному состоянию.

Модель BASE подходит не для каждой ситуации, но она, безусловно, является гибкой альтернативой модели ACID для баз данных, которые не требуют строгого соблюдения табличной формы представления данных.

Мы уже знаем что существует четыре основных типа систем: «ключ — значение» (англ. key-value store), документоориентированные (document store), «семейство столбцов» (column-family store), графовые

Но в этом модуле мы разберем более детально, как работают следующие хранилища:
* **Redis** (от англ. remote dictionary server) — система управления базами данных, работающая с данными ключ-значение (key-value). Используется как для баз данных, так и для реализации кэшей.
* **MongoDB** — документоориентированная система управления базами данных, не требующая описания схемы таблиц. Использует JSON-подобные документы и схему базы данных.
* **Hazelcast** — система управления базами данных, которая управляет данными в оперативной памяти.

## Redis
**Redis** — это хранилище структур данных в памяти с открытым исходным кодом (под лицензией BSD). Данные в Redis хранятся как пара ключ-значение (ключ — это указатель, по которому в базе данных можно найти значение), но значение может быть сложной структурой с дополнительными операциями.

Он использует всего пять структур (типов) данных:

* строка (пара ключ-значение);
* словарь или хэш (пара ключ-словарь, который сам состоит из набора пар ключ-значение);
* набор (неупорядоченный набор строк, служит для работы с множествами);
* отсортированный набор (имеет дополнительный параметр score, указывающий на порядок расположения);
* список (хранит данные в порядке времени добавления).

Чтобы достичь высокой производительности, он работает с данными в оперативной памяти, но есть возможность сохранить данные на жесткий диск. Размер БД ограничен объемами оперативной памяти. В каждом сервере Redis может содержаться до 16 независимых пространств ключей, которые принято называть базами данных.

docker-compose for redis:
```yaml
#how to start: docker-compose -f docker-compose-radis.yml up -d
#how to stop: docker-compose -f docker-compose-radis.yml down
version: "3.7"

services:
    redis:
        image: "redis:latest"
        ports:
            - 6379:6379
```


















