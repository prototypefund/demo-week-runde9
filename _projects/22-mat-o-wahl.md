---
layout: project
title: "Mat-O-Wahl"
image: /assets/images/project_images/mat-o-wahl/header.jpg
authors:
  - author: Mathias Steudtner
    link:
brief: "Wir informieren Wähler*innen spielerisch, schnell und einfach."
summary: "Der Mat-o-Wahl ist ein Programm zum Vergleichen von Parteipositionen mit der eigenen Meinung."
---

## Was ist der Mat-o-Wahl?

Der Mat-o-Wahl ist ein Programm (bzw. ein Umfrage-Werkzeug) zum Vergleichen von Parteipositionen mit der eigenen Meinung. Er kann frei kopiert und verändert werden, damit jede\*r _schnell und einfach selbst Umfragen zu politischen Themen_ gestalten kann.

## Warum das Ganze?

Der Mat-o-Wahl (MOW) orientiert sich am _Wahl-O-Mat_ der "Bundeszentrale für politische Bildung" (bpb). Der originale Wahl-O-Mat ist urheberrechtlich geschützt und technisch recht komplex, was den Einsatz im "kleinen Rahmen" erschwert.
Andere Wahl-o-Mat-Systeme – häufig zu Landtags- und Bundestagswahlen – arbeiten oft servergestützt (z. B. PHP, MySQL/MariaDB) oder nutzen verschachtelte Konfigurationsdateien (JSON) und/oder veröffentlichen keinen Quellcode.
Deshalb entstand vor über zehn Jahren, im Jahr 2009, die erste Version des Mat-o-Wahl.
Die ursprüngliche Idee war, digitale Wahlthemen auch digital abzufragen.(Datenschutz, Urheberrecht, Internetsperren, Transparenz in der Verwaltung, usw.) Die digitalen Themen haben es 2009 schließlich auf die Agenda geschafft und damit hätte das Thema Mat-o-Wahl im Prinzip erledigt sein können.
Im Laufe der folgenden Jahre und Monate wurde der Mat-o-Wahl dann verstärkt an Hochschulen und bei lokalen Wahlen eingesetzt. Nun kamen Anfragen und Verbesserungsideen von Nutzer\*innen aus allen Richtungen.
Spätestens ab diesem Zeitpunkt war klar, dass es einen Bedarf für einen einfachen Open-Source-Wahl-o-Maten gibt. Zusätzlich entbrannte auch mein persönlicher Ehrgeiz das Programm zu verbessern sowie mit dem aktuellen Stand der Technik mitzuhalten.

Mat-O-Wahl - Bild201 - Version 2-2.png
Mat-O-Wahl - Bild202 - Version 5-1.png
Mat-O-Wahl - Bild203 - Version 6-0.png

## Wer braucht das System?

Auf „kleiner“ Ebene - in den _Städten, Landkreisen oder Universitäten_ - wissen die Wähler\*innen oft nicht, wofür ihre Kandidat\*innen stehen (z. B. Umgehungsstraße oder Umweltschutz, sozialer Wohnungsbau, soziale Brennpunkte, neue KiTa, neue Schulden? Ja/Nein?). Ähnlich verhält es sich bei Landtags- und Bundestagswahlen, wenn man den Fokus auf ein spezielles Thema richten möchte (z. B. Wo stehen die Parteien im Bereich Verkehrswende, Inklusion oder Lärmschutz.).
Demgegenüber stehen _politikinteressierte Menschen / Vereine_, welche diese Informationen transparent darstellen wollen. Aber ihnen fehlt ein Werkzeug - wie ein Wahl-o-Mat - um viele Wahlberechtigte schnell, einfach und spielerisch zu informieren.
Der Mat-o-Wahl ist dieses Werkzeug und schließt damit die Lücke zwischen beiden Gruppen.

## Wie funktioniert es?

Der Mat-o-Wahl zeichnet sich durch seine _einfache Einrichtung_ aus. Es gibt eine _Konfigurations-Textdatei_ und zwei CSV-Textdateien mit den Fragen sowie den Antworten. Letztere können mit jeder _Tabellenkalkulation_ bearbeitet werden (z.B. MS Excel, OpenOffice / LibreOffice Calc, usw.)

VIDEO: Mat-o-Wahl - Video 501 – Konfiguration.mp4

Wer noch mehr Dinge anpassen möchte, kann aus einigen _Design-Vorlagen_ auswählen oder diese selbst anpassen.
Auch die Nutzer\*innen finden sich schnell innerhalb des Mat-o-Wahls zurecht. Die Auswahl-Buttons zum Zustimmen oder Ablehnen sind _selbsterklärend_ und die Ergebnisse werden _übersichtlich_ dargestellt.
BILD: Mat-O-Wahl - Bild501 – Ergebnisse.png

## Was wurde im Prototype Fund (PTF) gemacht?

Im PTF wurden einige neue Funktionen zum Mat-o-Wahl hinzugefügt.

### 1.) Neue Erweiterung: Anzeige der Partei-Antworten

In den älteren Versionen wurden am Ende alle Fragen wieder angezeigt. Darunter konnte man die jeweilige Antwort der Partei einblenden. Es fehlte aber eine Möglichkeit sich eine _einzelne Partei auszuwählen und nur ihre dazugehörigen Antworten anzuzeigen_.

Mat-O-Wahl - Bild61-01 - Version 5-1.png
Mat-O-Wahl - Bild61-02 - Version 6-0 Fragen.png
Mat-O-Wahl - Bild61-03 - Version 6-0 Parteien.png

### 2.) Verbesserte Erweiterung: Mehrere (gleichzeitige) Wahlen filtern

Es gibt Einsatzfälle, in denen man den Mat-o-Wahl mit den _gleichen Fragen für verschiedene „Wahlen_“ ausstatten möchte. Das könnte z. B. die gleichzeitige Wahl zum _Stadtrat und Bürgermeister\*in_ sein oder auch eine Wahl in _mehreren Stadteilen (Nord, Ost, Süd, West)_. In diesem Fall erhalten alle Kandidat\*innen die gleichen Fragen aber die Nutzer\*innen können in der Ergebnisübersicht filtern, wen sie sehen möchten.

Mat-O-Wahl - Bild62-01 - Alle Ergebnisse.png
Mat-O-Wahl - Bild62-02 – Buergermeister.png
Mat-O-Wahl - Bild62-03 – Suedfruechte.png
Mat-O-Wahl - Bild62-04 - Runde Fruechte.png

### 3.) Neue Erweiterung: Vorabfrage zur Lieblingspartei

Laut Wahl-o-Mat-Begleitforschung nutzen über die Hälfte der Teilnehmer\*innen das Werkzeug um ihren eigenen Standpunkt zu überprüfen. In diesem Arbeitspaket sollte deshalb eine _Vorabfrage_ erstellt werden, bei der die Nutzer ihre _„Lieblingspartei“ auswählen_. Diese Auswahl wird _am Ende wieder farblich hervorgehoben_. So sieht man, wie nah (oder auch weit) die eigene Präferenz von der Realität abweicht.

Mat-O-Wahl - Bild63-01 – Vorabfrage.png
Mat-O-Wahl - Bild63-02 – Ergebnisse.png

### 4.) Optische Verbesserungen

Im Zuge der anderen Punkte wurde auch Wert auf Verbesserungen in der Optik und _Nutzer\*innenfreundlichkeit_ gelegt. Dazu hat der Prototype Fund einige Coachings mit UX-Spezialist\*innen vermittelt. Dabei kam z. B. heraus, dass die bisherigen Auswahl-Buttons zu „unruhig“ waren und durch ihre Farben schon eine gewisse Vorauswahl provozieren.
Mat-O-Wahl - Bild64-01 - Version 5-1.png
Mat-O-Wahl - Bild64-02 - Version 6-0.png
Des Weiteren wurde unter der Haube an der _Barrierefreiheit_ geschraubt. Die Navigation mit der Tastatur und das Vorlesen mittels Screenreader sind wichtige Punkte um allen Menschen Zugang zu Informationen zu gewähren.

### 5.) Allgemeine Verbesserungen

Schließlich sind in Zusammenarbeit mit dem Projektpartner an einigen Stellen noch kleinere Bugs und Verbesserungsideen aufgefallen. So ist es nun auch möglich, den Mat-o-Wahl auf einer fremden (Partner)-Seite per iframe einzubinden, die Ergebnisse am Anfang zu begrenzen oder feinere Einstellungen zur Statistik-Datenbank zu definieren.

## Was ist sonst noch passiert?

Auf Basis des Mat-o-Wahl entstand vor einiger Zeit der „Mitwirk-O-Mat“ https://mitwirk-o-mat.de/ Dabei beantworten die Nutzer\*innen _Fragen zu ihren Interessen_ und bekommen anschließend diejenigen _Gruppen, Vereine und Initiativen vorgeschlagen_, mit denen sie die größte Übereinstimmung für ein mögliches _Ehrenamt_ haben. So finden (junge) Menschen ein passendes Engagement und die bestehenden Gruppen erhalten neue Mitglieder.

---

BILD: Mat-O-Wahl - Bild701 – Mitwirkomat.png

---

Im Juni 2021 gewann der „Mitwirk-O-Mat“ den _Preis in der Kategorie „Digitales Engagement“_ der Initiative „Digital für alle“ aus einer Auswahl von rund 300 Bewerber\*innen. [https://digitaltag.eu/presse/zwei-projekte-mit-preis-fuer-digitales-miteinander-ausgezeichnet](https://digitaltag.eu/presse/zwei-projekte-mit-preis-fuer-digitales-miteinander-ausgezeichnet) Die Jury lobte u. a. den „niedrigschwelligen Einstieg ins Ehrenamt“ und den „_intuitiven und unterhaltsamen Beitrag zur politischen Bildung_“.

---

BILD: Mat-O-Wahl - Bild702 - Preis fuer digitales Miteinander.png

---

Zu den Jury-Mitgliedern gehörten Vertreter\*innen von Medien, Start-Up-Firmen, des Bitkom e. V., Förderer von Barrierefreiheit, eine Staatssekretärin aus dem Bundesministerium für Familie, Senioren, Frauen und Jugend, Frau Julia Klöckner (Bundesministerin für Ernährung und Landwirtschaft) sowie weitere Vertreter\*innen.

## Wie geht es weiter?

Der Mat-o-Wahl ist _komplett einsatzbereit_ - aber nicht „fertig“.
Das heißt, dass _alle wichtigen Funktionen bereit stehen und auch funktionieren_. Es gibt aber immer wieder _neue Ideen_, was man hier und da noch verbessern und verändern kann. Das hat auch der PTF gezeigt, bei dem neue Wünsche zu Tage kamen. Diese werden nun Schritt für Schritt angegangen.

## Klingt gut. Kann ich helfen?

Ja, jederzeit gern.
Der Quelltext steht auf Github https://github.com/msteudtn/Mat-O-Wahl/ für alle frei verfügbar und ist gut dokumentiert. Der Mat-o-Wahl ist außerdem unter der Open-Source-Lizenz GPL lizenziert.
Wenn es dann noch Detailfragen gibt, können wir uns gern auf ein echtes oder ein virtuelles Bier zusammensetzen.
Viele Dank an das BMBF und DLR für die Unterstützung!
