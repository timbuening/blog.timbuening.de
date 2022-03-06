---
title: 'Windows USB-Drive unter Mac OSX'
published: true
visible: true
process:
    markdown: true
    twig: false
---
## Die Erstellung eines USB-Sticks zum installieren von Windows unter Mac OS X
Dieser Beitrag behandelt ein kurzes Problem auf welches ich stieß. Mein Windows auf meinem Gamingrechner wollte nicht mehr booten. Da auf der Platte mit Windows eh nur Windows liegt, wäre eine Neuinstallation kein großer Verlust. Gedacht - gewollt.
Allerdings nutze ich überwiegend Mac und mein Windows wollte ja nicht starten. Also musste ich einen Installations-Stick mit Windows unter Mac erstellen. Das war früher ein no-brainer für mich, aber seit Windows 10 Herbst 2021 ist die `install.wim`-Datei zu groß, um per Drag-and-drop die Daten auf einen vorbereiteten USB-Stick zu ziehen. (FAT Filesystem erlaubt maximal 4096 - die Datei hat etwa 4860 in meinem Fall.)

## Lösung des Problems: wimlib
Den USB Stick wie gewohnt formatieren als FAT mit MBR (Master Boot Record).
Dann alle Dateien aus dem frisch heruntergeladenen WIN10-Image rüberkopieren **außer** der Install.wim
Dann einen Terminal starten, falls noch nicht geschehen Homebrew installieren! 
Ansonsten:
- `brew install wimlib`
Dann mit `wimlib-imagex split /Volumes/CCCOMA_X64FRE_DE-DE_DV9/sources/install.wim /Volumes/WIN10/sources/install.swm 3800` die `install.wim` an ihren bestimmungsgemäßen Ort platzieren. wimlib unterteilt die install.wim nun nach, in meinem Fall 3800 MB und erstellt quasi eine install.wim2 mit dem Rest, der nicht in den ersten Teil passte. 
Windows 10 kann bei der Installation damit problemslos umgehen. 

## Viel Spaß!