---
layout: project
title: "b3scale"
image: /assets/images/project_images/b3scale/header.png
authors:
  - author: Annika Hannig
    link:
brief: "Wir verbessern den Betrieb von BigBlueButton-Clustern"
summary: "Durch b3scale können mehrere BigBlueButton-Frontends an einem großen Cluster betrieben werden. Die Middleware-Architektur ermöglicht eine flexible Lastverteilung und Feature-Erweiterungen."
---

## Motivation

Seit Beginn der COVID-19-Pandemie ist der Bedarf an Lösungen für den digitalen Remote-Unterricht kontinuierlich gestiegen. BigBlueButton hat sich dabei als gute, nicht proprietäre und datenschutzfreundliche Lösung im Einsatz an Bildungs-und Schuleinrichtungen etabliert.

Eine besondere Herausforderung ist dabei ein effizienter Betrieb, um wirtschaftlich konkurrenzfähig zu sein und somit eine attraktive Alternative zu bestehenden, nicht freien Angeboten zu bieten.

## Anforderungen

Die bisher am weitesten verbreitete Skalierungslösung Scalelite ermöglichte zwar einen Betrieb von BigBlueButton-Clustern zur Lastverteilung, allerdings musste für jede Einrichtung ein separates Cluster zur Verfügung gestellt werden. Dies führte dazu, dass viele Instanzen weitestgehend ungenutzt blieben.

Für eine effiziente Auslastung mussten alle Einrichtungen das gleiche Cluster ohne gegenseitige Interferenz nutzen können. Grundsätzlich sollte dabei allerdings die Kompatibilität mit Scalelite erhalten bleiben.

Weiter sollten für unterschiedliche Integrationen individuell einstellbare Optionen, wie die hinterlegte Standard-Präsentation, ermöglicht werden.

Eine weitere Anforderung war die Verteilung von Meetings anhand von Kriterien die für jedes Frontend einstellbar sein mussten, um beispielsweise dedizierte Bereiche zeitweise zu reservieren.

B3scale selbst muss ebenfalls einen Cluster-Betrieb ermöglichen, um Ausfallsicherheit zu gewährleisten.

Die Konfiguration soll mittels einer API erfolgen, um eine Automatisation des Betriebs zu ermöglichen.

## Architektur

Um die Anforderung der Ausfallsicherheit zu gewährleisten, war es notwendig, den Zustand in eine Datenbank auszulagern und nicht in der Anwendung selbst zu halten. Dies umfasste sowohl die Routing-Tabelle als auch die Konfiguration von BigBlueButton-Backend-Instanzen und Frontends. Die relationale Datenbank PostgreSQL wurde hier ausgewählt, weil diese bereits lange Zeit produktiv in vielen Projekten im Einsatz ist und ebenfalls Cluster-fähig ist.

![Abb.1 Cluster-Architektur mit BBB-Backends, PostgreSQL-, b3scale-Cluster und Nginx LoadBalancer.](/assets/images/project_images/b3scale/arch1.png)

### Anfrageverarbeitung

Die Anwendungsarchitektur von b3scale entspricht grundlegend der eines klassischen Proxy-LoadBalancers: HTTP-Anfragen werden entgegengenommen und dekodiert. Für das Routing wichtige Attribute wie die "MeetingID" oder die API-Ressource werden dabei strukturiert. Mit dieser Anfrage wird nun das Gateway aufgerufen und der Ablauf einer Middleware-Kette angestoßen.

In einzelnen Middlewares wird die Anfrage aufbereitet und nach Bedarf verändert. So kann beispielsweise die Standardpräsentation bei Erzeugung eines Raumes angepasst werden.

Am Ende der Kette sitzt eine Handler-Middleware, welche die BigBlueButton-API implementiert. In den meisten Fällen bedeutet das, ein Backend auszuwählen und die Anfrage dorthin weiterzuleiten. Anfragen, die aus dem Zustand der Applikation direkt erzeugbar sind, werden beantwortet, ohne das BigBlueButton-Backend hinzuzuziehen. Dazu gehört unter anderem die Auflistung der derzeit laufenden Meetings im Cluster.

Die Antwort der Handler-Middleware durchläuft die Kette in umgekehrter Richtung und kann ebenfalls modifiziert werden.

![Abb.2 b3scale Applikations-Architektur, Gateway- und Router-Middlewares](/assets/images/project_images/b3scale/b3scale_middlewares.png)

Muss zur Beantwortung einer Anfrage auf ein BigBlueButton-Backend zugegriffen werden, so muss dies zunächst durch den Router ausgewählt werden. Die Anfrage wird dabei, analog zum Gateway, durch eine Middleware-Kette geleitet und BigBlueButton-Backends anhand von Kriterien selektiert oder verworfen. Hier wird ebenfalls die Sortierung der Backends nach Last und die Partitionierung des Clusters mittels Tags durchgeführt.

### Middleware-Konfiguration

Einzelne Middleware-Module, wie beispielsweise das zum Einstellen der Standard-Präsentation bei Raum-Erzeugung, erfordern Konfiguration zur Laufzeit des Clusters. B3scale stellt allen Middlewares eine Schnittstelle zur Speicherung und Abfrage von Einstellungen zur Verfügung. Diese Schnittstelle wird ebenfalls über die HTTP-API angeboten.

### API

Änderungen des Applikationszustandes werden durch eine RESTful-API, die über das HTTP-Interface zur Verfügung gestellt wird, ermöglicht. Die Authentifikation erfolgt mittels JsonWebToken. Als Austauschformat wird JSON verwendet.

Die `b3scalecli` Terminal-Anwendung nutzt diese, um Backends und Frontends zu verwalten.

Durch die API kann die Verwaltung des BigBlueButton-Clusters in Automatisierungs- und Verwaltungslösungen integriert werden.

### Nebenläufige Datenverarbeitung

Periodische Aufgaben, wie das Abgleichen der Raum-Listen mit den Backends oder deren Prüfung auf Erreichbarkeit, werden im Hintergrund durchgeführt.

Durch die Anforderung des Cluster-Betriebs von b3scale, müssen diese Aufgaben auf die einzelnen Instanzen verteilt werden. Dazu wurde eine Job-Queue als Teil des gemeinsamen Zustandes implementiert. Alle Instanzen verarbeiten diese, allerdings kann jede Aufgabe nur durch jeweils eine Instanz gleichzeitig selektiert werden. Ausgenutzt wird dabei der Row-Level-Locking-Mechanismus der Postres-Datenbank. Die Aufgaben werden dadurch auf die einzelnen b3scale-Instanzen aufgeteilt.

Um eine größtmögliche Stabilität bei der Verarbeitung der Aufgaben zu erreichen, wird die Job-Queue periodisch abgefragt.

### Reaktive Ereignisverarbeitung

Um den Zustand des BigBlueButton-Backends mit dem von b3scale synchron zu halten, werden periodisch Meeting-Informationen von Backends abgefragt. Eine hohe Frequenz hätte dabei eine große Serverlast zur Folge. Mit einer niedrigen würde im Laufe der Zeit die interne Zustandsrepräsentation - und damit lastverteilungs-relevante Werte, wie die Anzahl der Teilnehmer\*innen - ihre Genauigkeit verlieren.

Für das Erreichen einer möglichst exakten Abbildung des Backend-Zustandes im Cluster wird durch b3scale auf interne Ereignisse (Events) von BigBlueButton zurückgegriffen: Ein auf dem Backend-Server installierter Dienst (`b3scalenoded`) abonniert die von BigBlueButton produzierten Ereignisse auf dem lokal laufenden Redis-Cache und aktualisiert den geteilten Zustand des Clusters. Beim Betreten oder Verlassen eines Raums wird so diese Information unverzüglich dem Cluster zugänglich gemacht und kann in Routing-Entscheidungen einfließen.

### Automatisches Clustermanagement

BigBlueButton-Backends können nicht nur manuell oder mittels API zum Cluster hinzugefügt werden: Der für die Ereignisverarbeitung zuständige Dienst kann so eingestellt werden, dass neue Backends automatisch am Cluster registriert werden. Dies erleichtert die Inbetriebnahme weiterer Instanzen.

### Protokollierung

Erfassung von Fehlern in Protokollen im Betrieb ist ebenfalls ein wichtiger Bestandteil von b3scale.

Detailgrad und Ebene des Protokolls können eingestellt werden. Für die Ausgabe kann dabei entweder eine klassische, textoriertierte oder eine strukturierte Variante gewählt werden.

Bei der strukturierten Protokollierung erfolgt die Ausgabe der Nachrichten in einem JSON-Format und kann dadurch im operativen Betrieb besser durch eine zentrale Protokollerfassung
verarbeitet werden.

### Metriken

Zentral für den Betrieb von Clustern ist die permanente Erfassung der Zustände der einzelnen Systeme. B3scale stellt dazu über HTTP Metriken zur Verfügung, die durch Datenbanken wie Prometheus (oder andere kompatible) erfasst und als Zeitserien aufgearbeitet werden können.

Zu den exportierten Daten gehören sowohl Kennzahlen über die Applikationsinstanz selbst - wie Speicherverbrauch oder Threads - als auch die Anzahl von Meetings und Teilnehmenden im Cluster.

![Abb.3 Grafana Visualisierung der Meeting-Kennzahlen](/assets/images/project_images/b3scale/grafana1.png)

![Abb.3 Grafana Visualisierung der Meeting-Kennzahlen](/assets/images/project_images/b3scale/grafana2.png)

## Ausblick

B3scale wird bereits produktiv eingesetzt und stellt für viele Anwendungsfälle eine gute Alternative zu Scalelite dar. Die Middleware-Architektur ermöglicht es, den Feature-Umfang von BigBlueButton zu erweitern und erlaubt eine einsatzspezifische Optimierungen der Backend-Auswahl im Cluster.

Die ursprünglich geplante Reverse-Proxy-Funktionalität, bei der die einzelnen Backend-Instanzen gänzlich hinter b3scale versteckt werden sollten, wurde allerdings aufgrund von Hürden durch die Architektur von BigBlueButton nicht weiter verfolgt.

Generell kann b3scale als Ersatz zu Scalelite verwendet werden. Allerdings fehlt zum aktuellen Zeitpunkt noch eine Unterstützung der in BigBlueButton integrierten Aufnahmefunktion. Diese befindet sich gegenwärtig noch in Entwicklung, wurde aber bisher aufgrund datenschutzrechtlicher Bedenken auch mit niedriger Priorität verfolgt.

Vielen Dank an das BMBF und das DLR für diese tolle Möglichkeit!
