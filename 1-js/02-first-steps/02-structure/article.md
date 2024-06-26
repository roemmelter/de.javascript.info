# Code-Struktur

Das Erste, was wir untersuchen werden, sind die Bausteine des Codes.

## Anweisungen

Anweisungen sind Syntaxkonstrukte und Befehle, die Aktionen ausführen.

Wir haben bereits eine Anweisung `alert('Hallo, Welt!')` gesehen, welche die Meldung "Hallo, Welt!" zeigt.

Wir können so viele Anweisungen in unserem Code haben, wie wir wollen. Anweisungen können durch ein Semikolon getrennt werden.

Zum Beispiel teilen wir hier "Hallo Welt" in zwei Warnungen:

```js run no-beautify
alert('Hallo'); alert('Welt');
```

Normalerweise werden Anweisungen in separate Zeilen geschrieben, um den Code besser lesbar zu machen:

```js run no-beautify
alert('Hallo');
alert('Welt');
```

## Semikolons [#semicolon]

Ein Semikolon kann in den meisten Fällen weggelassen werden, wenn ein Zeilenumbruch vorliegt.

Das würde auch funktionieren:

```js run no-beautify
alert('Hallo')
alert('Welt')
```

Hier interpretiert JavaScript den Zeilenumbruch als "implizites" Semikolon. Dies wird als [automatische Semikoloneinfügung](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) bezeichnet.

**In den meisten Fällen bedeutet ein Zeilenumbruch ein Semikolon. "Meistens" heißt aber nicht "immer"!**

Es gibt Fälle, in denen ein Zeilenumbruch kein Semikolon bedeutet. Beispielsweise:

```js run no-beautify
alert(3 +
1
+ 2);
```

<<<<<<< HEAD
Der Code gibt `6` aus, da JavaScript hier keine Semikolons einfügt. Es ist intuitiv klar, dass, wenn die Zeile mit einem Pluszeichen `"+"` endet, es sich um einen "unvollständigen Ausdruck" handelt, sodass das Semikolon nicht erforderlich ist. Und in diesem Fall funktioniert das wie vorgesehen.
=======
The code outputs `6` because JavaScript does not insert semicolons here. It is intuitively obvious that if the line ends with a plus `"+"`, then it is an "incomplete expression", so a semicolon there would be incorrect. And in this case, that works as intended.
>>>>>>> a82915575863d33db6b892087975f84dea6cb425

**Es gibt jedoch Situationen, in denen JavaScript ein Semikolon nicht annimmt, wenn es wirklich benötigt wird.**

Fehler, die in solchen Fällen auftreten, sind schwer zu finden und zu beheben.

````smart header="Ein Beispiel für einen Fehler"
Wenn du ein konkretes Beispiel für einen solchen Fehler sehen möchten, lies den folgenden Code:

```js run
alert("Hello");

[1, 2].forEach(alert);
```

<<<<<<< HEAD
Über die Bedeutung der Klammern `[]` und `forEach` muss noch nicht nachgedacht werden. Wir werden sie später studieren. Denk vorerst nur an das Ergebnis des Codes: Es zeigt `1`, dann `2`.

Fügen wir nun vor dem Code einen `alert` ein und beenden ihn *nicht* mit einem Semikolon:

```js run no-beautify
alert("Es wird ein Fehler auftreten")
=======
No need to think about the meaning of the brackets `[]` and `forEach` yet. We'll study them later. For now, just remember the result of running the code: it shows `Hello`, then `1`, then `2`.

Now let's remove the semicolon after the `alert`:

```js run no-beautify
alert("Hello")
>>>>>>> a82915575863d33db6b892087975f84dea6cb425

[1, 2].forEach(alert);
```

<<<<<<< HEAD
Wenn wir nun den Code ausführen, wird nur der erste `alert` angezeigt und dann haben wir einen Fehler!

Aber alles ist wieder in Ordnung, wenn wir nach `alert` ein Semikolon einfügen:
```js run
alert("Jetzt ist alles in Ordnung");

[1, 2].forEach(alert)
```

Jetzt haben wir die Nachricht "Jetzt ist alles in Ordnung" gefolgt von `1` und `2`.


Der Fehler in der Variante ohne Semikolon tritt auf, weil JavaScript kein Semikolon vor eckigen Klammern `[...]` annimmt.

Da das Semikolon nicht automatisch eingefügt wird, wird der Code im ersten Beispiel als einzelne Anweisung behandelt. So sieht es die Engine:

```js run no-beautify
alert("Es wird ein Fehler auftreten")[1, 2].forEach(alert)
```

Aber es sollten zwei getrennte Anweisungen sein, nicht eine. Eine solche Verschmelzung ist in diesem Fall einfach falsch, daher der Fehler. Dies kann auch in anderen Situationen auftreten.
=======
The difference compared to the code above is only one character: the semicolon at the end of the first line is gone.

If we run this code, only the first `Hello` shows (and there's an error, you may need to open the console to see it). There are no numbers any more.

That's because JavaScript does not assume a semicolon before square brackets `[...]`. So, the code in the last example is treated as a single statement.

Here's how the engine sees it:

```js run no-beautify
alert("Hello")[1, 2].forEach(alert);
```

Looks weird, right? Such merging in this case is just wrong. We need to put a semicolon after `alert` for the code to work correctly.

This can happen in other situations also.
>>>>>>> a82915575863d33db6b892087975f84dea6cb425
````

Es wird empfohlen, Semikolons zwischen Anweisungen zu setzen, auch wenn diese durch Zeilenumbrüche getrennt sind. Diese Regel wird von der Community weitgehend übernommen. Lass uns noch einmal festhalten -- es ist möglich, Semikolons die meiste Zeit wegzulassen. Aber es ist sicherer -- besonders für Anfänger -- sie zu benutzen.

## Kommentare [#code-comments]

Mit der Zeit werden Programme immer komplexer. Es müssen *Kommentare* hinzugefügt werden, die beschreiben, was der Code macht und warum.

Kommentare können an jeder Stelle eines Skripts eingefügt werden. Sie haben keinen Einfluss auf die Ausführung, da die Engine sie einfach ignoriert.

**Einzeilige Kommentare beginnen mit zwei Schrägstrichen `//`.**

Der Rest der Zeile ist ein Kommentar. Er kann eine ganze eigene Zeile belegen oder einer Anweisung folgen.

Wie hier:
```js run
// Dieser Kommentar belegt eine eigene Zeile
alert('Hallo');

alert('Welt'); // Dieser Kommentar folgt der Anweisung
```

**Mehrzeilige Kommentare beginnen mit einem Schrägstrich und einem Sternchen <code>/&#42;</code> und enden mit einem Sternchen und einem Schrägstrich <code>&#42;/</code>.**

So wie hier:

```js run
/* Ein Beispiel mit zwei Nachrichten.
Dies ist ein mehrzeiliger Kommentar.
*/
alert('Hallo');
alert('Welt');
```

Der Inhalt von Kommentaren wird ignoriert. Wenn wir also Code innerhalb <code>/&#42; ... &#42;/</code> einfügen, wird er nicht ausgeführt.

Manchmal kann es nützlich sein, einen Teil des Codes vorübergehend zu deaktivieren:

```js run
/* Code auskommentieren
alert('Hallo');
*/
alert('Welt');
```

<<<<<<< HEAD
```smart header="Benutze Tastenkombination!"
In den meisten Editoren kannst du eine Codezeile auskommentieren, indem du die Tastenkombination `key:Strg+/` für einen einzeiligen Kommentar und die Tastenkombination `key:Strg+Umschalt+/` für mehrzeilige Kommentare drückst (wähle ein Stück Code aus und drücke die Tastenkombination). Für Mac versuche "key:Cmd" anstelle von "key:Strg" und `key:Option` statt `key:Umschalt`.
=======
```smart header="Use hotkeys!"
In most editors, a line of code can be commented out by pressing the `key:Ctrl+/` hotkey for a single-line comment and something like `key:Ctrl+Shift+/` -- for multiline comments (select a piece of code and press the hotkey). For Mac, try `key:Cmd` instead of `key:Ctrl` and `key:Option` instead of `key:Shift`.
>>>>>>> 23ffde780605b3418101850a61d9496c3d7f927c
```

````warn header="Verschachtelte Kommentare werden nicht unterstützt!"
Es ist nicht möglich `/*...*/` innerhalb eines anderen `/*...*/` zu setzen.

Solcher Code resultiert in einem Fehler:

```js run no-beautify
/*
  /* verschachtelter Kommentar ?!? */
*/
alert( 'Welt' );
```
````

Bitte zögere nicht, deinen Code zu kommentieren.

Kommentare vergrößern den gesamten Code-Fussabdruck, aber das ist überhaupt kein Problem. Es gibt viele Werkzeuge, die den Code vor dem Veröffentlichen auf einem Produktionsserver minimieren. Sie entfernen Kommentare, sodass sie nicht in den Arbeitsskripten angezeigt werden. Kommentare wirken sich daher überhaupt nicht negativ auf die Produktion aus.

Später im Tutorial wird es ein Kapitel <info:code-quality> geben, in dem auch erklärt wird, wie man bessere Kommentare schreibt.
