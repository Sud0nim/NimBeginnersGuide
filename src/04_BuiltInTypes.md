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

The full list of built-in types is shown in the system module:

https://nim-lang.org/docs/system.html
