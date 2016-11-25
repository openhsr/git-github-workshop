# Git Kommandozeilen Philosophie

_Folie Git Syntax_

Syntax:

```bash
git <verb>
```

Hilfe bekommt man in den Manpages oder plattformübergreifend mit dem `help` Verb

_Wechsel auf Terminal_

```bash
$ git help
$ git help config
# Alternativ
$ man git
```

(Schliessen mit `q`, suchen mit `/`,`p` und `n`)

# Name und Email einstellen

Bitte alle überprüfen, ob Name und E-Mail konfiguriert sind:

```bash
$ git config --global user.name
$ git config --global user.email
```

Falls nicht gesetzt, dann jetzt machen:

```bash
git config --global user.name "Maria Muster"
git config --global user.email  "maria.muster@hsr.ch"
```

Anmerkung: Gleiche E-Mail wie auf Github (mehrere möglich) -  damit Commits korrekt zugeordnet werden können.

Wir haben hier die Konfiguration von Git angetroffen.

Kurzer Exkurs: Es gibt 3 Level von Einstellungen:

1. System
2. Global (Benutzer), überschreibt System
3. Lokal (Projekt / Repository), überschreibt System und Global

(gleiches Konzept wie Vererbung in der Objektorientierten Programmierung)

Warum muss das eingestellt werden? Diese Daten werden so in die Versionsgeschichte geschrieben. Mehr dazu gleich.

# Projekt Initialisieren

Begriff **Repository**
Enthält Dateien, History und Konfiguration - wird von Git verwaltet

VORSICHT: Ungleich SVN Repository:

- Wiederholung: Nicht Zentral! Man darf alles!
- Lokal!
- Je "Projekt" ein Git Repository - nicht ein Baum wie in SVN

## Ein neues Repository

Annahme: Wir haben ein Projekt, welches wir unter Versionskontrolle stellen möchten.
Wer kein eigenes solches Projekt hat kann dies mit dem Projekt vom Stick machen (wie in ich in den folgenden Demos)

```bash
$ # Neuer Ordner oder in eine Projekt wechseln, welches bereits existiert
$ git init .
Initialized empty Git repository in /home/user/projects/examples/.git/
$ ls -al # Alle Dateien auflisten
total 32
drwxr-xr-x 6 rzi users 4096 Sep 14 14:23 .
drwxr-xr-x 5 rzi users 4096 Sep 14 14:23 ..
drwxr-xr-x 2 rzi users 4096 Sep 14 14:23 css
drwxr-xr-x 7 rzi users 4096 Sep 14 14:23 .git
drwxr-xr-x 2 rzi users 4096 Sep 14 14:23 images
-rw-r--r-- 1 rzi users 4593 Sep 14 14:23 index.html
drwxr-xr-x 2 rzi users 4096 Sep 14 14:23 js
```

## Das Git-Verzeichnis

Enthält alle Meta-Daten, Commits und vieles mehr (Refs, Hooks etc.)

Die meisten Dateien sind Klartext. Beispiel: `.git/config`

Praktisch alle Git-Kommandos schreiben etwas in dieses Verzeichnis

```bash
$ cat .git/config
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
$ git config user.name "Demo"
$ cat .git/config
```

Das bedeutet auch, dass wenn dieser Ordner weg ist, weiss Git auch nichts mehr:

```bash
$ rm -Rf .git/
$ git config user.name "Peter"
fatal: not in a git directory
```

Aber wir wolle ja mit Git arbeiten, darum initialisiere ich das Repository erneut:

```bash
$ git init .
Initialized empty Git repository in /home/rzi/Desktop/examples/.git/
```

## Ein erster Commit
### Die drei Zustände

![Grundkonzept der 3 Zustände](images/stages.png)

Git definiert drei Haupt-Zustände, in denen sich eine Datei befinden kann:

_Aufzeichen von 3 Stages_

* Working Directory: Neue Dateien (untracked) bzw. geänderte Dateien (modified)
* Staging (auch Index): Vormerken für den nächsten Commit (Snapshot - dazu gleich mehr)
* Commit: Fix gespeichert in der "Git-Datenbank"

!!! todo

    Anpassung in Grafik: *tracked* → *modified*

Typisches vorgehen:

1. Ich mache eine Änderung
2. Geänderte Datei für den nächsten Commit vormerken - also in die Staging Area hinzufügen.
3. Commit anlegen - Der Snapshot der Stating Area wird teil der Git Geschichte.

Das Konzept scheint zu Beginn etwas seltsam, man gewöhnt sich mit etwas Übung daran und lernt es schätzen.

Beginnen wir also mit einem Beispiel:

```bash
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	css/
	images/
	index.html
	js/

nothing added to commit but untracked files present (use "git add" to track)
$ git add index.html
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	css/
	images/
	js/

$ git commit -m "Initial commit"
[master (root-commit) e33a5dc] Initial commit
 1 file changed, 22 insertions(+)
 create mode 100644 index.html
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	css/
	images/
	js/

nothing added to commit but untracked files present (use "git add" to track)

```

_Einzeichnen von Add / commit_

Wir können auch ganze Verzeichnisse oder einfach alles mit `git add` stagen:

```bash
$ git add css/
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   css/master.css

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	images/
	js/
$ git add .
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   css/master.css
	new file:   images/git-logo.png
	new file:   js/tweak.js
$ git commit -m "Add assets"
$ git status
On branch master
nothing to commit, working tree clean
```

Ein Tipp: Falls ihr etwas gestaged habt, was ihr nicht wollt, dann sagt euch git im **Output von "git status"**, was zu tun ist!

➪ Nun könnt ihr das selbst ausprobieren!
➪ Für die Schnellen: Schaut euch etwas vom "Self Study" an

### Staging Area = Snapshot

```bash
$ # CSS Einkommentieren
$ git add .
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   index.html
$ # JS Einkommentieren
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   index.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   index.html

```

Git add nimmt ein "Snapshot".

Git betrachtet die die beobachteten Daten als eine Reihe von Snapshots eines Mini-Dateisystems. Mit einem Commit wird der Zustand dieses Dateisystems gespeichert.

_Einzeichnen Fotoapparat_


## Sha1 Hashes
Ein Commit wird durch einen Hash Identifiziert.
Diesen sieht man nach dem Commit:

```bash
$ # Ein Paragraph löschen
$ git add index.html
$ git commit -m "Delete one paragraph"
[master 015ee1d] x
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Hier sieht man nur die Kurzversion.

## Hinweis zum Style

* Ein Commit sollte möglichst Atomar sein - also "genau eine Änderung" beinhalten.
* Commit Messages: Hauptsache konsistent (Sprache, Form).
    * Empfehlung: Englisch und Präsens im imperativ ("Add new File")

## Fazit
Wichtig ist, dass alle einen Commit machen können und das Konzept der 3 Zuständer verstanden haben.
Die nächsten Punkte in diesem Kapitel können je nach stärke der Gruppe weggelassen werden.

## Weiterführendes (Self-Study)

* Änderungen anzeigen mit `git diff`
    ```bash
    git diff
    git diff --staged
    ```
* Dateien löschen mit `git rm`
* Dateien verschieben `git mv`
* Dateien ignorieren `.gitignore`

### Änderungen verwerfen

* Alle Änderungen, die noch nicht commited ist verwerfen

```bash
git reset HEAD <file>
```

### Git log

```bash
git log
git log

git log --oneline --graph --decorate
git log 471bdf4...920a4a0
git log --since="3 days ago"
git show 471bdf4

# Commits, die nur eine Datei betreffen
git log -- statuten/statuten.tex
```

### Alte Zustände wiederherstellen
* Siehe [Reset, Checkout, and Revert](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/)

### Philosophische Frage zum verschieben von Dateien
Das Schiff des Theseus

* [Who am I? A philosophical inquiry - Amy Adkins](https://www.youtube.com/watch?v=UHwVyplU3Pg)
* [Ship of Theseus • GitHub & Git Foundations](https://www.youtube.com/watch?v=qk1UE-9qf0Q)

## Kompakte Git status Ausgabe

```bash
# Details nachlesen
$ git help status
$ git status --short
```

## Git alias

```bash
# Neuer alias hinzufügen
$ git config --global alias.l "log --oneline --graph --decorate"
# Wurde in config hinzugefügt?
$ cat ~/.gitconfig
# Alias ausprobieren
$ git l
```

## Git add --patch
Pro Tip: Mit Git-Patch können Änderungen gruppenweise gestaged werden - damit macht Ihr auch gleich ein Review, bevor ihr comitted.

```bash
$ # Eie Zeile in der Datei index.html verändern
$ git add --patch
```
