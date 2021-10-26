# Documentation for New commands

# Python

## REGex with Python

### Python Main Functions 
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


## SQLAlchemy

# WSL2

->suchen in Windows nach _"Windows Feature"_. In dem Fenster _Windows-Subsystem for Linux_ & _Virtual Machine Platform_ anhacken.

[Download OS](https://docs.microsoft.com/de-de/windows/wsl/install-manual)

Die .appx - Datein in .zip umbennen und zip - Datei öffnen. Von dort die .exe starten.
Erst nach der Installation soll Docker installiert werden. In Dockereinstellungen kann dann WSL2 und Docker Zusammenarbeit einstellen.

# Docker

Docker - ist ein Software zur Isolierung von Anwendungen mit Hilfe von Containervirtualisierung.

Container - Virtuele isolierung eines Prozesses. Es gibt zwei Konzepte:

    - Namespace - ID/Name des Prozesses
    - Cgroups - Zugewiesene Ressourcen
    - Image - Programme (OS -> Server -> Application), die in einem Container laufen

## [Docker-Installation on wsl2 Ubuntu](https://docs.docker.com/engine/install/ubuntu/):

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

## Docker image

Official Images sind Images der bekannten Programmen/Server/Services, die auf [dokerhub](https://hub.docker.com/) runter geladen werden können und man kann sie im Docker laufen lassen. Um die Images Herunterzuladen braucht man den Befehl _docker pull [image name]:version_ (wobei :version ist optional, wenn es nicht angegeben wird, wird die letzte Version genommen).

## Docker Befehle

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

*_docker rename [old name] [new name]_* - Container umbennenen

*_docker start [container name or id]_* - Container starten

*_docker stop [container name or id]_* - Container stoppen

*_docker rm [container id] || [container name]_* - Löschen Container

*_docker rm -f [container id] || [container name]_* - Löschen einen laufenden Container

*_docker ps_* - Container Liste anzeigen

*_docker ps -a_* - Zeitg alle Container an, auch die gestoppte Container

*_docker build -t [name of image] -f [path to Dockerfile]_* - Erstellen eines Images 

*_docker build -t [name:version] -f [Dockerfile] --build-arg [name of arg]=[value of arg] [path of dockerfile]_* - mit dem --buildarg werden die Argumente an Dockerfile übergeben

Bei jedem Build-Prozess wird automatisch in .dockerignore-Datei geschaut. Damit werden Datein und Ordner ausgeschlossen, die nicht in den Image reingehören, sich aber in dem Context-Path befinden (also dort wo der Build gestartet wird)

*_docker logs [Container name]_* - Zeigt Logeintrag zu dem Container

*_docker logs -f [Container name]_* - Zeigt Logeintrag zu dem Container (voll)

*_docker exec -ti [container name] bash_* - Container öffnen

*_docker inspect  [container name or id]_* - Zeigt Container Einstellungen

### Docker Best Practices
    - Ein Service ein Container
    - Build-Context so klein wie möglich
    - Unnötige Packages vermeiden
    - Wenig Layers - Wenn es möglich, mehrere Anweisungen mit && und \ verknüpfen


### Dockerfile:
FROM - Gibt einen Start Image an

RUN - Führt beliebige linux-cmd aus. Wird bei Zusammen stellen des Imges ausgeführt.

LABLE - Meta Informationen zu dem Build/Image. Es können mehrere hintereinander geschrieben werden.

COPY - [path to file on local machine] [path in image]

ADD - Download file aus Internet in Image

ENV - Deklarieren einer Variable

WORKDIR - setzt den Pfad, wo die Befehle ausgeführt werden

USER - User umswitchen (um CMD auszuführen muss man auf root - User umschalten)

EXPOSE - Hier wird Port für die Application angegeben

CMD - Wird beim Starten des Images ausgeführt.

# Big O

    - O(1) -> const time
    - O(log n) -> binary search
    - O(n) -> search element in Array
    - O(n log n) -> search algorithm (Quicksort, - mergsort, heapsort)
    - O(n²) -> for in for, sort algorithm
    - O(2^n)
    - O(n!)

# Cmd

# REGex

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

# __Git__
![git_merkblatt_01](.\git_merkblatt_01.jpg)
![git_merkblatt_02](.\git_merkblatt_02.jpg)


### [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)