---
layout: project
title: "HubGrep"
image: /assets/images/project_images/hubgrep/9y5NRb5.png
authors:
  - author: Jan Hartmann
    link:
  - author: Henrik Eliasson
    link:
brief: "Wir sind eine Suchmaschine für Open Source Code."
summary: "HubGrep erstellt einen Index verschiedener Hosting Services, um eine Suchmaschine zur Verfügung zu stellen."
---

# HubGrep im Prototype Fund

## Open-Source-Projekte finden

Sucht man etwas in der Open-Source-Welt, bekommt man schnell den Eindruck, dass alle Wege zu GitHub führen - eine Plattform, die Microsoft gehört.

Als Softwareentwickler\*:in benutzt du wahrscheinlich die default Suchmaschine deines Browsers, um nach Software und Libraries zu suchen und hoffst, dass etwas passendes möglichst weit oben in den Suchergebnissen ist - und wenn nicht, scrollst du durch nicht-so-ganz passende Stackoverflow-Posts (oder merkwürdige Kopien davon) und Links zu alten Posts in alten Foren.

Vermeiden könntest du das, indem du direkt auf einer Code-Hosting-Platform suchst, aber du weißt schon vorher, dass du dort nichts findest, das woanders gehostet wird - und es gibt nicht nur die großen Sourcecode-Hoster sondern auch eine unüberschaubare Zahl Hoster für einzelne Projekte und kleine Communities.

Ein weiteres Problem einiger Hoster ist die Intransparenz bei der Suche: Nach welchen Kriterien werden die Ergebnisse sortiert und in den Suchergebnissen gelistet? Für die Plattformen, die selbst keine Open-Source-Software sind, ist nicht klar, ob die Ergebnisse auf irgendeine Art "maßgeschneidert" sind oder ob jemand bezahlt hat, um in den Ergebnissen weiter oben zu sein. Idealerweise solltest du die Ergebnisse bekommen, nach denen du fragst - ohne dass externe Interessen einfließen.

Es gibt also einiges zu verbessern.

## Wir stellen vor: HubGrep!

![Search with HubGrep](/assets/images/project_images/hubgrep/d0yy3ih.gif)

Mit [HubGrep](https://hubgrep.io/) bauen wir eine Suchmaschine, die ihren Fokus auf Open-Source-Projekte legt und die Ergebnisse verschiedener Hoster kombiniert - ohne dass die Größe oder Bekanntheit des Hosters Einfluss auf das Ranking hat.

Natürlich kennen wir nicht "alle" Code-Hosting-Plattformen. Aber solltest du eine vermissen, [kannst du sie selbst hinzufügen](https://hubgrep.io/add_instance/step_1) und im nächsten Update des Suchindex ist sie dann enthalten.

Zusätzlich zu deinem Suchbegriff kannst du deine Ergebnisse über verschiedene Filter weiter einschränken. Vielleicht ist es wichtig für dich, wann ein Projekt das letzte Update bekommen hat oder in welcher Sprache es geschrieben wurde? Wir wollen dir die Ergebnisse geben, nach denen du fragst und nicht die, die deinem "Profil" entsprechen: Das einzige, was wir (eventuell irgendwann) speichern, ist ein Settings Cookie, um deine Filtereinstellungen zu behalten.

## Ein Klick weniger im Workflow

Erst zu einer anderen Website gehen zu müssen, anstatt die Standard-Suchmaschine zu nutzen, ist ein Schritt, den viele ungern zusätzlich gehen - und Routinen sind nicht einfach zu ändern. (Und wir Entwickler\*innen sind schließlich von Berufswegen her faul.)

Zum Glück haben die meisten Browser eine Funktion, neue Suchmaschinen mit einem bestimmten Keyword zu verknüpfen.

![search with a keyword](/assets/images/project_images/hubgrep/oKDGzB5.gif)

Zum Beispiel kannst du im Browser ein Keyword `h` mit der Url `https://hubgrep.io/` verknüpfen. Wenn du dann `h software dingsbums` aufrufst, wirst du direkt zu deinen Suchergebnissen auf hubgrep.io gebracht. Den Schritt, erst auf die Website zu gehen, sparst du also.

Da das jede\*r für sich selbst einrichten muss und es für alle Browser unterschiedlich funktioniert, kannst du für einige gänginge Browser in unserer [Dokumentation](https://docs.hubgrep.io/en/latest/docs/hubgrep_search/usage/add_to_browser.html) nachlesen, wie das genau geht.

## Der Weg zum Prototyp

Vielleicht interessiert dich, wie wir HubGrep gebaut haben. Unser erster Ansatz war relativ einfach und naiv: Wir haben eine Website mit einem Suchfeld gebaut, die Suchanfragen an Services, die wir kennen, weiterleitet. Wird eine Suche abgeschickt, sammeln wir alle Ergebnisse, ordnen jedem Resultat einen bestimmten Score zu und stellen die sortierte Liste als Suchergebnis dar.

Auf diese Art hatten wir relativ schnell einen ersten Prototyp, und es hat sich sofort wie ein sinnvolles Projekt angefühlt. Aber nur einen "Proxy"-Service zu haben hat einige Nachteile:

- Die Suchergebnisse können erst dargestellt werden, wenn der langsamste Hoster geantwortet hat, und je mehr Hoster man hinzufügt, desto unzuverlässiger und langsamer wird alles.
- Man muss den Hostern immer noch vertrauen, die "guten" Suchergebnisse zuerst zu liefern, da man jeweils nur "die erste Seite" der Suchergebnisse angezeigt bekommt (oder wahlweise noch länger warten muss).
- Die Hoster brauchen eine Suchfunktion in ihrer API.
- Die Ergebnisse müssen immer noch gewichtet und sortiert werden, obwohl die individuellen Ergebnisse der Services schon sortiert sind.

Wenn du ausprobieren möchtest, wie sich so eine Suchmaschine anfühlt, kannst du das [hier](https://meta.hubgrep.io/) tun.

Um von den besagten Problemen weg zu kommen, war unser nächster logischer Schritt, einen eigenen Suchindex aufzubauen. Wir haben [Crawler](https://github.com/HubGrep/hubgrep_crawlers) geschrieben, die zu jedem Projekt auf den Hosting Services Metadaten sammeln. Diese wiederum schicken die Daten an einen [Indexer](https://github.com/HubGrep/hubgrep_indexer), der sie speichert, so weit vereinheitlicht, dass sie vergleichbar sind, und in eine Form bringt, aus der wir später den Suchindex erstellen können. Bisher unterstützen der Indexer und die Crawler Projekte von GitHub, GitLab und Gitea.

Es gibt natürlich [noch viel mehr Hosting -Plattformen](<https://en.wikipedia.org/wiki/Forge_(software)>), aber zuverlässige Crawler zu schreiben ist recht aufwändig - vielleicht hilft ja irgendwann die ein oder andere Nutzer\*in.

Ein schöner Nebeneffekt dieser Sammlerei: Wir stellen auch die [unverarbeiteten Rohdaten](https://indexer.hubgrep.io/) zum Download zur Verfügung! Wenn du eine schöne Idee für ein Projekt hast, Datenvisualisierungen machen, oder einfach ein bisschen "drin rumstochern" möchtest: feel free!

Der in HubGrep verwendete Suchindex basiert auf den vereinheitlichten Daten; die Datengrundlage jedes Hosters ist in unserer [Exportübersicht entsprechend verlinkt](https://hubgrep.io/hosters).

## Wo es hingehen könnte

Wir haben nun eine funktionierende Suchmaschine - aber vielleicht ist das erst der Anfang.

Da wir gerade erst angefangen haben, unser eigenes Such-Backend zu nutzen, liegt unsere Priorität auf dem Verbessern der Gewichtung und dem Sortieren der Ergebnisse.
Eine andere naheliegende Erweiterung wäre, mehr Hosting-Services zu durchsuchen - beispielsweise Bitbucket.

Einige APIs stellen mehr Informationen bereit als andere, deshalb kennen wir beispielsweise die Lizenz oder Programmiersprache nicht von allen Projekten. Die Aufgabe, alle Projekte zu klonen, zu analysieren, und um die fehlenden Metadaten zu erweitern wäre eine ressourcen- und zeitintensive Aufgabe, aber wir haben eine Datenbasis, auf der wir aufbauen könnten. Mit den geklonten Projekten hätten wir dann, über die API Metadaten hinaus, auch alle Commit IDs und könnten über alle Hoster hinweg Forks und Mirrors von Projekten erkennen, und in den Ergebnissen gruppieren.

Alles in allem sind wir an einem guten Ausgangspunkt, HubGrep größeren Mehrwert zu geben, als "nur" Daten aus APIs zu indexen, und "nur" eine Suchmaschine zu sein.
Es könnte eine Landkarte der Open Source Welt sein.

Wir danken dem DLR, dem BMBF und dem Prototype Fund für das Vertrauen und die Unterstützung während der letzten sechs Monate!
