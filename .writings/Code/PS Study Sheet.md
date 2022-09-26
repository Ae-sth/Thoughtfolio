# Powershell Study Sheet
---
All command following the `Verb-Noun` naming convention.

## Discovery Commands
If we want to get info about a given command we can use `Get-Help <Command>` and if we want to check if a given command exists `Get-Command <Hint>`.

### Command Verbs
Checkout, https://learn.microsoft.com/en-us/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands?view=powershell-7.

### Commands Nouns
A short description of the object the command is expected to act on.

### Aliases
It is possible create a different reference to a command using `<Set-Alias>` and list all defined aliases in the system using `<Get-Alias>`.

### Providers
A provider in PowerShell is a specialized interface to a service or dataset that presents items to the end user in the same style as a filesystem. All operating systems offer the following providers, `Alias`, `Environment`, `FileSystem`, `Function` and `Variable`

### Drives
Drives are labels used to access data from providers by name. Drives are automatically made available for FileSystem based on the drive letters used for mounted partition in Windows.

### Splatting
Splatting is a way of defining the parameters of a command before calling it.
```powershell
$parameters = @{
	Prop = value
}
& Exec-Cmd @parameters
```

### Pipelines
The pipeline is used to send output from one command to another command as input.
```powershell
<First-Cmd> | <Second-Cmd>
```

### Streams
There are different kinds of output. Each of these different types of output is sent to a different stream, allowing each to be read separately. In PowerShell, the streams are Standard, Error, Warning, Verbose, Debug, and Information.

When assigning the output of a command to a variable, the assigned value is taken from the standard output (the output stream) of a command. 
```Powershell
$output = Exec-Cmd <parameters> # 'output' will contain what is pushed through the stdout.
```

Non-standard output, such as Verbose, will not be assigned to the variable.

```powershell
Write-Output # write to stdout
Write-Error # write to stderr
Write-Warning 
Write-Verbose 
Write-Debug 
Write-Information
```

The pipe (|) symbol is used to send the standard output (stdout) between commands.

### Objects
Everything in powershell is an object. To create an object we can use the command `New-Object`. 

### Members
The `Get-Member` command can be used to view the different members of an object. 
```powershell
# Use Pattern
Get-Process -Id $PID | Get-Member -MemberType Property #
```

1. The properties of an object in PowerShell may be accessed by writing the property name after a period, `<Object>.Property`.

The properties of an object are objects themselves.

If a property name has a space, it may be accessed using a number of different notation styles.

```powershell
$object."Some Name"
$object.'Some Name'
$object.{Some Name}
```

2. Methods effect a change in state, `<Object>.Method()`. That may be a change to the object associated with the method, or it may take the object and convert it into something else.

*Note: When a method is called without parentheses, PowerShell will show the overload definitions.*

`Add-Member` allows new members to be added to existing objects. This can be useful if the object type must be preserved.

```powershell
$empty = New-Object Object # Create an empty object.

# Adding a property.
$empty | Add-Member -NotePropertyName <Name> -NotePropertyValue <Value>
$empty | Add-Member -Name <Name> -MemberType ScriptProperty -Value {
	# We can use '$this' to refer to properties already existing within the object to compute the value for this property.
}

# Adding a method.
$method = @{
	Name = "MethodName"
	MemberType = "ScriptMethod"
	Value = {
		# Operation that changes the object. 
	}
}
```

*Note: The reserved variable $this is used to refer to itself.*

### Iteration
`ForEach-Object` may be used to work on an existing collection or objects, or used to work on the output from another command in a pipeline.

```powershell
Get-Process | ForEach-Object {
	Write-Host $_.Name -ForegroundColor Green
}
```

The special variable `$_` is used to access the current object.

```powershell
1..5 | ForEach-Object -Begin {
	Write-Host "Starting the pipeline. Creating value."
	$value = 0
} -Process {
	Write-Host "Adding $_ to value."
	$value += $_
} -End {
	Write-Host "Finished the pipeline. Displaying value."
	$value
}
```

In PowerShell 7, ForEach-Object gains a Parallel parameter. This, as the name suggests, can be used to run process blocks in parallel rather than one after another.

By default, ForEach-Object runs 5 instances of the process block at a time; this is controlled by the ThrottleLimit parameter. The limit may be increased (or decreased) depending on where the bottleneck is with a given process.

```powershell
1..10 | ForEach-Object -Parallel {
	Start-Sleep -Seconds 2
	$_
}
```

When using Parallel , each parallel script block runs in a separate thread.

```powershell
$string = 'Hello world'
1 | ForEach-Object -Parallel {
	# The $string variable is only accessible if using is used.
	$using:string
}
```

*Note: The snippet above shows how to access a variable define outside the parallel-script scope via the `$using:` accessor.*

*Note: For the most part, the $using scope modifier is one-way. That is, values may be **read** from the scope, but new values cannot be set.*


### Iteration+Filtering
`ForEach-Object` may also be used to get a single property via the parameter `-MemberName <Member>`.

```powershell
Get-Process | ForEach-Object -MemberName Path
```

### Filtering
Filtering the output from commands may be performed using `Where-Object`. 
```powershell
# Returns the processes that started after 9 AM.
Get-Process | Where-Object StartTime -gt (Get-Date 9:00:00)
# OR
Get-Process |
	Where-Object -Property StartTime -Value (Get-Date 9:00:00) -gt
```

`Where-Object` also accepts filters using the `FilterScript` parameter.
```powershell
Get-Service | Where-Object {
	$_.StartType -eq 'Manual' -and
	$_.Status -eq 'Running'
}
```

### Selecting
`Select-Object` acts on an input pipeline; either an existing collection of objects, or the output from another command. `Select-Object` can be used to select a subset of properties, to change properties, or to add new properties. `Select-Object` also allows a user to limit the number of objects returned.

```powershell
# limit the properties returned by a command by name:
Get-Process | Select-Object -Property Name, Id
# limit the properties returned from a command using wildcards:
Get-Process | Select-Object -Property Name, *Memory
#  list everything but a few properties:
Get-Process | Select-Object -Property * -ExcludeProperty *Memory*
#  get the first few objects in a pipeline:
Get-ChildItem C:\ -Recurse | Select-Object -First 2
# select the last few objects in a pipeline:
Get-ChildItem C:\ | Select-Object -Last 3
# skip items at the beginning – in this example, it selects the fifth item:
Get-ChildItem C:\ | Select-Object -Skip 4 -First 1
# get an object from a pipeline by index:
Get-ChildItem C:\ | Select-Object -Index 3, 4, 5
#  omit certain indexes:
Get-ChildItem C:\ | Select-Object -SkipIndex 3, 4, 5

```

The `-ExpandProperty` parameter of `Select-Object` may be used to expand a single property of an object.
```powershell
Get-Process | Select-Object -First 5 -ExpandProperty Name
```

`Select-Object` returns unique values from arrays of simple values with the `-Unique` parameter.

```powershell
1, 1, 1, 3, 5, 2, 2, 4 | Select-Object -Unique
# OR
1, 1, 1, 3, 5, 2, 2, 4 | Sort-Object | Get-Unique
```

### Sorting
The `Sort-Object` command allows objects to be sorted. By default, `Sort-Object` will sort objects in ascending order.

```powershell
Get-Process | Sort-Object -Property Id
```

A script block (a fragment of script, enclosed in curly braces) can be used to create a calculated value for sorting.
```powershell
$examResults = @(
	[PSCustomObject]@{ Exam = 'Music'; Result = 'N/A'; Mark = 0 }
	[PSCustomObject]@{ Exam = 'History'; Result = 'Fail'; Mark = 23 }
	[PSCustomObject]@{ Exam = 'Biology'; Result = 'Pass'; Mark = 78 }
	[PSCustomObject]@{ Exam = 'Physics'; Result = 'Pass'; Mark = 86 }
	[PSCustomObject]@{ Exam = 'Maths'; Result = 'Pass'; Mark = 92 }
)
$examResults | Sort-Object {
	switch ($_.Result) {
		'Pass' { 1 }
		'Fail' { 2 }
		'N/A' { 3 }
	}
}
```

### Grouping
`Group-Object` is a powerful command that allows you to group objects together based on a property or expression.
```powershell
6, 7, 7, 8, 8, 8 | Group-Object # will group similar numbers
```
By default, `Group-Object` is not case sensitive. 

### Measuring
When used without any parameters, `Measure-Object` returns a value for `Count` , which is the number of items passed in using the pipeline;
```powershell
1, 5, 9, 79 | Measure-Object # counts the length 
1, 5, 9, 79 | Measure-Object -Average -Maximum -Minimum -Sum # produces Sum, Average, Min and Max
Get-Content C:\Windows\WindowsUpdate.log |
	Measure-Object -Line -Word -Character # counts lines, words and characters.
```

### Comparing
You can use the `Compare-Object` command to compare collections of objects with one another. 
```powershell
Compare-Object -ReferenceObject 1, 2, 3, 4 -DifferenceObject 1, 2
```

### Importing
By default, `Import-Csv` expects the input to have a header row, be comma-delimited, and use ASCII file encoding.
```powershell
Import-Csv TabDelimitedFile.tsv -Delimiter `t
```

### Exporting
The `Export-Csv` command writes data from objects to a text file;
```powershell
Get-Process | Export-Csv processes.csv
```

---
## Operators
Arithmetic and assignement operators are just the same as in any other language. I will simply state what's different in `pwsh`.

Comprison operators,
- Equality, `-eq` and `-ne`.
- Likeness, `-like` and `-notlike`.
The `-like` and `-notlike` operators support wildcards. * matches a string of any length (zero or more characters long) and ? matches a single character. 
```powershell
'Hello world' -like '??llo w*'
```
Behind the scenes, PowerShell turns expressions used with -like and -notlike into regularexpressions.
- Greater, `-gt` and `-ge`.
- Less, `-lt` and `-le`.
- Containement, `-contains` and `-notcontains`.
- Membership, `-in` and `-notin`.
- Matching, `-match` and `-notmatch`.
The  `-match` and `-notmatch` operators test whether a string matches a regular expression. 

---
## Registry

---
## Filesystem

---
## Scheduling

---
## Network
```powershell
$tcpClient = New-Object System.Net.Sockets.TcpClient
$tcpClient.Connect("127.0.0.1", 135)
```