# <u>Jankins</u>



## <u>With Docker</u>

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

## <u>Jenkins sucurity</u>
