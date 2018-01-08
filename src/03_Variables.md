**Variables**

Variables are a way of assigning a name to some value or collection of values that will be used in your code. Variables have 
a location in the computer’s memory in which a value (or a combination of values) are stored and the value/s are referenced by 
the name or identifier provided by the programmer. Variables can be as simple (E.G. a single integer digit such as 5), or complex with the 
variable holding a number of different values which are stored together as a single data structure (E.G. a list of a thousand telephone 
numbers).

**Example 3.1**

```nim
var myVariableName = 999.99     # myVariableName is the variable name with a floating-point value of 999.99
```

When you are introducing a new variable in to your code, you will sometimes need to let the compiler know what type of value 
that variable will be. For example, it may be an integer type such as 1000, a floating-point decimal value such as 999.99 (as above), 
a 'boolean' value such as true or false, or a string (a series of characters) such as "This is a string".

The compiler needs to be able to understand what type of value each variable is in order to know how that variable can interact with 
other variables and parts of your code, as well as to know how much memory needs to be allocated for storing that variable. Different 
types of value take up different amounts of memory in your computer.

In a lot of cases you won't need to declare to the compiler exactly what type of value you are creating, as the compiler 
is smart enough to work that out itself based on the variable's interactions with the rest of your code and the system 
architecture you are compiling on. If you want to ensure the variable is of a certain type then you may need to be explicit, or  
if it cannot be inferred from the code the compiler will let you know to specify what type it is. 

**Example 3.2**
```nim
var a: int8 = 99                # an 8 bit integer
var b: int16 = 99               # a 16 bit integer
var c: int32 = 99               # a 32 bit integer
var d: int64 = 99               # a 64 bit integer
var e: int = 99                 # machine dependent integer type, E.G. will be 64 bits on a 64 bit machine

echo sizeof(a)                  # 1 bytes (8 bits)
echo sizeof(b)                  # 2 bytes (16 bits)
echo sizeof(c)                  # 4 bytes (32 bits)
echo sizeof(d)                  # 8 bytes (64 bits)
echo sizeof(e)                  # 8 bytes (64 bits) as this is compiled on a 64 bit machine
```
**Type inference**

**Example 3.3**
```nim
var a = 53                      # this will most likely be inferred as an 'int' type, the machine dependent integer type
var b: int8 = 53                # this will be created as an 8-bit integer as the type has been explicitly declared as an int8

proc returnsBoolean(): bool =   # a function that returns a boolean (bool) type to the user
  result = true

var c = returnsBoolean()        # automatically inferred by the compiler as a bool type due to the function's return type
```

Variables in Nim are always preceded by a keyword the first time they are declared, and that keyword has special meaning for the 
compiler. There are three main keywords that you will encounter in Nim when declaring your variables: 'const', 'let' and 'var'.

**const keyword**

Constants are signalled to the compiler with the 'const' keyword. A constant's value must be able to be determined at compile time, 
and cannot change once initialised. A const type is useful for defining variables such as natural constants 
(E.G an approximation of pi) and similar use cases where changing that value wouldn't make sense at any point in your program. 
Constants are typically global values that can be accessed from all or most parts of your code.

**Example 3.4**

```nim
const Pi = 3.14159
```

**let keyword**

Immutable variables are signalled with the 'let' keyword. Immutable variables, like constants, cannot change once initialised – they 
are immutable. Unlike constants however, immutable variables can be initialised anywhere in your code including run-time, but 
after that point they may not change. Immutable variables must be initialised at the time they are declared - meaning you 
cannot pre-declare to the compiler that you intend to use an immutable variable later in your code, it must be 
given a value when you first declare it. Where possible, use the let keyword in your run-time initialised variables as this prevents 
you accidentally changing the value of a variable where you did not mean to do so.

**Example 3.5**

```nim
let myNewValue = 10             # myNewValue is initialised with a value of 10 (an int)

myNewValue = 20                 # will not compile as the variable is immutable and can't be changed to 20

let mySecondValue: int          # will not compile as we cannot pre-declare immutable variable types
```

**var keyword**

Mutable variables are signalled with the 'var' keyword. Mutable variables, like immutable variables, can be initialised at any point 
in your code including run-time. Unlike immutable variables however, you may change the value after initialisation to a new value 
so long as the value remains of the same type (E.G an integer variable with a value of 10 can be changed to another integer value 
such as 20, but not to a boolean value such as false.

**Example 3.6**

```nim
var myNewValue = 10             # myNewValue is initialised with a value of 10 (an int)

myNewValue = 20                 # the variable is mutable and can be changed to 20, which is also an int type

var mySecondValue: int          # we can declare a mutable variable and its type here before we use it

mySecondVale = 900              # we can later initialise that mutable variable with an int value successfully
```

Those rules are summarised below:

Variable Type | Syntax | Use For | Example
------------ | ------------- | ------------- | --------------
Constant | const variable = | Fixed values known at compile-time  | const MaximumWidth = 10
Immutable | let variable = | Fixed values to be set only once in your program | let birthYear = 1950
Mutable | var variable = | Changeable values that can be altered repeatedly  | var countOfLines = 0

