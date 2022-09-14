# Tutorial: Finding and fixing errors in Java code

This tutorial shows how to find and fix errors in Java code with the help of IntelliJ IDEA.
This is test nine. Let's try git push. What else can we say.
Once a year, go some place you've never been before.
So what's your main focus for today?

IntelliJ IDEA automatically checks the code, highlights the possible problems, and offers
suggestions on how to fix these problems.
Let's try fixing errors found in a code sample with the help of these suggestions.

## Getting started

To start practicing, you need a new IntelliJ IDEA project with a code sample.

You can either download a ready-made project prepared for this tutorial
or just copy the code sample to an empty Java class.

### Option 1: Downloading a ready-made project

Download the [project .zip archive](https://github.com/arctic-dreamer/Tutorial/blob/main/codesample/calculations.tutorial.zip?raw=true)
with the code sample, unarchive it, and open it in IntelliJ IDEA.

If you are not sure how to open a project, here is [an instruction to help you](https://www.jetbrains.com/help/idea/import-project-or-module-wizard.html#open-project).

> The JDK version is not important for the current project. 
> If after opening the project IntelliJ IDEA warns you 
> that a certain version of JDK is missing and offers to download it, 
> you can ignore this notification.

### Option 2: Copying the tutorial code sample

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
}
```

If you need help creating a new project in IntelliJ IDEA, you can refer to these instructions:
- [How to create a new Java project](https://www.jetbrains.com/help/idea/creating-and-running-your-first-java-application.html#create-project).
- [How to create a package and a class](https://www.jetbrains.com/help/idea/creating-and-running-your-first-java-application.html#create-package-and-class).

### Moving on

This is how the project should look like:

![IntelliJ IDEA full-screen window of a project with a code example](/static/highlighted-problems.png)

The moment you paste the code, IntelliJ IDEA starts checking it and highlights the possible problems.
The bar in the upper right corner indicates the number of problems found.
Clicking this bar opens the "Problems" tab in the window below.
This tab lists every problem with the number of the line it was found in.
When you double-click one of the problems,
the caret automatically gets to the exact place where the problem is.

Now back to fixing errors.
Take a look at the problems highlighted by IDE:

- Error in line 5: `';' expected`.
- Error in line 6: `';' expected`.
- Error in line 7: `Cannot resolve symbol 'length'`.
- Warning in line 6: `Variable 'leength' is never used`.
- Typo in line 6: `Typo: In word 'leength'`.

As you can see, there are several syntax errors and one typo
that caused a warning and an error.
Let's start with the typo.

## Fixing a typo

There is a typo in the name of the `int` variable `length` in line 6.
This typo is also the cause of one warning (`Variable 'leength' is never used`)
and one error (`Cannot resolve symbol 'length'`).

This is how you can fix this typo using IntelliJ IDEA suggestions:

1. **Place the caret on the word with the typo**.

The moment you do so, a yellow bulb icon appears next to the current line
to give you suggestions about the fix.

2. **Click the yellow bulb icon** > **`Typo: Rename to…`**.

![A yellow bulb icon, which opens suggestions menu with fixing options](/static/yellow-bulb-suggestions.png)

IntelliJ IDEA suggests you to correct the typo according to the built-in dictionary.
After clicking the option `Typo: Rename to…`,
you will see that IntelliJ IDEA offers you to change the word to `length`:

![Fixing option: change 'leength' to 'length'](/static/typo-suggestion.png)

3. **Click `length`**.

IntelliJ IDEA automatically corrects the word.

With the typo gone, IntelliJ IDEA manages to find the variable.
As a result, the warning, and one of the errors disappear from the list of problems.
There are some other errors left to fix, though.

## Fixing syntax errors

Missing `;` symbol is a Java syntax error.
Let's fix it.
The process is similar to fixing typos.

1. **Place the caret on the red highlighted area on line 5**.

Again, a bulb icon appears next to the current line.
This time it's red-colored, which indicates an error.
IntelliJ IDEA is ready to give you suggestions about the fix.

2. **Click the red bulb icon, point to `Insert ;`, and move to the submenu option**.

![A red bulb icon, which opens suggestions menu with fixing options](/static/red-bulb-suggestions.png)

There are two suggestions to fix the error:
- `Insert ;` to insert the semicolon just in the current line (the main menu option).
- `Apply all 'Insert ;' fixes in file` to insert the semicolon in every place it is missing (the submenu option).

3. **Click `Apply all 'Insert ;' fixes in file`**.

With one click, you've just fixed two errors in lines 5 and 6.

The syntax is now correct, so IntelliJ IDEA tries to compile the program one more time 
and checks it for any other problems.
As a result of such a check, IDE finds two new errors and adds them to the list.
Let's look into it.

## Fixing wrong variable types

After the new check, IntelliJ IDEA added two new errors to the list of problems:

- Error in line 5: `Incompatible types. Found: 'double', required: 'int'`.
- Error in line 6: `Incompatible types. Found: 'double', required: 'int'`.

![The "Problems" tab with the list of errors](/static/wrong-variables.png)

It seems that the length of the sides of a rectangle is given in decimals (5.4 and 4.6).
The variable type is `int` though, which is for integers only.

Let's see what hints IntelliJ IDEA gives you to fix it.

1. **Place the caret anywhere on line 5**.

2. **Click the red bulb icon**.

![A red bulb icon, which opens suggestions menu with fixing options](/static/wrong-variables-fix-suggestions.png)

IntelliJ IDEA offers three solutions here:

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

4. **Change `int` for `double` in line 6 the same way you just did in line 5**.

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

In the "Problems" tab, you can see the message *"No problems in Area.java"*.

## Running the program

As no more problems are highlighted, let's run the program and find out what's the area of a rectangle is.

> For detailed instructions on how to build and run Java applications, refer to [this guide](https://www.jetbrains.com/help/idea/creating-and-running-your-first-java-application.html#run_app). 

To run the program:

1. **Click the green 'play' button in the gutter**.

![Clicking green play button opens a popup menu](/static/run-program.png)

2. **Click `Run 'Area.main()'`**

IntelliJ IDEA compiles and then runs the program.
The result is shown in the run tool window below.

The output is `Process finished with exit code 0`, 
which means the program was executed successfully without errors.

And here comes the result of the calculations for the parameters we set:
`The area of a rectangle is 24.84 square meters.`

![IntelliJ IDEA full-screen window with the final result](/static/final-result.png)

Well done!
