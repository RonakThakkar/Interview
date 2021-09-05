# Steps for using delegates for filtering

## Library Code

### Declaring delegate 

Ex: delegate bool ContextFilterDelegate(Context context, out bool deeper)

### Using delegates for filtering

Load method will accept "ContextFilterDelegate" delegate as parameter.

```
Public Load(ContextFilterDelegate ContextFilterDelegateMethod)
{
  Foreach(context c in projectHierarchyItems)
  {
    If( ContextFilterDelegateMethod(c, true) )
    }
  }
}
```

## Client-side code

### Instantiating delegate: "ContextFilterDelegate" compatible method (Same return type and signature) will be created in client application consuming Load Method. This method would have logic for context filteting.

```
public static bool IsContextValid(Context context, out bool deeper)
{
	Return true;
}
```

### Passing delegate instance as a parameter: 

Client will pass delegate instance created in step 2 as a parameter to this Load method.

Load(IsContextValid);

