# C# Style guide and coding practises :

The style guide we are using for coding practices is on top of ****[The Official raywenderlich.com C# Style Guide](https://github.com/raywenderlich/c-sharp-style-guide#misc).** 
#
### **Namespaces :**

- Namespaces are all **PascalCase**, multiple words concatenated together, without hyphens ( - ) or underscores ( _ ).
- The exception to this rule are acronyms like GUI or HUD, which can be uppercase:
- Namespace `using` declarations go at the top, before any namespaces. `using` import order is alphabetical, apart from `System` imports which always go first.
- Namespace are necessary for each file.
- New top-level namespace names must be globally unique and recognizable.

**Wrong :** 

`companyName.project.namespace`

**Right :** 

`CompanyName.Project.Namespace`
#
### **Classes :**

Classes and are written in **PascalCase**. For example `RadialSlider`.
#
### S**tructs :**

- Structs are very different from classes:
- Structs are always passed and returned by value.
- Assigning a value to a member of a returned struct doesn’t modify the original - e.g. `transform.position.x = 10` doesn’t set the transform’s position.x to 10; `position` here is a property that returns a `Vector3` by value, so this just sets the x parameter of a copy of the original.
- **Almost always use a class**.
- Consider struct when the type can be treated like other value types - for example, if instances of the type are small and commonly short-lived or are commonly embedded in other objects. Good examples include Vector3, Quaternion and Bounds.
#
### ****Interfaces****

All interfaces are writter in PascalCase with “I” as a prefix 

**Wrong :** 

```csharp
public interface ThisIsInterface

public interface iThisIsInterface,

public interface IthisIsInterface,

public interface I_ThisIsInterface
```

**Right :** 

```csharp
public interface IThisIsInterface;
```
#
### **Methods**

Methods are always written in **PascalCase**. 

**Wrong :** 

`doSomething()`, 

`do_something()`

**Right** 

`DoSomething()`
#
### **Fields**

- All non-static fields are written **camelCase**.
- **private and internal fields** should have a “_” prefix with **camelCase**.
- **non-private static and readonly fields** should be Pascalcase ****

```csharp
public class MyClass
{
    public int publicField;
    int packagePrivate;
    private int _myPrivate;
    protected int myProtected;
}
```
#
### **Properties**

- All properties are written in **PascalCase**. For example:

```csharp
public int PageNumber 
{
    get { return pageNumber; }
    set { pageNumber = value; }
}
```

- Use of Auto-property is encouraged.
#
### **Parameters**

Parameters are written in **camelCase**.

**Wrong:**

`void DoSomething(Vector3 Location)`

**Right:**

`void DoSomething(Vector3 location)`
#
### **Delegates**

Delegates are written in **PascalCase**.

For example:`public delegate int PerformCalculation(int x, int y);`
#
### Events

Actions are written in **camelCase**.

For example:`public event Action<int> onValueChanged;` 
#
### **Misc.**

In code, acronyms should be treated as words. For example:

**AVOID:**

`XMLHTTPRequest
String URL
findPostByID`

**PREFER:**

`XmlHttpRequest
String url
findPostById`
#
### **Access Level Modifiers**

- Access level modifiers should be explicitly defined for classes, methods and member variables.
#
### Modifiers

- Modifiers occur in the following order:
    
    [public](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/public) > [protected](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected) > [internal](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/internal) > [private](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private) > [new](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/new-modifier) > [abstract](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/abstract) > [virtual](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/virtual) > [override](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/override) > [sealed](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/sealed) > [static](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/static) > [readonly](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/readonly) > [extern](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/extern) > [unsafe](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/unsafe) > [volatile](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/volatile) > [async](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/async)
    
#
### **Fields & Variables**

Prefer single declaration per line.

**AVOID:**

`string username, twitterHandle;`

**PREFER:**

`string username;
string twitterHandle;`
#
### **Spacing**

Spacing is especially important in the code, as code needs to be easily readable

### **Indentation**

Indentation should be done using **spaces** — never tabs.**[ enforced in the config file ]**

### **Blocks**

Indentation for blocks uses **4 spaces** for optimal readability:

**AVOID:**

```csharp
for (int i = 0; i < 10; i++) 
{
  Debug.Log("index=" + i);
}
```

**PREFER:**

```csharp
for (int i = 0; i < 10; i++) 
{
    Debug.Log("index=" + i);
}
```

### **Line Wraps**

Indentation for line wraps should use **4 spaces** (not the default 8):

**AVOID:**

`CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);`

**PREFER:**

`CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);`

- **[ enforced in the config file ]**

### **Line Length**

Lines should be no longer than **100** characters long.

### **Vertical Spacing**

- There should be exactly one blank line between methods to aid in visual clarity and organization.
- Whitespace within methods should separate functionality, but having too many sections in a method often means you should refactor into several methods.
- Adding code immediately after a block is allowed.
- Multiple empty lines are discouraged and will be flagged by the IDE.

**[ enforced in the config file ]**

### **Brace Style**

All braces get their own line as it is a C# convention: **[ enforced in the config file ]**

**Wrong:**

```csharp
class MyClass {
    void DoSomething() {
        if (someTest) {
          // ...
        } else {
          // ...
        }
    }
}
```

**Right:**

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
          // ...
        }
        else
        {
          // ...
        }
    }
}
```
#
### Conditional statements

Conditional statements are always required to be enclosed with braces, irrespective of the number of lines required. **[ enforced in the config file ]**

**Wrong:**

```csharp
if (someTest)
    doSomething();  

if (someTest) doSomethingElse();
```

**Right:**

```csharp
if (someTest) 
{
    DoSomething();
}  

if (someTest)
{
    DoSomethingElse();
}
```
#
### **Switch Statements**

Switch-statements come with `default` case by default (heh). If the `default` case is never reached, be sure to remove it. **[ enforced in the config file ]**

**Wrong:**

```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
    default:
        break;
}
```

**Right:**

```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
}
```
#
### Files

- Filenames and directory names are `PascalCase`, e.g. `MyFile.cs`.
- Where possible the file name should be the same as the name of the main class in the file, e.g. `MyClass.cs`.
- In general, prefer one core class per file.

The style guide and config files are tested on Visual Studio 2022 Version 17.3.6 and Unity 2021.3.0f1
#
# Unity :

### UnityEvent and C# events

Advantage of `UnityEvent` is that it prevents the problem of Unity Object not being freed due to the misuse of delegates or using anonymous delegates with Unity Objects. Although they get freed when the main script that's holding them is destroyed. The reason for this is because `UnityEvent` is implemented with weak references therefore removing/minimizing this problem. 

These two things are still **not** worth it to use `UnityEvent` over native C# events.

**You should always use native event and delegate over UnityEvent if you are not making an Editor plugin because of its fast performance and small memory usage.**
#
### **Sample Code**

```csharp
using System;                                            // `using` goes at the top, 
                                                         //  outside the namespace.

namespace MyNamespace                                    // Namespaces are PascalCase.
{
    public interface IMyInterface                        // Interfaces start with 'I'
    {
        public int Calculate(float value, float exp);    // Methods are PascalCase
                                                         // ...and space after comma.
    }

    public enum EMyEnum                                  // Enumerations are PascalCase.
    {                                                   
        Yes,                                             // Enumerators are PascalCase.
        No,
    }

    public class MyClass// Classes are PascalCase.
    {                            
        public int foo = 0;                             // Public member variables are
                                                        // PascalCase.
        
				public bool noCounting = false;                 // Field initializers are 
																												// encouraged.

        private class Results
        {
            public int numNegativeResults = 0;
            public int numPositiveResults = 0;
        }

        private readonly Results _results;              // Private member variables are
                                                        // _camelCase.

        public static int numTimesCalled = 0;

        private const int _bar = 100;                   // const does not affect naming
                                                        // convention.

        private readonly int[] _someTable =          		// Container initializers use a 
          		          		          		          		// 4 space indent.
        {
            2, 3, 4,
        };

        public int[] SomeTable => this._someTable;

        public MyClass() => this._results = new Results
        {
            numNegativeResults = 1,                     // Object initializers use a 4 
            numPositiveResults = 1,                     // space indent.
        };

        public int CalculateValue(int mulNumber)
        {                                               // Line break before opening 
                                                        // brace.

            var resultValue = this.foo * mulNumber;     // Local variables are camelCase.
            numTimesCalled++;
            this.foo += _bar;

            if (!this.noCounting)
            {                                            // Line break after 'if'.
                                         
                if (resultValue < 0)
                {                                        // Braces used even when 
                                                         // optional and spaces around 
									                                       // comparison operator.
                    this._results.numNegativeResults++;
                }
                else if (resultValue > 0)
                {                                         // Line break between brace 
                                                          // and else.
                    this._results.numPositiveResults++;
                }
            }

            return resultValue;
        }

        public void ExpressionBodies()
        {
            // For simple lambdas, fit on one line if possible, 
						//no brackets or braces required.
            static int increment(int x) => x + 1;

            // Closing brace aligns with first character on line that includes 
            // the opening brace.
            static long difference1(int x, int y)
            {
                var diff = (long)x - y;
                return diff >= 0 ? diff : -diff;
            }

            // If defining after a continuation line break, indent the whole body.
            static long difference2(int x, int y)
            {
                var diff = (long)x - y;
                return diff >= 0 ? diff : -diff;
            }

            // Inline lambda arguments also follow these rules. Prefer a leading 
            // newline before groups of arguments if they include lambdas.
            this.CallWithDelegate(
                (x, y) =>
                {
                    var diff = (long)x - (long)y;
                    return diff >= 0 ? diff : -diff;
                });
        }

        private void CallWithDelegate(Func<object, object, long> value)
        {
            throw new NotImplementedException();
        }

        // Empty blocks should be concise.
        private void DoNothing() { }

        // If possible, wrap arguments by aligning newlines with the first argument.
        private void AVeryLongFunctionNameThatCausesLineWrappingProblems(
            int longArgumentName,
            int p1,
            int p2)
        { }

        // If aligning argument lines with the first argument doesn't fit, or is 
        //difficult to read, wrap all arguments on new lines with a 4 space indent.
        private void AnotherLongFunctionNameThatCausesLineWrappingProblems(
            int longArgumentName,
            int longArgumentName2,
            int longArgumentName3)
        { }

        private void CallingLongFunctionName()
        {
            int veryLongArgumentName = 1234;
            int shortArg = 1;

            // If possible, wrap arguments by aligning newlines with the first argument.
            this.AnotherLongFunctionNameThatCausesLineWrappingProblems(
                shortArg,
                shortArg,
                veryLongArgumentName);

            // If aligning argument lines with the first argument doesn't fit, or is 
            // difficult to read, wrap all arguments on new lines with a 4 space indent.
            this.AnotherLongFunctionNameThatCausesLineWrappingProblems(
                veryLongArgumentName,
                veryLongArgumentName,
                veryLongArgumentName);
        }
    }
}
```
