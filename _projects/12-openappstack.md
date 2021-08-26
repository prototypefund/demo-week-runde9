---
layout: project
title: "OpenAppStack"
image: /assets/images/project_images/openappstack/header.png
authors:
  - author: Varac
    link: https://www.varac.net
  - author: Mark
    link:
brief: "Mehr kollaborative Apps und Reichweite für OpenAppStack"
summary: "Wir ermöglichen Organisationen ihre Online-Applikationen dezentral zu hosten und sicher zur Verfügung zu stellen."
---

[OpenAppStack](https://openappstack.net/) (OAS) ist ein freies/Open-Source-Softwareprojekt, welches Nutzer\*innen ermöglicht, Online-Applikationen schnell und einfach in der eigenen Infrastruktur bereitzustellen und zu administrieren. Unser Ziel ist es, nicht-kommerzielle Alternativen zu den großen Online-Diensten für möglichst viele Nutzer\*innen zugänglich zu machen. OAS stellt zivilgesellschaftlichen Organisationen und Einzelpersonen alles bereit, was zur Organisation und Zusammenarbeit benötigt wird. Und das ohne Kompromisse bei den Themen Datensicherheit und Privatsphäre einzugehen.

Im Rahmen der 9. Förderrunde haben wir OAS um neue Applikationen und nützliche Funktionen erweitert. OAS ist nun noch flexibler, da wir die Installation und Pflege der Plattform vereinfacht haben und für mehr Menschen und Organisationen nutzbar, weil wir das System plattformunabhängiger gemacht haben.

## Vorgeschichte

Openappstack war wie viele andere freie Software-Projekte auch vom [politischen Kahlschlag bei Open Technology Fund](https://netzpolitik.org/2020/politischer-kahlschlag-trifft-open-technology-fund) unter der Trump-Administration betroffen, was einen abrupten Auszahlungs-Stopp im letzten Jahr zur Folge hatte.
Umso mehr freuten wir uns, dass der Prototype Fund uns mit der Förderung in der 9. Runde geholfen hat die Arbeit am Projekt fortzusetzen!

## Im Maschinenraum

Nach diesem erzwungenen spontanen Winterschlaf starteten wir mit Aktualisierungen (insbesondere der eingesetzten Software für automatische Updates, [flux](https://fluxcd.io/))
und dem Beheben vieler Fehler. Dazu sind wir tief in den _Maschinenraum_ eingestiegen und haben viele Kernkomponenten ausgetauscht und verbessert.

Das Erstellen eines Kubernets-Cluster als Grundlage für OAS und die eigentliche Installation ist nun getrennt, was den Vorteil hat, dass OAS nun auch auf bereits existierenden Clustern installiert werden kann.
Eine besondere Herausforderung bei der Entwicklung von komplexen Systemen/Plattformen ist - im Gegensatz zu einer einzelnen Applikation - der Aufwand des automatischen Testens aller Komponenten. Je mehr Komponenten dazukommen, desto länger dauert die Durchführung der automatisierten Tests (CI-Pipeline), die bei jeder Codeänderung ausgeführt werden. Wir haben uns viel Zeit genommen um diese Tests zu beschleunigen und stabiler zu machen. Letztlich konnten wir die Dauer eines vollen Test-Zyklus um ca. 5-10 Minuten reduzieren und uns viel Frustration durch die stabileren Tests ersparen.

Der Maschinenraum ist nun wieder voll in Schuss, was bedeutet, dass wir in jedem Entwicklungszyklus auch in Zukunft schneller sind und nachhaltig zur _Developer Happiness_ beitragen konnten.

![](/assets/images/project_images/openappstack/upload_75f68c346280fd9bcb3ca77d6d325961.png)
_So grün!_

## Neue Apps

Nachdem wir aus dem Maschinenraum wieder heraus waren, lag unser Fokus auf der Integration neuer Apps. Die Auswahl haben wir in mehreren Schritten vorgenommen.
Am wichtigsten war uns das Feedback von Organisationen, die Interesse an Openappstack haben. Zwei Umfragen halfen uns, die meistgewünschten Software-Kategorien zu finden.

Für die technische Evaluierung der Frage, welche App sich jeweils am besten in Openappstack integrieren lässt, mussten sie (neben anderen) folgende Anforderungen erfüllen:

- Unterstützung von Single-Sign-On mittels [OpenID Connect](https://de.wikipedia.org/wiki/OpenID_Connect)
- Aktive Entwicklung - idealerweise durch eine Community
- Gepflegte Code-Basis, aktuelle Container-images und helm charts
- Mobile Clients die die App z. B. auf dem Smartphone ergänzen
- ...

And the winners are:

![Calendar,Password,Wekan](/assets/images/project_images/openappstack/upload_ef82a297a3b7d947251a23af91bcddc4.png)

- [Nextcloud calendar](https://apps.nextcloud.com/apps/calendar), ein Online-Kalender mit vielen Features

![](/assets/images/project_images/openappstack/upload_feabdac1b670c92b874230960f851127.png)

- [Nextcloud passwords](https://apps.nextcloud.com/apps/passwords), eine kollaborative Passwort-Verwaltung für Gruppen

![](/assets/images/project_images/openappstack/upload_621c0e2f306ebb0a20ab56b749834739.png)

- [Wekan](https://wekan.github.io), ein freies Kanban-Board zur Aufgaben-Verwaltung und Arbeitsorganisation

![](/assets/images/project_images/openappstack/upload_9a0b07bf149316796852c7635d6f1de8.png)

Wir sind froh, dass wir damit die Zahl der in Openappstack integrierten kollaborativen Apps verdoppeln konnten!
Apps, deren Integration wir aus Zeitgründen nicht mehr geschafft haben, sind allerdings nicht vergessen und werden bald auch noch ihren Platz in OAS finden. Den Grundstein fuer eine Integration von [Jitsi-meet](https://jitsi.org/jitsi-meet/) haben wir z. B. schon gelegt.

## Single Sign-On

<video src="/assets/images/project_images/openappstack/admin-panel.mp4" autoplay controls muted loop width=800></video>
_Momentaner workflow zum Hinzufügen eines Users im Admin Panel_

<video src="/assets/images/project_images/openappstack/sso-tour.mp4" autoplay controls muted loop width=800></video>
_Single-Sign-On Tour mit allen 3 neuen Apps_

Auch an unserer Single Sign-On Lösung haben wir weitergearbeitet. Hinzugekommen sind ein self-service Feature, welches Nutzer\*innen erlaubt ihre Accounteinstellungen an einem Ort selber zu verwalten. Außerdem wurden eine “Password recovery”-Funktion und weitere nützliche Sicherheitsfeatures hinzugefügt.
Statt Nutzer\*innen einfach nur dazu zu zwingen, sehr lange und komplexe Passwörter zu verwenden, warnen wir nun unter anderem davor Passwörter zu nutzen, die in der Datenbank von [HaveIBeenPwned](https://haveibeenpwned.com/API/v3#PwnedPasswords) vorhanden sind. Wir erhoffen uns damit, Nutzer\*innen grundsätzlich zur Verwendung sicherer Passwörter anzuregen. Wir haben außerdem große Schritte in Richtung einer Authentifizierung über einen zweiten Faktor, z. B. SMS oder [Time-based One-Time Passwords](https://de.wikipedia.org/wiki/Time-based_One-time_Password_Algorithmus) gemacht.

Was uns an dem Fortschritt der letzten Monate im Bereich unserer SSO-Lösung besonders freut, ist dass wir einen großen Teil unseres eigenen Quellcodes reduzieren und vereinfachen konnten, indem wir das freie Open-Spource Projekt [Kratos](https://ory.sh/kratos) für elementare Teile des Loginprozesses nutzen. Zum einen gibt uns das eine Menge Sicherheit, da wir nun nicht mehr selbst Code zum Validieren und Verwalten von sensiblen Informationen schreiben und pflegen müssen. Zum anderen hoffen wir, durch Beiträge zum Upstream-Projekt auch indirekt anderen freien Projekten zu helfen.

## Das neue Admin-Panel

Das Admin-Panel von OAS wurde während der letzten Monate neu designed. Ein neues Backend ist in Arbeit, welches die Konfiguration von Applikationen einfacher machen soll. Leider sind wir nicht zur kompletten Umsetzung dieser Komponenten gekommen. Workflow, Wireframes und Mockups sind aber bereits umgesetzt.
In folgendem Video wollen wir euch das zukünftige Admin-Panel schon mal vorstellen. Hint: Name und Logo von OAS wurden ebenfalls erneuert. In der Zukunft heißen wir nicht mehr _OpenAppStack_ sondern **StackSpin**!

<video src="/assets/images/project_images/openappstack/frontend.mp4" autoplay controls muted loop width=800></video>

## Release

Wir haben zum Ende der Förderung ein neue Version veröffentlicht (siehe auch den englischen [Openappstack 0.7.0 release blogpost](https://openappstack.net/2021/08/23/Openappstack-0.7.0-release.html)).  Wie diese installiert werden kann, ist in der ebenfalls aktualisierten [Dokumentation](https://docs.openappstack.net/en/v0.7) beschrieben.
Leider haben es nicht alle Features in dieses Release geschafft. Die Single Sign-On Änderungen und das neue Admin-Panel werden ins nächste Release einfliessen.

## Fazit und Ausblick

Die anfängliche Arbeit am Kern von Openappstack hat uns etwas länger als geplant beschäftigt. Wir sind jedoch froh, dass wir uns diese Zeit am Anfang der Förderzeit genommen haben.
Die Zusammenarbeit mit anderen Teams an einer gemeinsamen Code-Basis und Upstream-Projekten brachte außerdem eigene Herausforderungen mit sich, da wir uns bezüglich den gemeinsamen Entwicklungsschritten bestmöglich abstimmen mussten. Wir sind aber dennoch glücklich, dass wir durch die Zusammenarbeit mit anderen Projekten und Teams Teil eines wachsenden Ökosystems sind, zu dem wir mit unseren Fortschritten in vielerlei Hinsicht beitragen konnten.

Alles in allem sind wir sehr zufrieden mit dem, was wir in der begrenzten Zeit umsetzen konnten.

[Greenhost](https://greenhost.net/) als Haupt-Maintainer des Projektes plant, Openappstack Anfang 2022 im Produktivbetrieb einzusetzen - nicht nur intern sondern auch als Service, der ihren Kund\*innen angeboten wird. Damit ist der Grundstein für eine nachhaltige Weiterentwicklung gelegt und wir hoffen, dass sich Openappstack in naher Zukunft zu einem großen Teil selbst finanzieren wird.

In ein paar Wochen wird ein **Beta-Test** stattfinden, an dem interessierte
Organisationen teilnehmen können. Wir stellen euch dann einen Openappstack
cluster zur Verfügung und ihr könnt OAS testen und uns Feedback geben.
Bitte schreib uns eine Email (siehe [Kontakt](#Kontakt)) wenn ihr daran Interesse habt.

Wir sind froh einen Teil dazu beigetragen zu haben und blicken mit freudiger Erwartung auf den Launch!

## Kontakt

Wer mit uns oder dem Openappstack Projekt in Kontakt bleiben möchte: Auf der [Openappstack contact](https://openappstack.net/contact.html) Seite
findet ihr unsere **Email Adresse**, unseren öffentlichen **Matrix Chat** und wie ihr
euch in unseren **Newsletter** eintragen könnt.
Ihr könnt uns auch gerne direkt kontaktieren:

* [Kontakt Varac](https://www.varac.net/contact)

## Danke!

Danke dem Team des Prototype Funds für die tolle Rundum-Betreuung, dem DLR für die reibungslose Organisation und Abrechnung (was bei so vielen Projekten bestimmt nicht immer einfach war). Unser Dank gilt ebenso dem BMBF für die Förderung von freien Software Projekten, Greenhost und vor allem den Rest des Openappstack-Teams für die gute Zusammenarbeit !
