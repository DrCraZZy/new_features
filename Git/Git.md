# Git

GIT - Global Information Tracker

GIT arbeitet mit _snapshots_. Es werden _snapshots_ von Files gemacht.
![Git snapshots](..\img\frpro_git_snapshots.png)
Wenn ein File sich nicht geändert hat, dann wird einfach nur der Link zu dem _snapshot_ weitergegeben.

Git hat drei Zustände in dem sich die Files befinden können:
- staged (vorbeireitet)
- modified (verändert)
- commited (gespeichert/fixiert)

![git_merkblatt_01](.\git_merkblatt_01.jpg)
![git_merkblatt_02](.\git_merkblatt_02.jpg)

## Git flow

### Centralized workflow
Dieses Modell geht von einem zentralen Repository mit einem einzigen Master-Branch aus, dem sich alle Entwickler verpflichten. Entwickler arbeiten in ihren lokalen Kopien des Master-Zweigs, im Konfliktfall werden lokale Commits auf den aktuellen Ursprungs-/Master-Stand verschoben. Somit bleibt die Änderungshistorie des Master-Zweigs linear.

Der Entwickler nimmt Änderungen am lokalen Branch vor;

```bash
git pull               # Aktualisieren Sie den aktuellen Status der lokalen Niederlassung
git add {file}         # Änderungen vornehmen und hinzufügen
git commit             # Lokales commit
```
Danach versucht es zu veröffentlichen.
```bash
git push origin master # push in origin master
```
Bei Konflikten
```bash
git pull --rebase origin/master
#oder
git rebase origin master
```

### Feature/Issue branch workflow
Das FeatureBranch-Modell wurde entwickelt, um Probleme zu lösen. Der Entwickler nimmt Änderungen in separaten Zweigen vor, sodass Sie zwischen Aufgaben wechseln oder sogar eine unfertige Aufgabe an Kollegen übertragen können. Der Begriff „Feature“ bezieht sich auf eine integrale Änderung, die ein bestimmtes Problem löst. Wenn das Team einen Issue-Tracker verwendet, wird häufig der Ansatz „One Ticket, One Branch“ verwendet (daher wird dieses Modell manchmal als Issue-Branch-Workflow bezeichnet). Das Feature-Branch-Modell führt auch das Konzept der __Master-Branch-Stabilität__ ein. Es kann nicht mehr von allen Entwicklern begangen werden, und der Prozess des Hinzufügens von Commits wird kontrolliert: Dies kann beispielsweise der zuvor diskutierte Ansatz mit Änderungsanfragen (Pull Request) sein, bei dem Änderungen formal geprüft werden müssen, bevor sie hineinkommen können der Meister.
```bash
# update local master
(master)  git pull

# create new feature-branch
(my-feature)  git checkout -b my-feature

(my-feature)  git add {file} # add changes
(my-feature)  git commit     # commit

# push to origin
(my-feature)  git push origin my-feature
```
Dann wird ein Pull-Request erstellt und kann im Verlauf des Code-Reviews zusätzlich Änderungen an diesem Branch vornehmen und veröffentlichen.

Nachdem alle Prüfungen bestanden wurden, werden der Developer-Branch und der Master-Branch zusammengeführt. In dieser Phase können Konflikte auftreten, die korrigiert werden müssen.

Zwei Optionen sind zulässig – die Verwendung der zuvor besprochenen Rebase oder die Zusammenführung mit dem neuen Status des Master-Zweigs:
```bash
# load origin master
(my-feature) git fetch origin master
# merge master to my-feature
(my-feature) git merge origin/master
```
### Git-flow
Eine der Fortsetzungen der im Feature-Branch-Modell verkörperten Ideen ist das Git-Flow-Modell. Dieses Modell beschreibt bereits nicht nur die Art und Weise, wie Änderungen am Projekt vorgenommen werden, sondern auch die Herangehensweise an die Organisation seines Lebenszyklus.

Zusätzlich zu den üblichen Feature-Branches führt das Modell die Konzepte von Release-Branches (Release-Branches), Hotfix-Branches (Hotfix-Branches) und Release-Tags oder Releases (Release-Tags) ein.

Dem Hauptzweig wird die Rolle der Historie offizieller Veröffentlichungen zugewiesen. Jeder Commit in diesem Zweig ist normalerweise mit der Release-Version gekennzeichnet. Dem Develop-Branch wird eine ähnliche Rolle wie dem Master-Branch aus dem Feature-Branch-Modell zugewiesen.

Wie bisher wird die gesamte Entwicklung in separaten Feature-Zweigen durchgeführt. Ein Feature-Zweig wird von der Entwicklung weggenommen und mit ihm zusammengeführt, wenn die Arbeit an einem Feature abgeschlossen ist. Sobald der development-Branch genug Änderungen gesammelt hat, um das Release freizugeben, wird der release-Branch vom development-Branch abgezweigt.

Release-Zweige werden verwendet, um eine zukünftige Release-Version eines Projekts zu stabilisieren. Der Code aus diesem Zweig wird ausgiebig getestet und Fehler in diesem Zweig behoben. Alle Fixes aus diesem Zweig werden zurück in den Entwicklungszweig gemergt. Nach allen Fixes wird der Release-Branch in den Master gemergt und der entsprechende Commit mit einem Release-Tag markiert.