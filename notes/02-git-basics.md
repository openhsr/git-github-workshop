# Git CLI
Syntax:

```bash
git <verb>
```

Hilfe gibt es in der man page - oder cross plattfrom mit git help:
```bash
git help <verb>
# bsp:
git help commit
```

# config
Testen mit:
git config --global user.name


git config --global user.name "Maria Muster"
git config --global user.email  "maria.muster@hsr.ch"

Diese E-Mail sollte auch diejenge sein, mit der ihr auf github arbeitet - damit werde die Commits auch deinem User zugeordnet

## Setting levels:
(system)
git config --global => ~/.gitconfig
git config --local => .git/config

local überschreibt global
global überschreibt system
Funktioniert wie vererbung: "Das nächste level gewinnt"

=> Bitte alle verifizieren!

# Projekt Initialisieren
- **Repository**: Enthält Dateien, History und Konfiguration - verwaltet von Git.
- => ungleich SVN Repo: Je "Projekt" ein Git Repo - nicht ein Baum wie in SVN

```bash
$ # Neuer ordner oder in eine Projekt wechseln, welches bereits existiert
$ git init .
$ ls -al # Alle Dateien auflisten
```

# .git ordner
Ordner mit Dateien - meist in Klartext
-> Praktisch alle Git-Commands schreiben etwas in diesen ordner - bsp.
git remote add ...
oder git config ...
Alles da drinn! Also wenn ich den lösche ist auch alles weg! (demo)

# Commit
## Grundkonzept: 3 Stages
![Loal Operations](https://git-scm.com/figures/18333fig0106-tn.png)
### Working Directory
### Staging
### Commit
Mit commit "teil der Geschichte" - schwer da raus zu bekommen :wink:

http://gitimmersion.com/
http://rogerdudler.github.io/git-guide/

Staging area "Snapshot" (erneutes add nach änderung)
am anfang etwas seltsam, wird aber mit der Zeit logischer!

TODO: add readme:
README.md wichtig, denn auf github wird die zum projekt angezeigt!

Commit = "Changes"

```bash
git add README
git add . #all!
git status
git commit -m "IJ"
git commit # öffnet text editor
```
Style: Atomar und "genau eine Änderung"

## Sha1 hash!



# TODO: mehr Tracking demoz
* Datei bearbeiten wenn in staging
* commit working direcotry
* Git add ordner
* git add css/\*.css


# Git diff
Welche stage?
# Git log
=> git help log

git log
git log

git log --oneline --graph --decorate
git log 471bdf4...920a4a0
git log --since="3 days ago"
git show 471bdf4


```
# Commits, die nur eine Datei betreffen
git log -- statuten/statuten.tex
```

TODO: mächtige beispiele - aber nur zur demo
(mit q "schliessen")

# Dateien löschen: Git rm / git ad
git rm file

# .gitignore
Ungewollte datein fernhalten


# Änderungen verwerfen:
git reset HEAD <file>

# Alte version wiederherstellen?


# TODO: Command listing / Cheat sheet

## Weiteres
# Dateien Verscheiben
git mv
-> "Ship of of Theseus"
https://www.youtube.com/watch?v=UHwVyplU3Pg
https://www.youtube.com/watch?v=qk1UE-9qf0Q

# Editor
TODO

# Color
Falls nicht bunt:
git config --global color.ui auto

# Git status short
(alias)

# Git alias
git config --global alias.l "log --oneline --graph --decorate"
cat ~/.gitconfig    
