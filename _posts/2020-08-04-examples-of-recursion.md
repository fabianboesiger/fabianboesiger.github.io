---
layout: post
title: Beispiele für Rekursion
date: 2020-08-04 13:00:00 +0200
categories: Programmieren
tags: [Rekursion, Memoisation, C++]
---

Rekursion ist eine Methode, Probleme zu lösen, wo die Lösung auf Lösungen für kleinere Instanzen des gleichen Problems basiert. Dies zeigt sich üblicherweise dadurch, dass die Funktion, welche die Lösung berechnet, sich selbst aufruft.

Wie in einem Induktionsbeweis müssen üblicherweise zwei Fälle unterschieden werden. Der *Base Case* und der *Step Case*. Der *Base Case* löst das kleinste Teilproblem, das nicht weiter in Probleme der gleichen Art aufgelöst werden kann. Der *Step Case* dagegen teilt ein Problem in kleinere Instanzen des gleichen Problems auf.

## Beispiele

### Fakultät

Die Fakultät kann rekursiv definiert werden:

$$
n! = \begin{cases}
    1, & n = 0 \\
    n \cdot (n - 1)!, & n > 0
\end{cases}
$$

Wir erkennen den *Base Case* $$0! = 1$$, und den *Step Case* $$\forall n > 0 : n! = n \cdot (n - 1)!$$. Relativ einfach können wir ein entsprechendes Programm schreiben:

~~~cpp
#include <assert.h>

// Berechnet die n-te Fakultät.
unsigned int factorial(const unsigned int n) {
    // Die Fakultät ist nur für n >= 0 definiert.
    assert(n >= 0);

    // Base Case, es wird kein rekursiver Funktionsaufruf ausgeführt.
    if (n == 0) {
        // Wichtig: Der Base Case muss vor dem Step Case definiert werden,
        // und weitere rekursive Funktionsaufrufe verhindern,
        // beispielsweise mit return. Andernfalls terminiert das Programm nicht.
        return 1;
    }

    // Step Case, das Problem wird in kleinere Teilprobleme aufgeteilt.
    // Der rekursive Funktionsaufruf erfolgt hier.
    return n * factorial(n - 1);
}

int main() {
    // 4! = 24.
    assert(factorial(4) == 24);

    return 0;
}
~~~

### Fibonacci-Folge

Die Fibonacci-Folge ist folgendermassen für definiert:

$$
f_n = \begin{cases}
    1, & 1 \leq n < 3 \\
    f_{n-1} + f_{n-2}, & 3 \leq n
\end{cases}
$$

Schon in dieser Definition kann die rekursive Natur des Problems gut erkannt werden. Wir identifizieren den *Base Case* mit den Anfangswerten $$f_1 = f_2 = 1$$, und den *Step Case*: $$\forall n \geq 3: f_n = f_{n-1} + f_{n-2}$$, wobei wir feststellen, dass der *Step Case* rekusiv definiert ist.

~~~cpp
#include <assert.h>

// Berechnet die n-te Fibonacci-Zahl.
unsigned int fib(const unsigned int n) {
    // Die Fibonacci-Zahlen sind nur für n >= 1 definiert.
    assert(n >= 1);

    // Base Case.
    if (n == 1 || n == 2) {
        return 1;
    }

    // Step Case.
    return fib(n - 1) + fib(n - 2);
}

int main() {
    // Die 6. Fibonacci-Zahl ist 8.
    assert(fib(6) == 8);

    return 0;
}
~~~

Betrachten wir, wie die Funktion `fib` bei der Ausführung des Programms aufgerufen wird:

~~~text
main()
    fib(6) -> 8
        fib(5) -> 5
            fib(4) -> 3
                fib(3) -> 2
                    fib(2) -> 1
                    fib(1) -> 1
                fib(2) -> 1
            fib(3) -> 2
                fib(2) -> 1
                fib(1) -> 1
        fib(4) -> 3
            fib(3) -> 2
                fib(2) -> 1
                fib(1) -> 1
            fib(2) -> 1
~~~

Wir sehen, dass die Rekusive Lösungsmethode hier in vielen Funktionsaufrufen mit den selben Werten resultiert, was für grosse `n` sehr ineffizient wird. `fib(3)` wird beispielsweise drei mal berechnet.

Wir können die Effizienz verbessern, indem wir eine Methode namens *Memoisation* verwenden. Dabei werden equivalänte Funktionsaufrufe nicht mehr neu berechnet, sondern beim ersten mal gespeichert, und danach bei erneuten Funktionsaufrufen einfach direkt die vorherige Lösung verwendet.

~~~cpp
#include <assert.h>

unsigned int fib(const unsigned int n, unsigned int *const results) {
    assert(n >= 1);

    // Step Case.
    // Falls wir im Base Case sind, ist results[n - 1] == 1 und wir
    // geben deshalb direkt 1 aus ohne eine rekursive Berechnung.
    if (results[n - 1] == 0) {
        // Falls dieses Zwischenresultat noch nie berechnet wurde,
        // berechnen wir es rekusiv und speichern es in unserer Tabelle ab.
        results[n - 1] = fib(n - 1, results) + fib(n - 2, results);
    }
    
    return results[n - 1];
}

unsigned int fib_dp(const unsigned int n) {
    assert(n >= 2);

    // Erstelle eine Tabelle, wobei alle Einträge ursprünglich 0 sind.
    // Falls der (n-1)-te Eintrag in der Tabelle 0 ist, heisst das für uns,
    // dass das Zwischenresultat noch nicht berechnet wurde.
    // Der Base Case kann direkt miteinbezogen werden, indem wir die
    // ersten beiden Einträge auf 1 setzen.
    unsigned int results[n] = {1, 1};

    // Starte die rekursive Berechnung.
    return fib(n, results);
}

int main() {
    assert(fib_dp(6) == 8);

    return 0;
}
~~~

Betrachten wir noch einmal, wie die Funktion `fib` bei der Ausführung des Programms aufgerufen wird:

~~~text
main()
    fib_dp(6) -> 8
        fib(6) -> 8
            fib(5) -> 5
                fib(4) -> 3
                    fib(3) -> 2
                        fib(2) -> 1
                        fib(1) -> 1
                    fib(2) -> 1
            fib(4) -> 3
~~~

Da wir beim zweiten Aufruf von `fib(4)` das Zwischenresultat bereits wissen und abgespeichert haben, können wir auf eine weitere rekursive Berechnung verzichten.

### Binärbaum

In einem Binärbaum soll die Anzahl eines bestimmten Eintrags gezählt werden.

Wir bemerken, dass die Vorkomisse eines Eintrags in einem Teilbaum die Summe der Vorkommnisse des linken und des rechten Teilbaums ist, addiert mit Eins, falls der Eintrag im aktuellen Knoten vorkommt.

~~~cpp
#include <assert.h>

class Node {
    private:
        int value;
        // Linker Teilbaum.
        Node *left;
        // Rechter Teilbaum.
        Node *right;
    public:
        Node(int, Node*, Node*);
        unsigned int count(int);
};

Node::Node(int value, Node *left, Node *right) {
    this->value = value;
    this->left = left;
    this->right = right;
}

unsigned int Node::count(int value) {
    return
        // Addiere Eins, falls der Eintrag übereinstimmt.
        (this->value == value ? 1 : 0) +
        // Linker Teilbaum.
        (this->left == nullptr
            // Base Case, es existiert kein linker Teilbaum.
            // Beachte, dass die Rekursion nicht weiter ausgeführt wird.
            ? 0
            // Step Case, zähle im linken Teilbaum weiter.
            : this->left->count(value)
        ) +
        // Rechter Teilbaum.
        (this->right == nullptr
            // Base Case, es existiert kein linker Teilbaum.
            // Beachte, dass die Rekursion nicht weiter ausgeführt wird.
            ? 0
            // Step Case, zähle im linken Teilbaum weiter.
            : this->right->count(value)
        );
}

int main() {
    // Konstruiere einen Baum mit zwei Vorkommnissen der Zahl 7.
    Node *tree = new Node(
        7,
        new Node(
            4,
            nullptr,
            nullptr
        ),
        new Node(
            5,
            nullptr,
            new Node (
                7,
                nullptr,
                nullptr
            )
        )
    );

    assert(tree->count(7) == 2);

    return 0;
}
~~~

## Kurzgesagt

1. Idenifiziere den *Base Case* des Problems, welcher nicht in Teilprobleme derselben Art zerlegt werden kann.
2. Identifiziere den *Step Case*, also die Rekusion des Problems. Finde heraus wie das Problem in kleinere Teilprobleme der selben Art aufgeteilt werden kann.
3. Schreibe die rekursive Funktion.
   1. In dieser Funktion, implementiere zuerst den *Base Case*.
   2. Implementiere anschliessend den *Step Case*. Stelle sicher, dass der *Step Case* nicht ausgeführt wird, wenn der *Base Case* greift, beispielsweise durch Abbruch der Funktion mit `return` im Falle des *Base Case*.
