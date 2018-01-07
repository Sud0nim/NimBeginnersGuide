**Comments**

The purpose and effects of well written code should be clear to the reader, however there are cases where additional documentation might 
be required in the code to inform readers of extra details or nuances. Documentation is also important for distributing your code to 
others so that they know how you intended it to be used.

Adding comments to your Nim code can be done in a few ways, and each is suited for a different purpose:

Comment Type | Syntax | Use For | Example
------------ | ------------- | ------------- | --------------
Single Line | # comment | Brief notes for contributors | # This is a single line comment
Multi-Line | #[ comment ]# | Detailed explanations for contributors | #[ This Comment Can Span Multiple Lines ]#
Documentation | ## comment | End-user documentation | ## Documentation for users
Example | ## .. code-block:: Nim | End-user examples | ## .. code-block:: Nim let x = 10

Single line comments use the '#' symbol – everything to the right of the # on the line will be ignored by the compiler. 

Multi-line comments are opened with '#[' and closed with ']#' any code in between will be ignored by the compiler 
(in this case the words ' and closed with ' are ignored). 

Documentation comments, which are comments that Nim’s inbuilt documentation generator (DocGen) will read and export to 
an HTML file so that it can be posted on the official Nim website as a guide for users. Documentation comments use a 
double '#' symbol: '##'. Everything to the right of the double-hash on a line will be ignored by the compiler but 
picked up for export by Nim’s documentation generation software.

**Example 2.1**

```Nim
# This is a single line comment

#[ This
Comment
Spans
Multiple
Lines ]#

## This comment will be read and exported by DocGen
```
Below in example 2.2 shows how documentation in code (from the system module of the Nim standard library) is automatically converted to 
HTML which can be added on the Nim website. This code below is translated to the following entry in this module's documentation: 

https://nim-lang.org/docs/system.html#pairs.i,openArray[T]

**Example 2.2**

```nim

iterator pairs*[T](a: openArray[T]): tuple[key: int, val: T] {.inline.} =
  ## iterates over each item of `a`. Yields ``(index, a[index])`` pairs.
  var i = 0
  while i < len(a):
    yield (i, a[i])
    inc(i)

```

DocGen also allows including examples for your documentation using the '.. code-block:: Nim' syntax. 
In example 2.3 below there 3 lines of examples which can be found exported to the documentation: 

https://nim-lang.org/docs/system.html#[]=,string,Slice[int],string

**Example 2.3**

```nim
  proc `[]=`*(s: var string, x: Slice[int], b: string) =
    ## slice assignment for strings. If
    ## ``b.len`` is not exactly the number of elements that are referred to
    ## by `x`, a `splice`:idx: is performed:
    ##
    ## .. code-block:: nim
    ##   var s = "abcdef"
    ##   s[1 .. ^2] = "xyz"
    ##   assert s == "axyzf"
    var a = x.a
    var L = x.b - a + 1
    if L == b.len:
      for i in 0 .. <L: s[i+a] = b[i]
    else:
      spliceImpl(s, a, L, b)
```

**Using DocGen**

Once your project is ready and you want to host the documentation online for others to use, 
you can create your documentation with the command line. Simply navigate to your project directory and run the command:

> nim doc myProjectName

This creates output which should resemble below:

> C:\projects\Nim>nim doc myProjectName
> Hint: used config file 'C:\Users\MyUser\Downloads\nim-0.17.2_x64\nim-0.17.2\config\nim.cfg' [Conf]
> Hint: used config file 'C:\Users\MyUser\Downloads\nim-0.17.2_x64\nim-0.17.2\config\nimdoc.cfg' [Conf]
> Hint: operation successful (1575 lines compiled; 0.006 sec total; 1.004MiB peakmem; Debug Build) [SuccessX]

There are additional options with DocGen, so be sure to read more here:

https://nim-lang.org/docs/docgen.html
