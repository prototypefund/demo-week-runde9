---
layout: project
title: "Quba-Viewer"
image: /assets/images/project_images/quba-viewer/header.png
authors:
  - author:
    link:
brief: "Wir vereinfachen die Prüfung von e-Rechnungen."
summary: "Der Quba-Viewer ist eine Anwendung, um strukturierte e-Rechnungen bildhaft darstellen und ausdrucken zu können."
---

# Elektronische Rechnungen gewinnen an Bedeutung

Sie werden erstens immer wichtiger und zweitens immer strukturierter.

Erstens: Beispielsweise nehmen Behörden seit November 2020 keine Papierrechnungen mehr entgegen, es müssen elektronische Rechnungen sein ([Details](https://www.mustangproject.org/einvoices/?lang=de&pk_campaign=qpr10&pk_source=prototype#European)).

Zweitens nimmt die maschinenlesbare Bedeutung innerhalb der Rechnungen zu: Normale PDF-Dateien, die wie andere Dokumente praktisch nur menschenlesbar sind, werden zunehmend durch maschinenlesbare, "strukturierte" XML-Dateien entweder komplett ersetzt oder ergänzt ([mehr Info zu hybriden Formaten](https://www.mustangproject.org/zugferd/?lang=de&pk_campaign=qpr10&pk_source=prototype)).

## Strukturierung

Vorteil von XML-Rechnungen sind beispielsweise die Möglichkeit, automatisch nachzurechnen oder ganze Dateien zu bezahlen: Bei der Zahlung entfällt das typische “Copy & Paste” des Betrags, des Fälligkeitsdatums, der Bankverbindung, des/der Empfänger\*in und des Verwendungszwecks. Moderne Onlinebankingsoftware wie beispielsweise [Hibiscus](https://www.willuhn.de/products/hibiscus/) hat einen Knopf um alle zahlungsrelevanten Daten anzuzeigen und für die Zahlung freizugeben.

Die Phase der bloßen <em>Digitalisierung</em> der Rechnungen wird allmählich abgelöst durch eine Phase der <em>Strukturierung</em> der Daten.

Reine XML-Daten kann aber wiederum kein Mensch prüfen.
![XML-Quelltext einer E-Rechnung](/assets/images/project_images/quba-viewer/screenshot2.png "XML-Quelltext einer E-Rechnung")

Und leider versteht auch noch nicht jede Buchhaltungssoftware jedes XML-Format. Daher machen hybride Formate Sinn und übergangsweise werden Anzeigeprogramme gebraucht, die aus den maschinenlesbaren XML-Daten wieder menschenlesbare und anzeigbare Rechnungen machen.

## Quba

Unseren E-Rechnungsviewer lädt man sie sich für Windows, Linux oder Mac [herunter](http://quba-viewer.org/?pk_campaign=qpr10&pk_source=prototype): Quba ist komplett offlinefähig, die Rechnungen müssen den heimischen Rechner nie verlassen.
Nach der Installation kann man UN/CEFACT CII oder UBL-Dateien (beides XML) oder PDF über Datei|Öffnen anzeigen - hat man gerade keine zur Hand, kann man sich [Beispiele herunterladen](https://quba-viewer.org/beispiele/?pk_campaign=qpr10&pk_source=prototype).

Der Ablauf, wie Beispiele heruntergeladen und angezeigt werden können, sieht dann so aus:

![Screenshot von Quba mit einer geöffneten hybriden Rechnung](/assets/images/project_images/quba-viewer/header.png/Quba.gif "Screenshot von Quba mit einer geöffneten hybriden Rechnung")

Die Anzeige erfolgt in den Tabs für die allgemeinen Rechnungsdaten, Rechnungsdetails und Positionsdaten.

Enthalten die PDF-Dateien strukturierte Rechnungsinformationen, erscheint neben dem PDF ein Knopf um auf Wunsch zusätzlich das eingebettete XML zu visualisieren.
![Screenshot von Quba mit einer geöffneten hybriden Rechnung](/assets/images/project_images/quba-viewer/screenshot2.png "Screenshot von Quba mit einer geöffneten hybriden Rechnung")

## Ausblick

Danke für die Initialzündung an den [Prototype Fund](https://prototypefund.de/), an das BMBF und das DLR, an Dominique für die Übersetzungen und [an so viele weitere](https://quba-viewer.org/p/thank-you/?pk_campaign=qpr10&pk_source=prototype) für das ganze Open-Source Ökosystem.
Es geht auf jeden Fall weiter. Wie vom [Schwesterprojekt](http://mustangproject.org?pk_campaign=qpr10&pk_source=prototype) gewohnt arbeiten wir an einigen Sachen ohnehin unbezahlt, bei einigen weiteren Punkten können wir ansetzen, wenn konkreter Bedarf signalisiert wird. Beispielsweise haben wir an einem Wochenende ein Feature angedeutet, das Rechnungen automatisch nachrechnet. Und obwohl das eigentlich nie nötig sein sollte (Rechnungen werden generell nie „korrigiert“ sondern zurückgewiesen) haben wir für eine konkrete Anfrage kurz angedeutet, dass und wie man Rechnungsattribute in der Benutzeroberfläche ändern und ins XML zurückschreiben könnte.

Unser Beitrag zur Open-Source-E-Rechnungsthematik ist abgesehen von der eigentlichen Elektron-Anwendung der Ansatz, eben auch Factur-X/ZUGFeRD zu unterstützen. Die Visualisierung haben wir ja schon um das erste Attribut (Skonto) aus Factur-X/ZUGFeRD Extended ergänzt - es wird interessant, ob noch weitere Attribute folgen.

Ziemlich sicher ergänzen wir die Visualisierung und unsere Anwendung auch noch um eine englische und französische Übersetzung. Um eine noch zu veröffentlichende Version 1.1 kommen wir also gar nicht umhin.
