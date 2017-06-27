# Style Guide

## Naming

### Style

 Kind                 | Style            | Notes             | Example      
 -------------------- |------------------|-------------------|--------------
 Types and Namespaces | Upper Camel Case |                   | public class **ClassName**
 Interfaces           | Upper Camel Case | Prepend with ``I``| public interface **IInterfaceName**
 Type Parameters      | Upper Camel Case | Prepend with ``T``| public class ClassName<**TType**>
 Methods              | Upper Camel Case |                   | public bool **Method**()
 Properties           | Upper Camel Case |                   | public int Property { get; set; }
 Local variables      | lower Camel Case |                   | var localVariable = 4;
 Local constants      | lower Camel Case |                   | const int constantVariable = 4;
 Parameters           | lower Camel Case |                   | public bool MethodName(int **typeParameterOne**)
 Public Fields        | Upper Camel Case |                   | public int **PublicField**;
 Private Fields       | lower Camel Case | Prepend with ``_``| private int **_privateField**;
 Private Static       | Upper Camel Case |                   | private static int **StaticField** = 4;
 Public Static        | Upper Camel Case |                   | public static int **StaticField** = 4;
 Private Constants    | Upper Camel Case |                   | private const int **StaticField** = 4;
 Public Constants     | Upper Camel Case |                   | private const int **StaticField** = 4;
 Enum Members         | Upper Camel Case |                   | public enum **EnumMember**

### General Rules
1. Try not to abbreviate!
2. Make sure the name gives the reader context of what the subject is or does.
3. Prefer using business domain names when possible.
4. Avoid adding the design pattern name to the class name.

## Braces

1. [Allman/BSD style](https://en.wikipedia.org/wiki/Indent_style)
2. In general all braces should be places on the next line at the same level on indentation as the control block.

## Blank Lines

### General rules
1. Blank lines should be used to logically group statements.

### Examples
~~~~csharp

private void CreateClientFrom(IConnectionPool connectionPool, IConnection connection, int defaultIndex)
{
    var settings = new ConnectionSettings(connectionPool, connection)
        .DisableDirectStreaming()
        .ThrowExceptions()
        .DefaultIndex(defaultIndex);

    if (Environment.IsDevelopment)
        settings.DisableDirectStreaming();

    return new ElasticClient(settings);
}

~~~~

## Properties

### General rules
1. Auto properties should remain on one line.
2. There should be a space inside the braces and between the ``get;`` and ``set;``
3. If your property has a body split the property across multiple lines.
4. There should be not space between multiple single line properties.
5. There should be a space between multi-line properties.
6. Auto properties should be placed before multi-line ones.

### Examples
~~~~csharp

public int SingleLineAutoProperty1 { get; set; }
public int SingleLineAutoProperty2 { get; set; }

public int MultiLineAutoProperty1
{
        get
        {
            return SingleLineAutoProperty1;
        } 
        set
        {
            SingleLineAutoProperty1 = value;
        }
}

public int MultiLineAutoProperty2 
{
        get
        {
            return SingleLineAutoProperty1;
        } 
        set
        {
            SingleLineAutoProperty1 = value;
        }
}

~~~~

## If Statements

### General rules
1. The body of an ``if`` statement should always be surrounded with braces.
2. If the body is only a single line then the braces should be omitted.
3. There should be a space between the keyword and the statement.
4. If the statement feels too long to be on one line break on the logical operators.
5. If the statement contains more than two statements then break over new lines on the logical operators.
6. If possible extract complex logic into variables to give context to the statement.

### Examples
~~~~csharp

if (MultiLine)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

if (SingleLine)
    Console.WriteLine("1");

~~~~

~~~~csharp

if (MultiLine1 && MultiLine2)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

if (MultiLine1 
        && MultiLine2
        && MultiLine3
        && MultiLine4
        && MultiLine5
        && MultiLine6
    )
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

if ((MultiLine1 && MultiLine2) || (MultiLine3 && MultiLine4))
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

if ((MultiLine1 && MultiLine2)
        || (MultiLine3 && MultiLine4)
        || (MultiLine5 && MultiLine6)
   )
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

var shouldWriteToFile = MultiLine1 && MultiLine2;
var fileWritingIsEnabled = MultiLine3 && MultiLine4;

if (shouldWriteToFile && fileWritingIsEnabled)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

## Else Statements

### General rules
1. The body of an ``else`` statement should always be surrounded with braces.
2. If the body of **both** the ``if`` *and* ``else`` statements is a single line then the braces should be omitted.
3. ``else`` and ``else if`` statements should be on a new line.

### Examples
~~~~csharp

if (SingleLine)
    Console.WriteLine("1");
else
    Console.WriteLine("2");

~~~~

~~~~csharp

if (MultiLine)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}
else
{
    Console.WriteLine("2");
}

~~~~

~~~~csharp

if (SingleLine)
    Console.WriteLine("2");
else
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

if (MultiLine)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}
else if (SingleLine)
{
    Console.WriteLine("1");
}

~~~~

~~~~csharp

if (MultiLine)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}
else if (MultiLine)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

## For loops

### General rules
1. The body of a ``for`` loop should always be surrounded with braces.
2. If the body is only a single line then the braces should be omitted.
3. There should be a space between the keyword and the statement.
4. There should be a space only **after** each semicolon in the statement .
5. ``var`` should be used for the iterator type.

### Examples
~~~~csharp

for (var i = 0; i < 10; i++)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

for (var i = 0; i < 10; i++)
    Console.WriteLine("1");

~~~~

## ForEach loops

### General rules
1. The body of a ``foreach`` loop should always be surrounded with braces.
2. If the body is only a single line then the braces should be omitted.
3. There should be a space between the keyword and the statement.
4. ``var`` should be used be used when possible for the iterator type.

### Examples
~~~~csharp

foreach (var item in _items)
{
    Console.WriteLine("1");
    Console.WriteLine("2");
}

~~~~

~~~~csharp

foreach (var item in _items)
    Console.WriteLine("1");

~~~~

## While

### General rules
1. The body of a ``while`` loop should always be surrounded with braces.
2. There should be a space between the keyword and the statement.

### Examples
~~~~csharp

while (isRunning)
{
    Console.WriteLine("1");
}

~~~~

## Do While

### General rules
1. The body of a ``do while`` loop should always be surrounded with braces.
2. There should be a space between the keyword and the statement.
3. The ``while`` statement should be on a new line.

### Examples
~~~~csharp

do
{
    Console.WriteLine("1");
} 
while (isRunning);

~~~~

## Using
### General rules
1. The body of a ``using`` loop should always be surrounded with braces.
2. If the ``using`` has a single line body then the braces should be omitted. 
3. There should be a space between the keyword and the statement.
4. ``var`` should always be used when possible.

### Examples
~~~~csharp

using (var content = new Context())
{
    Console.WriteLine(1);
    Console.WriteLine(2);
}

~~~~

~~~~csharp

using (var content = new Context())
    Console.WriteLine(1);

~~~~

## Lock
### General rules
1. The body of a ``lock`` loop should always be surrounded with braces.
2. There should be a space between the keyword and the statement.

### Examples
~~~~csharp

lock (_lock)
{
    Console.WriteLine(1);
}

~~~~

~~~~csharp

lock (_lock)
{
    Console.WriteLine(1);
    Console.WriteLine(2);
}

~~~~

## Try Catch Finally
### General rules
1. The body of ``try``, ``catch``, and ``finally`` should always be surrounded with braces.
2. There should be a space between the keyword and the statement.
3. The exception name should never be abbreviated.

### Examples
~~~~csharp

try
{
    Console.WriteLine(1);
}
catch (Exception exception)
{
    Console.WriteLine(1);
}
finally
{
    Console.WriteLine(1);
}

~~~~


## Class Layout

### Member Order

Every class should match the following layout for their members:

~~~~
usings

namespace
{
    class
    {
        # Public Delegates

        # Public Enums

        # Constants

        # Properties

        # Fields

        # Static Constructors

        # Constructors

        # Destructor

        # Methods

        # Operators

        # Equality

        # Formatting / Conversion

        # Nested Types
    }
}

~~~~

### Access Modifiers

Within each member type the members should be ordered by their access level. The order is as follows:

~~~~

1. Public
2. Protected
3. Internal
4. Private

~~~~

## Examples

### Business Object

~~~~csharp

using Namespace;

namespace Name.Space
{
    public class BusinessObject : IBusinessObject
    {
        public const int PublicConstField = 3;
        private const int PrivateConstField = 3;

        public static int PublicStaticProperty { get; set; }
        private static int PrivateStaticField;

        public int PublicBackingFieldProperty => _privateField;
        public int PublicReadonlyProperty { get; }
        public int PublicProperty { get; set; }

        private readonly int _privateReadonlyField;
        private int _privateField;

        public static BusinessObject From(int privateField)
        {
            return new BusinessObject(privateField, privateField + 1);
        }

        private BusinessObject(int privateField, int publicProperty)
        {
            _privateField = privateField;
            PublicProperty = publicProperty;
        }

        public static bool PublicStaticMethod(int parameter)
        {
            return true;
        }

        public bool PublicMethod(int parameter)
        {
            return true;
        }

        protected bool ProtectedMethod(int parameter)
        {
            return true;
        }

        internal bool InternalMethod(int parameter)
        {
            return true;
        }

        private bool PrivateMethod(int parameter)
        {
            return true;
        }

        public static bool operator ==(BusinessObject a, BusinessObject b)
        {
            if (ReferenceEquals(null, a) && ReferenceEquals(null, b))
                return true;

            if (ReferenceEquals(null, a) || ReferenceEquals(null, b))
                return false;

            return ReferenceEquals(a, b) || a.Equals(b);
        }

        public static bool operator !=(BusinessObject a, BusinessObject b)
        {
            return !(a == b);
        }

        protected bool Equals(BusinessObject other)
        {
            return _privateField == other._privateField;
        }

        public override bool Equals(object obj)
        {
            if (ReferenceEquals(null, obj))
                return false;

            if (ReferenceEquals(this, obj))
                return true;

            return obj.GetType() == GetType() && Equals((BusinessObject)obj);
        }

        public override int GetHashCode()
        {
            unchecked
            {
                var hashCode = (int)_privateField;
                hashCode = (hashCode * 397) ^ (PublicProperty.GetHashCode() ?? 0);
                return _privateField;
            }
        }

        public int ToResponse()
        {
            return _privateField;
        }
        
        public override string ToString()
        {
            return $"{nameof(_privateField)}: {_privateField}";
        }
    }    
}

~~~~

### DTO

~~~~csharp

using Namespace;

namespace Name.Space
{
    public class Dto
    {
        public int Property1 { get; set; }
        public int Property2 { get; set; }
        public int Property3 { get; set; }
        public int Property4 { get; set; }

        public int Property4 
        {
             get
             {
                 return Property1.ToString();
             }
             set
             {
                 Property1 = int.Parse(value);
             } 
        }
    }
}

~~~~

### DTO with attributes

~~~~csharp

using Namespace;

namespace Name.Space
{
    public class DtoWithAttributes
    {
        [Attribute]
        public int Property1 { get; set; }

        [Attribute]
        public int Property2 { get; set; }

        [Attribute]
        public int Property3 { get; set; }

        [Attribute]
        public int Property4 { get; set; }
    }
}

~~~~