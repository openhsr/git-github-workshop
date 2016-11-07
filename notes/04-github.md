# Github

* Github ist grösste Kollaborationsplattform
* Kostenlos für öffentliche Projekte (kostenlose private Repositories mit dem [Github Student Developer Pack](https://education.github.com/pack))

Github bietet Projekten

* Hosting (Statische Webseiten mit Jekyll)
* Issue Tracker
* Pull Reuests aka "Github Flow" - mehr dazu Später
* Integration in Drittdienste
    * Bsp. Continous integration mit Travis-CI usw.
* Vieles, vieles mehr...

## Remotes

* Recap: Dezentral ➪ alle Repositories sind gleichwertig
* Neuer Begriff **Remote**: Kopien/Versionen des Git-Repositories, welches (typischerweise) im Internet gehostet ist.
* Einzige Möglichkeit der Zugriffsregelung, wer auf "Remote" schreiben darf

![](images/github-setup.svg)


## Neues Repository

* Wir erstellen ein neues Repository auf Github (Name mit dashes und ohne white spaces)
* In der Navigation oben Rechts auf "+" →  "New Repository"
* README sollte existieren, da diese angezeigt werden.

➪ Alle erstellen neues Repository

## Exkurs: Protokolle

* Git kann über mehrere Protokolle "gesprochen" werden, u.a. https, SSH und über das lokale Dateisystem (bsp. für Experimente oder `mount`)
* SSH empfohlen - primär wenn Zweifaktorauthentisierung aktiv. Wenn ihr also sowieso SSH Keys habt, dann nutzt es - sonst schaut es euch mal an, nutzt aber für den Moment https.

## Neues Remote & Push

* Wie kommen nun Änderungen auf Remote?
* `git remote add origin <url>`
* Die URL finden wir auf der Übersicht des Repositories.
* Origin ist einfach eine Konvention auf Github
```bash
$ git remote -v
origin	git@github.com:openhsr/git-github-workshop.git (fetch)
origin	git@github.com:openhsr/git-github-workshop.git (push)
```
* Um nun Änderungen auf das Remote zu kriegen müssen wir *pushen*
```bash
$ # $ git push <remote-name> <branch>
$ git push origin master
```

* Pushen können nur Berechtigte → hier ist also unsere Zugriffsschranke

➪ Alle pushen ihre lokalen Repositories

## Clone

* Code ist nun geteilt - doch wie können Andere mitarbeiten?
* Zur Demonstration lösche ich mein lokales Repository
 ```bash
 $ cd ../
 $ rm -Rf repo-name
 ```
* Suche die URL auf der Seite des Repositories
* Nun Klonen - Hinweis: klont so in ein neues Verzeichniss
```bash
$ git clone <url>
```
* Um zu Beweisen, dass wirklich alle Änderungen vorhanden sind:
```bash
$ git log
```

➪ Alle klonen mein Repository

## Pull

* Jedes mal das Repository löchen ist nicht sinnvoll
* Wie können wir "updaten"? Wir möchten die Änderungen "pullen"
* Zu Demo-Zwecken lösche ich den Letzten commit - DON'T TRY THIS AT HOME! `git reset --hard HEAD~`
    * Exkurs: Solange ihr nicht wisst, was hard und force machen und was die Konsequenzen sind - Finger weg!
* Mit `git log` sehen wir also, dass wir einen Commit "hintendrein" sind.
* Mit `git fetch` laden wir die Commits und History vom Remote in unser lokales git Repository. Dies ist die einzige Aktion, die Internet benötigt
    ```bash
    $ git fetch
    ```

* Nun haben wir die Änderungen im lokalen Repo - aber wo?
    ```bash
    $ git branch -a
    * master
      remotes/origin/master
    ```

* Nun können wir das Anwenden, was wir vorher gelernt haben: Merge bzw. Rebase :tada:
    ```bash
    $ git rebase origin/master
    ```

* Hinweis: Pull - Pull macht fetch & merge bzw. fetch & rebase wenn das Flag `--rebase` gesetztw wird.
* Ich empfehle am Anfang das "von Hand" zu machen - das Hilft fürs Verständnis und sich Gedanken zu machen, ob man Rebasen oder Mergen möchte.

➪ Ich mache eine Änderung an meine Repository - nun können alle Pullen

➪ Für Interessierte: Ihr könnt einen Merge-Konflikt provozieren und auflösen!

## Repetition an der Grafik

![](images/github-overview.svg)

# Guithub Workflow

Repetion: In Git ist alles auf auf einem Branch - "Seil"

Der Github-Flow läuft in der Theorie wie folgt ab:

1. Wir "forken" das Originalprojekt. Forken bedeutet, dass wir auf Github einen Klon erstellen.
    * Die beiden Repositories sind komplett voneinander unabhängig (Ausnahme: Github merkt sich semantische Informationen - hat aber keinen Einfluss auf Git)
    * Dieser fork aktuallisiert sich also nicht auf magische Weise - das müssen wir alles manuell tun
2. Wir machen unsere Änderungen auf unserem Fork - auf den wir (im Gegensatz zum Original) schreiben dürfen
3. Wir stellen eine "Pull-Request" - also eine Anfrage, dass der Besitzer des Original-Repository unsere Änderungen in das Original-Repository *pullt*. Ein Pull-Request ist nichts anderes, als ein Semantischer Link: User X möchte Branch Y vom X/A ind Y/A mergen. Zudem kann Kommentiert werden - tatsächlich ist ein Github PR auch ein Github Issue. Siehe [git request-pull](https://git-scm.com/docs/git-request-pull)
4. Der Pull-Request wird in das Original-Repository gemerged oder abgeleht.

![](images/github-setup-pull.svg)

➪ Alle können anhand der Step-by-Step Checkliste durchführen. Im Idealfall einen Tippfehler o.ä. auf der open\HSR Website - alternativ eine neue Datei (um Konflikte zu vermeiden) in meinem Demo-Repository.

## Step-by-Step Checkliste
1. Projekt auswählen
    * Arbeit für ein bekanntes Projekt
        * Eigenes Problem → Am Besten neues Ticket erstellen und abklären, ob diese Funktion/Fehler bereits bekannt und erwüncsht ist und wie bzw. wo es implementiert werden kann.
        * Durchsuchen des Issue Trackers auf ein geeignetes Issue
            * Label "help wanted", "easy fix", "up for grabs" usw.
    * Arbeit an einen Populären / "Hilfsbedürftigen" Projekts
        * [Project showcases](https://github.com/explore)
        * Github Suche - Bsp. [label:"help wanted"](https://github.com/search?q=label%3A%22help+wanted%22&type=Issues) usw.
    * Prüfe ob das Projekt noch Lebt - nicht dass die Arbeit für die Tonne ist
    * Prüfen der Software-Lizenz
2. Anleitungen/Richtlinien für Contribution lesen
    * Typischerweise gibt es Dokumente (`CONTRIBUTING.md`, `CONTRIBUTE.md`, `CONVENTIONS.md` oder ein Abschnitt in der `README.md`), wo die Maintainer beschreiben wie man Vorgehen möchte.
    * Man sollte sich unbedingt an diese Richtlinien halten
    * Beispiel Linux Kernel: Mirror auf Github - es werden keine Pull-Request & Issues akzeptiert
3. Projekt Forken
    ![](images/github_fork.png)
4. Geforktes Projekt klonen
    ```bash
    $ git clone <fork-repo-url>
    $ cd <dir>
    ```
5. Geklontes Projekt einrichten
    ```bash
    $ git remote add upstream <original-repo-url>
    ```
6. Neuer Branch Erstellen
    * Kurzer und beschreibender Name verwenden
    ```bash
    $ git checkout -b <branch-name>
    ```
7. Änderungen umsetzen
    * Fokus auf genau eine Funktion
    * Sinvolle Commits (und Commit-Messages)
    * Neue Branches (und Pull-Request) für andere Features
    * Änderungen vom upstream (original Projekt) regelmässig (mindestens vor jedem push push) mergen your changes to origin (your fork)
    ```bash
    $ git fetch upstream
    $ git rebase upstream/master
    ```
8. Pull-Request erstellen
    * Geht alles noch und sind Guidelines eingehalten?
        * Funktionieren noch alle Tests?
        * Müssen noch Tests geschrieben werden?
    * Änderungen pushen
    ```bash
    $ git push origin <branch-name>
    ```
    * Auf der Übersichtsseite des Forks den Branch auswählen
    * Den Branch auswählen und einen neuen Pull-Request starten.
    ![](github_new_pr.png)
    * Ausführliche Beschreibung und Referenzen/Beweggründe notieren
9. Weiterverfolgen
    * Warten auf Feedback → Benachrichtigung erfolg automatisch per E-Mail.
    * Änderungen mit dem Maintainer disskutieren und eventuelle Änderungen vornehmen.
    ```bash
    $ git fetch upstream
    $ git rebase upstream/master
    $ # do changes...
    $ git push origin <branch-name>
    ```
10. Aufräumen
    * Nachdem dein beitrag gemerged (oder abgelehnt) wurde kann der lokale Branch und der Remote-Branch auf dem Fork gelöscht werden
    ```bash
    $ # Lokaler Branch löschen
    $ git branch -D BRANCH_NAME
    $ # Remote Branch löschen
    $ git push origin --delete BRANCH_NAME
    ```

# Weiteres
## TODO: Checkout Remote Branch

## TODO: git push -u origin (Tracking Branches)


## Github Pull-Requests lokal auschecken

Wer auf Github ein Projekt wartet, kennt die Situation: Ein neuer Pull-Request wird eröffnet und man möchte die Änderungen gerne lokal ausprobieren, bevor man sie merged. Aber wie geht das am einfachsten?

Damit wir nicht jeden Pull-Request von Hand herunterladen müssen, ergänzen wir die Git-Konfiguration, so dass auch Pull-Requests bei einem `fetch` heruntergeladen werden.

```bash
$ git config --add remote.origin.fetch '+refs/pull/*/head:refs/remotes/origin/pr/*'
```

Wenn wir nun mittels `fetch` Änderungen aus Remote Repository herunterladen, werden auch Pull-Requests als Branches heruntergeladen:

```bash
$ git fetch
remote: Counting objects: 53, done.
remote: Total 53 (delta 20), reused 20 (delta 20), pack-reused 33
Unpacking objects: 100% (53/53), done.
From https://github.com/openhsr/www.openhsr.ch
 * [new ref]         refs/pull/14/head -> origin/pr/14
 * [new ref]         refs/pull/24/head -> origin/pr/24
 * [new ref]         refs/pull/27/head -> origin/pr/27
 * [new ref]         refs/pull/28/head -> origin/pr/28
 * [new ref]         refs/pull/29/head -> origin/pr/29
 ...
```

Mit jedem `fetch` werden nun also alle Pull-Requests als Branches heruntergeladen.

Ein beliebiger Pull-Request kann jetzt wie jeder andere Branch ausgecheckt werden:

```bash
$ git checkout pr/51
```
