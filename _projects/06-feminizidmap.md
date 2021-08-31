---
layout: project
title: "Feminizidmap"
image: /assets/images/project_images/feminizidmap/header.png
authors:
  - author: Lisa Passing
    link: feminizidmap.org
brief: "Wir helfen dabei, Femizide in Deutschland zu dokumentieren."
summary: "Feminizidmap hilft dabei Femi(ni)zide, also Morde an Frauen aufgrund ihres Geschlechts, in Deutschland zu dokumentieren und stellt gewonnene Daten für akademische Forschung und zivilgesellschaftlichen Aktivismus zur Verfügung."
---

# Feminizidmap

## Hintergrund

> "Der Begriff Femi(ni)zid bezieht sich auf Tötungen von Frauen\* und Mädchen\* durch Männer. Diese finden im Kontext hierarchischer Machtverhältnisse statt, in denen die getöteten Subjekte – Frauen/Mädchen – eine untergeordnete Position innerhalb der Machtstruktur einnehmen." [https://feminizidmap.org/de/ueber/](https://feminizidmap.org/de/ueber/)

In den letzten Jahren findet der Begriff des Femizids bzw. des Feminizids (nachfolgend Femi(ni)zid) auch in Deutschland immer mehr mediale Verwendung. Vor allem um die eigentliche Tat in verharmlosenden Begriffen wie "Beziehungstat" oder "Eifersuchtsdrama" herauszustellen: Mord. Durch bestehende (patriarchale) Machtstrukturen ermöglichte Morde an Frauen sind ein weltweit verbreitetes Problem.

Bewusstsein, Gegenmaßnahmen und Forschung zum Thema sind vor allem in Lateinamerika weit vorangeschritten, dort ist die Tat teilweise bereits eigener Strafbestand. Hier sind wir jedoch noch am Anfang, das gesellschaftliche Ausmaß zu verstehen.

Im Rahmen der 2014 in Kraft getretenen Istanbul-Konvention haben sich mehrere europäische Länder, unter anderem Deutschland, zur Verhütung und Bekämpfung von häuslicher Gewalt und Gewalt gegen Frauen verpflichtet. Trotz dieser Verpflichtung und den steigenden Zahlen der Opfer von Partnerschaftsgewalt laut [Kriminalstatistik](https://www.bka.de/DE/AktuelleInformationen/StatistikenLagebilder/Lagebilder/Partnerschaftsgewalt/partnerschaftsgewalt_node.html) wird das Thema in der Politik scheinbar noch nicht erst (genug) genommen.

Um Femi(ni)zide als Teil von geschlechterspezifischer Gewalt und ihre Verflechtung in der Gesellschaft besser zu verstehen, benötigt es Daten, die von offizieller Seite so allerdings nicht erhoben werden. Deswegen setzen hier zivilgesellschaftliche Initiativen an.

2018 gründete sich das Forschungsprojekt [Feminizidmap](https://feminizidmap.org), das ich von Anfang an technisch unterstütze. Seit 2019 sammelt das Projekt Daten zu Femi(ni)ziden in Deutschland, um die beschriebene Datenlücke zu schließen. Die Freiwilligen im Projekt arbeiten sich durch Schlagworte in identifizierten Zeitungsberichten und fügen relevante Informationen in einer geteilten Tabelle zusammen.

Diese Arbeit ist durch viele manuelle Schritte an verschiedenen Stellen sehr fehleranfällig und kann, durch die Natur von einfachen Tabellen, nicht immer automatisiert werden.

Aus diesem Grund kam im Projekt schon früh die Idee auf, eine Datenbanksoftware zur Dokumentation von Femi(ni)ziden zu entwickeln.

## Plan

Das Kerntool, an dem im Rahmen des Prototype Funds gearbeitet wurde, ist [Mapper](https://github.com/feminizidmap/feminizid-mapper). Mapper soll alle wesentlichen Aufgaben übernehmen, die im Verlauf der Förderung und im Austausch mit dem Team von Feminizidmap erarbeitet wurden:

- Nutzer\*innen-Management mit verschiedenen Rollen und Rechten.

- Interface um eine Datenstruktur veränder- bzw erweiterbar zu machen.

- Dateneingabe-Interface, das sowohl einen Schritt-für-Schritt-Workflow als auch ein punktuelles Springen zwischen Datenebenen ermöglicht.

- Automatisiertes Erstellen von PDFs der Originalquellen zur Dokumentation.

- Such- und Filter-Interface um schnell bestimmte Fälle zu finden und weiter bearbeiten zu können.

- Alle Änderungen sollen automatisch gespeichert und Bearbeitungslogs geführt werden. Daraus soll eine "History" pro Eintrag entstehen, aus der zur Not vergangene Zustände wiederhergestellt werden können.

- Review- bzw Nachbereitungworkflow sowie ein Veröffentlichungsmechanismus von jährlichen Berichten und Statistiken.

- Progammierschnittstelle zum einfachen Abfragen der bereits veröffentlichten Daten, die zum Beispiel für Visualisierungen genutzt werden kann.

## Verlauf

Der einfachste Startpunkt für die Entwicklung von Mapper war das gewünschte Usermanagement aufzusetzen. Hier waren die Vorstellungen unkompliziert und überschaubar und die Funktionalitäte eignete sich perfekt dafür, die Architektur von Mapper auszutesten.

Im nächsten Schritt ging es an das Datenbankdesign, das die Struktur der in den Tabellen gesammelten Daten umsetzen sollte. Hier entschied ich mich zunächst dafür, mich eng an der Struktur der Tabelle zu orientieren. Nach dem ersten Aufsetzen und Austesten stellte sich aber schnell heraus, dass meine Idee des Datenbankaufbaus an vielen Stellen nicht mit den tabellarischen Lösungen kompatibel war.
Ich hatte ein einfaches Abstraktions- und Abhängigkeitslevel zwischen einem "Fall" und den gegebenen "Feldern" gewählt, aber viele Felder hatten besondere Ansprüche (entweder schon existierend oder gewünscht), die mir beim ersten Durchsehen nicht völlig bewusst waren und sich nachfolgend nicht abbilden ließen.

Durch mehrere Gespräche mit dem Team über die Problemlage der Datenstruktur ergab sich auch immer mehr, dass ohnehin mehr Flexibilität in der Organisation der Datenstruktur gebraucht wird als ich zuerst angenommen hatte. Es gibt immer wieder Diskussionen und Anpassungen in den Tabellen und das Team soll in der Lage sein, die Struktur ähnlich einfach, wie in einer Tabelle, anpassen zu können. Deshalb verwarf ich die erste Version des Datenbankdesigns und überlegte mir ein neues abstrakteres und flexibleres Design.

![Datenbankdesign version 2 auf Papier](/assets/images/project_images/feminizidmap/db-sketch.png)
_Alles neu: Den groben Plan der zweiten Datenbank habe ich erstmal komplett auf Papier skizziert_

In dieser Version kann die Datenstruktur direkt im Administrations-Interface beliebig zusammengesetzt werden. Zwar kostete mich das Planen und Umsetzen dieses Interfaces relativ viel Zeit, aber das Ergebnis gibt Mapper das Potential, auch in anderen Kontexten genutzt zu werden, weil es nun der Art der gesammelten Daten gegenüber agnostisch ist.

![Datenstrukturen](/assets/images/project_images/feminizidmap/datenstrukturen.gif)
_Flexible Datenstrukturen: Hier kann die Zusammensetzung eines einzelnen Datums festgelegt werden. Informationsebenen und Benennung sind frei wählbar_

![Kategorien und Elemente](/assets/images/project_images/feminizidmap/kategorien-elemente.gif)
_In der Datenstruktur auswählbare Felder (hier Kategorien genannt) und die später in der Dateneingabe auswählbaren Optionen (hier Elemente genannt) sind einfach anpassbar_

Während der Neuplanung der Datenbank auf Papier konzentrierte ich mich in Sachen Interface auf die Dateneingabe. Hier ist mir eine gute User-Experience extrem wichtig, weil dies der Hauptteil des Tools ist, mit dem alle Teammitglieder in Berührung kommen werden.

![Eingabewizard](/assets/images/project_images/feminizidmap/datenwizard.gif)
_Eine frühe Iteration des Eingabe-Wizard mit dem angebundenen Bearbeitungslog_

Neben Mockups des Eingabe-Wizards beschäftigte ich mich vor allem mit dem automatisierten Speichern und dem Erstellen der Bearbeitungslogs. Bis ich mit der Datenbank und den Möglichkeiten der Neukonfiguration der Datenstruktur fertig war, konnte ich den Wizard noch nicht im Detail ausarbeiten.

Jetzt bin ich an einem Punkt, an dem genug planerische Vorarbeit geleistet und Änderungen umgesetzt wurden um die verschiedenen halbfertigen Teile zusammenzufügen und auf ein erstes brauchbares Deployment hinzuarbeiten. Aber diese Arbeit wird außerhalb der Förderphase stattfinden müssen.

![Zeitbasiertes Löschen Indikator](/assets/images/project_images/feminizidmap/zeitbasierter-delete.gif)
_Bessere UX: Anstatt einer "Bist du sicher?" Abfrage oder eines kleinen Banners mit "Rückgängig machen", habe ich mich beim Löschen von wichtigen Daten für einen zeitbasierten, in-Ort Indikator mit Abbruchfunktion entschieden_

Neben der Arbeit an Mapper entstand auch das Tool [Briefkasten](https://github.com/feminizidmap/briefkasten), das das (falls gewünscht, anonyme) Melden von Femi(ni)ziden aus der Zivilgesellschaft direkt an das Projekt erleichtern soll.

## Ausblick

Am Ende der Förderphase sind neben dem Prototyp von Mapper vor allem genauere Vorstellungen und Pläne für die Weiterentwicklung entstanden. Viele der anfänglichen Ideen sind noch nicht umgesetzt, jetzt aber besser ausgearbeitet und haben innerhalb des Prototypen mehr Kontext. Hoffentlich dient dies als geeigneter Ausgangspunkt, um aktiv nach Unterstützung in verschiedenen Communities zu suchen.

Ich bedanke mich beim DLR sowie dem Bundesministerium für Bildung und Forschung für die Unterstützung.

## Links

- [Feminizidmap Projektwebsite](https://feminizidmap.org/)
- [Feminizidmap GitHub-Organisation](https://github.com/feminizidmap)
- [Technische Dokumentation von Mapper und Briefkasten](https://tech.feminizidmap.org/)
- [API Docs für Mapper](https://mapper-api.feminizidmap.org/)
