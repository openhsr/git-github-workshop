# Git/GitHub Workshop
Open Source Software Entwicklung ohne Git ist heute nicht mehr vorstellbar! Das unglaublich mächtige Tool zur Versionsverwaltung hat die Herzen der
Entwickler im Sturm erobert - also unbedingt etwas, was man sich mal genauer anschauen sollte. Millionen von Open Source Projekten vertrauen heute zudem auf das Projekt-Hosting von GitHub.

Leider sind Git und GitHub in den Studienplänen der HSR nicht gerade prominent vertreten - eine Lücke die wir füllen möchten.

Der Workshop dauert ca. 2 Stunden.

# Warum sollte ich den Workshop besuchen?

In diesem Workshop überwindest du mit unserer Unterstützung die ersten Hürden beim Arbeiten mit Git und GitHub.
Wir wollen dir die Hemmschwelle nehmen, damit du unbeschwert zu Open Source und open\HSR Projekten beitragen kannst.


# Voraussetzungen und Anforderungen

* Git ist installiert und kann über die Kommandozeile aufgerufen werden. [Bei git-scm.org gibt es gute Installationsanleitungen.](https://git-scm.com/)
* Du besitzt einen [GitHub-Account](https://github.com/).
* [Du verfügst über minimale Grundkenntnisse der Kommandozeile](https://wiki.ubuntuusers.de/Shell/Einf%C3%BChrung/) - viel mehr als `cd`, `ls` und `git` brauchen wir nicht.
* Ein einfacher Text-Editor ist auf deinem System installiert (Gedit, Atom, Vim, Sublime, Notepad++ etc.).

# Inhalt

## Kurz-Intro
Wozu brauchen wir Versionskontrolle? Warum Git? Und was hat GitHub damit zu tun?
Diese Fragen klären wir kurz ein einem Intro - dabei bleiben wir relativ oberflächlich und stellen Links zu weiteren Ressourcen zur Verfügung.

(Zeitrahmen: 10' Präsentation)


## Git - Kommandozeilen Grundlagen
In diesem Block lernst du die wichtigsten Git-Kommandos kennen. Du lernst, wie man einen Commit macht und durch die
Versionsgeschichte navigiert. Zudem zeigen wir dir kurz, was für grundlegende Git-Funktionen im Alltag hilfreich sind.

(Zeitrahmen: 10' Präsentation, 20' Ausprobieren mit kurzen Inputs)

## Git Branches
Branches sind das wohl mächtigste Feature von Git und sollten unbedingt genutzt werden. Hier lernst du, wie man
einen Branch erstellt, zwischen Branches wechselt, diese merged, rebased und löscht.

(Zeitrahmen: 10' Präsentation, 20' Ausprobieren mit kurzen Inputs)


## Arbeiten mit GitHub
Mit GitHub kann man gemeinsam an Projekten arbeiten. Du wirst Repositories erstellen, lokale Änderungen veröffentlichen (pushen),
das lokale Repository aktualisieren und Pull-Requests beitragen. Zusätzlich werden wir kurz `GitHub Issues` anschauen.

(Zeitrahmen: 10' Präsentation, 20' Ausprobieren mit kurzen Inputs)

## Abgrenzung zu "Konfigurationsmanagement mit Git" in Software Engineering 1
Versionskontrolle wird im Modul Software Engineering 1 in  zwei Lektionen kurz besprochen. Dabei werden vorallem Gründe Versionskontrolle besprochen.
In der Vorlesung geht man davon aus, dass man bereits Vorkentnisse hat.
Im Gegensatz zur Vorlesung tauchtst du in diesem Kurs tief in dies "Philosophie" von Git ein - du verstehts warum gewisse Dinge in Git gelöst sind und tippst nicht einfach kommandos ein ohne genau zu erstehen was passiert.

* Effektive Terminologie (Commit?/Push?/Pull?/Fetch?...)
* Git ist eines der wichtigsten und mächtigsten Werkzeuge, das auch von den Entwicklern tief verstanden werden soll
* Fokus auf Grundlagen - stashing, pathsets usw. sind advanced bzw benötigen zuerst ein gutes Verständis vonder git basics

![](https://imgs.xkcd.com/comics/git.png)

## Ausblick / Weitere Ressource
Nachdem du nun Basiswissen zu Git und GitHub hast, bekommst du eine Liste von Links auf denen du weiterführende Informationen findest.
Falls du noch etwas weiteres wissen möchtest, können wir das hier ebenfalls noch besprechen.

(Zeitrahmen: 10' Präsentation)


todo:
https://www.atlassian.com/git/tutorials/comparing-workflows/centralized-workflow
http://nvie.com/posts/a-successful-git-branching-model/
http://wiki.hsr.ch/HSRWiki/GitAnDerHsr
https://hackernoon.com/lesser-known-git-commands-151a1918a60#.jij5ib87v


digraph G {

  "Welcome" -> "To"
  "To" -> "Web"
  "To" -> "GraphViz!"
  x [shape=box, fixedsize=True, height=0.35]
  x -> "GraphViz!"
}

http://www.webgraphviz.com/
http://www.graphviz.org/pdf/dotguide.pdf
>>>>>>> Erweiterungen Rund um Github
