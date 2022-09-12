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