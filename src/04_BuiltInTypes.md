**Primitive and Built-in Types**

Nim has a large standard library as well as a number of types built-in to the language so that you don't need to create or import them 
to start using them.

The main types you will likely encounter early on in your learning will be:

1. int (integers, whole numbers)
2. float (floating-point numbers, which approximate decimal numbers)
3. bool (true or false)
4. char (characters such as letters or numbers)
5. array (a fixed-size sequence of values of the same type)
6. seq (a growable sequence of values of the same type)
7. string (a growable sequence of characters)
8. exception (error flags which the compiler or your program may use to handle bugs)
9. enum (an enumeration type)
10. tuple (a sequence of values of the same or different types)

The details of each is briefly summarised below:

Type | Use For | Example
------------ | ------------- | -------------
int | When only whole number precision is needed (such as a count)  | var countOfLines = 0
float | When precision below whole numbers is needed | var averageTemperature = 53.485
bool | When needed to control the flow of your program | var isEven = true
char | To express a single (often alphanumeric) character | var firstLetterOfName = 'C'
array | To store multiple values of the same type together and you know how many values you need to store | let days = ['M', 'T', 'W', 'T', 'F', 'S', 'S']
seq | To store multiple values of the same type together where you may need to add or remove values | let names = @["Bill", "Bob", "Jill", "Rob"]
string | When you need to store a word, sentance or sequence of characters | var welcome = "Welcome to the Nim Beginner's Guide"
exception | When you need to create logic to handle bugs or user behaviour | try: let x = readLine() except: "Line couldn't be read!"
enum | When you have a small range of possible values and want to group those possible values together as a type | let today = Tuesday
tuple | To store multiple values of any type in a known order | let point = (98.88, 43.2)

Let's look at these types in more detail. #TODO

**Integers**

Nim has a range of integer or whole round number types, which are available in varying sizes. As can be seen in the table below, build-in integers can not represent infinitely large or small numbers - they have constraints on the possible range of values based on the amount of memory the type of integer occupies.

When you are designing your program, you want to avoid choosing an integer that might not be able to represent the value your variable will grow to. While it may be tempting to always use the smallest integer type possible to try and conserve memory, in most use-cases this won't be neccessary because Nim is fast enough as it is, and it may make your code more fragile. 

Similarly, while it may be tempting to always use an int64 or uint64 type so that you avoid reaching a value larger than the maximum size, this also may mean that your code can only compile on 64 bit machines - making it more difficult to distribute. You must also consider if your variables can go negative, or if they may only ever be positive. 'uint' types are un-signed, which means they can only represent positive numbers. This allows them to take a greater range of positive values, but makes your code potentially prone to errors.

If unsure, the best thing to do is use the 'int' type which is an integer that automatically sizes based on the machine your code is compiled on. A 32 bit machine will use 32 bit integers and a 64 bit machine will use 64 bit integers, allowing your code to be redistributed across a greater range of hardware architectures and allowing you to think about your program logic rather than worrying about integer sizing.

As you gain more experience, you might find situations where changing to an explicit integer size is beneficial. You also may find that you need an integer that is even larger than 64 bit integer to hold your values. There are solutions to this such as a 'BigInt', which is an integer that can grow to practically any size, though these do come with the downside of being a little slower to use so it is best to make sure they are required before resorting to their use. 

Some examples of a BigInt type are found in the libraries below, which are third party libraries and not built-in to the compiler:

Pure-Nim BigInts: https://github.com/def-/nim-bigints

A Wrapper of GMP (a C numerical library): https://github.com/FedeOmoto/nim-gmp

The specific details of each integer type are outlined in the table below:

Type | Size | Range of Values
------------ | ------------- | -------------
int | Up to 64 bits | –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
int8 | 8 bits  | –128 to 127
uint8 | 8 bits | 0 to 255
int16 | 16 bits  | –32,768 to 32,767
uint16 | 16 bits | 0 to 65,535
int32 | 32 bits | –2,147,483,648 to 2,147,483,647
uint32 | 32 bits | 0 to 4,294,967,295
int64 | 64 bits | –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
uint64 | 64 bits | 0 to 18,446,744,073,709,551,615
BigInt | arbitrary | any size within the constraints of your machine

**Floats**

Floats, or floating-point numbers are the default type used in most computers to represent a fractional value such as 128.38723872 (a number with a decimal place).

The full list of built-in types is shown in the system module:

https://nim-lang.org/docs/system.html
