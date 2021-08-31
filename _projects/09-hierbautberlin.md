---
layout: project
title: "Hier Baut Berlin"
image: /assets/images/project_images/hierbautberlin/header.jpg
authors:
  - author: Bodo Tasche
    link: https://bodo.tasche.me
brief: "Wir informieren Menschen über Bauvorhaben in ihrem Umfeld."
summary: "Mit HierBautBerlin bekommt jede*r genau die Informationen, die das direkte Lebensumfeld betreffen."
---

## Das Projekt

Hast du dich schon mal gewundert, wo plötzlich die Baustelle vor deinem Haus hergekommen ist? Und warum du nicht nach deiner Meinung gefragt wurdest? Was viele nicht wissen: Die Stadt Berlin betreibt diverse Webseiten, die jede\*n Bürger\*in über diese Veränderungen informieren sollen sowie ein Portal auf [mein.berlin.de](https://mein.berlin.de), um sich frühzeitig zu beteiligen. Leider sind diese interessanten Informationen auf zu vielen Seiten verteilt. Im Falle des Amtsblattes sogar in einem PDF, das nach einigen Wochen vom Server gelöscht wird.

![Ansicht der Webseite](/assets/images/project_images/hierbautberlin/screenshot_map.jpg)

[HierBautBerlin](https://hierbautberlin.de) behebt dies, indem alle Informationen auf einer Karte zusammengeführt werden. So ist es einfach möglich, einen Überblick über die Neuigkeiten im eigenen Umfeld zu bekommen.

Damit nichts mehr verpasst wird, bietet [HierBautBerlin](https://hierbautberlin.de) sogar eine E-Mail-Benachrichtigung an. Bei einem neuen Eintrag im eigenen Umfeld wirst du sofort informiert und bleibst so auf dem Laufenden.

![Ansicht eines Detail-Dialoges zur Bürgerbeteiligung Auerdreieck](/assets/images/project_images/hierbautberlin/screenshot_details.jpg)

## Die Umsetzung

Bei der Programmierung wurde schnell klar, dass es zwei Themengebiete gibt, die von besonderer Bedeutung sind: Das Auslesen von Informationen aus PDFs und die Suche nach Adressen in Fließtext. Ersteres konnte mit vorhandenen Bibliotheken und Tools gut abgedeckt werden. Für die Suche nach Adressen im Fließtext gab es leider keine gute Lösung. Glücklicherweise gab es aber mit OpenStreetMap eine Datenquelle, die ich als Basis für die Lösung des Problems nutzen konnte.

Die Anwendung wurde in Elixir geschrieben und so vorbereitet, dass weitere Städte und Datenquellen aufgenommen. Aktuell sind elf Datenquellen angebunden, weitere sind in Planung.

Der Code der Anwendung kann auf [GitHub](https://github.com/HierBautBerlin/website/) angesehen werden.

## Die Zukunft

Nach dem Ende der Förderung geht das Projekt jetzt in die nächste Phase über. Vom Prototyp zum Live-Betrieb.

In den nächsten Wochen werde ich versuchen, die Anwendung in Politik und Medien zu streuen, damit mehr Menschen von diesem Tool erfahren. Zusätzlich sind noch weitere Verbesserungen und neue Datenquellen geplant. Zum Beispiel eine API, damit die Daten auch in weitere Tools eingelesen werden können. Es gibt also noch viel zu tun.

Ich würde mich freuen, wenn Menschen Interesse haben, das System auch für ihre Stadt einsetzen zu wollen.

Ich bedanke mich beim Bundesministerium für Bildung und Forschung und dem Deutschen Zentrum für Luft- und Raumfahrt für die Möglichkeit, das Projekt umzusetzen.
