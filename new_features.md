# Documentation for New commands

# Python

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

[Docker-Installation on wsl2 Ubuntu](https://docs.docker.com/engine/install/ubuntu/):

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
    

# Big O

- O(1) -> const time
- O(log n) -> binary search
- O(n) -> search element in Array
- O(n log n) -> search algorithm (Quicksort, - mergsort, heapsort)
- O(n²) -> for in for, sort algorithm
- O(2^n)
- O(n!)

# Cmd

# PowerShell

# __Git__
![git_merkblatt_01](.\git_merkblatt_01.jpg)
![git_merkblatt_02](.\git_merkblatt_02.jpg)


### [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)