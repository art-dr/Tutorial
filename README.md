# Tutorial: Finding and fixing errors in Java code

This tutorial shows how to find and fix errors in Java code with the help of IntelliJ IDEA.

IDEA automatically checks the code, highlights the possible problems, and offers
suggestions on how to fix these problems.
Let's try fixing errors found in a code sample with the help of these suggestions.

## Getting started

To start practicing, download the [project archive](https://github.com/arctic-dreamer/Tutorial/blob/main/codesample/calculations.tutorial.zip?raw=true)
with a code sample and open it IntelliJ IDEA.

If you don't need a ready-made project, just copy the code from the example below
and paste it to an empty Java class:

```java
package rectangle;

public class Area {
    public static void main(String[] args) {
        int width = 5.4
        int leength = 4.6 
        int area = width * length;
        
        System.out.println("The area of a rectangle is " + area + " square meters.");

}
```

Here is how the project should look like:

![IntelliJ IDEA full-screen window of a project with a code example](/static/highlighted-problems.png)

The moment you paste the code, IDEA starts checking it and highlights the possible problems.
The bar in the upper right corner indicates the number of problems found.

Also, in the window below, there is the "Problems" tab.
It lists every problem with the number of the line it was found in.
When you double-click one of the problems,
the caret automatically gets to the exact place where the problem is.

Now back to fixing errors.
Take a look at the problems highlighted by IDEA:

- Error in line 5: `';' expected`.
- Error in line 6: `';' expected`.
- Error in line 7: `Cannot resolve symbol 'length'`.
- Error in line 11: `'}' expected`.
- Warning in line 6: `Variable 'leength' is never used`.
- Typo in line 6: `Typo: In word 'leength'`.

As you can see, there are several syntax errors and one typo
that caused a warning and an error.
Let's start with the typo.

## Fixing a typo

There is a typo in the name of the `int` variable `length` in line 6.
This typo is also the cause of one warning (`Variable 'leength' is never used`)
and one error (`Cannot resolve symbol 'length'`).

Imagine you do not remember how to spell the word "length" correctly.
This is how you can fix this typo using IDEA suggestions:

1. **Place the caret on the word with the typo**.

The moment you do so, a yellow bulb icon appears next to the current line
to give you suggestions about the fix.

2. **Click the yellow bulb icon** > **`Typo: Rename to…`**.

![A yellow bulb icon, which opens suggestions menu with fixing options](/static/yellow-bulb-suggestions.png)

IDEA suggests you to correct the typo according to the built-in dictionary.
After clicking the option `Typo: Rename to…`,
you will see that IDEA offers you to change the word to `length`:

![Fixing option: change 'leength' to 'length'](/static/typo-suggestion.png)

3. **Click `length`**.

IDEA automatically corrects the word.

As a result, the typo, the warning, and one of the errors have disappeared from the list of problems.
There are some other errors left to fix, though.

## Fixing syntax errors

Missing `;` and `}` symbols are Java syntax errors.
Let's fix the missing semicolon first.
The process is similar to fixing typos.

1. **Place the caret on the red highlighted area on line 5**.

Again, a bulb icon appears next to the current line.
This time it's red-colored, which indicates an error.
IDEA is ready to give you suggestions about the fix.

2. **Click the red bulb icon**.

![A red bulb icon, which opens suggestions menu with fixing options](/static/red-bulb-suggestions.png)

There are two suggestions here:
- `Insert ;` to insert the semicolon just in the current line.
- `Apply all 'Insert ;' fixes in file` to insert the semicolon in every place it is missing.

3. **Click `Apply all 'Insert ;' fixes in file`**.

With one click you've just fixed two errors in lines 5 and 6.

Only one syntax error left: `'}' expected` in line 11.
As you've already learned how to fix syntax errors using IDEA suggestions,
you can just add the missing symbol manually to save time.

## Fixing wrong variable types

Now that you've fixed the syntax errors, IDEA can compile the program and check it for any other problems.
As a result of such a check, IDEA added two new errors to the list:

- Error in line 5: `Incompatible types. Found: 'double', required: 'int'`.
- Error in line 6: `Incompatible types. Found: 'double', required: 'int'`.

![The "Problems" tab with the list of errors](/static/wrong-variables.png)

It seems that the length of the sides of a rectangular is given in decimals (5.4 and 4.6).
The variable type is `int` though, which is for integers only.

Let's see what hints IDEA gives you to fix it.

1. **Place the caret anywhere on line 5**.

2. **Click the red bulb icon**.

![A red bulb icon, which opens suggestions menu with fixing options](/static/wrong-variables-fix-suggestions.png)

IDEA offers three solutions here:

- `Cast to 'int'`,
  which transforms the line the following way: `int width = (int) 5.4;`.
  As a result, only the number before the point will be taken for calculations.
- `Migrate width type to 'double'`,
  which changes `int` to `double` in every line where `width` is used.
- `Change variable 'width' type to 'double'`,
  which changes `int` to `double` only in the current line.

Let's choose the second option to make changes in every line where `width` is used.

3. **Click `Migrate width type to 'double'`**.

The error is now fixed.

Change `int` for `double` in line 6 the same way you just did in line 5.

## Making final checks

As a result, the code should look like this:

```java
package rectangle;

public class Area {
    public static void main(String[] args) {
        double width = 5.4;
        double length = 4.6;
        double area = width * length;

        System.out.println("The area of a rectangle is " + area + " square meters.");

    }
}
```

In the "Problems" tab, you can see the message *"No problems in Area.java"*:

![IntelliJ IDEA full-screen window with the final version of the project](/static/no-problems-in-project.png)

Well done!
