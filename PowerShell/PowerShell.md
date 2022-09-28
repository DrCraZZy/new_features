# PowerShell

* Win + x a - PowerShell starten

## Varialble anlegen

* $name = "[value]"
* Get-Date -Format dd/MM/yyyy - Datum in dem angegebenen Format

## PowerShell commands

- *Get-Command* - Zeigt alle möglichen Kommandos an
- *Get-Host* - Version der PS abrufen
- *Clear-Host* - Bildschirm clear
- *Get-ExecutionPolicy* - Ausführungsrichtlinien abfragen
- *Set-ExecutionPolicy* - Ausführungsrichtlinien setzen (*Unrestricted*)
- *Get-ChildItem* - wie `dir`
- *Set-Location* - wie `cd`

## Cmdlets: Verb-Nomen-Parameter

* Cmdlets - Befehlchen, bestehen aus Verben und Nomen
* Suchen eines Befehls anhand des Verbs: `Get-Command -Verb Install`
* Suchen eines Befehls anhand des Nomens: `Get-Command -Noun Computer`

## Parmeter
Parameter können an eine Position gebunden sein, verpflichtend sein, nur bestimmte Werte akzeptieren 


* `-Confirm` - nach einer Bestätigung fragen
* `-WhatIf`- was wird gemacht wenn ich es ausführe
* `-Verbose` - Kommentare zu dem Vorgehen eines Befehls

## Execution Policy
* Restricted
* Unrestricted
* REmodeSigned
* AllSigned

Execution Policy umgehen

`powershell -ExecutionPolicy Bypass -File Bla.ps1`

## Profiledatei
```ps
# Profildatei erstellen

New-Item $PROFILE –ItemType File -Force
# Wo ist die Datei ?

$PROFILE

# Achtung! Profil ist ps1 Datei, kann nur geladen werden wenn die Executionpolicy dies zulässt!

Get-ExecutionPolicy # muss remotesigned oder unrestricted sein
Set-ExecutionPolicy RemoteSigned # optional

# Datei öffnen

notepad $PROFILE

# Beispielprofil (in $PROFILE kopieren)

Set-Location -Path C:\
Clear-Host
function Google {
    Start-Process "https://www.google.at/search?q=$args"
}
```

## Pipeline
Die Piping Technik ermöglicht die „Verknüpfung“ von PowerShell Code. Die Verwendung der Pipe (Rohr, Rohrleitung) ist eine Schlüsseltechnologie in PowerShell. Pipe nimmt die Ausgabe des Befehls link (von Pipe) und leitet die an das Befehl rechts (von Pipe). 

Was passiert bei `Get-Process | Stop-Process`?
```powershell
Start-Process notepad
Trace-Command -Name ParameterBinding -Expression {Get-Process notepad | Stop-Process} -PSHost
```

```powershell
# Format-Table

Get-Process -Name VSSVC

Get-Process -Name VSSVC | Format-Table Id,ProcessName

Get-Process -Name VSSVC | Format-Table Id,ProcessName,CPU(s) # führt zu Fehler, CPU (s) ist falsch

Get-Process -Name VSSVC | Get-Member # Was ist mit CPU (s) das Problem ?

Get-Process -Name VSSVC | Format-Table Id,ProcessName,CPU

# Format-List

Get-Process -Name VSSVC | Format-List

Get-Process -Name VSSVC | Format-List Id,ProcessName
```

`$_` - ist eine Pipeline-Variable und beinhaltet aktuellen Pipeline-Object.
