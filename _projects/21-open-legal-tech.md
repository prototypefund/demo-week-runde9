---
layout: project
title: "Open Legal Tech"
image: /assets/images/project_images/openlegaltech/header_small.jpg
authors:
  - author: Magdalena
    link:
brief: "Wir unterstützen Menschen in der Kommunikation mit Verwaltung und Behörden."
summary: "Die Software bietet die Möglichkeit, einfache Rechtsberatungsprozesse automatisierbar zu machen und online anzubieten."
---

# Automatisierte Rechtsberatung für gemeinnützige Organisationen

## Die Idee …

Kommunikation von Behörden mit Bürger\*innen orientiert sich regelmäßig an Erfordernissen der Verwaltungen, nicht aber an den Bürger\*innen selbst. Dies führt dazu, dass beispielsweise Bescheide von Arbeitsämtern oder Ordnungsämtern für die Betroffenen häufig unverständlich und ohne Jura-Studium kaum zu beantworten sind.

Idee ist es daher, einfache Rechtsberatungsprozesse automatisierbar zu machen und online anzubieten. Im kommerziellen Bereich gibt es bereits verschiedene Online-Anwendungen, die automatisiert rechtliche Dokumente für Betroffene erstellen. Beispiele sind automatisiert erstellte Einsprüche gegen Strafzettel für zu schnelles Fahren oder Entschädigungsforderungen gegenüber Fluggesellschaften, wenn der Flug ausgefallen ist. Die Rechtsberatung dieser einfachen Fälle erfolgt hier mithilfe eines Online-Fragebogens.

Im Rahmen des Projekts ‘Open Legal Tech’ habe ich nun prototypisch ein System entwickelt, mit dem genau solche automatisierten Online-Fragebögen zur Rechtsberatung erstellt werden können. Zielgruppe sind dabei gemeinnützige Initiativen wie z. B. Organisationen, die ehrenamtliche Beratungen von Geflüchteten durchführen, Sozialberatungen oder Verbraucherzentralen. Das System kann vor allem dann weiterhelfen, wenn Betroffene in den jeweiligen Bereichen oft gleichlautende standardisierte Briefe erhalten, auf die regelmäßig ähnliche Antworten erfolgen sollen.

## Recherche

Während meiner Recherche habe ich verschiedene gemeinnützige Organisationen, die Rechtsberatung anbieten, zu meiner Idee und zu möglichen praktischen Szenarien befragt. Während es in einigen Bereichen tatsächlich möglich erscheint, auf Basis eines Online-Fragebogens ein Dokument - z. B. eine Klage oder einen Widerspruch - zu erstellen, ist das in anderen Bereichen schwieriger. Hier war die Idee eher, das System - auch in mehreren Sprachen - zur Vorbereitung auf eine persönlich Rechtsberatung zu nutzen.

Aus der Recherche hat sich ergeben, dass für eine automatisierte Rechtsberatung in vielen Fällen folgenden Schritte durchlaufbar und konfigurierbar sein müssen:

1. Prüfen - kann der\*die Betroffene überhaupt rechtlich vorgehen?
2. Fallspezifische Informationen, wie Name oder Adresse, erfassen (optional)
3. Informationen aus Schritt 2 in ein Dokument überführen (optional)

Während für Schritt 1 und Schritt 2 Fragebögen konfiguriert werden können müssen, muss für Schritt 3 eine Dokumentvorlage mit Platzhaltern erstellt werden können. Die größte Herausforderung war es, für jeden der Schritte ein entsprechendes User Interface zu zu implementieren.

## Umsetzung und Features

### Anlegen von Fragebögen und Entscheidungsbäumen

Wenn es im ersten Schritt möglich sein soll, zu überprüfen, ob bestimmte Bedingungen erfüllt sind, muss es möglich sein Fragen anzulegen und je nach gegebener Antwort zu anderen Fragen springen zu können.

#### Fragen anlegen
<video autoplay loop muted playsinline>
  <source src="/assets/images/project_images/openlegaltech/create_questions.mp4" type="video/mp4">
</video>

#### Abbruchbedingungen festlegen
<video autoplay loop muted playsinline>
  <source src="/assets/images/project_images/openlegaltech/create_conditions.mp4" type="video/mp4">
</video>

#### Fragebogen anschauen
<video autoplay loop muted playsinline>
  <source src="/assets/images/project_images/openlegaltech/preview.mp4" type="video/mp4">
</video>

### Anlegen von Dokumenten mit Platzhaltern und Bedingungen

Wenn der Fragebogen erfolgreich durchlaufen wurde und Informationen zum konkreten Fall angegeben wurden, soll es möglich sein, ein Dokument zur Verfügung zu stellen. Je nach der jeweiligen Antwort im Fragebogen zuvor sollen Textbausteine eingefügt oder nicht eingefügt werden. Im Text selber muss es möglich sein, Platzhalter einzufügen, die dann mit der jeweiligen Antwort befüllt werden.

#### Template mit Platzhaltern für die Antwort anlegen
<video autoplay loop muted playsinline>
  <source src="/assets/images/project_images/openlegaltech/add_platzhalter.mp4" type="video/mp4">
</video>

#### Textblöcke nur bei bestimmten Antworten anzeigen
<video autoplay loop muted playsinline>
  <source src="/assets/images/project_images/openlegaltech/add_text_block_conditions.mp4" type="video/mp4">
</video>

#### Fragebogen mit Dokument als Resultat
<video autoplay loop muted playsinline>
  <source src="/assets/images/project_images/openlegaltech/preview_with_document.mp4" type="video/mp4">
</video>

## Ausblick und Links

Eine erste funktionsfähige Version der Software liegt vor und muss nun umfangreich getestet und im praktischen Einsatz erprobt werden. Als nächstes möchte ich gerne eine API bauen, über die man den Fragebogen durchgehen kann. Darüber hinaus würde ich es gerne ermöglichen, mehrsprachige Inhalte anzulegen.

Zur Projektseite geht es [hier](https://openlegaltech.github.io/).  
Der Quellcode liegt [hier](https://github.com/OpenLegalTech/django-legal-advice-builder).

## Dank

Dieses Projekt im Rahmen des Prototype Funds umzusetzen, hat großen Spaß gemacht. Ich habe viel über Gesetze, Entscheidungsbäume und rechtliche Dokumente gelernt!
Vielen Dank an das Bundesministerium für Bildung und Forschung für die Förderung sowie an das ganze Prototype Fund-Team für die Unterstützung!
