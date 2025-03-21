---
layout: post
title: Wie sich der Kapitalismus selbst zerstört
date: 2024-11-30 10:00:00 +0100
category: Politik
description: "Eine Analyse der Kapitalintensivierung, und warum ich mich für einen demokratischen Sozialismus einsetze."
image: "/public/media/posts/wie-sich-der-kapitalismus-selbst-zerstört/background.png"
---

{% katexmm %}

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

### Länderspezifische Analyse

Die oben gezeigten Berechnungen und Limiten gelten zwar global gesehen, nicht aber wenn man Länder isoliert betrachtet. Pro Land kann der Gewinn $G$ nicht nur vom Konsum oder vom Lohn der Arbeiterschaft $K_A$ kommen, sondern auch vom Handel zwischen den Ländern, konkret dem Exporthandel $H_E$. Für den Gewinn gilt dann:

$$
G = K_A + H_E
$$

Für die Rendite und den Zinsfuss gilt somit:

$$
z \leq r \leq \frac{K_A + H_E}{K_S + K_A}
$$

Der Importhandel muss in der Berechnung dieser oberen Limite nicht vom Gewinn abgezogen werden, da beispielsweise auch Investitionen in der Form von Importen von Maschinen oder anderen Produktionsmitteln geschehen können und somit nicht unbedingt einen Gewinnverlust mit sich bringen.

### Miteinbezug der Staats

Staaten erheben Steuern, welche sich negativ auf die Rentabilität auswirken. Diese Steuern werden aber grösstenteils wieder in das eigene Land investiert, was diese negative Wirkung wieder aufhebt. Grundsätzlich investieren kapitalistische Staaten insbesondere dann, wenn es dem Land wirtschaftlich schlecht geht, um so der Wirtschaftskrise entgegenzuwirken. So kann der Staat über längere Zeit hinweg gesehen sogar stabilisierend auf die Rentabilität wirken. Um auch dieser Faktor miteinzubeziehen, erweitern wir die Definition für den länderspezifischen Gewinn, um staatliche Investitionen $S$ zu berücksichtigen:

$$
G = K_A + H_E + S
$$

Für die Rendite und den Zinsfuss gilt somit:

$$
z \leq r \leq \frac{K_A + H_E + S}{K_S + K_A}
$$

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

Wir stellen zudem eine positive Korrelation von 0.42 zwischen der Obergrenze der Rentabilität und dem internen Zinsfuss fest.

### Länderspezifische Analyse der Daten

Viele, insbesondere ressourcenreiche Länder, sind definiert durch einen grossen ausländischen Kapitalanteil. Ausländische Firmen investieren in diese ressourcenreichen Länder, um die Ressourcen zu extrahieren und anschliessend zu exportieren. Der Gewinn bleibt somit nicht im Inland. Dieser Kapitalexport zur Gewinnextraktion wird seit der Zeit des Kolonialismus traditionell von westlichen Firmen betrieben.

Ein Beispiel eines Landes, in dem dieser Prozess geschieht, ist der Irak. Der Irak ist ein ölreiches Land, in dem vor der Zeit von Saddam Hussein westliche Firmen ein Ölmonopol hatten. Nach seiner effektiven Machtübernahme im April 1982 verstaatlichte Hussein westliche Ölfirmen. In den Daten können wir sehen, wie sich ab 1982 die durch unser Modell berechnete Rentabilitätsgrenze und der interne Zinsfuss perfekt annähern. Durch die Invasion im Irak im Jahr 2003 fielen die irakischen Ölfelder wieder in westliche Hände, ebenfalls gut sichtbar in unseren Daten.

![](/public/media/posts/wie-sich-der-kapitalismus-selbst-zerstört/iraq.png)
*Obergrenze der Rentabilität und der Interne Zinsfuss im Irak hat sich durch Verstaatlichung der Ölfelder zwischen 1982 und 2003 stark angenähert.*

Die nahezu perfekte Übereinstimmung der berechneten Obergrenze der Rentabilität und den tatsächlichen historischen Geschehnissen interpretiere ich als weiteren starken Indikator für die Korrektheit dieses Modells.

## Diskussion

### Das Endspiel

Wir haben gesehen, dass die Kapitalintensität eine Approximierung für die Rentabilität und für den Zinsfuss ist. Weiter haben wir festgestellt, dass die Kapitalintensität stetig zunimmt durch den Konkurrenzdruck innerhalb einer Marktwirtschaft. Somit muss die Rentabilität auf lange Sicht gezwungenermassen sinken. Dies ist der zentrale Widerspruch im Kapitalismus.

Führen wir dieses Szenario ins Endspiel. Nehmen wir an, der technische Fortschritt ist soweit, dass keine Arbeitskräfte mehr benötigt werden, $K_A/K_S = 0$. Keine Arbeitsstellen mehr bedeutet keine Löhne, keine Löhne bedeutet kein Konsum, bedeutet keinen Gewinn, $G = K_A = 0$. Der Kapitalismus wurde zu Ende gespielt und kann in dieser Form nicht mehr existieren.

Um dies zu veranschaulichen, habe ich die Daten der technischen Zusammensetzung des Kapitals, der oberen Grenze der Rentabilität und dem internen Zinsfuss via einem exponentiellen Wachstumsmodell $f(x) = ax^b + c$ extrapoliert. Laut diesem Modell wird die obere Grenze für die Rentabilität noch vor 2060 den Nullpunkt erreicht haben und somit jegliche Kapitalakkumulation verunmöglichen.

Wir sehen auch, dass sich die Linien des internen Zinsfusses und der oberen Grenze der Rentabilität um das Jahr 2030 schneiden. Wenn unser Modell $z \leq r$ korrekt ist, muss noch vor 2030 entweder eine Korrektur des internen Zinsfusses stattfinden oder aber die Rentabilität muss aufhören zu fallen. Beide Optionen sind laut diesem Modell im Rahmen des Möglichen.

Dieses Modell soll also nicht als Vorhersage gedeutet werden. Die Kapitalintensität und andere Faktoren können aktiv durch gewisse politische Massnahmen beeinflusst werden, welche die fallende Rentabilität weiter abflachen können. Es soll höchstens als *Tendenz* betrachtet werden, welche eintritt, falls keine politischen Massnahmen getroffen werden. Massnahmen wie z.B. ein bedingungsloses Grundeinkommen können dieser Tendenz entgegenwirken.

### Faschismus als Nachfolger des Kapitalismus

Angenommen, 

### Bedingugsloses Grundeinkommen



### Krieg als Zerstörung von Kapitalstock

Wir haben ein Beispiel gesehen, wie $K_A$ erhöht werden kann. Umgekehrt besteht aber auch die Möglichkeit, $K_S$ zu reduzieren. Natürlich vernichtet kein Kapitalist freiwillig einen Teil seines Kapitalstocks, aber es gibt andere Möglichkeiten.

Eine Möglichkeit ist ein System des ewigen Kriegs. Der Krieg, abstrakt betrachtet, ist eine ständige Zerstörung von Produktionsmitteln. Ständige strategische Bombardierung von Fabriken und Infrastruktur ist im Grunde nichts anderes als Vernichtung von Kapitalstock. Als Bonus kann durch Eroberung von Ländereien nicht nur "feindliches" Kapital zerstört werden, sondern in die eigene Wirtschaft einverleibt werden und so die eigene Gewinnrate kurzfristig erhöhen.


### Der Übergang zum Sozialismus


## Nachwort

Falls du, liebe:r Leser:in, mir widersprichst und in den Formeln und Argumenten irgendwo einen Fehler gefunden hast, dann bitte ich dich, schreibe mir doch eine Mail und lass es mich wissen. Gerne würde ich Gegenargumente zu dieser Theorie hören.

{% endkatexmm %}