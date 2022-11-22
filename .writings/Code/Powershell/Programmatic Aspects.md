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

>A single item can be added to the end of an array using the assignment by addition operator.

```powershell
$myArray = @() 
$myArray += "New value"
```

>In the background, a new array is created with one extra element. The content of the existing array is copied, then the value for the new element is assigned. Once complete, the original array, stored in memory, is removed. The larger the array, the less efficient this operation becomes.

>If an array is necessary, and the size of the array might change, a List (`System.Collections.Generic.List`) is often a better choice.

>Using `@()` around a set of elements or expressions is often the cleanest way to merge values into a single array.


```powershell
$firstArray = 1, 2, 3 
$mergedArray = @( 
	Get-Process 
	'someString' 
	$firstArray 
)
```

>Individual elements from an array may be selected by index.

>In a similar manner, array elements can be accessed counting backward from the end. The last element is available using -1 as the index, and the penultimate element using -2 as the index.

>Ranges of elements may be selected either going forward (starting from 0) or going backward (starting with -1).


```powershell
$myArray[2..4] 
$myArray[-1..-5]
```

Since arrays are immutable removing a value doesn't make sense. To achieve a similar effect a new array must be created where the elements of interest are absent and this can be done by iterating through all elements and filtering out the ones we don't want (either index-based or value-based filter).


```powershell
$newArray = for ($i = 0; $i -lt $oldArray.Count; $i++) { 
	if ($i -ne 49) { 
		$oldArray[$i] 
	} 
}
```

>Finally, an array may be completely emptied by calling the `Clear` method.

>*It is possible to create two (or more) variables when assigning an array*.

>If the array is longer than the number of variables, ==all remaining elements are assigned to the last variable==.

### Hashtables

>A **Hashtable** is an *associative array* or an indexed array. Values in the Hashtable are added with a unique key. Each key has a value associated with it; this is also known as a key-value pair. <u>Keys cannot be duplicated within the Hashtable</u>.

>*Hashtables are important in PowerShell*. They are used to create custom objects, to <u>pass parameters into commands</u>, to create custom properties using Select-Object, and as the type for values assigned to parameter values of many different commands, among other things.

>An empty Hashtable is created in the same manner as the following.

```powershell
$hashtable = @{}
```

```powershell
$hashtable = @{Key1 = "Value1"; Key2 = "Value2"}
$hashtable = @{ 
	Key1 = "Value1" 
	Key2 = "Value2" 
}
```

```powershell
$hashtable = @{} 
$hashtable.Add("Key1", "Value1")
```

>The `Contains` method returns true or false, depending on whether a key is present in $hashtable.


```powershell
$hashtable = @{ Existing = "Old" } 
$hashtable["New"] = "New" # Add this 
$hashtable["Existing"] = "Updated" # Update this

# OR 

$hashtable = @{ Existing = "Old" } 
$hashtable.New = "New" # Add this 
$hashtable.Existing = "Updated" # Update this
```

>==Keys cannot be added nor can values be changed while looping through the keys in a Hashtable using the keys property==. Doing so changes the underlying structure of the Hashtable, invalidating the iterator used by the loop operation.


```powershell
# Workaround
$hashtable = @{ Key1 = 'Value1' Key2 = 'Value2' } 
[Object[]]$keys = $hashtable.Keys 
foreach ($key in $keys) { $hashtable[$key] = "NewValue" }
```

>Keys can be returned using the Keys property of the Hashtable, which returns `KeyCollection`. 

```powershell
$hashtable.Keys 
```

>Values can be returned using the Values property, which returns `ValueCollection`. The key is discarded when using the Values property.

```powershell
$hashtable.Values
```

>An element can be removed using the `Remove` method.

### Lists

```powershell
$list = [System.Collections.Generic.List[String]]::new() 

# Add elements at the end of list
$list.Add("David")
$list.AddRange(@("Tim", "Robert"))

# Selecting elements
$index = $list.FindIndex( { $args[0] -eq 'Richard' } )
$list.IndexOf('Richard')
$list.BinarySearch('Richard')

# Removing eleemnts
$list.RemoveAt(1) # By Richard by index 
$list.Remove("Richard") # By Richard by value
$list.RemoveAll( { $args[0] -eq "David" } )
```

### Dictionaries

```powershell
$dictionary = [System.Collections.Generic.Dictionary[String,IPAddress]]::new()

$dictionary.Add("Computer1", "192.168.10.222")
$dictionary.Computer3 = "192.168.10.134"

if (-not $dictionary.ContainsKey("Computer2")) { 
	$dictionary.Add("Computer2", "192.168.10.13") 
}

$dictionary["Computer1"] # Key reference 
$dictionary.Computer1 # Dot-notation

$dictionary.Remove("Computer1")
```

### Queues

>A queue is a *first-in, first-out* ==array==. Elements are added to the end of the queue and taken from the beginning.

> PowerShell displays the contents of a queue in the same way as it would the contents of an array. <u>It is not possible to access elements of the queue by the index</u>.

```powershell
$queue = [System.Collections.Generic.Queue[String]]::new()

$queue.Enqueue("Tom") 
$queue.Enqueue("Richard") 
$queue.Enqueue("Harry")

$queue.Dequeue() # This returns Tom.

$queue.ToArray()
$queue.Peek()
```

>The queue has a `Peek` method that allows the retrieval of the next element in the queue without it being removed.

### Stacks

>A stack is a collection of objects in which objects are accessed in *Last-In, First-Out* (LIFO) order. Elements are added and removed from the top of the stack.


```powershell
$stack = [System.Collections.Generic.Stack[String]]::new()

$stack.Push("Up the road") 
$stack.Push("Over the gate") 
$stack.Push("Under the bridge")

$stack.Pop() # This returns Under the bridge

$stack.ToArray()
$stack.Peek()
```

# Conditionals

> An `if` statement is used to execute an action when a condition is met.


```powershell
if (<condition>) { 
	<statements>
}
```

>The `elseif` statement allows several conditions to be tested in order.


```powershell
if (<first-condition>) { 
	<first-statements>
} elseif (<second-condition>) { 
	<second-statements>
} elseif (<third-condition>) { 
	<third-statements>
}
```


>The `else` statement is optional and runs if all previous conditions evaluate to false.

```powershell
if (<condition>) { 
	<statements>
} else { 
	<alternative-statements>
}
```

>A `switch` statement executes statements where a case evaluates to `true`. The case can be a number, a string, or any other value.


```powershell
switch [-regex|-wildcard|-exact][-casesensitive] (<value>) { 
	<case> { <statements> } 
	<case> { <statements> } 
	default { <statements> } 
}
```

>The `switch` statement can be used on both scalar (single) values and arrays of values. If the value is an array, then each case will be tested against each element of the array.

```powershell
$arrayOfValues = 1..3 
switch ($arrayOfValues) { 
	1 { 'One' } 
	2 { 'Two' } 
	3 { 'Three' } 
}
```

>The wildcard parameter allows the use of the characters ? (any single character) and * (any string of characters) in a condition.

```powershell
switch -Wildcard ('cat') { 
	'c*' { Write-Host 'The word begins with c' } 
	'???' { Write-Host 'The word is 3 characters long' } 
	'*t' { Write-Host 'The word ends with t' } 
}
```

>The Regex parameter allows for the use of regular expressions to perform comparisons.

```powershell
switch -Regex ('cat') { 
	'^c' { Write-Host 'The word begins with c' } 
	'^[a-z]{3}$' { Write-Host 'The word is 3 characters long' } 
	't$' { Write-Host 'The word ends with t' } 
}
```

>`switch` allows a script block to be used in place of the simpler direct comparison cases used in the preceding sections. The script block is executed, and the result determines if the case is matched.

```powershell
switch (Get-Date) { 
	{ $_ -is [DateTime] } { Write-Host 'This is a DateTime type' } 
	{ $_.Year -ge 2020 } { Write-Host 'It is 2020 or later' } 
}
```

>The `break` and `continue` keywords may be used within the switch statement to control when it should stop testing a value. break *ends the switch statement*; continue, when the value is an array, *continues to the next element in the array*.

# Loops

>Loops may be used to iterate through collections, performing an operation against each element in the collection, or to repeat an operation (or series of operations) until a condition is met.

>==The foreach loop is perhaps the most common of these loops.==

```powershell
foreach ( <element> in <collection> ) { 
	<statement>
}
```

>If the collection is $null or empty, the body of the loop will not execute.

>If `foreach` is placed after a pipe then the alias is used, the `ForEach-Object` (foreach) is used.


```powershell
$array | foreach { }
```

>`do until` and `do while` each execute the body of the loop at least once, as the condition test is at the end of the loop statement. Loops based on do until will exit when the condition evaluates to `true`; loops based on do while will exit when the condition evaluates to `false`.


```powershell
do { 
	<body-statements>
} <until | while> (<condition>)
```

>The `break` keyword can be used to end a loop early.

>The `continue` keyword may be used to move on to the next iteration of a loop immediately.

>In PowerShell, a loop can be given a **label**. The label may be used with break and continue to define a specific loop to break from or continue to.

```powershell
:ThisIsALabel foreach ($value in 1..10) { 
	$value 
}
```

```powershell
:outerLoop for ($i = 1; $i -le 5; $i++) { 
	:innerLoop foreach ($value in 1..5) { 
		Write-Host "$i :: $value" 
		if ($value -eq $i) { 
			continue outerLoop 
		} 
	}
}
```






# Functions

>*Scripts*, *functions*, and *script* blocks share many of the same capabilities.
>1. Define parameters 
>2. Support pipeline input 
>3. Support common parameters, including support for `Confirm` and `WhatIf` 
>4. Allow other functions to be nested inside.

### 1. Parameters

>Parameters can be defined as a block using the `param` keyword, which is the most popular approach as parameter blocks in PowerShell can become quite large.


```powershell
function New-Function { 
	param ( 
		$parameter1, 
		$parameter2
	) 
}

# function-specific syntax
function New-Function($Parameter1, $Parameter2) { # Function body }
```

>==When used, the `param` block must appear before all other code.== An exception to this is `using` statements in a script, which must be written before `param`.


```powershell
param ( 
	[string]$Parameter1  # typed parameter
	[string]$Parameter2 = 'DefaultValue' # parameter with default value

	# an example of cross-referencing within a default value
	[string]$String, 
	[int]$Start, 
	[int]$Length = ($String.Length - $Start)

)
```

### 2. Pipeline


```powershell
function Show-Pipeline { 
	begin {  
		# before pipeline processing starts.
		
		# A pipeline that contains several commands will run each of the begin blocks for each command in turn before taking any further action.

		# can be used to create things that are reused by the process block
	} 

	process {
		# runs once for each value received from the pipeline. The built-in variable $_ or $PSItem may be used to access objects in the pipeline within the process block.
	}

	end {
		# executes after process has acted on all objects in the input pipeline.

		# $_ will be set to the last value received from a pipeline.
	}
}
```

>==PowerShell does not have a means of strictly enforcing the output from a script or function.==

>Any statement, composed of any number of commands, variables, properties, and method calls, may generate output. This ==output will be automatically sent to the output pipeline by PowerShell as it is generated==. <u>Unanticipated output can cause bugs in code</u>.

>When writing a function or script, it is important to *be aware of the output of the statements used*. If a statement generates output, and that ==output is not needed, it must be explicitly discarded==. PowerShell will not automatically discard output from commands in functions and scripts. There are several techniques available for dropping unwanted output; the following subsections show the common approaches.

>Piping output to `Out-Null` is a robust choice for discarding unwanted output.

```powershell
AppendLine() | Out-Null
```

>Redirection to `$null` can be added at the end of a statement to discard output.

```powershell
AppendLine() > $null
```

>It is possible to cast to `System.Void` to discard output.

```powershell
[Void](Get-Command Get-Command)
```

### 3. Common parameters & co

>The `CmdletBinding` attribute is used to turn a function into an advanced function and is placed immediately above a `param` block.
>- Add common parameters, such as ErrorAction, Verbose, Debug, ErrorVariable, WarningVariable, and so on 
>- Enable use of the built-in $PSCmdlet variable 
>- ==Declare support for `WhatIf` and `Confirm` and define the impact level of the command==

```powershell
function Test-EmptyParam { 
	[CmdletBinding()] 
	param ( ) 
}
```

[...]

### x. Docs

```powershell
function Get-Something { 
	<# 
		.SYNOPSIS 
		Briefly describes the main action performed by Get-Something 
		
		.DESCRIPTION 
		A detailed description of the activities of Get-Something. 
		
		.EXAMPLE 
		$something = Get-Something 
		$something | Do-Something 

		.NOTES
		This function is incomplete ...
		
		Gets something from somewhere. 
	#>
	
	param ( 
		# Describes the purpose of Parameter1. 
		$Parameter1, 
		# Describes the purpose of Parameter2. 
		$Parameter2 
	)
}
```







