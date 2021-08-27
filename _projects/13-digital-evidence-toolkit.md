---
layout: project
title: "Digital Evidence Preservation Toolkit"
image: /assets/images/project_images/digital-evidence-toolkit/header.png
authors:
  - author: Basile Simon
    link: https://basilesimon.fr
brief: "Wir unterstützen und erleichtern die digitale Beweisführung."
summary: "Ein Proof-of-Concept für Forscher*innen und kleine Teams, die Online-Materialien durchsuchen."
---

# Digital Evidence Preservation Toolkit

Ein Archivierungs- und Annotations-Tool, das die Beweismittelkette (Chain of Custody) bei internationalen Strafverfolgungen demonstriert.

---

Das DEPToolkit ist eine Proof-of-Concept-Software für Forscher\*innen und kleine Teams, die Online-Material durchsuchen.

Mit nur einem Mausklick wird ein Rahmen geschaffen, in dem das Material in einer Beweismittelkette archiviert und dauerhaft aufbewahrt werden kann (Chain of Custody Framework). Nach der Aufnahme in die wachsende Datenbank können die Nutzer\*innen zurückgehen, um das Material zu durchsuchen und zu kommentieren sowie Arbeitsexemplare dieses Materials zur Veröffentlichung und Verbreitung exportieren.

Eine so aufgebaute Datenbank kann selbst zehn Jahre später einer Staatsanwaltschaft übergeben werden, die mit mathematischer Sicherheit sagen kann: „Das Material in diesem Archiv ist zeitgenössisch korrekt und identisch mit dem, was damals vor zehn Jahren gespeichert wurde.“

## Problemdefinition

Was wäre, wenn digitale Beweise, die über einen Zeitraum von Jahren oder sogar Jahrzehnten gesammelt wurden, vor Gericht nicht zulässig wären, weil sie von Einzelpersonen, wenn auch mit den besten Absichten, unsachgemäß behandelt wurden? Mangels international anerkannter Rechtsnormen zur Erfassung, Handhabung und Archivierung digitaler Beweismittel sind künftige Strafverfolgungsbemühungen weiterhin gefährdet.

Als Journalist habe ich aus erster Hand gesehen, wie einige dieser Beweise von Rechtsabteilungen beurteilt und freigegeben werden. Als Mitbegründer von Airwars, einer NGO, die militärische Maßnahmen beobachtet und dokumentiert, habe ich selbst erfahren, welche Schritte wir unternommen haben, um sicherzustellen, dass unser Material nicht verschwindet. Und wenn mein Jurastudium mich nicht trügt, bleiben beide Erfahrungen hinter dem zurück, was die Gerichte an Beweismaßstäben fordern.

---

## Das Toolkit

Wir wollen, dass das Toolkit der plastikversiegelte Beutel ist, in dem Beweise aufbewahrt werden und der dann in einem Beweisraum überwacht wird, in dem jeder Zugriff verfolgt und in einem Protokoll festgehalten wird.

Unser Toolkit macht mehrere Dinge:

### Ein Klick zum Aufbewahren:

Das Toolkit bietet ein Ein-Klick-Recherche-Tool, das digitale Beweise über den Webbrowser speichert. Die Ein-Knopf-Browsererweiterung liefert Inhalte an den selbst gehosteten Mikrodienst. Das heißt: Kein Warten, kein aufwendiges Rumklicken, sondern mehr Zeit für die Recherche.

![](/assets/images/project_images/digital-evidence-toolkit/1.png)

### Zukunftssichere Archive und Echtheitsnachweis:

Das Toolkit bewahrt eine Kopie des Materials sowie den Nachweis für seine Authentizität auf. Es werden zukunftssichere Offline-Kopien erstellt und ihre digitalen Signaturen sofort einem unveränderlichen Remote-Ledger hinzugefügt. Das gesamte Material wird durch SHA256, einen Kryptographiestandard der US-Bundesregierung, identifiziert.

![](/assets/images/project_images/digital-evidence-toolkit/2.png)

### Ihr Archiv gehört Ihnen – Zum Durchsuchen, Kommentieren, Exportieren:

Das Toolkit erleichtert das Durchsuchen des erstellten Archivs, seine Annotation und Metadatenanreicherung sowie den Export von Arbeitskopien. Alle Zugriffe und Ergänzungen werden dem unveränderlichen Protokoll hinzugefügt, damit erfasst und können nach Belieben wiedergegeben werden.

![](/assets/images/project_images/digital-evidence-toolkit/3.png)

### Umgekehrte Verifizierung der Sicherung (Lookup and Prove)

Das Toolkit bietet einen „Lookup-and-Prove“-Mechanismus, der die ordnungsgemäße Sicherungskette des Materials demonstriert, für den Fall, dass ein Dokumentensatz mit den Beweismechanismen des Toolkits abgeglichen werden muss.

![](/assets/images/project_images/digital-evidence-toolkit/4.png)

---

## Nutzen

Unsere Herausforderung mit dem Toolkit besteht darin, ein Beweisstück von dem Moment an zu sichern, in dem es uns erreicht. Wir haben es mit nachträglichen Recherchen zu tun, im Gegensatz zu denen, die direkt aus dem Feld kommen, wie es beispielsweise [EyeWitness] (https://www.eyewitness.global) vorschlägt, ein Leuchtturmprojekt, bei dem Prozesse von von der Kamera direkt zum Gerichtssaal übertragen werden sollen.

Wie oben bereits ausgeführt:

„**\*Das Toolkit befasst sich nur mit der Provenienz und der Beweismittelkette ab dem Zeitpunkt der Aufzeichnung.** Die gespeicherten Inhalte können natürlich nicht authentisch, manipuliert oder gefälscht sein – aber mit dem Toolkit werden sie angemessen gesichert.“\*

Dies hat verschiedene Auswirkungen auf die Metadaten:

- Zusätzlich zur **zukunftssicheren Archivierung von Webseiten und Screenshots** erfassen wir **einige Metadaten** über die Seiten und befragen Nutzer\*innen nach ihren potenziellen Bedürfnissen über das Offensichtliche hinaus (Google Analytics Tracking Codes, DNS-Einträge usw.).
- Diese Metadaten bleiben erhalten und ihre eindeutigen Signaturen werden in dem von uns verwendeten **unveränderlichen Hauptbuch** notariell beglaubigt. Das bedeutet, dass - abgesehen von einer vollständigen Löschung - keine Verluste oder Änderungen möglich sind, sobald etwas in die Datenbank aufgenommen wurde. Nochmals: Wir sprechen nur von der Beweismittelkette _ab dem Moment der Aufzeichnung_.
- Das zentralisierte, von Amazon Web Services betriebene Ledger bietet eine hybride Methode der [Trusted Timestamping](https://en.wikipedia.org/wiki/Trusted_timestamping) gemäß[ANSI ASC X9.95](https://en.wikipedia.org/wiki/ANSI_ASC_X9.95_Standard) und [ISO/IEC 18014](http://en.wikipedia.org/wiki/ISO/IEC_18014): Jede Einfügung und Überarbeitung des Ledgers hat einen Zeitstempel, _gestempelt_ von Amazon. Es ist ein sehr wünschenswertes Feature, kein Bug.

**Wir sind nun in der Lage, die ordnungsgemäße Verwahrung einer archivierten Webseite zu einem bestimmten Zeitpunkt nachzuweisen, der nicht gefälscht werden konnte.**

---

## Wie es weitergeht

Wir arbeiten an einer Reihe von Partnerschaften, die darauf abzielen, einige unserer Annahmen zu bestätigen.

Aus ersten Nutzer\*innen-Interviews und Kontakten mit Praktiker\*innen arbeiten wir nun an zwei parallelen Wegen: Der Zusammenarbeit an kollektiven Datensätzen/Fällen und der Interoperabilität mit anderen Dokumentenmanagementsystemen.

Wir werden Pro-Bono-Kanzleien und schutzbedürftigen Gruppen unterstützen, einschließlich einzelner Opfer, die ihre Probleme selbst dokumentieren.

---

Wir bedanken uns beim Bundesministerium für Bildung und Forschung für die Förderung und beim Deutschen Zentrum für Luft- und Raumfahrt für die Unterstützung in der Förderzeit.

## Nützliche Links

- [Newsletter](https://digitalevidencetoolkit.substack.com/)
- [Getting started](https://digitalevidencetoolkit.notion.site/Getting-started-15521f4125534f4aa758a2575c27ad5c) and [technical documentation](https://digitalevidencetoolkit.notion.site/Technical-Journal-01ad0720aebc4f9c9a8036da0fd7426b)
- [Addressing the criteria of the Berkeley Protocol](https://digitalevidencetoolkit.notion.site/Back-to-Berkeley-c06f02ededfa41dc8605689d018ca3a4)
- [Releases and changelog](https://github.com/digitalevidencetoolkit/deptoolkit/releases)
- [Roadmap board](https://github.com/orgs/digitalevidencetoolkit/projects/3)
