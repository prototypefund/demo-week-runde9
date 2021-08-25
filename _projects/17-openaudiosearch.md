---
layout: project
title: "OpenAudioSearch"
image: /assets/images/project_images/openaudiosearch/header.png
authors:
  - author: Sid Moreira da Silva
    link:
  - author: Franz Heinzmann
    link:
  - author: Joseline Veit
    link:
  - author: Henning Schumann
    link:
brief: "Wir machen Speech2Text für viele Nutzer*innen verfügbar."
summary: "Open Audio Search ist eine Open-Source-Audiosuchmaschine, die gesprochenes Wort in Text umwandelt und diesen anschließend in einem Suchindex speichert."
---

# Open Audio Search

![Open Audio Search logo](https://raw.githubusercontent.com/openaudiosearch/resources/main/prototype-demo/logo.svg)

Open Audio Search ist eine intelligente Suchmaschine für Audiodateien. Über automatische Spracherkennung wird gesprochene Sprache in Text umgewandelt, der dann in einer Volltextsuchmaschine indiziert wird. Die Engine kann RSS-Feeds abonnieren, um Inhalt von verschiedenen Quellen zu importieren. Über eine webbasierte Oberfläche können Nutzer\*innen die generierten Transkripte von Radiosendungen und Podcasts durchsuchen und direkt von der Zeitmarke der Suchergebnisse abspielen.

Open Audio Search wird als kollaboratives [Open-Source-Projekt](https://github.com/openaudiosearch/openaudiosearch) entwickelt und kann leicht auf einem beliebigen Server installiert werden.

## Motivation und Hintergrund

Wir haben einen Hintergrund in Community-Media-Netzwerken. Es gibt bereits kommerzielle Lösungen zur Spracherkennung, aber diese sind für freie Radios und andere nichtkommerzielle Medienprojekte nicht gut verfügbar: Ein minutenbasiertes Preismodell für die Sprachtranskription ist schlicht nicht finanzierbar oder zumindest sehr unattraktiv. Zwar sind Open-Source-Tools sowohl zur Spracherkennung als auch zur Volltextsuche vorhanden, aber diese sind bislang schwer aufzusetzen und nicht integriert - was einen großen händischen Aufwand bedeutet, um zu nutzbaren Ergebnissen zu kommen.

Gleichzeitig gibt es mehrere große Bestände an interessanten und relevanten Audio-Dateien wie Radio-Features und Podcasts, die unter freien Lizenzen veröffentlicht sind. Ein gutes Beispiel ist unser Partner in diesem Projekt, das [“community broadcasting archive”](https://cba.fro.at) oder auch [freie-radios.net](https://freie-radios.net). Auf diesen Plattformen ist viel toller Audio-Inhalt archiviert, aber die einzelnen Beiträge und Features sind oft nur schwer wieder aufzufinden. Insbesondere für ehrenamtlich getragene Projekte bleibt oft wenig Zeit, um Beschreibungstexte, Metadaten oder gar Transkripte einzupflegen, nachdem die eigentliche Produktion abgeschlossen ist – umso mehr für Inhalte, die vor zwanzig Jahren produziert wurden und nun im Rahmen von Digitalisierungsprojekten online gestellt werden.

Mit Open Audio Search wollen wir diese Herausforderungen angehen und dazu beitragen, eine zukunftssichere und gut wartbare Open-Source-Plattform für _community media discovery_ herzustellen. Über ein modulares Backend wollen wir Experimente mit neuen Technologien und intelligenten Algorithmen ermöglichen, um Inhalte aus den _Community Media_ ins Rampenlicht zu bringen. Wir hoffen, dass wir so Community-Media-Produzent\*innen mit mehr Reichweite und einem breiteren Publikum versorgen können – denn wenn Inhalte nach ihrer Produktion Teil eines lebendigen und leicht durchforstbaren Archivs werden, dann gehen sie auch nicht so schnell wieder verloren, wie es derzeit oft der Fall ist.

## Stand der Dinge

Mit der Förderung durch den Prototype Fund haben wir die letzten 6 Monate damit verbracht viele Ideen zu jonglieren, Backend, Frontend und Spracherkennungspipeline zu implementieren und ein Setup aufzubauen, um Open Audio Search als Open-Source-Projekt auch in Zukunft weiterentwickeln zu können.

Heute können wir nun unsere erste öffentliche Demo präsentieren:

### [demo.openaudiosearch.org](https://demo.openaudiosearch.org)

![Screencast Open Audio Search demo](https://github.com/openaudiosearch/resources/raw/main/prototype-demo/intro.gif)

Diese Demo-Seite indiziert derzeit einigen aktuellen Inhalt von [cba](https://cba.fro.at) und [freie-radios.net](https://freie-radios.net). Vorsicht, bitte: Das ist ein Alpha-Release und es ist mit Bugs und fehlenden Features zu rechnen. Wir freuen uns, wenn du uns Probleme und Ideen mitteilst - am einfachsten über unseren [Issue-Tracker auf GitHub](https://github.com/openaudiosearch/openaudiosearch/issues/new/choose)!

### Features

Open Audio Search steht beim ersten Preview-Release, ein größeres Beta-Release folgt bald. Mit heutigem Stand sind die folgenden Features implementiert und nutzbar:

- RSS-Feeds können von beliebigen Quellen importiert und in eine lokale Datenbank gespeichert werden
- Alle in den RSS-Feeds verlinkten Audiodateien können automatisch über unsere Speech-To-Text-Pipeline transkribiert werden
- Die Zuordnung von Metadaten-Feldern in den RSS-Feeds kann angepasst werden
- Umfassende Volltext-Suche ist in sowohl den Metadaten als auch den automatisch erstellten Transkripten verfügbar
- Ein responsives, webbasiertes User Interface, über das alle importierten Medien abgespielt und alle indizierten Daten durchsucht und gefiltert werden können
- Wenn die Suche Ergebnisse aus einem Transkript findet, dann kann der zugehörige Audiotrack direkt von der Zeitmarke des Suchergebnisses im Transkript abgespielt werden
- Eine (bislang minimalistische) Admin-UI, um die eingebundenen RSS-Feeds zu verwalten
- Eine HTTP-API mit Authentifizierung, über die Anbindungen an Drittsysteme entwickelt werden können

## Zukunftspläne

Wir haben im Moment ein funktionierendes Setup, das in unserer [Demo](https://demo.openaudiosearch.org) ausprobiert werden kann. Darüber hinaus haben wir schon einige konkrete Ideen, was in der näheren Zukunft passieren soll:

- Mit unseren Partner\*innen von [cba](https://cba.fro.at) und [freie-radios.net](https://freie-radios.net) wollen wir in den nächsten Monaten eine Open Audio Search Produktivinstanz für deutschsprachige Community Media in Betrieb nehmen.
- In einem Schwesterprojekt, gefördert durch [netidee](https://www.netidee.at/), setzen wir unsere eigene Trainings- und Evaluationspipeline auf, um die Spracherkennung zu verbessern. Außerdem wollen wir durch Natural Language Processing und das Matchen mit einer Wissensdatenbank wie [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) bessere und bedeutsamere Suchergebnisse erzielen.
- Nächstes Jahr wollen wir ein Replikationssystem zwischen Open Audio Search Instanzen implementieren. Das ist der nächste Schritt in Richtung eines europäischen Inhalts-Netzwerks für Community Media. Mit Unterstützung der [European Cultural Foundation](https://culturalfoundation.eu/) und Partner\*innen in Irland und Spanien wollen wir in absehbarer Zukunft eine erste Pilotversion dieses [_european cultural backbone_](https://ecb-preview.arso.xyz/) starten.

Wir laden alle, die Interesse daran haben, Community Media besser durchsuchbar und auffindbar zu machen, herzlich dazu ein, mit uns in Kontakt zu treten! Was technische Details betrifft, öffnet gerne Issues in unserem [GitHub repo](https://github.com/openaudiosearch/openaudiosearch). Für andere Kommentare, Ideen oder potentielle Zusammenarbeit besucht bitte unseren [Discord Chat Server](https://discord.openaudiosearch.org) oder [schickt uns eine Email](mailto:info@arso.xyz).

## Technische Architektur

Open Audio Search ist komplett Open Source. Wir bauen auf verschiedenen Tools und Bibliotheken auf und unsere eigene Codebase besteht derzeit aus drei Hauptkomponenten in drei verschiedenen Programmiersprachen: Dem Backend (in Rust), dem Worker für Spracherkennung und Analysen (in Python) sowie dem Web-Frontend (in JavaScript). In unserem Repository befindet sich eine ausführliche [Dokumentation der technischen Architektur](https://github.com/openaudiosearch/openaudiosearch/blob/main/docs/architecture.md), die wir fortlaufend ausbauen und verbessern werden.

## Erfahrungen während der Förderung im Prototype Fund

In den sechs Monaten des Prototype Funds haben wir diese erste Version von Open Audio Search von Grund auf entworfen und implementiert.

Wir haben mit einem in Python geschriebenen Proof-of-Concept-Backend angefangen. Das hat gut funktioniert, aber uns wurde im Prozess klar, dass Python nicht unsere Programmiersprache der Wahl ist für eine stabiles, auf langfristige Weiterentwicklung und gute Wartbarkeit ausgerichtetes Backend. Daher haben wir ungefähr zur Hälfte de Förderlaufzeit beschlossen, das Backend in [Rust](https://www.rust-lang.org/) zu schreiben. Rust ist eine recht neue Programmiersprache, die über ihre strenge Typisierung und diverse weitere Features viel dazu beitragen kann, zuverlässige und effiziente Software zu bauen. Die Umstellung des Backends auf Rust erwies sich als Herausforderung und lohnende Aufgabe zugleich: Die anfängliche Implementierung hat eine Weile gedauert, erwies sich aber schon in der Anfangsphase als sehr zuverlässig und erlaubt es uns, zu iterieren und _refactoring_ zu betreiben, ohne dass wir uns große Sorgen machen müssen.

Recht frühzeitig haben wir uns für den derzeitigen Stack an Datendiensten entschieden, die in Open Audio Search verwendet werden: [CouchDB](https://couchdb.org) als unser primärer Datenspeicher und [Elasticsearch](https://www.elastic.co/) für den Suchindex.

Parallel haben wir ein webbasierte Frontend entwickelt: Fließendes Hin und Her zwischen Mockups und Entwürfen, der Implementierung als _single page application_ mit [React](https://reactjs.org). Im Vordergrund stand dabei eine flott funktionierende Suchseite

Von Anfang an haben wir versucht, ein reibungsloses Packaging zu bieten. Wir haben ein Setup zur _continuous integration_, das nach jedem Commit ein neues [Docker](https://www.docker.com/)-Container-Abbild erzeugt. Damit können wir Produktivinstanzen wie die aktuelle Demo-Seite laufend auf den neuesten Entwicklungsstand aktualisieren und andere Nutzer\*innen können ebenfalls schnell und unkompliziert ein Instanz aufsetzen.

Zwei zunächst angedachte Features mussten in die nähere Zukunft geschoben werden: Durch Natural Language Processing (NLP) wollen wir Schlüsselwörter und Tags aus den Transkripten extrahieren, die wir dann für eine bessere Suche und Kategorisierung einsetzen möchten. Wir haben zwar ein minimales proof-of-concept Setup für NLP und Named Entity Recognition (NER) in der derzeitigen Codebase, das braucht aber noch etwas Tuning und Entwicklung um tatsächlich nutzbare Ergebnisse zu produzieren.

Wir wollen außerdem eine Möglichkeit herstellen, um die Datenbanken von verschiedenen Instanzen von Open Audio Search über ein _peer-to-peer_-Netzwerk zu synchronisieren. Wir haben dazu bereits einige Ansätze, diese sind aber noch nicht in der Hauptlinie der Codebase integriert. Mit dem in CouchDB integrierten [_replication feature_](https://docs.couchdb.org/en/main/replication/intro.html) haben wir dafür eine solide Grundlage.

Bevor wir in einigen Monaten in Production gehen sind noch ein paar Features zu entwickeln: Wir brauchen eine bessere Fehlerberichterstattung, eine zuverlässigere Auftragswarteschlange und eine bessere Vorverarbeitung, um Musik und Geräusche in den Audiofiles von Sprache zu trennen.

Bei einem Open-Source-Projekt geht es nicht nur ums Programmieren. Für eine lebendige Zukunft braucht es Dokumentation und Offenheit für weitere Entwickler\*innen. Hier haben wir in den letzten sechs Monaten viel nachgeholt. Wir haben jetzt READMEs und _issue templates_ in unserem [GitHub-Repository](https://github.com/openaudiosearch/openaudiosearch) und einen öffentlichen [Chat auf Discord](https://discord.openaudiosearch.org). Außerdem konnten wir unser internes Projektmanagement deutlich verbessern. Der Workshop mit [zero360](https://zero360.de/en/), den wir im Rahmen des Prototype Funds durchführen konnten, hat uns hier sehr weitergeholfen. Wir haben damit angefangen, öfters virtuelle Whiteboards zur Projektplanung zu benutzen und haben erfolgreich effektivere Abläufe in unseren wöchentlichen Treffen eingeführt.

Wir bedanken uns beim BMBF und dem DLR für die Förderung von Open Audio Search.
