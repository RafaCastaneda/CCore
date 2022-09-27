# Modules

## Module declarations

Modules are declared with the `module` keyword:

```cs
module System
{

}
```

And they can be nested, or declared as a qualified path:

```cs
module System
{
    module Math
    {

    }
}

module System::Math
{

}
```

As expected, modules define a namespace, and items (classes, functions, consts) can be resolved by their fully-qualified name: 

```cs
module System::Math
{
    func float Sqrt(float x) { ... }
}

func void Main() {
    var x = System::Math::Sqrt(10.0);
}
```

or by importing (`using`) its module:

```cs
using System::Math;

func void Main() {
    var x = Sqrt(10.0);
}
```

Modules can be imported at any block level, like inside functions, methods and classes:

```cs
func void Main() {
    using System::Math;

    var x = Sqrt(10.0);
    ...
}
```

or even in its own block scope:

```cs
func void Main() {
    using System::Math {
        var x = Sqrt(10.0);
        ....
    }
}
```

Note that, unlike C#, and like Rust and C++, module paths are separated by `::`, and not by `.`. That is to explicitly differentiate between namespace resolution and member access.

It is illegal to have two items with the same name in the same module namespace. Name collisions can be resolved qualifying the item name:

```cs
func void Main() {
    var x = Library1::Sqrt(10.0);
    var y = Library2::Sqrt(10.0);
}
```

## Access modifiers

Items in modules can have three access levels: `public`, `internal`, and `private`. When no access level is specified, it defaults to `private`. `private` is accessible only inside the module, `internal` anywhere inside the assembly, and `public` everywhere.

```cs
module System::Math
{
    public func float Sqrt(float x) { ... }

    internal class Configuration
    {
        ...
    }

    private func void Helper() { ... }
}
```

## Generic modules

Just as generic classes and functions (more on this later), CCore modules can be parameterized by type:

```cs
module System::Math<T>
    where T : Number
{
    public const T Pi = ...;

    public func T Sqrt(T x) { ... }
    public func T Sin(T angle) { ... }
}
```

And then be imported with its type parameters instantiated:

```cs
using System::Math<double>;

func void Main() {
    double angle = 10.0m;
    double x = Sin(angle);
}
```
