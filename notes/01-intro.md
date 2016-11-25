# Vorbereitung

* Notizen drucken
* Unterlagen Drucken
    * Cheat-Sheet
    * Links & Weitere Ressourcen
    * Feedback
* Agenda auf Flipchart / Whiteboard
* Beamer einschalten / verbinden
* Präsentation testen
* Schriftgrösse Terminal vergrössern
* Tische verschieben
* Genügend Steckdosen? Eventuell Verlängerungskabel und Verteilstecker besorgen.
* [Git Cheat Sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf) drucken
* Github Ablauf cheat sheet drucken
* Stick mit Beispielen bereitmachen
* Stick mit Beispielen an Teilnehmer verteilen
* Terminal öffnen und unterordner mit beispielprojekt auschecken.
* [Explain Git im Zen-Mode](http://onlywei.github.io/explain-git-with-d3/#zen)

# Begrüssung
_Folie Git & Github Workshop_

* Kurz Vorstellung: Verein & Workshop Leiter

_Folie Motivation_

* Ziel des Workshops = Agenda (Siehe Flipchart / Whiteboard)
    * Git Basics
    * Branching
    * Arbeiten mit Github
    * Aber: Hauptziel ist, die Konzepte zu vermitteln
    * Kommandos könnt Ihr auf Cheat-Sheets / im Internet finden.
* Was habt ihr bereits für Erfahrungen mit Versionskontrolle?
* Was habt ihr bereits für Erfahrungen mit Git/Github?
  (Bestimmt Tempo und evtl. Schwerpunkte)
* Es führen viele Wege nach Rom! Dieser Kurs zeigt genau ein Weg (Derjenige, den wir für am einfachsten halten)
* Sehr komplexes Thema - darum Konzentration auf Konzepte.

_Folie Vorbereitung_

* Haben alle Teilnehmer Git installiert?
* Haben alle Teilnehmer einen Github-Account erstellt?
* Probleme?
* Weiteres?


_Folie Regeln_

* Regeln:
    * Fragen sind immer erlaubt und erwünscht! Workshop ≠ Vortrag
    * "stop" sagen - dann schalten wir einen Gang zurück oder vor.
    * Pause zwischen den Blöcken oder bei Bedarf - andere Wünsche?
    * Ablauf:
        * Ich werde etwas vorführen (beispielsweise wie man ein Git Repository erstellt)
        * Bitte während diesen Sequenzen zuhören und zuschauen,
        * Danach könnt ihr den Vorgestellten Stoff selbst ausprobieren

# Versionskontrolle?

_Folie Wozu Versionskontrolle_

* Dieser Punkt nur kurz, da auch in SE1 Thema

## 2 Wichtigste Punkte für VCS

1. Nichts geht verloren
    * Versionskontrolle **protokollieren Änderungen** an Dateien über die Zeit
    * Man kann jederzeit **auf ältere Versionen** von Dateien oder des ganzen Projekts **zurückgreifen** (wiederherstellen oder vergleichen)
    * Ist nützlich, wenn man bsp. etwas gelöscht hat
2. Gemeinsam arbeiten
    * VCS protokolliert Änderungen: Damit ist immer klar **_wer_ _was_ _wann_ geändert hat**.
    * dies ermöglicht das **effiziente Vereinen** von unterschiedliche Änderungen
    * Kein unbeabsichtigtes Überschreiben möglich
    * Extremes Beispiel: Linux-Kernel:
	* [3'738 Entwickler](http://arstechnica.com/information-technology/2015/02/linux-has-2000-new-developers-and-gets-10000-patches-for-each-version/) (Stand 2015)
	* produzieren [durchschnittlich 3'509 neue Zeilen code PRO TAG!](http://royal.pingdom.com/2012/04/16/linux-kernel-development-numbers/)
	* Zahlen zum Kernel sind kein Zufall: Da GIT von Torwalds u.a für den Linux Kernel entworfen wurde

Weitere Gründe:

* Code Reviews
* Gleichzeitig an mehreren Features arbeiten (Context Switching)
* Traceability: Wo/Wann/Wie entstand ein Bug

## Zentrale vs. Dezentrale Versionskontrollsysteme

### Zentrale Versionskontrollsysteme
_Folie Zentrale Versionskontrollsysteme_

* Bsp. SVN, CVS
* Eine gemeinsame "Wahrheit"
* Mächtige **zentrale Administration**
    * Schreibrechte (commit access): Ist eine grosse Hürde bei Open Source Projekten!
* Die meisten **Änderungen passieren auf dem zentralen Server**
    * Offline arbeiten nicht möglich
* "Single Point of Failure"
    * Bsp. Server ist 1. Stunde = Alle Entwickler sind eine Stunde blockiert

### Dezentrale Versionskontrollsysteme
_Folie Dezentrale Versionskontrollsysteme_

* Dezentral = Distributed = Verteilt
* Bsp. Git, Mercurial, Bazaar
* Viele "Wahrheiten"
* Flexibel (ermöglicht unterschiedlichste Workflows)
* Die **Änderungen passieren lokal** - also theoretisch überall
* **Offline** arbeiten möglich
* Alle haben **Schreibrechte** (commit access) - aber für "offizielle Remotes" gelten spezielle Berechtigungen (mehr dazu später)
* Git ist dezentral!
* Mehr dazu im Github Teoil

## Fazit
- Moderne Software-Entwicklung ohne VCS nicht möglich!
- Dezentrale Versionskontrollsysteme sind mächtig und flexibel

# Warum Git?

_Folie Git_

- ["Git is not better than Subversion. But is also not worse. It's different."](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion)
- Am populärsten (Auch bei Google, Facebook, Twitter etc.) -> Grosse Wahrscheinlichkeit, dass ihr damit arbeiten werdet
- Sehr viele Open Source Projekte arbeiten mit Git
    - Ohloh: [Zunahme der Git-Projekte um 90% seit August 2010 (26'485) bis Juli 2016 (274'605)](http://programmers.stackexchange.com/questions/136079/are-there-any-statistics-that-show-the-popularity-of-git-versus-svn)
    - Ohloh: [Aktuell 39%](https://www.openhub.net/repositories/compare)
    - Github: [April 2016: 14 Mio Benutzer](https://en.wikipedia.org/wiki/GitHub)
    - Github: [Mehr als 10 Mio repos (Stand 2013)](https://github.com/blog/1724-10-million-repositories)
    - Github: [2.2 Mio Aktive Repos und 3.4 Mio Users](http://githut.info/)
- Branching ist einfach & billig (mehr dazu später)
    - Grund warum toll: Weil Features nicht von Anfang an funktionieren!
- Sehr schnell
- Skaliert gut
    - Ausnahme: Binärformate (Bilder, PDF-Dokumente usw.)

## Anmerkung: Git Clients
- Graphische Tools wie Gitkraken, Github Desktop, SourceTree usw. und diverse Integrationen in Editoren/IDEs
- Im Workshop "zwingend" auf der Kommandozeile Arbeiten
- Grund: **Kommandozeile hilft beim "verstehen"** von Git - GUIs sind oft sehr überladen und verlangen Kenntnis vieler Konzepte
    - Wer mit dem CLI arbeiten kann versteht die GUIs intuitiv
    - Historische Gründe (da als Kommandozeilenprogramm entworfen)
    - Wer nach Hilfe sucht findet in 99% der Fälle wie man es auf der Kommandozeile macht
    - Dokumentation (Manpages)
    - Mächtiger (GUIs implementieren typischerweise nicht 100% von git))
    - Konsistent und plattformübergreifend

## Fazit
- Git ist sehr Populär und weit verbreitet
- Git ist dezentral

## Weiteres (Bei Zeit / Interesse)
- [Git Aware Prompt](https://github.com/jimeh/git-aware-prompt)

## Quellen / Weiterführende Informationen
* [Pro Git](https://git-scm.com/book/en/v2) - Kapitel 1: Getting Started (deutsch/englisch)
* [Pro Git](https://git-scm.com/book/en/v2) - Kapitel 5: Distributed Git - Distributed Workflows
* [SVN vs Git](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion)
* [GitSvnComparison](https://git.wiki.kernel.org/index.php/GitSvnComparsion)
* [Tech Talk: Linus Torvalds on git (2007)](https://www.youtube.com/watch?v=4XpnKHJAok8)
* [The next Generation of Code Hosting Platforms](https://blog.schiessle.org/2016/02/12/the-next-generation-of-code-hosting-platforms/)
