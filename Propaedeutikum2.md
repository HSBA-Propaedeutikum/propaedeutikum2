## Boolsche Datentypen 
Beim letzten Mal haben wir bereits zwei wichtige Datentypen in JavaScript kennengelernt, die Datentypen *String* und *Number*. Nun lernen wir einen weiteren wichtigen Datentypen kennen. Den Datentyp *Boolean*. Anders als Strings, welche aus beliebigen Zeichenketten bestehen und der Datentype Number, welcher Zahlen beliebiger Größe beinhaltet, hat der Datentyp Boolean nur die zwei Ausprägungen `true` und `false`.  
Eine häufige Art wie wir boolsche Werte erzeugen ist über Abfragen mit **Vergleichsoperatoren**.

### Mathematische Vergleichsoperatoren
Vergleichsoperatoren vergleichen wie der Name andeutet zwei beliebige Zahlen und weist dem Ergebnis einen boolschen Wert zu. Am besten können wir dies anhand eines Beispieles erläutern.

    let x = 6;
    console.log(x >= 5); // liefert true zurück
    console.log(x < 4); // liefert false zurück

Es gibt 6 mathematische Operatoren, welche es uns erlauben beliebige Zahlen miteinander zu vergleichen. Es muss beachtet werden, dass nur Werte vom Typ *Number* miteinander verglichen werden dürfen, da es sonst zu unerwarteten Konsequenzen kommen kann auf die wir später noch eingehen werden. Für unser nachfolgenden Beispiel ist `x = 5`.

|Operator | Beschreibung             | Beispiel   |Ergebnis   |
|:-------:|--------------------------|------------|-----------|
|   `==`  | EQUALS TO                |  `x == 5`  |  `true`   |
|   `!=`  | NOT EQUALS TO            |  `x != 5`  |  `false`  |
|   `>`   | GREATER THAN             |  `x > 5`   |  `false`  |
|   `<`   | LESS THAN                |  `x < 6`   |  `true`   |
|   `>`   | GREATER THAN OR EQUAL    |  `x >= 5`  |  `true`   |
|   `<`   | LESS THAN OR EQUAL       |  `x <= 4`  |  `false`  |

### Logische Operatoren
Häufig wollen boolsche Werte miteinander Verknüpfen, um kompliziertere Sachverhalte ausdrücken zu können. Somit ist es wenig überraschend, dass es ähnlich wie für *Strings* und *Numbers* auch Operatoren für boolsche Werte gibt. Wir nehmen für diese Beispiel `x = 5` und `y = 11` an.
|Operator | Beschreibung             | Beispiel                      |Ergebnis   |
|:-------:|--------------------------|-------------------------------|-----------|
|   `&&`  | AND                      | `x >= 10 && x <= 20`          |`false`    |
|  `\|\|` | OR                       | `x > 20 \|\| x == 5`          |`true`     |
|   `!`   | NOT                      | `!(x >= 10 && x <= 20)`       |`true`     |

Wie bereits bei mathematischen Operatoren können wir logische Ausdrücke klammern, wenn wir wollen, dass ein Ausdruck zuerst evaluiert wird. Wenn keine Klammern gesetzt sind, so wird zuerst der **NOT** Operator, dann der **AND** Operator und zum Schluss der **OR** Operator ausgewertet.

## Strukturierte Programmierung 
Selbsterständlich sind boolsche Werte für sich genommen wenig interessant. Aber sie sind wichtige Grundlage der sogenannten strukturierten Programmierung. Bisher haben wir die imperative Programmierung kennengelernt, welche besagt, dass Befehle Zeile für Zeile exakt vom Computer ausgeführt werden. Was ist aber, wenn wir bestimmte Befehle nur unter bestimmten Bedingungen oder sehr häufig ausführen wollen? An dieser Stelle kommt die strukturierte Programmierung in Spiel. Sie erlaubt es uns die Ausführung von Codeblöcken an Bedingungen in Form von boolschen Werten zu knüpfen.

### Bedingte Ausführung
Die einfachste bedingte Anweisung is eine `if` Verzweigung. Wie das Schlüsselwort hier schon andeutet wird der eingeschlossene Codeblock einer if-Verzweigung nur ausgeführt, falls die zugrundeliegende Bedingung `true` ist.

    let x = 7;

    // Die Bedingung ist wahr und der Code in den Klammern wird ausgeführt.
    if (x > 0) {
        console.log("x ist größer als 0")
    }

    // Die Bedingung if falsch und der Code in den Klammern wird ignoriert.
    if (x > 10) {
        console.log("x ist größer als 10")
    }
Da wir häufig beim Abfragen einer Bedingung einen Codeblock oder im negativen Falle einen anderen Codeblock ausführen wollen können wir mit dem Schlüsselwort `else` Befehle geben, sofern die zugrunde liegende Bedingung falsch ist.

    let x = 5;

    // Nur der else Fall wird hier ausgeführt.
    if (x == 42) {
        console.log("Die Antwort ist 42");
    } else {
        console.log("Die Antwort ist nicht 42");
    }

Sollten wir mehrere Codeblöcke haben, von denen wir wollen, dass nur einer unter einer bestimmten Bedingung ausgeführt wird, so gibt es das Schlüsselwort `else if`, welches es uns erlaubt nach einer `if` Abfrage weitere Abfragen durchzuführen. Wichtig ist zu beachten, dass alle weiteren `else if` Bedingungen ignoriert werden, falls bereits eine frühere als wahr evaluiert wird.

    let  x = 10;
     
    if(x % 3 == 0) {
        // Wird nicht ausgeführt.
        console.log("x ist durch 3 teilbar."); 
    } else if (x % 5 == 0) {
        // Wird ausgeführt.
        console.log("x ist durch 5 teilbar."); 
    } else if (x % 2 == 0) {
        // Wird nicht ausgeführt. Da die vorherige Bedingung bereits wahr war. 
        console.log("x ist durch 2 teilbar."); 
    } else {
        // Wird nur ausgeführt, wenn keine Bedingung zutrifft.
        console.log("x ist weder durch 2, 3 noch 5 teilbar.");
    }

Eine andere Form der bedingten Ausführung sind `switch` Statements in JavaScript. Von der Synthax her wird bei switch ein Ausdruck ausgewertet und mit definierten Fällen abgeglichen.

    let tag = "Montag";

    switch(tag) {
        case "Montag":
            console.log("Es ist Montag");
            break;
        case "Dienstag":
            console.log("Es ist Dienstag");
            break;
        case "Dienstag":
            console.log("Es ist Mittwoch");
            break;
        case "Dienstag":
            console.log("Es ist Donnerstag");
            break;
        case "Dienstag":
            console.log("Es ist Freitag");
            break;
        default: 
            console.log("Es ist Wochenende");
    }

Wie wir diesem Beispiel entnehmen können können wir bedingte Ausführungen auch für andere Datentypen als *Number* durchführen. Wir werden die Vergleichsoperatoren auch noch andere Datentypen genauer unersuchen, um zu verstehen wie wir in diesen Fällen logische Aussagen treffen können. Wichtig ist, dass hier nach jedem `case` ein `break` gesetzt wird, da ansonsten nach dem ersten zutreffenden Fall auch alle weiteren Fälle ausgeführt werden. 

### Schleifen und Iteration
Die nächste wichtige Art von Steuerelementen sind `for`-Schleifen und Iteration. Wir brauchen Schleifen oder Iteration stets, wenn wir einen Codeblock sehr häufig mit minimaler oder keiner Anpassung erneut ausführen lassen wollen. Es gibt mehrere Arten von `for` Schleifen, aber wir werden hier nur die am häufigsten läufige Variante erklären. 

    for(let i = 0; i < 10; i++) {
        console.log("Das ist das " + i + "-te Mal");
    }

Auf den ersten Blick sieht eine `for`-Schleife sehr kompliziert aus, daher gehen wir auf alle Details ein. Um eine `for`-Schleifen auszuführen, müssen wir drei Befehle angeben. Der erste Ausdruck wird nur einmal zu Beginn der Schleife ausgeführt. Der zweite Ausdruck stellt eine Bedingung dar, welche vor jeder erneuten Ausführung erneut geprüft wird. Evaluiert die übergebene Bedingung zu `false`, so wird die Schleife abgebrochen, andernfalls wird der Codeblock im inneren ausgeführt. Die `for`-Schleife hat den Vorteil, dass wir eine eigene Variable nur für die Lebensdauer der Schleife definieren können, welche es uns erlaubt genau zu bestimmen in welcher Iteration wir uns befinden. Wenn wir aber einen Codeblock nur solange wiederholen wollen, wie eine bestimmte Bedingung gegeben ist, so eignet sich in diesem Fall eine `while`-Schleife besser.

    let bedingung1 = true;
    let bedingung2 = true;
    while(bedingung1 || bedingung2) {
        console.log("Das ist das " + i + "-te Mal");
        
        bedingung1 = false;
        if(!bedingung1) {
            bedingung2 = false;
        }
    }

Letztendlich kann man jede `for`-Schleife auch als `while`-Schleife schreiben kann und umgekehrt. Somit ist es unerheblich für welche Variante man sich entscheidet.
