---
layout: project
title: "Klinik-DB"
image: /assets/images/project_images/klinikdb/header.png
authors:
  - author:
    link:
brief: "Wir sind die offene, maschinenlesbare Krankenhausdatenbank."
summary: "Klinik-DB bereitet gesellschaftlich relevante Informationen zur deutschen Kliniklandschaft in maschinenlesbarer, strukturierter und nutzer*innenfreundlicher Form auf."
---

# KLINIK-DB: Die freie Krankenhausdatenbank

![Klinik-DB Datenbankschema](/assets/images/project_images/klinikdb/datenbankschema.png "Klinik-DB Datenbankschema")
Abbildung 1: Klinik-DB Datenbankschema

## Die Ausgangslage: eine nicht hinnehmbare Datenlage über die deutsche Kliniklandschaft

Nicht erst mit dem Eintreten der Corona-Krise ist der unmittelbare Zusammenhang zwischen politischen Entscheidungen in der deutschen Kliniklandschaft und den daraus resultierenden gesellschaftlichen Auswirkungen jedem und jeder von uns deutlich geworden. Um fundierte politische Entscheidungen treffen zu können, ist es aber essenziell, dass diese nicht nur auf Basis von Daten und Fakten getroffen werden, sondern auch, dass die Datengrundlage für die Allgemeinheit transparent und offen dargelegt werden kann.

Im Widerspruch dazu ist es verwunderlich, dass die verfügbaren Daten zur Bewertung solcher Entscheidungen oft unvollständig, wenig strukturiert, selten maschinenlesbar – und, wenn vorhanden, nur zu hohen Preisen zu erwerben sind. So sind Rohdaten der Bertelsmann Studie „Neuordnung Krankenhaus-Landschaft“ nicht frei verfügbar und deren Schlussfolgerungen daher kaum überprüfbar. Ein weiteres Beispiel sind die jährlichen strukturierten Qualitätsberichte der Krankenhäuser, zu dessen Einreichung beim Gemeinsamen Bundesausschuss (GBA) die Krankenhäuser verpflichtet sind. Diese Daten sind für die Allgemeinheit nur in aggregierter Form (z. B. Destatis) maschinenlesbar verfügbar, oder müssen aus einzelnen Krankenhausdateien auf Jahresbasis zusammengesucht werden. Klinikspezifische Daten (z. B. „Weiße Liste“) sind hingegen nicht maschinenlesbar und erlauben darüber hinaus keine überjährigen Vergleiche.

Will man z. B. diese Daten aus den Qualitätsberichten für eigene Analysen nutzen, müssen diese Daten als XML-Dateien beim GBA bestellt – Beantragung per schriftlichem Antrag und dann Zustellung der Daten ausschließlich per Post auf DVD – und danach aufwändig aufbereitet werden. Es gibt zwar erstmals seit 2019 auch vom GBA selbst herausgegebene Berichte über die einzelnen Kliniken [https://g-ba-qualitaetsberichte.de/#/search](https://g-ba-qualitaetsberichte.de/#/search), diese stellen aber nur sogenannte „Referenzberichte“ dar, die für jede Klinik einzeln als PDF-Version abgerufen werden können und teilweise 800-1000 Seiten pro Klinik umfassen. Dadurch sind sie für übergreifende Analysen vollständig ungeeignet.
Wie schwierig es sein kann, an vermeintlich frei verfügbare Daten über deutsche Krankenhäuser zu gelangen, offenbarte sich, als wir das offizielle und auch technisch per API abrufbare Intensivbetten-Register (heutzutage in aller Munde: die „Deutsche Interdisziplinäre Vereinigung für Intensiv- und Notfallmedizin“ – DIVI) in die Datenbank integrieren wollten. Die dort handelnden Akteure, DIVI und RKI, kommunizierten hier aber deutlich, dass sie die weitergehende Nutzung dieser „öffentlichen“ Daten als „urheberrechtsgeschützt“ nicht akzeptieren wollen und sogar verfolgen würden – zum Teil mit Androhung rechtlicher Konsequenzen. Daher konnte dieses gerade in Corona-Zeiten nützliche Feature leider nicht in unsere Datenbank einbezogen werden.

## Unsere Lösung: eine freie und übergreifende Klinikdatenbank

Klinik-DB ist die erste und einzige transparente, vollständige und öffentlich zugängliche Datenbasis für Klinik-Strukturdaten. Klinik-DB umfasst eine Vielzahl gesellschaftlich relevanter Informationen zur deutschen Kliniklandschaft in maschinenlesbarer, strukturierter und nutzerfreundlicher Form. Der freie Zugang zu den maschinenlesbaren Rohdaten ermöglicht eine einfache Anwendung für sämtliche Nutzer\*innengruppen, erleichtert aufwändige Rechercheaufgaben und ermöglicht hochwertige Analysen. Damit stellt Klinik-DB einen zentralen Anlaufpunkt für Fachpublikum aus dem Gesundheitswesen und interessierte Menschen aus der Bevölkerung, aber auch für Journalist\*innen, Recherchenetzwerke, Behörden, Institutionen oder NGOs dar.

## Unsere Umsetzung: systematische Datenaufbereitung, Schaffung von Transparenz, freie Daten

Der erste Schritt in unserem Projekt war die _Befreiung der Daten aus den GBA-XML-Dateien_ durch automatisches Einlesen und Parsen in ein einheitliches Format sowie die Abbildung dieser Daten in einer SQL-Datenbank. Dieser Vorgang wurde für die letzten fünf Jahre vollzogen.
Hierbei ist u. a. auch die örtliche Position (d. h. die in den Rohdaten nicht enthaltenen Koordinaten) jedes Krankenhauses in die Datenbank integriert worden, um räumliche Analysen zu ermöglichen. Die Informationen wurden so miteinander verknüpft, dass die Kliniken über die Jahre verfolg- und vergleichbar sind. Hiermit wird der Aufwand für die Nutzer\*innen enorm reduziert, da ein überjähriger Vergleich anhand der GBA-Rohdaten bisher nicht möglich ist (es gibt z. B. keinen verlässlichen übergreifenden ID-Code über die Jahre hinweg) oder intensive Handarbeit erfordert. Da wir den Programmcode für unseren XML-Parser unter einer Open-Source-Lizenz verfügbar machen (R-Package „qbgbaReader“), kann das Einlesen der Daten aus den XML-Dateien in eine Datenbank von allen, die den Code nutzen, reproduziert werden, solange die GBA-Rohdaten verfügbar sind.

![Startseite der Dokumentation für das Parsing R-Package „qbgbaReader“](/assets/images/project_images/klinikdb/dokumentation.png "Startseite der Dokumentation für das Parsing R-Package „qbgbaReader“")
Abbildung 2: Startseite der Dokumentation für das Parsing R-Package „qbgbaReader“

Um die Nutzbarkeit und den Informationsgehalt von Klinik-DB weiter zu steigern, wurden die GBA-Daten mit weiteren Drittdaten angereichert. So befinden sich in der Datenbank weitere demographische und ökonomische Daten auf regionaler Ebene.
Damit sich alle User einen Eindruck von den Möglichkeiten der Klinik-DB machen können, wurden bereits verschiedene und einfach durchzuführende Beispielanalysen erstellt, die sich mit den Daten realisieren lassen. Diese stellen wir über einen Docker-Container bereit, in dem eine R-Analyse-Umgebung und eine Shiny-basierte interaktive Weboberfläche enthalten ist. Damit besteht z. B. die einfache Möglichkeit, sich die Kliniken auf einer interaktiven Karte anzeigen und sich zu jeder Klinik zusätzliche Informationen über die verfügbaren Jahre ausgeben zu lassen.
Neben diesem nutzer\*innenfreundlichen Analysetool steht ein kompletter Daten-Download für die Jahre 2015 bis 2019 im SQL-Format zur Verfügung: Sämtliche eingelesenen Daten können als vollständiger SQL-Dump heruntergeladen werden, so dass sich die SQL-Datenbank mit allen Informationen problemlos reproduzieren lässt. Da die Gesamtdaten mit mehr als 2 GB jedoch zu groß für einen Docker-Container sind, haben wir kleinere Auszüge aus den Daten für die oben genannten Analysen zusammengestellt. Auch diese bieten wir neben dem Download der gesamten Datenbank auch als einzelne CSV-Dateien an. Darüber hinaus haben wir für die gesamte Datenbank eine maschinenlesbare REST-API erstellt, über die (aus Gründen der Serverkapazität mit gewissen Limits pro Request) jede Tabelle der Datenbank abgefragt werden kann. Schlussendlich stellen wir eine Websuche zur Verfügung, über die einzelne Krankenhäuser gesucht und verschiedene Datenpunkte aus den Berichten direkt eingesehen werden können.

Programmcode und Container: [https://gitlab.com/klinik-db](https://gitlab.com/klinik-db)

Online-Suche: [https://klinik-db.de/](https://klinik-db.de/)

API: [https://api.klinik-db.de](https://api.klinik-db.de)

Wir bedanken uns beim BMBF und dem DLR für die Unterstützung.
