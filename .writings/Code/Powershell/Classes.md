>A class is used to describe an object. This may be any object, which means that a class in PowerShell might be used for any purpose.

```powershell
class MyClass { 
	[string]$Value = 'My value' 
}
```

>You can create the class by using either the `New-Object` command or the `::new()` method.

```powershell
New-Object MyClass
# OR
[MyClass]::new()
```

>The properties defined in a class may define a .NET type and may have a *default value* if required.

>*A constructor is executed when either New-Object or ::new() is used to create an instance of a class*. The implicit or default constructor does not require arguments. 
>
>An explicit constructor may be created to handle more complex actions when creating an object. 
>
><u>The constructor has the same name as the class.</u> The reserved variable `$this` is used to refer to properties and methods within the class.

```powershell
class MyClass { 
	[string]$Value 
	
	MyClass( [string] $Argument ) { 
		$culture = Get-Culture 
		$this.Value = $culture.TextInfo.ToTitleCase( $Argument ) 
	} 
}
```

>Constructors may be overloaded to allow the class to accept different arguments or combinations of arguments when the class is created.

><u>A method causes a change to the object</u>. This may be an internal change, such as opening a connection or stream, or it may take the object and change it into a different form as is the case with the `ToString` method.


```powershell
class MyClass { 
	[string]$Value = 'Hello world' 
	
	[string] ToString() { 
		return $this.Value 
	} 
}
```


>Methods can accept arguments in the same way as constructors. Methods can also be overloaded.

>Classes may implement static properties and static methods using the `static` modifier keyword.


```powershell
[MyClass]::Property 
[MyClass]::Method()
```

>Classes in PowerShell can inherit from other classes, from classes in PowerShell and .NET. The properties and methods in a base class are available to an inheriting class.


```powershell
class MyBaseClass { 
	[string]$BaseProperty = 'baseValue' 
} 

class MyClass : MyBaseClass { 
	[string]$Property = 'Value' 
}
```

>Constructors in an inheritance hierarchy are not overridden, but instead executed in sequence.

*Parents first, then children.*







