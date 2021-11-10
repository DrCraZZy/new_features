# <u>Documentation for New commands</u>

# <u>Python</u>

## <u>Python Syntax</u>

### <U>Variablen</u>

```python
example_number = 1
example_float = 1.0
example_string = "Example String"
example_boolean = True
```

### <U>Conditionals</u>
```python
if mood == "good":
  print("I am happy!")
else:
  print("I am grumpy!")

#oder 

if mood == "good":
  print("I am happy!")
elif mood == "bad":
  print("I am grumpy!")
else:
  print("I am smack-dab in the middle!")
```

### <U>Loops</u>
```python
# for - loop
answer = 0
for i in range(1, 10**9 + 1):
  answer += i

# while - loop
answer = 0
number = 0
while number < 10**9 + 1:
 answer += number
 number += 1
```

### <U>Data Structures</u>

### List
```python
# create list of strings
groceries = ['apples', 'oranges', 'avocados', 'grapes']

# empty list
my_list = list()
my_list = []

# list with mixed data types
my_list = [1, "Hello", 3.4]

# nested list
my_list = ["mouse", [8, 4, 6], ['a']]

# convert to list
lett_set = {'a', 'e', 'i', 'o', 'u'}
lett_list = list(lett_set)
```

```python
# Access list elements
my_list = ['p', 'r', 'o', 'b', 'e']

# List Index 
# first item
print(my_list[0])

# third item
print(my_list[2])

# Nested indexing
print(n_list[0][1])

# last item
print(my_list[-1])

# fifth last item
print(my_list[-5])

# ----------------------------------------------

# List slicing
# List slicing in Python

my_list = ['p','r','o','g','r','a','m','i','z']

# elements from index 2 to index 4
print(my_list[2:5])

# elements from index 5 to end
print(my_list[5:])

# elements beginning to end
print(my_list[:])
```

```python
# Add/Change List Elements
# Correcting mistake values in a list
odd = [2, 4, 6, 8]

# change the 1st item    
odd[0] = 1  # -> [1, 4, 6, 8]           

# change 2nd to 4th items
odd[1:4] = [3, 5, 7] # -> [1, 3, 5, 7]

# ----------------------------------------------

# Appending and Extending lists in Python
odd = [1, 3, 5]

odd.append(7) # -> [1, 3, 5, 7]

odd.extend([9, 11, 13]) # -> [1, 3, 5, 7, 9, 11, 13]

# ----------------------------------------------

# Concatenating and repeating lists
odd = [1, 3, 5]

odd + [9, 7, 5] # -> [1, 3, 5, 9, 7, 5]

["re"] * 3 # -> ['re', 're', 're']

# Demonstration of list insert() method
odd = [1, 9]

odd.insert(1,3) # -> [1, 3, 9]

odd[2:2] = [5, 7] # -> [1, 3, 5, 7, 9]
```

```python
# Deleting list items
my_list = ['p', 'r', 'o', 'b', 'l', 'e', 'm', 'z', 'x']

# delete one item
del my_list[2] # -> ['p', 'r', 'b', 'l', 'e', 'm', 'z', 'x']

# delete multiple items
del my_list[1:5] # -> ['p', 'm', 'z', 'x']

# delete the entire list
del my_list # -> NameError: name 'my_list' is not defined

# remove
my_list.remove('p') # -> ['m']

# pop - pop ohne Argumente pop() -> letzter element
my_list.pop(0) # -> m
my_list # -> ['z', 'x']

# clear
my_list.clear() # -> []
```

|Methods|Descriptions|
|---|---|
|append()|	adds an element to the end of the list|
|extend()|	adds all elements of a list to another list|
|insert()|	inserts an item at the defined index|
|remove()|	removes an item from the list|
|pop()|	returns and removes an element at the given index|
|clear()|	removes all items from the list|
|index()|	returns the index of the first matched item|
|count()|	returns the count of the number of items passed as an argument|
|sort()|	sort items in a list in ascending order|
|reverse()|	reverse the order of items in the list|
|copy() |	returns a shallow copy of the list|

## <u>NumPy</u>
![numpy_merkblatt.jpg](.\numpy_merkblatt.jpg)



## <u>Best practice</u>

### <u>Unpacking</u>
```python
x, y, z = (12, 23, 34)
```
### <u>map</u>
Volumen berechnen, hierbei wir die erste Funktion auf alle nachfolgende Werte angewendet.
```python
x, y, z = map(int, input().strip().split())
print(f'Volume is {x * y * z}")


names = ['John ', ' Nonex ', '  Test']
names = map(str.strip, names)
```

### <u>reduce</u>
reduce(fun, list) - wird benutzt um aus einer Liste der Elemente eine Element zu bekommen, z. B. Summe, Max, Min

```python
import functools
 
# initializing list
lis = [1, 3, 5, 6, 2, ]
 
# using reduce to compute sum of list
print("The sum of the list elements is : ", end="")
print(functools.reduce(lambda a, b: a+b, lis))
 
# using reduce to compute maximum element from list
print("The maximum element of the list is : ", end="")
print(functools.reduce(lambda a, b: a if a > b else b, lis))
```

### <u>List comprehensions</u>
```python
# Ausdruck/Transformation for Element in Quelle if Bedinung
# Dieser Konstrukt [] {} oder in () stehen
# [] -> es entsteht eine Liste
# {} -> es entsteht ein Set oder Dict

# List
names = ['Max', 'Test', 'John', 'Sven', 'Tor'] 
names_start_t = [f'_{name}_' for name in names if name.startswith('T')]

# Set
names = ['Max', 'Test', 'John', 'Sven', 'Tor', 'Test'] 
names_start_t = {f'_{name}_' for name in names if name.startswith('T')}

# Dict
names = ['Max', 'Test', 'John', 'Sven', 'Tor', 'Test'] 
names_start_t = {index: f'_{name}_' for index, name in enumerate(names) if name.startswith('T')}

# Genexp -> Ergebnis dieser Operation ist ein Objekt und keine Datenstruktur
# dieses Objekt kann mit for - Loop iteriert werden oder es kann auf nächstes 
# Element mit next() zugegriffen werden.
names = ['Max', 'Test', 'John', 'Sven', 'Tor'] 
names_start_t_gen = (f'_{name}_' for name in names if name.startswith('T'))
# Genexp verfolg lazy - Prinzip, das heißt es wir nur dann Speicher beansprucht,
# wenn auf nächstes Element zugegriffen wird. Davor wir nur eine ein Objekt 
# angelet => geht sehr sparsam mit Speicher um 
```

### <u>Generator-Funktion</u>
yield - zeigt, das die Funktion ein Generator-Objekt zurückkommt. Dieses Objekt beinhaltet nicht die Daten, sondern die Logik wie die Daten erzeugt werden. Auf die Daten kann mit der Funktion _next()_ => _for-Loop_ zugegriffen werden. 

```python
def squares2():
    for e in range(0, 11, 2):
        yield e ** 2

# Generator-Funktion kann auch einen "return" beinhalten
```

### <u>Unboxing</u>
```python
# hierbei werden die Werte der linken Seite der Variablen der rechten Seite zugewiesen
a, b, c = [1, 2, 3]
a, b, c = (1, 2, 3)
a, b, c = 1, 2, 3
a, b, c = '123'

a, *b = [1, 2, 3] 
# => a = 1 und b = [2, 3]
# * - 1 in a und Rest in b
```
#### First and Last of iterable
```python
first, *_, last = [1,2,3,4,5,6,7] # => first = 1 and last = 7
```

### <u>Filter</u>
```python
names = ['Max', 'Test', 'John', 'Sven', 'Tor']
names_start_t = filter(lambda name: name.startswith('T', names))
```

### <u>Kopiere der Liste</u>
```python
indexes = [1, 2, 3]
another_indexes = [x for x in indexes] # zu lang
another_indexes = indexes[:] # alle Werte aus der alten Liste in neue Liste
```

### <u>Reverse der Liste</u>
```python
indexes = [1, 2, 3]
another_indexes = indexes[::-1] Liste
```

### <u>Prüfen ob alles True</u>
```python
if a and b and c and d:
    print('Ok')

ODER

if all(a,b,c,d):
    print('Ok')
```

### <u>Prüfen ob eins True</u>
```python
if a or b or c or d:
    print('Ok')

ODER

if any(a,b,c,d):
    print('Ok')
```

### <u>IF in line</u>
```python
color = 'green' if user.active else 'red'
```

### <u>Aufrufkonfiguration</u>
```python
if user.group == 'admin':
    process_admin_request(user, request)
elif user.group == 'manager':
    process_manager_request(user, request)
elif user.group == 'client':
    process_client_request(user, request)

ODER

group_to_method = {
    'admin': process_admin_request,
    'manager': process_manager_request,
    'client': process_manager_request
}

group_to_method[user.group](user, request)
```

## Unittest
Bei der Erstellung der Unittest wird normalerweise eine neue Date erstellt, die einen *test_* prefix bekommt *test_{test file}.py*. In diese neue Datei wird zutestende Datei importiert

```python
import unittest
import {zu testende Datei}

class Test{Name}(unittest.TestCase):

    # jede Test-Methode muss mit test_ anfangen sonst wird es nicht als Test
    # vom Framework gesehen
    def test_{method_name}(self):
        assertEqual({call_method}, {right_return})

```

Starten der Tests
```bash
python -m unittest test_{name der Datei}.py
```

Wenn man die Datei mit Tests wie folgt erweitern:
```python
import unittest
import {zu testende Datei}

class Test{Name}(unittest.TestCase):

    # jede Test-Methode muss mit test_ anfangen sonst wird es nicht als Test
    # vom Framework gesehen
    def test_{method_name}(self):
        assertEqual({call_method}, {right_return})


if __name__ == "__main__":
    unittest.main()
```

dann kann die Datei wie gewohnt gestartet werden.

```bash
python test_{name der Datei}.py
```

|Method|Checks that|New in|
|---|---|---|
|assertEqual(a, b)|a == b||
|assertNotEqual(a, b)|a != b||
|assertTrue(x)|bool(x) is True||
|assertFalse(x)|bool(x) is False||
|assertIs(a, b)|a is b|3.1|
|assertIsNot(a, b)|a is not b|3.1|
|assertIsNone(x)|x is None|3.1|
|assertIsNotNone(x)|x is not None|3.1|
|assertIn(a, b)|a in b|3.1|
|assertNotIn(a, b)|a not in b|3.1|
|assertIsInstance(a, b)|isinstance(a, b)|3.2|
|assertNotIsInstance(a, b)|not isinstance(a, b)|3.2

Wenn man bei mehreren Tests z. B. man testet eine Klasse, jede Test-Methode mit dem Anlegen eines Objektes anfängt. Dann kann man diese Zeile auslagern. Es gibt Methoden

```python
def setUp(self):
    pass

def tearDown(self):
    pass
```
die namen sollen genau so geschrieben werden. Die Methode ```setUp(self)``` wird am Anfang jeden Test gestartet. Die Methode ```tearDown(self)``` wird am Ende jeden Test gestartet.

Außerdem kann man am Anfang aller Tests und am Ende aller Tests bestimmten Code ausführen lassen. Dafür muss man folgende Methoden anlegen

```python
@classmethod
def setUpClass(cls):
    pass

@classmethod
def tearDown(cls):
    pass
```

## <u>REGex with Python</u>

### <u>Python Main Functions</U>
__re.match()__
+ Matcht am Anfang eines Strings
+ Achtung: Das gilt auch in Multiline-Mode
+ Rückgabewert: MatchObject | None

re.match(r'pattern', string, flags=0)

|__Flags__||
|---|---
|re.IGNORECASE	|Ignoriert Klein- und Großschreibung
|re.MULTILINE	|Integriert alle Zeilen, nicht nur die erste
|re.DOALL	    |Erweitert „.“ Auf neue Zeilen (\n)
|re.UNICODE	    |Erweiter {\w, \W, \b, \B} auf Unicode
|re.VERBODE	    |Erlaubt Kommentare in dem regulären Ausdruck
|Mehrfach Auswahl möglich, über den \| - Pipe-Operator.

__re.fullmatch()__
+ Matcht den gesamten String
+ Rückgabewert: MatchObject | None

    re.fullmatch(r'pattern', string, flags=0)

__re.search()__
+ Matcht an dem ersten Vorkommen eines Musters im String
+ Rückgabewert: MatchObject | None

    re.search(r'pattern', string, flags=0)

__matchObject.group()__
+ Ermöglicht den Zugriff auf den Inhalt einer oder mehrere Gruppen des MatchObjects
+ Gruppen starten bei (1), in Gruppe (0) steht kompletter Match
+ Rückgabewert: String

__matchObject.groups()__
+ Zeigt alle inhalte der Gruppen an
+ Rückgabewert: Liste

__re.sub()__
+ Das gematchte Muster wird durch einen definierten Ersatzstring ersetzt
+ Rückgabewert: Vollständiger String mit ersetztem/überschriebenen Inhalt

re.sub(r'pattern', 'repl', string, counter=0, flags=0)
+ Pattern – gesuchter Muster
+ Repl – durch was wird das Gefundene ersetzt
+ String – text in dem nach Muster gesucht wird
+ Counter – wie oft soll das Ersetzen stattfinden

__re.findall()__
+ Scannt den String von links nach rechts und wirft die Matches in der Reihenfolge des Vorkommens zurück
+ Rückgabewert: Liste mit allen Matches

    re.findall(r'pattern', string, flags=0)

__re.finditer()__
+ Erzeugt einen Iterator in der Höhe der Anzahl aller gefundener Matches
+ Rückgabewert: Callable Iterator
re.finditer(r'pattern', string, flags=0)

__re.split()__
+ Teilt den String an der Stelle an des das Muster gematcht wird.
+ Rückgabewert: Liste mit Strings

    re.split(r'pattern', string, flags=0)

## <u>SQLAlchemy</u>

# <u>WSL2</u>

->suchen in Windows nach _"Windows Feature"_. In dem Fenster _Windows-Subsystem for Linux_ & _Virtual Machine Platform_ anhacken.

[Download OS](https://docs.microsoft.com/de-de/windows/wsl/install-manual)

Die .appx - Datein in .zip umbennen und zip - Datei öffnen. Von dort die .exe starten.
Erst nach der Installation soll Docker installiert werden. In Dockereinstellungen kann dann WSL2 und Docker Zusammenarbeit einstellen.

# <u>Docker</u>

Docker - ist ein Software zur Isolierung von Anwendungen mit Hilfe von Containervirtualisierung.

Container - Virtuele isolierung eines Prozesses. Es gibt zwei Konzepte:

    - Namespace - ID/Name des Prozesses
    - Cgroups - Zugewiesene Ressourcen
    - Image - Programme (OS -> Server -> Application), die in einem Container laufen

## <u>[Docker-Installation on wsl2 Ubuntu](https://docs.docker.com/engine/install/ubuntu/)</u>

    - sudo apt-get update

    - sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        lsb-release -y

    - curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

    - echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/
        keyrings/    docker-archive-keyring.gpg] https://download.docker.com/
        linux/debian \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

    - sudo apt-get update

    - sudo apt-get install docker-ce docker-ce-cli containerd.io

    - sudo docker run hello-world

## Docker premission denied

```bash
#Create the docker group if it does not exist
$ sudo groupadd docker

#Add your user to the docker group.
$ sudo usermod -aG docker $USER

#Run the following command or Logout and login again and run (that doesn't work you may need to reboot your machine first)
$ newgrp docker

#Check if docker can be run without root
$ docker run hello-world

#Reboot if still got error
$ reboot
```

## Docker image

Official Images sind Images der bekannten Programmen/Server/Services, die auf [dokerhub](https://hub.docker.com/) runter geladen werden können und man kann sie im Docker laufen lassen. Um die Images Herunterzuladen braucht man den Befehl _docker pull [image name]:version_ (wobei :version ist optional, wenn es nicht angegeben wird, wird die letzte Version genommen).

## <u>Docker Befehle</u>

*_docker info | grep -i root_* - Zeigt Docker-Root Verzeichnis

*_docker images_* - Zeigt alle zur Verfügung stehende Images an

Wenn man ein neues Image erstellt mit einem Namen und Tag die schon existieren, bekommt das alte Image \<none> \<none> (dangling image) und das neue Image bekommt den Namen und den Tag. 

*_docker images -f dangling=true_* - Zeigt alle dangling Images an

*_docker images -f dangling=true -q_* - Zeigt alle dangling Image IDs an

*_docker rmi [repository]:[tag]_* - Löschen eines Images

Dangling images können anhand der ID gelöscht werden.

*_docker rmi $(docker images -f dangling=true -q)_* - Löschen alle dangling Images

*_docker run [repository]:[tag]_* - Starten Container mit Image (repository:tag) im Vorgergrund

*_docker run -d [repository]:[tag]_* - Starten Container mit Image (repository:tag) im Hintergrund

*_docker run -p [porst of local machin]:[port of image] [repository]:[tag]_* - Starten Container mit Image (repository:tag) im Hintergrund

*_docker run --name [name of container] [porst of local machin]:[port of image] [repository]:[tag]_* - Mit dem Parameter --name, kann man dem Container einen Name zuweisen

*_docker run -e "[var_name]=[var_value]" [repository]:[tag]_* - Container starten und eine Environment-Variable im Container anlegen.

*_docker run --memory "200mb" [repository]:[tag]_* - Begrenzen der zur Verfügung stehenden RAM für Container

*_docker run -v [local path OR valuem]:[container path] [repository]:[tag]_* - Volume, hierbei werden alle Inhalt aus [container path] Container in [lockal path] gesichert und wenn man einen neuen Container starten dann können bestimmte daten aus diesem Ordner mit Container syncronisier werden und so bekommt der Container alle Daten wieder. Wenn man beim Erstellen eines Containers *_[local path OR valuem]_* weglässt, dann wird ein Anonymous-Valume erstellt (hat ein HASH-String als name). Um zu erfahren werlches Volume zu dem Container gehört kann man es mit _docker inpect_ in dem Unterpunkt Mounts nachschauen.

*_docker volume create_* - Erstellt einen Volume. Ist eine Ordner im Docker-Verzeichnis

*_docker volume rm [volume name]_* - Volume löschen

*_docker valume ls -f=dangling=true_* - Liste aller nicht gebungenen Volumes (-q - Zeigt nur die ID-Liste an)



*_docker rename [old name] [new name]_* - Container umbennenen

*_docker start [container name or id]_* - Container starten

*_docker stop [container name or id]_* - Container stoppen

*_docker rm [container id] || [container name]_* - Löschen Container

*_docker rm -f [container id] || [container name]_* - Löschen einen laufenden Container

*_docker rm -fv [container id] || [container name]_* - Löschen einen laufenden Container und dazugehörige Volume !!! Funktioniert nur bei Anonymous-Volume

*_docker ps_* - Container Liste anzeigen

*_docker ps -a_* - Zeitg alle Container an, auch die gestoppte Container

*_docker build -t [name of image] -f [path to Dockerfile]_* - Erstellen eines Images 

*_docker build -t [name:version] -f [Dockerfile] --build-arg [name of arg]=[value of arg] [path of dockerfile]_* - mit dem --buildarg werden die Argumente an Dockerfile übergeben

Bei jedem Build-Prozess wird automatisch in .dockerignore-Datei geschaut. Damit werden Datein und Ordner ausgeschlossen, die nicht in den Image reingehören, sich aber in dem Context-Path befinden (also dort wo der Build gestartet wird)

*_docker logs [Container name]_* - Zeigt Logeintrag zu dem Container

*_docker logs -f [Container name]_* - Zeigt Logeintrag zu dem Container (voll)

*_docker exec -ti [container name] bash_* - Container öffnen

*_docker exec [container name] bash -c "[command]"_* - Befehl ausführen ohne Container zu öffnen

*_docker inspect  [container name or id]_* - Zeigt Container Einstellungen

*_docker stats  [container name or id]_* - Zeigt Container Resourcen

*_docker cp [container name]:[destination in container(path)]_* - Datei vom Dockerhost nach Container kopieren

*_docker cp [container name]:[destination in container(path)] [local path]_* - Datei vom Container zu Dockerhost kopieren

*_docer commit [container id] [name of new image]:[tag]_* - Erstellt ein Image aus einem Container

### <u>Docker Best Practices</u>
    - Ein Service ein Container
    - Build-Context so klein wie möglich
    - Unnötige Packages vermeiden
    - Wenig Layers - Wenn es möglich, mehrere Anweisungen mit && und \ verknüpfen

### <u>Dockerfile</u>
FROM - Gibt einen Start Image an

VOLUME - Erstellen und Verknüpfen des Volumes

RUN - Führt beliebige linux-cmd aus. Wird bei Zusammen stellen des Imges ausgeführt.

LABLE - Meta Informationen zu dem Build/Image. Es können mehrere hintereinander geschrieben werden.

COPY - [path to file on local machine] [path in image]

ADD - Download file aus Internet in Image

ENV - Deklarieren einer Variable

WORKDIR - setzt den Pfad, wo die Befehle ausgeführt werden

USER - User umswitchen (um CMD auszuführen muss man auf root - User umschalten)

EXPOSE - Hier wird Port für die Application angegeben

CMD - Wird beim Starten des Images ausgeführt.

# <u>Jankins</u>

1. Install Docker
2. [Download](https://hub.docker.com/r/jenkins/jenkins) Jenkins-Image

    a. Docker pull jenkins/jenkins
3. Docker-Compose-File erstellen: _docker-compose.yml_

``` docker-compose
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "8080:8080"
    volumes:
      - "$PWD/jenkins_home:/var/jenkins_home"
    networks:
      - net
networks:
  net:
```

Vor dem Start soll der jenkins_home - Pfad existieren
Sicher gehen, dass der User Zugriff auf diesen Ordner hat

```bash
sudo chown [user id]:[group id] [Pfad zu dem Ordner] -R
# -R - auch für alle Verzeichnise in dem Pfad
```

4. _docker-compose up -d_ - Starten Docker-Container
5. Nach dem Starte des Containers kann Jenkins im Browser gestartet werden. Hierfür wir als Adresse _[server id/sever adresse]:8080_ angegeben. 
6. Man wird nach einem Password gefragt. __docker logs -f jenkins__ bekommt man den benötigten Password angezeigt.


# <u>Big O</u>

    - O(1) -> const time
    - O(log n) -> binary search
    - O(n) -> search element in Array
    - O(n log n) -> search algorithm (Quicksort, - mergsort, heapsort)
    - O(n²) -> for in for, sort algorithm
    - O(2^n)
    - O(n!)

# <u>Cmd</u>

# <u>REGex</u>

||_Anchors_|
| --- | --- |
|^	|Anfang des Strings oder der Zeile
|\A	|Anfang des Strings oder der Zeile
|$	|Ende des Strings oder der Zeile
|\Z	|Ende des Strings oder der Zeile
|\b	|Wortgrenze
|\B	|Keine Wortgrenze
|\<	|Anfang des Wortes
|\>	|Ende des Wortes


||_Special Sequences_|
| --- | --- |
|.	|Jedes Zeichen, bis auf neue Zeile \n
|\s	|Weißraum (Leerzeichen, Tabs)
|\S	|Kein Weißraum
|\d	|Zahlen
|\D	|Keine Zahlen
|\w	|Worte (Buchstaben und Zahlen)
|\W	|Keine Worte


|       |_Quantifiers_      |
| ---   | ---               |
|*	    |0 oder mehr
|+	    |1 oder mehr
|?	    |0 oder 1
|{3}	|Genau 3
|{3,}	|3 oder mehr
|{3,5}	|3 bis 5
|       |Mit "?" Non-Greedy.


||_Sets, Ranges & Groups_|
| --- | --- |
|[abc]	|Set beinhaltet (a or b or c)
|[^abc]	|Set beinhaltet nicht (a or b or c)
|a-z	|Range - Kleinbuchstaben von a bis z
|A-Z	|Range - Großbuchstaben von A bis Z
|0-9	|Range Zahlen 0 bis 9
|(...)	|(Capturing) Gruppe
|(a\|b)	|a oder b
|(?:...)|Passive (non-capturing) Gruppe

<br>

_Special Characters_
|   |   |   |
|---|---|---|
|^	|[	|]
|+	|{	|}
|*	|(	|)
|\|	|<	|>
|$	|?	|\
|.	|	|

Escape Sequences: \	- Escape "Special Characters"

_String replacements_

* Verkürzt den RegEx-Ausdruck
* Reduziert Redundanzen im RegEx
* Verifizieren gewollte Wiederholungen

Wenn man für einen Ausdruck eine Gruppe erstellt (\d\d\d\d) dann besteht die Möglichkeit an einer anderen Stelle auf die Gruppe zu referenzieren mit \1 wenn es die erste Gruppe in dem Ausdruck war. 
r“^(\d\d\d\d)\.\1\.\1“ => z. B.: 1234.1234.1234
in dem Fall referenziert \1 auf die Gruppe (\d\d\d\d)

_Benannte Gruppen_

Standardmäßig sind Gruppen unbenannt. Sie werden automatisch von 1 aufsteigen benannt. Bei einer Vielzahl von Gruppen kann das unübersichtlich werden. In dem Fall können benannte Gruppen helfen. Als Gruppenname kann jeder String gewählt werden.

r“^(?P\<Zahl\>\d\d\d)\_\1\_\d{4}$“ -> matchObj.group(„Zahl“)

||_Assertions_|
| --- | --- |
|?=	| Lookahead assertion
|?!	| Negative lookahead
|?<=| Lookbehind assertion
|?>	| Once-only Subexp¬ression
|?!= or ?<!	| Negative lookbehind
|?()| Condition [if then]
|?()| Condition [if then else]
|?#	| Kommentar

Defeniere Regeln im Muster. 

Lookahead (?=) – Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster darauf folgt.

Negative lookahead (?!) – Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster _NICHT_ darauf folgt.

Lookbehind (?<=) - Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster vorhergeht.

Negative lookbehind (?<!) - Matcht ein definiertes Muster nur, wenn ein weiteres definiertes Muster NICHT vorhergeht.

_Conditionals_
+	Wenn-Dann-Sonst Statement
+	(?(WENN A) DANN B |SONST C) 
+	Der SONST und der DANN Blöcke sind Optional
    +	(?(WENN) DANN)
    +	(?(WENN)|SONST)

# <u>Git</u>
![git_merkblatt_01](.\git_merkblatt_01.jpg)
![git_merkblatt_02](.\git_merkblatt_02.jpg)

<hr/>

## Zum Nachschlagen

### [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

### [LaTeX Formeln](https://www.grund-wissen.de/informatik/latex/mathematischer-formelsatz.html)