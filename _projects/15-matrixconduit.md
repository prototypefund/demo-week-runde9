---
layout: project
title: "MatrixConduit"
image: /assets/images/project_images/matrixconduit/header.png
authors:
  - author: Timo Kösters
    link:
brief: "Wir bieten einen sicheren und offenen Chatserver."
summary: "Conduit ist ein neuer Server für das Matrix Netzwerk, um unabhängig von großen Unternehmen Nachrichten sicher senden zu können."
---

## Worum geht es?

WhatsApp, Facebook Messenger, iMessage - das sind ein paar der meist genutzten Chat-Programme in Deutschland. Das muss aber nicht heißen, dass sie das sein sollten. Jedes dieser Programme wird von einem riesigen Unternehmen entwickelt mit dem Ziel, möglichst viel Profit zu machen. Es ist also kein Wunder, dass sie [Sicherheit und Datenschutz ignorieren, um Daten an Werbeunternehmen zu verkaufen](https://www.tagesschau.de/wirtschaft/verbraucher/whatsapp-messenger-facebook-datenschutz-101.html). Auch wenn bei Programmen wie Signal ein besserer Umgang mit Daten versprochen wird, werden Daten trotzdem zentralisiert in den USA gespeichert.

Gibt es ein Chat-Programm, bei dem die Daten nur dahin gelangen, wo sie ankommen sollen? **Matrix** ist genau das und noch viel mehr.

Matrix ist nicht nur ein Programm, sondern ein ganzes Netzwerk, welches für alle offen ist. Es gibt keinen offiziellen, zentralen Ort an dem alle Daten gespeichert werden, sondern tausende kleinere Server, die miteinander reden können.

Zudem hat Matrix alle Eigenschaften, die man von einem modernen Messenger erwartet, wie zum Beispiel Ende-zu-Ende-Verschlüsselung: Selbst Besitzer\*innen von Servern können Nachrichten von anderen Nutzer\*innen nicht lesen.

## Warum gibt es Conduit?

Bei Matrix kann sich jede\*r einen eigenen Server aufbauen und diesen nutzen, um mit anderen Nutzenden im Matrix-Netzwerk zu kommunizieren. Wenn man sich aber genauer mit Matrix befasst, erkennt man, dass viele Nutzer\*innen diesen Vorteil von Matrix nicht ausnutzen. Stattdessen sammeln sich alle Nutzer\*innen auf wenigen großen Servern. Also werden die Daten doch wieder zentralisiert. Das liegt daran, dass es sehr aufwendig und teuer sein kann, einen eigenen Matrix-Server zu betreiben. Denn das Matrix-Server-Programm “Synapse”, welches normalerweise verwendet wird, war ursprünglich nur als Experiment gedacht und es wurde nicht viel Wert auf Optimierung gelegt.

Das MatrixConduit-Projekt, welches im Rahmen des Prototype Fund weiterentwickelt wurde, ist eine Alternative zu Synapse, die effizienter für kleinere Server ist.

Conduit wird in der Programmiersprache Rust entwickelt, welche für Performance und Zuverlässigkeit bekannt ist.

Außerdem wurde Conduit kompakt als ein einziger Prozess mit eingebetteter Datenbank entwickelt, sodass viele Latenzen entfallen, die bei einem verteilten System nötig wären. Das bedeutet zwar, dass Conduit nicht für riesige Server geeignet ist. Doch dies verstärkt für Nutzer\*innen den Anreiz, einen eigenen Server zu hosten.

## Wie weit ist das Projekt gekommen?

Dank der Förderung durch den Prototype Fund konnte ich fast alle notwendigen Features für Conduit implementieren.

Eines der wichtigsten Aufgaben war es, Nachrichten an andere Server weiterzuleiten und von anderen zu empfangen. Dies wirkt auf den ersten Blick einfach, aber ein dezentrales Netzwerk wie Matrix muss sehr vorsichtig mit Daten von anderen Servern umgehen.

Nehmen wir an, es gibt drei Server: A, B und C. Server A möchte Verwirrung stiften und teilt Server B mit, dass eine Person gebannt wurde. Gleichzeitig sagt er zu Server C diese Person habe nur seinen Namen geändert. Damit dies nicht zu einem Konflikt führt, gibt es in Matrix einen komplizierten Algorithmus namens “State Resolution”. Wenn Server B und C miteinander sprechen, bemerken sie, dass es einen Konflikt gibt. Nun werden alle "Versionen" des Raums genommen und nach festen, deterministischen Regeln zu einer "korrekten" Version zusammengeführt. So werden sich alle Server bald einig, dass die Person gebannt wurde.

Viel Zeit wurde verwendet, um diesen Algorithmus in Conduit zu implementieren und alle Fehler zu beseitigen. Dazu wurden viele andere notwendige Funktionen implementiert und sowohl Speichernutzung als auch CPU-Belastung stark optimiert.

Conduit ist nun in der Beta-Phase. Man kann das Programm schon als Synapse-Ersatz verwenden, aber es gibt noch kleine Probleme, sodass es noch nicht für jede\*n geeignet ist.

## Persönliche Erfahrungen in der Open-Source-Community

Conduit ist ein Open-Source-Projekt mit einer aktiven Community. Ich bin sehr dankbar dafür, dass eine Rust-Bibliothek für Matrix namens Ruma entwickelt und aktiv auf meine Anfragen hin verbessert wurde. Ruma ist eine wichtige Grundlage für Conduit.

Während der Großteil der Implementierung von mir erstellt wurde, halfen mir einige Personen freiwillig bei kleineren Problemen. Der erste Code für die “State Resolution” wurde von einem Contributor geschrieben und mehrere arbeiteten an der Dokumentation oder bei automatischen Tests.

Hier ist mir aber auch klar geworden, dass das nicht immer so hilfreich ist, wie es klingt. Es dauert sehr lange, den Code einer anderen Person zu lesen, zu verstehen und zu bewerten. Es ist nicht leicht, Fehler zu entdecken, aber diese immer freundlich mitzuteilen, ist manchmal schwer.

Oft stand ich vor der Entscheidung, ob ich selber die nötigen Änderungen vornehmen sollte, damit ich schneller voran komme, oder ob ich der anderen Person die Fehler und Lösungsvorschläge ausführlich erklären sollte, damit diese Person lernt und hoffentlich noch öfter hilft.

Dennoch ist die Open-Source-Community der Grund, warum mir das Arbeiten an Conduit weiterhin so viel Spaß macht wie am Anfang. Interessante Diskussionen und positive Rückmeldungen zu neuen Entwicklungen haben mich sehr motiviert.

---

Ich bedanke mich sehr beim Prototype Fund, dem Deutschen Zentrum für Luft-und Raumfahrt (DLR) sowie dem BMBF dafür, dass sie dieses Projekt ausgewählt und die Finanzierung ermöglicht haben.
