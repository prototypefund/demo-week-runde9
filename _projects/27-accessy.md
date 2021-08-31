---
layout: project
title: "Accessy"
image: /assets/images/project_images/accessy/header.png
authors:
  - author: Michael Helmbrecht
    link:
brief: "Wir verhelfen Menschen mit Sehbehinderung zu mehr Mobilität."
summary: "Accessy stellt mit einer App und einer offenen API barrierefreie Routen für Menschen mit Sehbeeinträchtigung bereit."
---

<div class="iframe-container">
    <iframe src="https://www.youtube-nocookie.com/embed/CJ11fJXwn2Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

# Das Problem

Blinde Menschen sind in fremden Umgebungen auf Hilfe angewiesen. Normalerweise wird ihnen ein Weg mehrmals von Freund\*innen oder Assistenzdiensten gezeigt. Erst danach können sie diesen Weg eigenständig ablaufen. Der Nachteil ist, dass es sich nur um diesen einen Weg handelt. Man kann also nicht wirklich von einer Auflösung dieser Barriere sprechen.

Kartendienste von namenhaften Anbietern helfen an dieser Stelle auch nicht weiter. Sie beinhalten keine Informationen zu Bürgersteigen, Ampeln etc. und sind damit nur für sehende Menschen ausgelegt.

# Persönliche Motivation

Im Sommer 2019 hatte ich im Rahmen eines Service Design Prozesses für ein Verkehrsunternehmen ein Interview mit einer blinden Studentin. Sie wohnte nicht in dieser Stadt und erzählte mir, dass sie nur den Weg vom Bahnhof zu ihrer Universität kennt. Dieser Weg wurde ihr einige Male von einem Assistenzdienst gezeigt. Ansonsten konnte sie sich nicht frei in der Stadt bewegen.

Ich war in diesem Moment fassungslos, dass es noch keine digitale Lösung gibt, die eine freie Mobilität für blinde Menschen ermöglicht. Auch 6 Monate später hat mich dieses Problem nicht losgelassen und ich habe mich an eine Lösung gesetzt.

# Die Lösung

Accessy versucht dieses Problem auf mehrere Arten zu lösen. Zum einen über eine iOS App und zum anderen über eine Serveranwendung.

## Die App

Freund\*innen, Bekannte, Assistenzdienste, Städte oder grundsätzlicher jede\*r andere kann über die App Routen anlegen. Zum Beispiel vom Bahnhof zur Universität oder von einem Zuhause zum anderen. Diese Routen können dann mit einer anderen Person geteilt werden. Wenn man Routen anlegt, dann generiert man automatisch Infrastrukturen (Gehwege, Treppen, Ampeln, Zebrastreifen, Verkehrsinseln etc.). Diese Infrastruktur steht automatisch allen zur Verfügung. Sie können sie erweitern oder an einer anderen Stelle ganz neue hinzufügen. Dadurch entsteht nach und nach ein Netzwerk für die verschieden Städte. Je mehr Infrastruktur es gibt, desto mehr Informationen hat Accessy um eigenständig Routen berechnen zu können.

Das Ablaufen einer Route wird dann blindengerecht über eine Sprachausgabe ermöglicht. Anders als bei konventionellen Kartendiensten gibt Accessy weitere Informationen zu den einzelnen Wegabschnitten aus: Anzahl an Treppenstufen, ob es ein Geländer gibt und wenn, auf welcher Seite, Vibration oder Piepton an Ampeln, ob es sich um eine Fußgängerzone handelt und vieles mehr.

![1.png](/assets/images/project_images/accessy/1.png)

## Die Serveranwendung

Das Herzstück von Accessy ist die Serveranwendung. Hier werden zum einen alle Infrastruktur-, Routen und User\*innen-Daten gespeichert und das korrekte Anlegen der Infrastruktur überprüft. Zum anderen findet hier die Berechnung für Routen statt. Diese Berechnung erfolgt mit Hilfe des [Dijkstra Algorithmus](https://de.wikipedia.org/wiki/Dijkstra-Algorithmus). Wenn eine Infrastruktur angelegt wird, dann erhält sie je nach Art (Fußgängerzone, Gehweg, unsichere Straßenüberquerung) und Beschaffenheit (Breite des Gehwegs, Kopfsteinpflaster, Zebrastreifen mit stark befahrener Straße) einen Barriereindikator. So kann die schnellste und barrierefreiste Route berechnet werden.

![2.png](/assets/images/project_images/accessy/2.png)

# Technische Aspekte

App und Serveranwendung sind beide in Swift geschrieben. Für den Server wurde [Vapor](https://vapor.codes) verwendet. Da über 90% der blinden Menschen iOS als Betriebssystem verwenden, wurde sich hier für eine reine iOS Anwendung entschieden. Hier liegt ganz klar der Vorteil darin, dass beide Systeme (Server und App) ein nahezu gleiches Datenmodell verwenden, was die Entwicklung des Prototypen erleichtert hat.

Außerdem ist noch eine [iOS SDK](https://github.com/NeoGolightly/AccessySwiftSDK) entstanden, die es anderen Entwickler\*innen erleichtert, Accessy in ihre App einzubauen. Die SDK ist mit dem neuen [DocC Format von Apple](https://developer.apple.com/documentation/docc) dokumentiert und [hier](http://api.accessy.city/documentation/accessyswiftsdk) zu finden.

![3.png](/assets/images/project_images/accessy/3.png)

Die Open-Source-Anwendung Accessy ist aber nicht nur für iOS ausgelegt. Über eine REST Schnittstelle kann jeder mit Accessy interagieren.

Ich bedanke mich beim BMBF sowie dem DLR für die Förderung des Projektes und die Unterstützung in der Umsetzung.

# Zukunft

Accessy hat es in den 6 Monaten Förderzeit noch nicht in den Beta-Status geschafft. Dieser Release ist für Ende Oktober geplant. Ich freue mich schon darauf die App mit User:innen testen und ihre Vorschläge einbauen zu können.

Nach einer erfolgreichen Beta-Phase geht es dann an die Verbreitung der App. Ich hoffe, dass ich viele Städte und Assistenzdienste für mein Projekt gewinnen kann und so eine breites Angebot an Routen für blinde Menschen entsteht. Den Anfang wird dabei sicher meine Heimatstadt Goslar bilden.

Ein großer Dank gilt dem Bundesministerium für Bildung und Forschung und dem Deutschen Zentrum für Luft- und Raumfahrt, die dieses Projekt erst ermöglicht haben. Und zuletzt natürlich an den Prototype Fund, der durch seine tolle Betreuung ein wundervolles Arbeitsumfeld geschaffen hat.

### Weitere Informationen

[www.accessy.city](https://www.accessy.city)

Twitter: [@accessyapp](https://twitter.com/accessyapp)

Instagram: [@accessyapp](https://www.instagram.com/accessyapp/)
