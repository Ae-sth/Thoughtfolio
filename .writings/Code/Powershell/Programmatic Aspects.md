## Components

>Variables in PowerShell are preceded by the dollar symbol (`$`).

>The name of a variable may contain numbers, letters, and underscores.

>*It is possible to use more complex variable names using the bracing style.*

```powershell
${My Variable}
```

>One of the most commonly accepted practices is that *variables used as parameters* must use **Pascal case**. *Variables used only within* a script or a function must use **camel case**.

>Variables do not need to be declared prior to use, nor does a variable need to be assigned a specific type.

>It is possible to assign the same value to several variables in one statement.

```powershell
$i = $j = 0
```

### Types

> PowerShell (and all other .NET languages) has two main categories of types, *value types* and *reference types*.

>When a value type is used, for instance, by assigning it to another variable or using the variable as an argument for a parameter, *the value is copied*.

>A variable assigned a reference type holds only the reference to that object (not the object itself). Two (or more) variables may reference the same object. ... When used as an argument for a parameter, the reference to the object is passed (the object is not copied).

>A string is not a value type, but it has the same behavior. *Strings are immutable – any change to a string will result in the creation of a new string*. Strings therefore behave in much the same way as value types.

### Variable Commands

>The `Clear-Variable` command *removes the value* from any existing variable.

>The `Get-Variable` command provides *access to any variable* that has been *created in the current session* as well as *the default (automatic) variables created by PowerShell*.



## Conditionals

## Loops

## Functions
