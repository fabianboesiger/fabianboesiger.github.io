---
layout: post
title: Automatisierte Astrofotografie
date: 2021-03-26 16:00:00 +0100
category: Astrofotografie
description: "So habe ich mein Astrofotografie-Prozess automatisiert."
---

## Das Problem

Obwohl manuelle Astrofotografie schon sehr interessant ist, gibt es dennoch einige Ungemütlichkeiten. Als Informatiker ist es sozusagen mein Instinkt, diese ungemütlichen Prozesse zu automatisieren.

### Die Kälte

Es ist zwar schön, mitten in der Nacht draussen die Sterne zu beobachten, mit der Zeit kann es aber ziemlich kalt werden. Eine ferngesteuerte Bedienung, die sich nach drinnen verschieben lässt, wäre klar von Vorteil.

### Langzeitbelichtungen

Die Kamera, derzeit eine Canon EOS 1300d, unterstützt "out of the box" eine maximale Belichtungszeit von 30 Sekunden. Natürlich ist diese Zeit viel zu kurz für die Fotografie dunklerer Deep-Sky Objekte.

Mit dem "Bulb"-Modus belichtet die Kamera solange wie der Benutzer den Auslöser gedrückt hält. Jedoch führt der ständige Druck auf den Auslöser zu Vibrationen in der Teleskopoptik, was das Bild unbrauchbar macht.

Die Kamera kann über ein eigenes Netzwerk mit einem Smartphone verbunden und bedient werden, was gegen die Vibrationen hilft. Dennoch muss der Auslöser über die gesamte Belichtungszeit gedrückt gehalten werden.

### Stacking

Stacking ist eine Methode, um die Gesamtbelichtung nochmal zu verlängern. Dabei werden mehrere, teilweise hunderte Bilder des selben Objekts durch eine Software aufeinandergelegt oder "gestackt", um die Details maximal hervorzubringen.

Es muss also nicht nur ein Bild geschossen werden, sondern eher hundert. Wenn jedes Bild zwei Minuten belichtet wird, bedeutet das schnell mal über drei Stunden Arbeit, wobei für jedes Bild der Auslöser gedrückt gehalten wird. Diese repetitive Arbeit, welche draussen in der Kälte gemacht werden muss, ist für einen verweichlichten Informatiker natürlich völlig unzumutbar.

## Die Lösung

Die Idee ist es, sowohl Kamera, als auch die motorisierte Montierung des Teleskops an einen Raspberry-Pi Computer anzuschliessen. Der Raspberry Pi ist per WLAN mit einem Computer drinnen verbunden, über den sich die gesamte Ausrüstung steuern lässt. Hier eine Übersicht des Plans, und eine Demonstration meiner Zeichenkünste:

![übersicht](/public/media/posts/astrophotography-setup/overview.png)
*Eine Übersicht der Ausrüstung.*

Scheint einfach zu sein, oder? Natürlich müssen noch einige Hürden überwunden werden. Wie genau kommunizert der Raspberry Pi mit der Ausrüstung? Und mit welcher Software lässt sich das Teleskop am besten bedienen? Glücklicherweise gibt es kaum ein Problem, welches noch nicht gelöst wurde.

Die [INDI Library](https://www.indilib.org/) ist eine Open Source Software, welche verwendet wird, um Astronomie-Equipment anzusteuern. INDI agiert als Brücke zwischen der Teleskop-Hardware und der Steuerungs-Software.

Ein einfacher Weg, INDI auf dem Raspberry Pi zum laufen zu bringen, ist der [Astroberry Server](https://www.astroberry.io/). Astroberry Server ist ein vorgefertigtes Betriebssystem für den Raspberry Pi, welches nur auf die SD Karte geflasht werden muss, und dann sofort betriebsbereit ist.

Der INDI Server ist dann über das lokale Netzwerk zum [KStars Astronomieprogramm](https://edu.kde.org/kstars/) verbunden, welches auf dem Computer drinnen läuft.

Interessant ist auch, dass sämtlichte verwendete Software Open Source und somit kostenlos verwendbar ist.

## Der Test

### Aufstellen des Teleskops

Natürlich muss das Teleskop noch immer manuell aufgestellt und nach dem Nordstern ausgerichtet werden. Zusätzlich muss der Raspberry Pi eingesteckt werden. Der Hand-Controller der Montierung ist aber nicht mehr notwendig.

Ausserdem fällt der relativ aufwendige Prozess des N-Star-Alignments weg. Dabei richtet sich das Teleskop nach verschiedenen Sternen aus. Anschliessend muss der Benutzer manuell den Stern im Zielsucher zentrieren. Daraus berechnet das Teleskop die genaue Position der Sterne relativ zum Standort des Teleskops.

Dieser Prozess kann jetzt vollständig durch die Astronomiesoftware übernommen werden, da diese Zugriff auf die Kamera und die Montierung des Teleskops hat.
So nimmt die Software ein Bild auf, vergleicht dieses Bild mit einer Sternenkarte
und berechnet daraus die Differenz zwischen der gewünschten und der wirklichen
Position.

### Auswählen des Ziels

Das Ziel kann nun gemütlich drinnen vor dem Computer ausgewählt werden. Nach der Auswahl schwenkt das Teleskop automatisch zum Ziel und verfolgt es. Hier wählen wir die Pinwheel-Galaxie als Ziel.

![](/public/media/posts/astrophotography-setup/map.png)
*Auf der Sternenkarte wählen wir die Pinwheel-Galaxie als Ziel.*

### Fotografie

In der Software können wir nun gemütlich die gewünschte Anzahl an Aufnahmen und die Belichtungszeit angeben werden. Der Computer übernimmt den Rest.


![](/public/media/posts/astrophotography-setup/summary.png)
*In der Übersicht sehen wir den Gesamtfortschritt der Aufnahme.*

### Das Resultat

![](/public/media/posts/astrophotography-setup/pinwheel-galaxy.jpg)
*Das Resultat nach dem Stacking und einigen Anpassungen.*
