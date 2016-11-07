# Vorbereitung

* Feedbackbögen drucken
* Notizen drucken
* Agenda auf Flipchart / Whiteboard
* Beamer einschalten / verbinden
* Präsentation testen
* Tische verschieben
* Genügend Steckdosen? Eventuell Verlängerungskabel und Verteilstecker besorgen.
* [Git Cheat Sheet](https://services.github.com/kit/downloads/github-git-cheat-sheet.pdf) drucken
* Stick mit Beispielen bereitmachen
* Stick mit Beispielen an Teilnehmer verteilen

# Begrüssung
**Folie Git & Github Workshop**

- Kurz Vorstellung: Verein & Workshop Leiter
- Ziel des Workshops ("Abstract aus kurs")
- Agenda (Flipchart / Whiteboard)

- Haben alle Teilnehmer Git installiert?
- Haben alle Teilnehmer einen Github-Account erstellt?
- Probleme?
- Weiteres?

- Was habt ihr bereits für Erfahrungen mit Git/Github?
  (Bestimmt Tempo und evtl. Schwerpunkte)

- Regeln:
    - Fragen sind immer erlaubt und erwünscht! Workshop ≠ Präsentation
    - Ihr könnt immer "stop" sagen - dann schalten wir einen Gang zurück oder vor.
    - Pause zwischen den Blöcken oder bei Bedarf - andere Wünsche?
    - Ich werde etwas vorführen, beispielsweise wie man ein Git Repository erstellt. Bitte während diesen Sequenzen zuhören und zuschauen,
      denn ich werde dazu Konzepte und Hintergründe erläutern. Kurz danach könnt ihr den Vorgestellten Stoff selbst ausprobieren
    - Zu allem vorgeführten bekommt ihr die Code-Listings zum nachschauen

- Es führen viele Wege nach Rom! Dieser Kurs zeigt genau ein Weg (Derjenige, den wir für am einfachsten halten)

# Wozu brauchen wir Versionskontrolle?

## 2 Wichtigste Punkte für VCS:

1. Nichts geht verloren
    - Versionskontrolle protokollieren Änderungen an Dateien über die Zeit
    - Man kann jederzeit auf ältere Versionen von Dateien oder des ganzen Projekts zurückgreifen (wiederherstellen oder vergleichen)
    - Ist nützlich, wenn man etwas aus versehen gelöscht hat
    - Aber: VCS ≠ Backup! Backups müssen trotzdem gemacht werden 😉
2. Gemeinsam arbeiten
    - VCS protokolliert Änderungen: Damit ist immer klar *was* sich *wann* geändert hat.
    - dies ermöglicht das effiziente vereinen von unterschiedliche Änderungen
    - Kein unbeabsichtigtes Überschreiben möglich
    - Extremes Beispiel: Linux-Kernel:
	- [3'738 Entwickler](http://arstechnica.com/information-technology/2015/02/linux-has-2000-new-developers-and-gets-10000-patches-for-each-version/) (Stand 2015)
	- produzieren [durchschnittlich 3'509 neue Zeilen code PRO TAG!](http://royal.pingdom.com/2012/04/16/linux-kernel-development-numbers/))
	- Zahlen zum Kernel sind kein Zufall: Da GIT von Torwalds primär für ein Projekt wie den Linux Kernel entworfen wurde

Weitere Gründe:

- Code Reviews
- Context Switching (Gleichzeitig an mehreren Features arbeiten)
- Isolation von Änderungen
- Traceability: Wo/Wann/Wie entstand ein Bug

## Probleme
- Bsp. Binärformate (Bilder, PDF-Dokumente usw.)
- VCS "kennen"/"verstehen" diese Dateiformate nicht und können diese nicht effizient speichern
- Wird sehr gross!

## Zentrale vs. Dezentrale Versionskontrollsysteme

### Zentrale Versionskontrollsysteme
- Bsp. SVN, CVS
- Eine gemeinsame "Wahrheit"
- Mächtige zentrale Administration
    - Schreibrechte (commit access): Ist eine grosse Hürde bei Open Source Projekten!
- Die meisten Änderungen passieren auf dem zentralen Server
- "Single Point of Failure"
    - Bsp. Server ist 1. Stunde = Alle Entwickler sind eine Stunde blockiert
- Offline arbeiten nicht möglich


### Dezentrale Versionskontrollsysteme
- Dezentral = Distributed
- Bsp. Git, Mercurial, Bazaar
- Viele "Wahrheiten"
- Flexibel (ermöglicht unterschiedlichste Workflows)
- Die Änderungen passieren lokal - also theoretisch überall
- Offline arbeiten möglich
- Alle haben Schreibrechte (commit access) - aber für "offizielle Remotes" gelten spezielle Berechtigungen (mehr dazu später)

## Fazit
- Moderne Software-Entwicklung ohne VCS nicht möglich!
- Dezentrale Versionskontrollsysteme sind mächtig und flexibel

## Weiteres (Bei Zeit / Interesse)
- ?

# Warum Git?
- ["Git is not better than Subversion. But is also not worse. It's different."](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion)
- Am populärsten (Auch bei Google, Facebook, Twitter etc.) -> Grosse Wahrscheinlichkeit, dass ihr damit arbeiten werdet
- Sehr viele Open Source Projekte arbeiten mit Git
    - Ohloh: [Zunahme der Git-Projekte um 90% seit August 2010 (26'485) bis Juli 2016 (274'605)](http://programmers.stackexchange.com/questions/136079/are-there-any-statistics-that-show-the-popularity-of-git-versus-svn)
    - Ohloh: [Aktuell 39%](https://www.openhub.net/repositories/compare)
    - Github: [April 2016: 14 Mio Benutzer](https://en.wikipedia.org/wiki/GitHub)
    - Github: [Mehr als 10 Mio repos (Stand 2013)](https://github.com/blog/1724-10-million-repositories)
    - Github: [2.2 Mio Aktive Repos und 3.4 Mio Users](http://githut.info/)
- Git ist dezentral
- Branching ist einfach & billig (mehr dazu später)
    - Grund warum toll: Weil Features nicht von Anfang an funktionieren!
- Ist sehr schnell
- Skaliert gut (Ausnahme: Blobs)

## Anmerkung: Git Clients
- Es gibt graphische Tools wie Gitkraken, Github Desktop, SourceTree usw. als auch diverse Integrationen in Editoren/IDEs
- Im Workshop "zwingend" auf der Kommandozeile Arbeiten
- Grund: Kommandozeile hilft beim "verstehen" von Git - GUIs sind oft sehr überladen und verlangen Kenntnis vieler Konzepte
    - Historische Gründe (da als Kommandozeilenprogramm entworfen)
    - Wer nach Hilfe sucht findet in 99% der Fälle wie man es auf der Kommandozeile macht
    - Dokumentation (Manpages)
    - Mächtiger (GUIs implementieren typischerweise nicht 100% von git))
    - Konsistent und plattformübergreifend
- Wer mit dem CLI arbeiten kann versteht die GUIs intuitiv

## Fazit
- Git ist sehr Populär und weit verbreitet
- Git ist dezentral

## Weiteres (Bei Zeit / Interesse)
- [Git Aware Prompt](https://github.com/jimeh/git-aware-prompt)

# Github?
- DIE Kollaberationsplattform und und Rückgrat von Millionen von Open Source Projekten
- Bietet mehrere "Dienste":
    - Git Hosting
    - Issues
    - Workflow zur Kollaboration (Forking, Pull-Requests)
    - Integrationen in CI
    - ...
- Es gibt div. Alternativen wie Bitbucket, Gitlab etc.
- Mehr dazu später

## Bei Zeit / Interesse
- Github ist eine von vielen Kollaberationsplattformen
- Sehr populär im Open Source Umfeld

## Quellen / Weiterführende Informationen
* [Pro Git](https://git-scm.com/book/en/v2) - Kapitel 1: Getting Started (deutsch/englisch)
* [Pro Git](https://git-scm.com/book/en/v2) - Kapitel 5: Distributed Git - Distributed Workflows
* [SVN vs Git](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion)
* [GitSvnComparison](https://git.wiki.kernel.org/index.php/GitSvnComparsion)
* [Tech Talk: Linus Torvalds on git (2007)](https://www.youtube.com/watch?v=4XpnKHJAok8)
* [The next Generation of Code Hosting Platforms](https://blog.schiessle.org/2016/02/12/the-next-generation-of-code-hosting-platforms/)
