# Pfeilfunktionen, die Grundlagen

Es gibt eine weitere sehr einfache und prägnante Syntax für die Erstellung von Funktionen, die oft besser ist als der Funktionsausdruck.

Sie werden Pfeilfunktionen genannt, weil sie so aussehen:

```js
let func = (arg1, arg2, ..., argN) => expression;
```

<<<<<<< HEAD
...Dies erzeugt eine Funktion `func`, welche die Argumente `arg1..argN` akzeptiert, dann den Ausdruck `expression` auf der rechten Seite auswertet und ihr Ergebnis zurückgibt.
=======
This creates a function `func` that accepts arguments `arg1..argN`, then evaluates the `expression` on the right side with their use and returns its result.
>>>>>>> 29216730a877be28d0a75a459676db6e7f5c4834

In anderen Worten, es ist die verkürzte Version von:

```js
let func = function(arg1, arg2, ..., argN) {
  return expression;
};
```

Sehen wir uns ein konkretes Beispiel an:

```js run
let sum = (a, b) => a + b;

/* Diese Pfeilfunktion ist eine kürzere Form von:

let sum = function(a, b) {
  return a + b;
};
*/

alert( sum(1, 2) ); // 3
```

<<<<<<< HEAD
Wie man sehen kann, hat `(a, b) => a + b` die Bedeutung einer Funktion, die zwei Argumente `a` and `b` akzeptiert. Bei der Ausführung wird der Wert `a + b` ausgewertet und das Ergebnis zurückgegegeben.
=======
As you can see, `(a, b) => a + b` means a function that accepts two arguments named `a` and `b`. Upon the execution, it evaluates the expression `a + b` and returns the result.
>>>>>>> 29216730a877be28d0a75a459676db6e7f5c4834

- Wenn nur ein Argument vorhanden ist, können die Klammern um den Parameter wegelassen werden, was den Ausdruck noch weiter verkürzt.

    Zum Beispiel:

    ```js run
    *!*
    let double = n => n * 2;
    // ungefähr dasselbe wie: let double = function(n) { return n * 2 }
    */!*

    alert( double(3) ); // 6
    ```

<<<<<<< HEAD
- Wenn es keine Argument gibt, sind die Klammern leer (aber sie sollte vorhanden sein):
=======
- If there are no arguments, parentheses are empty, but they must be present:
>>>>>>> ac7daa516fa8e687427eac51186af97154748afa

    ```js run
    let sayHi = () => alert("Hallo!");

    sayHi();
    ```

Pfeilfunktionen können auf die gleiche Weise wie Funktionsausdrücke verwendet werden.

Zum Beispiel, um eine Funktion dynamisch zu erstellen:

```js run
let age = prompt("Wie alt bist Du?", 18);

let welcome = (age < 18) ?
<<<<<<< HEAD
  () => alert('Hallo') :
  () => alert("Grüße!");
=======
  () => alert('Hello!') :
  () => alert("Greetings!");
>>>>>>> 291b5c05b99452cf8a0d32bd32426926dbcc0ce0

welcome();
```

Pfeilfunktion mögen auf den ersten Blick ungewohnt und nicht sehr lesbar erscheinen, aber das ändert sich schnell, wenn sich die Augen an die Struktur gewöhnen.

Sie sind sehr praktisch für einfache einzeilige Aktionen, wenn wir einfach zu faul sind, viele Worte zu schreiben.

## Mehrzeilige Pfeilfunktionen

<<<<<<< HEAD
Die Beispiele oben nahmen Argumente von der linken Seite `=>` und bewerteten damit den Ausdruck auf der rechten Seite.

Manchmal brauchen wir etwas Komplexeres, wie mehrfache Ausdrücke oder Anweisungen. Das ist auch möglich, aber wir sollten sie in geschweifte Klammern einschließen. Dann verwende ein normales `return` innerhalb dieser Klammern.
=======
The arrow functions that we've seen so far were very simple. They took arguments from the left of `=>`, evaluated and returned the right-side expression with them.

Sometimes we need a more complex function, with multiple expressions and statements. In that case, we can enclose them in curly braces. The major difference is that curly braces require a `return` within them to return a value (just like a regular function does).
>>>>>>> ac7daa516fa8e687427eac51186af97154748afa

Etwa so:

```js run
let sum = (a, b) => {  // die geschweifte Klammer öffnet eine mehrzeilige Funktion
  let result = a + b;
*!*
<<<<<<< HEAD
  return result; // wenn wir geschweifte Klammern verwenden, dann brauchen wir ein explizites "return"
=======
  return result; // if we use curly braces, then we need an explicit "return"
>>>>>>> 29216730a877be28d0a75a459676db6e7f5c4834
*/!*
};

alert( sum(1, 2) ); // 3
```

```smart header="Noch mehr später"
Wir haben Pfeilfunktionen für ihre Kürze gelobt. Aber das ist nicht alles!

Pfeilfunktionen haben weitere interessante Eigenschaften.

Um diese zu verstehen, müssen wir erst einige weitere Aspekte von JavaScript kennenlernen. Wir werden im Kapitel <info:arrow-functions> zu Pfeilfunktion zurückkehren.

Für den Moment können wir Pfeilfunktionen für einzeilige Aktionen und Callback-Funktionen verwenden.
```

## Zusammenfassung

<<<<<<< HEAD
Pfeilfunktionen sind praktische Einzeiler. Es gibt sie in zwei Varianten:

1. Ohne geschweifte Klammern: `(...args) => expression` -- die rechte Seite ist ein Ausdruck: die Funktion wertet diesen aus und gibt das Ergebnis zurück.
2. Mit geschweiften Klammern: `(...args) => { body }` -- Klammern erlauben es mehrere Anweisungen zu schreiben, aber es braucht ein explizites `return` um etwas zurückzugeben.
=======
Arrow functions are handy for simple actions, especially for one-liners. They come in two flavors:

1. Without curly braces: `(...args) => expression` -- the right side is an expression: the function evaluates it and returns the result. Parentheses can be omitted, if there's only a single argument, e.g. `n => n*2`.
2. With curly braces: `(...args) => { body }` -- brackets allow us to write multiple statements inside the function, but we need an explicit `return` to return something.
>>>>>>> ac7daa516fa8e687427eac51186af97154748afa
