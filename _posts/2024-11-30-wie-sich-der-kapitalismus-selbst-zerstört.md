---
layout: post
title: Wie sich der Kapitalismus selbst zerstört
date: 2024-11-30 10:00:00 +0100
category: Politik
description: "Eine Analyse der Kapitalintensivierung, und warum ich mich für einen demokratischen Sozialismus einsetze."
image: "/public/media/posts/wie-sich-der-kapitalismus-selbst-zerstört/background.png"
---

## Einführung

Der moderne Kapitalismus, der seit etwa 200 Jahren dominiert, steht vor Problemen, die seine langfristige Existenz bedrohen. Klimawandel, soziale Ungleichheiten, Kriege und wirtschaftliche Instabilitäten lassen sich nur schwer in einem sozioökonomischen System lösen, welches als oberstes Ziel die Maximierung des Profits anstrebt. So wird die Fähigkeit des Kapitalismus, diese Herausforderungen zu bewältigen, zunehmend in Frage gestellt.

Schon vor dem Kapitalismus gab es sozioökonomische Systeme, wie zum Beispiel den Feudalismus, welche andere Probleme mit sich brachten und im Laufe der Zeit ersetzt wurden. Es wäre naiv zu glauben, dass dies nicht auch mit dem Kapitalismus geschehen kann.

Doch selbst wenn wir uns einen "perfekten" Kapitalismus vorstellen, ohne Klimawandel oder sonstige externe Probleme, bleiben dennoch gewisse inhärente Probleme bestehen. Der Kapitalismus ist von Natur aus auf ständiges Wachstum und die ständige Akkumulation von Kapital angewiesen. Diese Mechanik führt jedoch zu internen Widersprüchen, die früher oder später seine eigene Zerstörung herbeiführen werden. Auf diese internen Widersprüche möchte ich hier eingehen und auf mathematische Art und Weise aufzeigen, wie genau das geschehen wird.

## Hintergrund

Dieser Abschnitt enthält einige mathematische Ausdrücke. Ich bitte Leser:innen, die nicht in diesem Gebiet versiert sind, um etwas Geduld. Ich möchte auch anmerken, dass ich kein Ökonom bin. Ich verlasse mich hier auf allgemein akzeptierte Definitionen der Wirtschaftslehre und auf die Mathematik. Weiter möchte ich alle Behauptungen, die nicht direkt aus Definitionen folgen, im nächsten Abschnitt empirisch durch Daten des World Penn Table belegen.

### Der Gewinn kommt vom Haushaltskonsum

Fragen wir uns zuerst: Woher kommt der Gewinn? Wir meinen hier den Gewinn über die gesamte Wirtschaft hinweg gesehen und nicht über einen einzelnen Kapitalisten. Der gesamtwirtschaftliche Gewinn $G$ kann nicht daher kommen, dass Kapitalisten untereinander tauschen, das wäre ein Nullsummenspiel. Der Gewinn muss also vom Haushaltskonsum kommen, also durch die Löhne der Arbeiterschaft, welche wieder ausgegeben werden für Nahrung, Wohnen, Unterhaltung, Transport usw. Wir behaupten:

$$
G = \text{Haushaltskonsum}
$$

Um diese Behauptung zu beweisen, summieren wir das Bruttoinlandsprodukt nach Verwendungsrechnung aller Länder auf und zersetzen es in seine Bestandteile:


$$
\begin{aligned}
\text{BIP} &= \text{Haushaltskonsum} \\
&+ \text{Investitionen} \\
&+ \text{Staatskonsum} \\
&+ \text{Exporte} \\
&- \text{Importe}
\end{aligned}
$$

Wir analysieren auch das Bruttoinlandsprodukt nach Entstehungsrechnung aller Länder und zersetzen es ebenfalls in seine Bestandteile:

$$
\begin{aligned}
\text{BIP} &= \text{Produktionswert} \\
&- \text{Vorleistungen} \\
&+ \text{Staatssteuern}
\end{aligned}
$$

Beide diese Berechnungsweisen des BIP sind allgemein akzeptierte Definitionen. Setzen wir beide Berechnungen des BIP gleich, erhalten wir:

$$
\begin{aligned}
&\text{Produktionswert} \\
-&\text{Vorleistungen} \\
+&\text{Staatssteuern}
\end{aligned}
=
\begin{aligned}
&\text{Haushaltskonsum} \\
+&\text{Investitionen} \\
+&\text{Staatskonsum} \\
+&\text{Exporte} \\
-&\text{Importe}
\end{aligned}
$$


Da sich gesamtwirtschaftlich gesehen die Exporte und die Importe aufheben, können wir diese für eine globale Analyse streichen:


$$
\begin{aligned}
&\text{Produktionswert} \\
-&\text{Vorleistungen} \\
+&\text{Staatssteuern}
\end{aligned}
=
\begin{aligned}
&\text{Haushaltskonsum} \\
+&\text{Investitionen} \\
+&\text{Staatskonsum}
\end{aligned}
$$

Da die Staatssteuern gleich dem Staatskonsum sein müssen, können wir diese ebenfalls streichen:



$$
\begin{aligned}
&\text{Produktionswert} \\
-&\text{Vorleistungen}
\end{aligned}
=
\begin{aligned}
&\text{Haushaltskonsum} \\
+&\text{Investitionen}
\end{aligned}
$$

Wir vernachlässigen hier, dass der Staat grundsätzlich einfach Geld drucken kann. Denn Inflation mag zwar die Quantität des Geldes erhöhen, nicht aber den Wert des Geldes. Sprich, der Gewinn kann nicht aus dem Gelddrucker kommen.

Wir bemerken weiter, dass Produktionswert minus die Vorleistungen per Definition der *Bruttowertschöpfung* entspricht:

$$
\text{Bruttowertschöpfung}
=
\begin{aligned}
&\text{Haushaltskonsum} \\
+&\text{Investitionen}
\end{aligned}
$$

Die Bruttowertschöpfung ist, ebenfalls per Definition, gleich der *Nettowertschöpfung*, also dem Gewinn $G$, plus den Abschreibungen.

$$
\begin{aligned}
&G \\
+&\text{Abschreibungen}
\end{aligned}
=
\begin{aligned}
&\text{Haushaltskonsum} \\
+&\text{Investitionen}
\end{aligned}
$$

Die Abschreibungen müssen per Definition gleich den Investitionen sein. Wir erhalten:

$$
G = \text{Haushaltskonsum}
$$

Da niemand Geld aus dem Nichts zaubern kann, muss der Haushaltskonsum kleiner oder gleich dem Lohn, oder für den Kapitalisten den Kosten der Arbeitskräfte, $K_A$ sein:

$$
G \leq K_A
$$

Natürlich wäre es für Konsumenten auch möglich, einen Kredit aufzunehmen, doch dieser muss früher oder später wieder zurückgezahlt werden. So können die Haushaltsausgaben bis zu einem gewissen Grad höher sein als die Löhne durch eine ständige Verschuldung der Konsumenten.

Auch wäre es für Konsumenten möglich, den Lohn zu investieren, um so später mehr Geld zur Verfügung zu haben. Doch in dem Moment, in dem Arbeiter ihr Geld investieren, agieren sie zumindest mit dem investierten Anteil als Kapitalisten. Wie schon zuvor bemerkt, wäre der aus Investitionen erwirtschaftete Gewinn daher wieder ein Nullsummenspiel, gesamtwirtschaftlich gesehen.

Nehmen wir beispielsweise an, dass alle Arbeiter die Hälfte ihres Lohns investieren würden. Das würde auch bedeuten, dass sie nur noch halb so viel konsumieren. Wie wir gesehen haben, kommt der Gewinn vom Konsum. Wenn nun nur noch halb so viel konsumiert wird, kann auch nur noch halb so viel Gewinn erzielt werden. Wir sehen, auch dieses Argument wäre ein Zirkelschluss.

Wir haben somit gezeigt, dass über die Gesamtwirtschaft hinweg gesehen, der Gewinn $G$ kleiner oder gleich den Kosten der Arbeitskräfte $K_A$ sein muss.


### Fallende Rentabilität

Die wohl wichtigste Kernkennzahl des Kapitalismus ist die *Rentabilität*. Die Rentabilität besagt, wie viel Gewinn durch die Investition einer bestimmten Menge Kapital erwirtschaftet werden kann. Wenn die Rentabilität hoch ist, kann sich Kapital durch hohe Gewinne schnell vermehren, der Kapitalismus gedeiht. Gleichermassen bedeutet eine niedrige Rentabilität schlechte und unsichere Zeiten für den Kapitalismus. Keine Rentabilität bedeutet den Tod des Kapitalismus.

Die Rentabilität wird im Folgenden $r$ genannt. Sie wird definiert als Verhältnis vom erwirtschafteten Gewinn $G$ zum eingesetzten Kapital $K$.

$$
r = \frac{G}{K}
$$

Das eingesetzte Kapital $K$ kann in zwei Teile kategorisiert werden. Erstens der Kapitalstock oder die Kosten der Produktionsmittel $K_S$, also Maschinerie, Bauten, Roh- und Hilfsstoffe usw. Zweitens die Kosten der eingesetzten Arbeitskräfte $K_A$, welche der Arbeiterschaft als Lohn ausgezahlt werden. Das eingesetzte Kapital ist somit die Summe dieser beiden Teile.

$$
K = K_S + K_A
$$

Eingesetzt in die obere Formel für die Rentabilität, erhalten wir nun den Ausdruck:

$$
r = \frac{G}{K_S + K_A}
$$

Der Term kann durch Multiplikation der rechten Seite mit $1/K_A$ umgeformt werden zu:

$$
r = \frac{\frac{G}{K_A}}{\frac{K_S}{K_A} + 1}
$$

Analysieren wir zuerst den oberen Term $G/K_A$ genauer. Wir haben den Gewinn $G$ im Verhältnis zu den Kosten der eingesetzten Arbeitskraft $K_A$. Wir wissen vom vorherigen Abschnitt, dass $G \leq K_A$ gilt. Der obere Bruch muss somit kleiner oder gleich Eins sein.

Die Rentabilität kann somit vereinfacht werden zu:

$$
r \leq \frac{1}{\frac{K_S}{K_A} + 1} = \frac{K_A}{K_S + K_A}
$$

### Auswirkungen auf den Zinsfuss

Der *interne Zinsfuss* $z$ wird durch Gleichsetzung der Investition $I$ und der Summe der abgezinsten Cashflows $C_t$ berechnet.

$$
I = \sum_{t=1}^{T}\frac{C_t}{(1+z)^t}
$$

Da wir hier den jährlichen Zinsfuss betrachten, gilt $T = 1$,
und wir können den Zinsfuss vereinfachen und nach $z$ auflösen:

$$
z = \frac{C}{I}-1
$$

Die Investitionen $I$ sind kleiner oder gleich dem Gesamtkapital $K$,
und der Cashflow ist gleich den initialen Investition plus dem Gewinn:

$$
C = I + G \leq K + G
$$

Wir erhalten für den Zinsfuss:

$$
z = \frac{C}{I}-1 \leq \frac{K + G}{K}-1 = \frac{G}{K} = r
$$

Somit gilt, dass die Rentabilität eine obere Grenze für den Zinsfuss darstellt.

### Kapitalizusammensetzung als limitierender Faktor

Wir haben mit $\frac{K_A}{K_S + K_A}$, also dem Verhältnis von den Kosten der Arbeitskraft zu den Kosten der eingesetzten Produktionsmittel, eine obere Limite für die Rentabilität, sowie auch eine obere Limite für den Zinsfuss gefunden. Die *Technische Zusammensetzung des Kapitals* $\frac{K_A}{K_S}$ bietet wiederum eine obere Limite für diesen Bruch und verhält sich umgekehrt zur *Kapitalintensität*:

$$
\frac{K_A}{K_S + K_A} \leq \frac{K_A}{K_S} 
$$

Wie verhält sich die Kapitalintensität im Laufe der Zeit? Durch Automatisierung und technischem Fortschritt nehmen die Kosten der Produktionsmittel immer mehr zu im Verhältnis zur Arbeitskraft. Wo früher eine Schaufel gereicht hat, muss jetzt ein Bagger her. Vom Pflug zum Traktor, von der Kutsche zum Auto, vom Spinnrad zur Spinnmaschine. Durch den Konkurrenzdruck innerhalb der Kapitalisten wird dieser Fortschritt erzwungen. Kapitalisten, die nicht modernisieren, können im Wettbewerb nicht mehr mithalten und werden vom Markt verdrängt. Das hat zur Folge, dass die Kapitalintensität stetig steigt, und somit das Verhältnis der Kosten der Arbeitskraft zu den Kosten der eingesetzten Produktionsmittel stetig sinkt. Der Bruch $\frac{K_A}{K_S}$ wird also kleiner im Laufe der Zeit.

Wenn aber $\frac{K_A}{K_S}$ kleiner wird, muss gezwungenermassen durch die oben etablierten Beziehungen auch die Rentabilität und somit der Zinsfuss kleiner werden.

## Ergebnisse

Im vorherigen Abschnitt wurden eine ganze Reihe von Behauptungen aufgestellt, welche die einen oder anderen Leser:innen in Frage stellen werden. Deshalb möchte ich in diesem Abschnitt die aufgestellten Behauptungen durch eine Analyse der verfügbaren Daten der letzten Jahrzehnte belegen. Sämtliche untenstehenden Daten wurden vom [Penn World Table](https://www.rug.nl/ggdc/productivity/pwt/) bezogen, einer Datenbank mit Informationen zu den relativen Einkommens-, Output-, Input- und Produktivitätsniveaus, die 183 Länder zwischen 1950 und 2019 abdeckt.

### Die Konsumausgaben sind kleiner oder gleich den Löhnen

Meine erste Behauptung war, dass über die Gesamtwirtschaft hinweg gesehen, der Gewinn die Konsumausgaben kleiner oder gleich den Löhnen sein muss.

![](/public/media/posts/wie-sich-der-kapitalismus-selbst-zerstört/worldwide_labcomp_hhcons.png)
*Die Löhne (rot) und die Konsumausgaben (orange) im Verhältnis zum Gesamtkapitalstock.*

Es gibt eine offensichtliche starke positive Korrelation zwischen den Löhnen und den Ausgaben von 0.98. Wir sehen aber auch, dass die Konsumausgaben zum grössten Teil etwas höher als die Löhne sind. Diese Diskrepanz ist aber so klein, dass sie auf Kreditaufnahmen und Verschuldung zurückgeführt werden kann.

### Die Kapitalintensität ist eine obere Limite für den Zinsfuss

Die zentrale Vorhersage dieses Modells ist es, dass die Kapitalintensität $K_A/K_S$ eine obere Grenze für den internen Zinsfuss $z$ darstellt. Im folgenden Diagramm können wir einfach erkennen, dass dies bis zum Ende der Datenreihe 2019 der Fall war. Ob das Modell auch weiterhin korrekt ist, wird wohl erst die Zukunft zeigen.

![](/public/media/posts/wie-sich-der-kapitalismus-selbst-zerstört/worldwide_r_z.png)
*Die technische Zusammensetzung des Kapitals $K_A/K_S$ (rot), die berechnete obere Grenze der Rentabilität $K_A/(K_S + K_A)$ (blau) und der interne Zinsfuss aus den Daten des Penn World Table (schwarz).
Die Daten wurden ab 2019 mit einem exponentiellen Modell extrapoliert (gestrichelte Linien)*

Wir stellen aber eine positive Korrelation von 0.42 zwischen der Obergrenze der Rentabilität und dem internen Zinsfuss fest, was heisst, dass ich diese beiden Werte zumindest ähnlich verhalten.

## Diskussion

### Das Endspiel

Wir haben gesehen, dass die Kapitalintensität eine Approximierung für die Rentabilität und für den Zinsfuss ist. Weiter haben wir festgestellt, dass die Kapitalintensität stetig zunimmt durch den Konkurrenzdruck innerhalb einer Marktwirtschaft. Somit muss die Rentabilität auf lange Sicht gezwungenermassen sinken. Dies ist der zentrale Widerspruch im Kapitalismus.

Führen wir dieses Szenario ins Endspiel. Nehmen wir an, der technische Fortschritt ist soweit, dass keine Arbeitskräfte mehr benötigt werden, $K_A/K_S = 0$. Keine Arbeitsstellen mehr bedeutet keine Löhne, keine Löhne bedeutet kein Konsum, bedeutet keinen Gewinn, $G = K_A = 0$. Der Kapitalismus wurde zu Ende gespielt und kann in dieser Form nicht mehr existieren.

### Konzentration der Produktion in Grosskonzernen

Die steigende Kapitalintensität hat zur Folge, dass kleine und mittelgrosse Unternehmen nicht mehr Wettbewerbsfähig sind. Dies führt zu einer Konzentration der Produktion in immer grössere Betriebe, die teils ganze Produktionsketten aufkaufen, um ihre Renditen durch vertikale Integration zu steigern. So nähert sich die effektive Rentabilität immer mehr unserer berechneten oberen Grenze an.

In der Praxis sehen wir das z.B. in den grossen südkoreanischen Chaebol, die zahlreiche Industriezweige dominieren so Wettbewerbsvorteile erzielen. Ein Beispiel hierfür ist Samsung, das nicht nur Smartphones herstellt, sondern auch eigene Chips, Displays und Batterien produziert.

Ein weiteres Beispiel findet sich in der Automobilindustrie, wo Konzerne wie Volkswagen oder Tesla ganze Lieferketten kontrollieren, von der Batteriezellenproduktion bis hin zu Softwareentwicklungen. Diese vertikale Integration macht es für kleinere Hersteller zunehmend schwieriger, mitzuhalten, da sie weder über die finanziellen Mittel noch über die Skaleneffekte der Grosskonzerne verfügen.

Amazon hat nicht nur eine riesige Handelsplattform aufgebaut, sondern besitzt auch eigene Logistikzentren, Lieferdienste und sogar eine wachsende Produktionssparte für Eigenmarken. Dadurch kann das Unternehmen Kosten senken und seine Marktstellung weiter ausbauen, während kleinere Händler oft von Amazons Infrastruktur abhängig sind oder Schwierigkeiten haben, eigenständig wettbewerbsfähig zu bleiben.

### Banken als Grosskapitalisten

Eine zentrale Rolle im Prozess der stegendenden Kapitalintensivierung spielen die Banken. Sie sind nicht länger nur passive Vermittler von Kapital, sondern aktive Akteure, die durch Kreditvergabe und Investitionen gezielt bestimmte Wirtschaftsbereiche fördern oder schwächen können. Im Zusammenhang damit verwandeln die Banken brachliegendes Geldkapital in funktionierendes, d.h. profitbringendes Kapital, sie sammeln alle und jegliche Geldeinkünfte und stellen sie der Kapitalistenklasse zur Verfügung. So wird das vorhandene Kapital maximal im Produktionsprozess eingesetzt, was wiederum bedeutet, dass sich die effektive Rentabilität immer mehr unserer berechneten oberen Grenze angleicht.

Diese aktive Rolle der Banken kommt aber auch mit Risiken. Ein besonders eindrucksvolles Beispiel für die enge Verflechtung von Banken, Industrie und Staat ist der Zusammenbruch der Credit Suisse im Jahr 2023. Die Grossbank geriet nach einer Serie von Skandalen, Fehlinvestitionen und Liquiditätsproblemen in eine existenzielle Krise. Aufgrund ihrer systemischen Bedeutung für den globalen Finanzmarkt und die Schweizer Wirtschaft musste der Staat massiv eingreifen.

Die Schweizer Regierung, die Schweizerische Nationalbank und die Finanzmarktaufsicht koordinierten eine Notübernahme durch die UBS, die mit staatlichen Garantien in Milliardenhöhe abgesichert wurde. Dies zeigt, wie Banken nicht mehr nur Vermittler von Kapital sind, sondern selbst zu mächtigen Akteuren geworden sind, deren Überleben im Zweifel mit öffentlichen Mitteln gesichert wird. Auch wird klar welche Rolle der Staat wahrnimmt: Er ist hauptsächlich der Beschützer des Kaptitals.

### Der neue Imperialismus

Die Konzentration des Finanzkapitals in wenigen Händen führt zwangsläufig zur Entstehung einer Finanzoligarchie, die nicht nur die Wirtschaft, sondern auch die Politik massgeblich beeinflusst. Grosskonzerne und Superreiche sind längst nicht mehr nur Marktakteure, sondern aktive Gestalter politischer Entscheidungen. Sie nutzen ihr Kapital, um Lobbyismus zu betreiben, politische Parteien zu unterstützen oder direkt regulatorische Massnahmen zu beeinflussen.

Nach und nach wird es offensichtlich, dass wirtschaftliche Massnahmen alleine nicht mehr ausreichen, um die Rentabilität weiter zu maximieren, denn irgendwann hat die Rentabilität seine Obergrenze erreicht. Also was tun, wenn diese Situation eintritt? Wie kann der Gewinn weiter erhöht werden, wenn alle friedlichen Massnahmen ausgeschlachtet wurden. Man wendet sich zum Krieg, und der Wirtschaftsimperialismus verwandelt sich mehr und mehr in einen Kriegsimperialismus. Die Erroberung fremder Märkte und Ressourcen, mit allen Mitteln die nötig sind.

Putin führt einen Angriffskrieg gegen die Ukraine, und besetzt die besonders Ressourcenreichen Gebiete, darunter 63% der ukrainischen Kohlevorkommen, mehrere Erdgas- und Ölfelder sowie bedeutende Eisenerz- und Titanvorkommen.

Trump schlägt ein Abkommen zwischen den USA und der Ukraine vor, welches vorsah, dass die Ukraine 50% ihrer Einnahmen aus natürlichen Ressourcen, einschliesslich Mineralien, Gas, Öl sowie Einnahmen aus Häfen, Kraftwerken und anderer Infrastruktur, an einen Fonds abtritt, der vollständig im Besitz der USA wäre. ​Dies obwohl sich die USA im Zuge der Atomwaffenabgabe der Ukraine verpflichtet haben, das Land zu schützen.

Trump spricht auch immer wieder von der Annexion Grönlands. Grönland besitzt enorme Rohstoffvorkommen, darunter seltene Erden, Uran und Öl, die für die USA wirtschaftlich und technologisch wertvoll wären. Zudem hat die Insel eine zentrale geostrategische Lage im Arktisraum, der aufgrund des Klimawandels und schmelzender Eisflächen zunehmend für neue Handelsrouten und militärische Positionierung relevant wird. 

Natürlich war diese Form des neuen Imperialismus war nie wirklich ein Ding der Verganenheit. So gab es z.B. bereits vor dem Irakkrieg 2003 Pläne und Absprachen über die Verteilung der irakischen Ölreserven. US-amerikanische und britische Unternehmen zeigten starkes Interesse an den riesigen Ölreserven des Landes. Interne Dokumente und Berichte legen nahe, dass grosse Ölkonzerne wie ExxonMobil, BP und Shell strategische Interessen am Irak hatten und sich frühzeitig auf eine mögliche Neuverteilung vorbereiteten. Nach dem Krieg erhielten westliche Ölunternehmen durch sogenannte "Production Sharing Agreements" Zugang zu irakischen Ölfeldern, während staatliche irakische Unternehmen geschwächt wurden. Der grosse Unterschied ist aber, dass diese Absprachen nicht mehr im Verborgenen geschehen, sondern geradeaus der Öffentlichkeit präsentiert werden. Die neue geopolitische Situation "der Stärkere bedient sich beim Schwächeren" wird mehr und mehr akzeptiert.

Doch es ist nicht das erste Mal, wo so etwas geschieht. Bereits vor 1914 gab es eine intensive Konkurrenz um Märkte, Rohstoffe und Einflusszonen zwischen den europäischen Grossmächten. Deutschland, Grossbritannien und Frankreich standen in einem wirtschaftlichen Wettlauf, in dem insbesondere Kolonien deren Ressourcen von entscheidender Bedeutung waren. Die imperialistischen Mächte konkurrierten Investitionsgebiete, vor allem in Afrika, Asien und dem Nahen Osten. Als wirtschaftliche Expansion nicht mehr allein durch Handel und Diplomatie möglich war, eskalierten die Spannungen in einen militärischen Konflikt. Nur sind es heute nicht mehr imperialistische Staatsmächte, sondern Verbände von Finanzoligarchen.

### Vom Imperialismus zum Faschismus

Wenn der Wirtschaftsimperialismus in den Kriegsimperialismus übergeht, führt dies unweigerlich zu gesellschaftlichen Umbrüchen. Die wachsende Militarisierung und die damit verbundene Konzentration von Macht in den Händen weniger Akteure schaffen die Grundlage für autoritäre Herrschaftsstrukturen. In der Geschichte sehen wir, dass ökonomische Krisen, gepaart mit militärischen Konflikten, oft zu einer Radikalisierung der Politik führen. Wenn Demokratien zunehmend instabil werden und die soziale Ungleichheit wächst, entsteht ein fruchtbarer Boden für faschistische Bewegungen.

So geschah es in den 1920er und 1930er Jahren, als der wirtschaftliche Niedergang nach dem Ersten Weltkrieg und die Weltwirtschaftskrise extremistische Ideologien in Deutschland und Italien befeuerten. Grossindustrielle und Finanzoligarchien unterstützten den Faschismus, da er ihnen versprach, Arbeitskämpfe zu unterdrücken, linke Bewegungen zu zerschlagen und den Staat vollständig in den Dienst der Kapitalinteressen zu stellen. Hitler und Mussolini wurden von den Eliten gefördert, weil sie eine aggressive Expansion verfolgten, die neue Absatzmärkte und Rohstoffquellen erschloss. Der Krieg diente als Mittel zur wirtschaftlichen Wiederbelebung und zur Erhöhung der Profite der Rüstungsindustrie.

Wenn die Schuld am Versagen des kapitalistischen Wirtschaftssystems nicht im Kapitalismus selbst gesucht wird, da ja gerade die vom Kapitalismus profitierenden Oligarchen an der Macht sind, werden andere Sündenböcke benötigt. Die Schuld wird in anderen Kulturen, Religionen oder Ansichten gesucht. Überall, nur nicht im Kapitalismus selbst.

Auch heute sehen wir Parallelen: Die zunehmende politische Polarisierung, der Aufstieg autoritärer Politiker, die gezielte Schwächung demokratischer Institutionen und die Instrumentalisierung nationalistischer Rhetorik zur Rechtfertigung wirtschaftlicher und militärischer Aggressionen. Die Grenzen zwischen Kapitalismus, Imperialismus und Faschismus verschwimmen zunehmend.

![](/public/media/posts/wie-sich-der-kapitalismus-selbst-zerstört/elon-musk.png)
*Der reichste Mann der Welt und seine "peinliche Geste".*

### Sozialismus oder Faschismus

Wir haben gesehen, wie die inneren Mechanismen des Kapitalismus zu einer stetigen Kapitalintensivierung führen, und wie die Kapitalintensivierung nach und nach zu einer Finanzoligarchie führen. Es ist im Interesse dieser Finanzoligarchie, den Kapitalismus beizubehalten, wenn nötig auch durch Kriege oder gar einen Übergang zum Faschismus.

All dies ist aus meiner Sicht nicht abwendbar, es sei denn, wir überwinden den Kapitalismus selbst und lassen so auch die inneren Widerspüche des Kapitalismus hinter uns. Die Interessen der Finanzoligarchie sind schlicht nicht vereinbar mit den Interessen der breiten Bevölkerung.

Die Sozialdemokratische Partei ist die einzige grosse Partei der Schweiz, welche diesen Standpunkt vertritt, und für mich somit die einzige Partei, die effektiv gegen diese drohenden Gefahren ankämpfen kann.

> Die Sozialdemokratische Partei der Schweiz (SP Schweiz) tritt auf der Grundlage
ihres Programms für die Ziele des demokratischen Sozialismus ein
*Statuten der SP Schweiz, Artikel 1, Paragraph 1*