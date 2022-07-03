
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

## <u>Docker image</u>

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