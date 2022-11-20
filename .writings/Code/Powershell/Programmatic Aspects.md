# Components

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

>The `New-Variable` command can be used to create a variable.

```powershell
New-Variable -Name today -Value (Get-Date)

// <=>

$today = Get-Date
```

>`New-Variable` gives more control over the created variable, including adding metadata such as descriptions.

```powershell
New-Variable -Name startTime -Value (Get-Date) -Option Constant
```

>the `Remove-Variable` command removes a variable. If this is the only variable referring to an object, the object will be removed from memory shortly afterward.

>The `Set-Variable` command allows certain properties of an existing variable to be changed.

## Variable Provider

>`Get-ChildItem` may be used to *list all the variables in the current scope* by running,

```powershell
Get-ChildItem variable:
```

>`Test-Path` may be used to determine whether a variable exists. 

```powershell
Test-Path variable:\VerbosePreference
```

>Note: Get-Variable may be used instead, but Get-Variable will throw an error if the variable does not exist.

```powershell
Set-Item variable:\new -Value variable
Get-Content variable:\OutputEncoding
```

>PowerShell uses scopes to *limit access to variables* (and other items, such as functions). **Scopes are layered one on top of another**; *child scopes inherit from parent scopes*. Parent scopes **cannot** access variables created in child scopes.

> 1. ***Global*** is the topmost scope; it is the scope the prompt in the console uses and is available to all child scopes.
> 2. ***Script*** scope, as the name suggests, is specific to a single script. Script-scoped items are available to all child scopes (such as functions) within that script. The Script scope is also available in modules, making it an *ideal place to store variables that should be shared within a module*.
> 3. ***Local*** is the current scope and *is therefore relative*. In the console, the Local scope is also the Global scope. In a script, the Local scope is the Script scope. Functions and ScriptBlock also have a Local scope of their own.

>When PowerShell retrieves the value for a variable, <u>it starts by looking for the variable in the Local scope</u>. If the variable does not exist in the Local scope, it looks through parent scopes until it either finds the variable or it runs out of scopes to search.


```powershell
$Global:variableName = 123
```

>Note: A private variable is hidden from child scopes. (to elaborate on later)

## Type Conversion

>Type conversion in PowerShell is used to change between different types of values.

>*Type names are written between square brackets*.


```powershell
[String](Get-Date) # 10/27/2016 13:14:32

[DateTime]"01/01/2016" # 01 January 2016 00:00:00
# OR
'01/01/2016' -as [DateTime]
```

>If the cast fails, an error will be displayed. ==If the cast fails when using `-as`, no error is returned and the result of the expression will be `null`.==

> NOTE: When assigning values, casting may be performed on either the left-hand side or right-hand side of the expression.

>*Casting on the right-hand* side has **no impact on subsequent assignments** to the variable. If the ==type is placed on the left-hand side== of the assignment, the type will also **apply to any subsequent assignments to the variable**.

## Numerics

>The following list shows the suffixes that can be added to numeric values to influence the resulting type: 
>
>- s: short, Int16, or a signed 16-bit integer 
>- us: ushort, UInt16, or an unsigned 16-bit integer 
>- u: uint, UInt32, or an unsigned 32-bit integer 
>- l: long, Int64, or a signed 64-bit integer 
>- ul: ulong, UInt64, or an unsigned 64-bit integer 
>- d: Decimal

## Arrays

>***Arrays*** in PowerShell (and .NET) *are immutable* (fixed size). <u>The size is declared on creation and cannot be changed</u>. A new array must be created if an element is to be added or removed.

>An empty array (containing no elements) can be created as follows,


```powershell
$myArray = @()
```

```powershell
$myArray = [Object[]]::new(10) # 10 objects 
$byteArray = [Byte[]]::new(100) # 100 bytes 
$ipAddresses = [IPAddress[]]::new(5) # 5 IP addresses
```

```powershell
$myGreetings = "Hello world", "Hello sun", "Hello moon"
$myGreetings = @("Hello world", "Hello sun", "Hello moon")
$myGreetings = @( 
	"Hello world" 
	"Hello sun" 
	"Hello moon" 
)
# All equivalent.
```



## Objects


# Conditionals

# Loops

# Functions
