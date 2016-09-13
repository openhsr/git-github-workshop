# Vorbereitung:
* Feedbackbogen drucken
* Notizen drucken
* Agenda auf Flipchart / Whiteboard
* Beamer einschalten / verbinden
* Präsentation testen
* Tische verschieben
* Genügend Strom?
* Drucken: https://services.github.com/kit/downloads/github-git-cheat-sheet.pdf

# Begrüssung
**Folie Git & Github Workshop**

- Kurz Vorstellung: Verein & Workshop Leiter
- Ziel des Workshops / warum sind wir da? ("Abstract aus kurs")
- Agenda (Flipchart / Whiteboard)

- Git installiert
- Github-Account erstellt?
- Weiteres?

- Was habt ihr bereits für Erfahrungen mit Git/Github?
  => Bestimmt Tempo und evtl. Schwerpunkte

- Regeln:
    - Fragen sind immer erlaubt und erwünscht! Workshop ≠ Präsentation
    - Ihr könnt immer stop sagen - dann schalten wir einen Gang zurück oder vor.
    - Pause zwischen den Blöcken oder bei Bedarf - andere wünsche?
    - Ich werte etwas vorführen, bsp. git repo erstellen. Da bitte zuschauen, zuhören, denn ich werde konzepte etc. dazu erklären. Kurz danach könnt ihr das ausprobieren - ihr bekommt auch die code listings dazu!
- Es gibt viele Wege! Dieser Kurs zeigt ein Weg den wir für am einfachsten halten

# Wozu brauchen wir Versionskontrolle?

## 2 Wichtigste Punkte für VCS:

1. Nichts geht verlohren ()
    - Versionskontrolle protokollieren Änderungen an Dateien über die Zeit
    - Man kann jederzeit auf ältere Versionen von Dateien oder des ganzen Projekts zurückgreiffen (wiederherstellen oder vergleichen)
    - Bsp. Nütlzich falls etwas ausversehen gelösch wurde
    - Aber: Ungleich Backup! Backups müssen trozdem gemacht werden :wink:
2. Gemeinsam arbeiten
    - VCS protokolliert Änderungen: Damit ist immer klar *was* sich *wann* geändert hat.
    - so können unterschiedliche Änderungen vereint werden!
    - Kein unbeabsichtigtes überschreiben möglich
    - Extrembeispiel Linux-Kernel: [3'738 Entwickler](http://arstechnica.com/information-technology/2015/02/linux-has-2000-new-developers-and-gets-10000-patches-for-each-version/) (Stand 2015) produzieren [durchschnittlich 3'509 neue Zeilen code PRO TAG!](http://royal.pingdom.com/2012/04/16/linux-kernel-development-numbers/))
    - Zahlen zum Kernel sind kein Zufall: Da GIT von Torwalds primär für ein Projekt wie den Linux Kernel designed wurde

Weitere Gründe:

- Code Reviews
- Context Switching (Gleichzeitig an mehreren Features arbeiten)
- Isolation von Änderungen

## Probleme
- Bsp. Blobs (Bilder, PDFS usw.)
- VCS kennen diese Typen nicht und können diese nicht platzspaarend speichern
- Wird sehr gross!

## Zentrale vs. Dezentrale Versionskontrollsysteme

### Zentrale Versionskontrollsysteme
- Bsp. SVN, CVS
- Eine gemeinsahme "Wahrheit"
- Mächtige zentrale Administration
    - commit access: Problem bei OSS: Grosse hürde!
- Die meisten Änderungen passieren auf dem zentralen Server
- "Single Point of Failure" (1. Stunde offline = 1 Stunde kann niemand arbeiten)
- Offline arbeiten nicht möglich


### Dezentrale Versionskontrollsysteme
- = Distributed
- Bsp. Git, Mercurial, Bazaar
- Viele "Wahrheiten"
- Flexibel (ermöglicht unterschiedlichste Workflows)
- Die Änderungen können überall passieren
- Offline arbeiten möglich
- Alle haben Commit access - aber einzelne "offizielle remotes" haben speizielle berechtigungen (mehr daszu später)

## Fazit
- Moderne Software-Entwicklung ohne VCS nicht möglich!
- Dezentrale Versionskontrollsysteme sind mächtig und flexibel

## Weiteres (Bei Zeit / Interesse)
- ?

# Warum Git?
- ["Git is not better than Subversion. But is also not worse. It's different."](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion)
- Am populärsten (Auch bei Google, Facebook, Twitter etc.) -> Grosse Wahrscheinlichkeit, dass ihr damit arbeiten werdet
- Extren viele OpenSource Projekte arbeiten mit Git
    - Ohloh: [Zunahme der Git-Projekte um 90% seit August 2010 (26'485) bis Juli 2016 (274'605)](http://programmers.stackexchange.com/questions/136079/are-there-any-statistics-that-show-the-popularity-of-git-versus-svn)
    - Ohloh: [Aktuell 39%](https://www.openhub.net/repositories/compare)
    - Github: [April 2016: 14 Mio Benutzer](https://en.wikipedia.org/wiki/GitHub)
    - Github: [Mehr als 10 Mio repos (Stand 2013)](https://github.com/blog/1724-10-million-repositories)
- Git ist dezentral
- Branching ist einfach & billig (mehr dazu später)
    - Grund warum toll: Weil features nicht von anfang an funktionieren!
- Sehr perfomant & Skalliert gut (ausnahme: Blobs)

## Anmerkung: Git Clients
- Es gibt graphische Tools wie Gitkraken, Github Desktop, SourceTree usw. - wir werden aber auf der Kommandozeile arbeiten
- Grund: Kommandozeile hilft beim "vertehen" von Git - GUIs sind oft auch sehr überladen
    - Historische Gründe (da als CLI designed)
    - Wer nach Hilfe sucht findet in 99% der Fälle wie man es auf der Kommandozeile macht
    - Dokumentation (man pages)
    - Mächtiger (GUIS implementieren typischerweise nicht 100% von git)
    - Konsistent und cross plattform
- Wer mit dem CLI arbeiten kann versteht die GUI clients intuitiv
- Integration in div. Editoren / IDEs

## Fazit
- Git ist sehr Populär und weit verbreitet
- Git ist dezentral

## Weiteres (Bei Zeit / Interesse)
- Bash: Git branch / clean auf prompt

# Github?
- DIE Kollaberationsplattform und und Rückgrad von Millionen von Open Source Projekten
- Beitet mehrere "Dienste":
    - Git Hosting
    - Issues
    - Workflow zur Kollaboration (Forking, Pull-Requests)
    - Integrationen in CI
    - ...
- Es gibt div. Alternatieven wie Bitbucket, Gitlab etc.

## Bei Zeit / Interesse
- Github ist eine von vielen Kollaberationsplattformen
- Sehr populär im OpenSource Umfeld

## Quellen / Weiterführende Informationen
* [Pro Git](https://git-scm.com/book/en/v2) - Kapitel 1: Getting Started (deutsch/englisch)
* [Pro Git](https://git-scm.com/book/en/v2) - Kapitel 5: Distributed Git - Distributed Workflows
* [SVN vs Git](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion)
* [GitSvnComparison](https://git.wiki.kernel.org/index.php/GitSvnComparsion)
* [Tech Talk: Linus Torvalds on git (2007)](https://www.youtube.com/watch?v=4XpnKHJAok8)
* Github goldener Käfig (link?)
