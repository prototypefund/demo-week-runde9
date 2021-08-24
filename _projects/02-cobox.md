---
layout: project
title: "Cobox"
image: /assets/images/project_images/cobox/header.png
authors:
  - author: Mooness Davarian
    link:
  - author: Gregory Jones
    link:
brief: "Wir bieten eine sichere und kooperative Form der Datenspeicherung."
summary: "CoBox ist eine kooperative Cloud für Einzelpersonen oder kleine Organisationen."
---

## Co-Designing CoBox, Bausteine für eine kooperative Cloud

### Was ist CoBox?

CoBox ist ein verteiltes Dateispeicher- und Sicherungssystem für kleine Organisationen und Einzelpersonen. Es basiert auf dem Peer-to-Peer-Protokoll DAT (jetzt Hyper), das die Echtzeitreplikation eines Dateisystems ermöglicht. CoBox erweitert DAT so, dass mehrere Benutzer\*innen oder Geräte Dateien hinzufügen und ändern können. Unser Projekt fügt DAT eine Verschlüsselung hinzu, damit dynamische Backups von "Partner\*innen" gehostet werden können und diese selbst keinen Zugriff auf das Backup haben.

Organisationen, die zu klein sind, um Systemadministrator\*innen für die Verwaltung ihrer Dateispeicherinfrastruktur zu beschäftigen, nutzen stattdessen in der Regel kommerzielle Cloud-Dienste. Unsere anfängliche Bedarfsermittlung, die vor Beginn der Entwicklung von CoBox durchgeführt wurde, hat gezeigt, dass viele Gruppen mit diesen Diensten zufrieden sind: Sie eignen sich gut für Remote-Teams, machen Daten auf mehreren Geräten verfügbar und schützen vor dem Ausfall des Computers eines bestimmten Gruppenmitglieds. Die Nutzer\*innen waren jedoch unzufrieden mit der Art und Weise, wie dies erreicht wird, und äußerten Bedenken hinsichtlich des Datenschutzes und der Einhaltung der Datenschutzgrundverordnung (DSGVO) aufgrund von extraktivistischen Geschäftsmodellen. Auch die Abhängigkeit von Unternehmensanbietern, die häufig die Nutzungsbedingungen und die Preisgestaltung ändern oder einfach ausfallen (und den Nutzer\*innen damit den Zugang zu den Daten nehmen), wurde kritisch gesehen.

In der Praxis verhält sich CoBox ähnlich wie Dienste wie Dropbox und Google-Drive. Allerdings räumt CoBox die oben geschilderten Bedenken aus, indem es den Zugang der Nutzer\*innen zu und die Kontrolle über ihre Daten, Datenschutz und Dezentralisierung beibehält. Darüber hinaus trägt CoBox durch den Verzicht auf große zentrale Serverkomplexe und die Verwendung von ARM-Geräten mit geringem Stromverbrauch zu einem massiv reduzierten CO2-Fußabdruck bei.

### Benutzerzentriertes Design

Das Prinzip der gegenseitigen Hilfe ist das Herzstück von CoBox. In unserer Entwicklungspraxis bedeutet dies, dass wir unsere Design- und Entwicklungsentscheidungen auf die tatsächlichen Bedürfnisse unserer Nutzendengemeinschaft und Early-Adopter-Gruppen stützen.

Auf der Grundlage einer frühen Bedarfsermittlung war unser ursprünglicher Plan die Einrichtung eines Registers für das Matching. Ein Register würde es CoBox-Nutzergruppen ermöglichen, einander zu entdecken, zu verbinden und Vereinbarungen zur Sicherung ihrer Daten zu treffen. Die Umsetzung hat mit einer Reihe von nutzerzentrierten Design-Workshops begonnen, um das Registermodell gemeinsam zu entwerfen.

Unser Engagement für nutzerzentriertes Design bedeutet jedoch, dass wir gelernt haben, dass man manchmal von unerwarteten Ergebnissen überrascht wird!

### Was wir entdeckt haben

Unsere spezifischen Ziele für die benutzerzentrierten Design-Workshops waren
herauszufinden, welche Art von Informationen die Nutzer\*innen bereit wären weiterzugeben
welche Informationen sie über potenzielle Backup-Partner\*innen wissen müssen, bevor sie sich auf eine Vereinbarung zur gegenseitigen Sicherung ihrer Dateien einlasse
zu fragen: Wie werden Verbindungen hergestellt und Vertrauen zwischen Gruppen aufgebaut?
herauszufinden, welche Arbeitsabläufe während des Vereinbarungsprozesses am intuitivsten und einfachsten zu befolgen sind
zu erkennen: Welches Vokabular ist für die Nutzer\*innen verständlich und wie sollten Dinge in der Benutzeroberfläche erscheinen und benannt werden?

Es stellte sich heraus, dass die Nutzer\*innen und Gruppen, die an unseren Workshops teilnahmen, weniger daran interessiert waren, mit Organisationen zusammengebracht zu werden, die ihnen vorher unbekannt waren. Die Teilnehmer\*innen fühlten sich bestehender Netzwerke von Gruppen und Einzelpersonen zugehörig, die sich online oder persönlich treffen und über bestehende Plattformen und Räume für Verbindungen und Kommunikation verfügen.

Was ihnen bei CoBox mehr Sorgen bereitete, war ihre eigene Fähigkeit und die anderer Gruppen, unter dem Stress und der Belastung ihres täglichen Lebens und ihrer Arbeit konsistente und zuverlässige Backups aufrechtzuerhalten, wenn die Aufrechterhaltung von Backups nicht zu den Kernzielen der Gruppe gehörte.

Eine Grundvoraussetzung für den Aufbau von Partnerschaften zur gegenseitigen Datensicherung war daher, dass Gruppen und Einzelpersonen die "Gesundheit" dieser Sicherungen leicht überprüfen können - sowohl derjenigen, die sie für andere aufbewahren, als auch derjenigen, die Partnergruppen für sie hosten würden. Nur mit dieser Sicherheit wären die Gruppen bereit, die Verfügbarkeit ihrer eigenen Daten zu riskieren und die Verantwortung für die Verfügbarkeit der Daten von Partnergruppen zu übernehmen. Unter diesen Umständen könnte ein Ökosystem digitaler gegenseitiger Hilfe entstehen.

### Anpassung an die Bedürfnisse der Nutzer\*innen

Nach einigen Stunden des Kopfzerbrechens, einigen Gesprächen mit dem Prototype-Fund-Team und der Ausarbeitung einer neuen Reihe von User-Stories auf der Grundlage der Ergebnisse und des Feedbacks aus unseren Workshops haben wir einen angepassten Fahrplan für die Umsetzung der Überprüfung und Sichtbarkeit der "Backup-Gesundheit" in der CoBox-App entwickelt. Wir untersuchten auch, wie dies in der Benutzeroberfläche aussehen würde, wobei es eine Priorität war, dass keine Gruppe spezielle Systemadministrator\*innen benötigt, um die App nutzen zu können.

![](/assets/images/project_images/cobox/J8Flpvx.png)

![](/assets/images/project_images/cobox/iwbPgB1.png)

Den Bericht über unseren nutzerzentrierten Design-Workshop finden Sie hier. (**Link einfügen**)

Unsere überarbeitete Serie von User Stories finden Sie hier. (**Link einfügen**)

### Implementierung

#### Zuletzt gesehen & Zuletzt synchronisiert

Um die neuen Backup-Gesundheitsdaten für die Nutzer\*innen leicht zugänglich zu machen, mussten zusätzliche Datenbanken hinzugefügt werden, um Informationen darüber zu speichern und zu aktualisieren
wann eine bestimmte Person (aus der eigenen Gruppe oder einer mit der Datensicherung beauftragten "Partner\*innen"-Gruppe) das letzte Mal online gesehen wurde,
ob sie jetzt online ist (d. h. ob sie gerade Daten sichert)
und wann die eigene Kopie der Daten das letzte Mal vollständig mit den erstellten Sicherungskopien synchronisiert wurde.
In Übereinstimmung mit anderen Datenbanken, die in der App verwendet werden, haben wir uns für LevelDBs entschieden, um diese Daten zu speichern, vor allem wegen ihrer effizienten Geschwindigkeit und minimalen Größe. Denn bei der Replikation von Hypercores können Synchronisationsnachrichten in schneller Folge ausgegeben werden. Auch bei der An- und Abmeldung muss die App den Status der Peers effizient im Batch-Verfahren schreiben.

Der Zugriff auf die gewünschten Informationen über den Peer-Status und die Synchronisationen aus dem zugrundeliegenden DAT(/Hyper)-Protokoll erwies sich als weitaus schwieriger als erwartet. Dies liegt an der zugrundeliegenden Struktur der Kanäle und Streams, die zwischen zwei Peers, die sich einen bestimmten Raum teilen oder Hypercores austauschen, geöffnet sind. Die Nachrichten, die für eine bestimmte Verbindung ausgegeben werden, unterscheiden nicht zwischen einer ersten und nachfolgenden Verbindungen zwischen zwei Peers, so dass wir zusätzliche Funktionen hinzufügen mussten, um den Peer-Status korrekt zu speichern, wenn verschiedene Kanäle zwischen zwei Peers geöffnet und geschlossen werden.

Die Implementierung der Backend-Komponenten dieser Funktionen erforderte das Hinzufügen neuer Datenbanken und das Navigieren im Netzwerkstapel und dem zugrunde liegenden Protokoll. Das Hinzufügen eines Frontends zog sich durch die übrigen Schichten der Codebasis, von der Benutzeroberfläche bis hin zum Server, Router und den Controllern, die den Zugriff auf die gespeicherten Informationen ermöglichen. Bei der Ausarbeitung und Ausführung der Implementierung entdeckten wir einige wichtige Effizienzgewinne, die durch die Umstrukturierung einiger Teile des Codes erzielt werden konnten.

#### API Refactor

Zuvor war der CoBox-Server ad-hoc geschrieben worden, um bestimmte Funktionen zu erfüllen, die in der Roadmap während unseres ersten Entwicklungssprints auftauchten. Das bedeutete, dass der Code schnell unübersichtlich wurde und Patches für neue Funktionen erstellt wurden, die ohne ein umfassendes Refactoring nicht vollständig implementiert werden konnten. Dieses Refactoring wurde aufgeschoben, um die Anforderungen an die Funktionalität zu erfüllen. Dies hatte zur Folge, dass die Injektion von Abhängigkeiten in der gesamten Anwendung nicht effektiv gehandhabt wurde. Dieses Problem trat erneut bei der Implementierung der neuen Routen und Controller auf, die zum Abrufen von Informationen aus den Datenbanken "Zuletzt gesehen" und "Zuletzt synchronisiert" erforderlich waren.

Anstatt den Code neu zu patchen, konnten wir dieses Mal eine erhebliche Umstrukturierung der API vornehmen, indem wir einen einzigen Abhängigkeits-Container an die Controller und Dienste der Anwendung weitergaben. Die Abhängigkeiten einer Funktion werden nun zur Laufzeit abgerufen, um ihre Verfügbarkeit zu gewährleisten. Dies ermöglicht auch die asynchrone Initialisierung und Injektion von Abhängigkeiten, z. B. nach dem Login und der Entschlüsselung des übergeordneten Schlüssels, sowie die Regeneration von beschreibbaren Hypercores. Corestore und das DHT-Netzwerk müssen initialisiert und in den Container eingespeist werden, damit sie vom Rest der API verwendet werden können, und sie müssen beim Abmelden heruntergefahren und entsorgt werden.

### Sicherheitsüberprüfung

Zusätzlich zu der oben beschriebenen Roadmap und Funktionsimplementierung bot uns die Teilnahme an dieser Runde des Prototype-Fund zwei Sicherheits-Workshops von Least Authority. Während dieser Workshops wurden die Kernmodule von CoBox einer Sicherheitsüberprüfung unterzogen, bei welcher der Prüfer einige wichtige Optimierungen empfahl, die die Widerstandsfähigkeit des Systems gegenüber Angriffen verbessern würden. Einige davon konnten wir innerhalb des Förderzeitraums in Angriff nehmen.

Zum Beispiel speicherte CoBox ursprünglich private Schlüssel im Klartext auf dem lokalen Dateisystem. Diese wurden zwar nie über die Web-API für einen lokalen Client zugänglich gemacht, aber das bestehende System wies eine Sicherheitslücke auf, durch die Malware, die nativ im Betriebssystem installiert war, auf diese Schlüssel zugreifen konnte. Im Anschluss an die Überprüfung haben wir eine Verschlüsselung der Schlüssel auf der Festplatte mit einem Kennwortschutz eingeführt. Der primäre, übergeordnete Schlüssel - von dem alle Signier- und Verschlüsselungsschlüsselpaare beim Starten der App abgeleitet werden - wird nun mit einem Passwort verschlüsselt. Bei dieser Sicherheitsoptimierung wird der Industriestandard für Passwort-Hashing, bcrypt, verwendet. Durch die Einführung dieses Verfahrens wurde der Ablauf der Anwendung erheblich verändert, da vor dem Laden von CoBox-Schlüsseln (und den entsprechenden Hypercores) ein neuer Authentifizierungsschritt erforderlich ist. Controller, die eine Authentifizierung erfordern, werden durch eine serverseitige Sitzung geschützt.

Es sind weitere Arbeiten erforderlich, um andere Empfehlungen umzusetzen. Wir untersuchen derzeit, wie umfangreich die Änderungen am bestehenden Code sein werden.

### Schlussfolgerung

Während der Förderung durch den Prototype Fund haben wir eine Menge gelernt und CoBox hat bedeutende Fortschritte gemacht! Wir haben gelernt, was nutzerzentriertes Design wirklich bedeutet und wie man bei unerwarteten Ergebnissen umschwenkt. Wir kämpften mit Entscheidungen darüber, ob und was wir überarbeiten sollten, wenn wir Ineffizienzen im Code entdeckten, und wie man sich an ein zugrunde liegendes Protokoll anpasst, das einem nicht genau das gibt, was man braucht. CoBox bietet seinen Nutzer\*innen jetzt einen beruhigenden Überblick über die Verfügbarkeit ihrer Daten sowie über die Anwesenheit ihrer Mitstreiter\*innen. Die App ist dank der Least-Authority-Prüfung auch sicherer geworden und wird im Zuge der Weiterentwicklung weiter verbessert werden.

Wir bedanken uns herzlich beim Bundesministerium für Bildung und Forschung sowie dem Deutschen Luft- und Raumfahrtzentrum.
