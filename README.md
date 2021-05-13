# Python Concepts
Master notes for python core concepts

<hr/>
<br/>
<p> Python is interpreted, garbage-collected and dynamically typed </p>

<h1> Scope </h1> 

```
class Class1():
    def __init__(self, sharedVar):
        sharedVar += 1   # ** We pass by reference in all cases but not when we instantiate class **
        print("Class1",sharedVar) # output is 2

class Class2():
    def __init__(self, sharedVar):
        print("Class2",sharedVar) # output is 1 but expected to be 2

sharedVar = 1
my_child1 = Class1(sharedVar)  # expecting to print 1
my_child2 = Class2(sharedVar)  # expecting to print 2// But in actual you'll see print of 1


```


<h1> List and Set Comprehensions </h1>
<br/>
<h2> Comprehensions </h2>
<p> Concise syntax for describing lists, sets and dictionaries. General sytax for list comprehensions : </p>

```
[ expr(item) for item in iterable ]
```

<p> General syntax for set comprehensions : </p> 

```
{ expr(item) for item in iterable }
```

<p> General syntax for dict comprehensions : </p>

```
{
    key_expr(item) : value_expr(item)
    for item in iterable
}
```
<p> Dictionary compreshensions don't work directly on dict sources. User <i> dict.items()</i> to get keys and values from <i>dict</i> sources. </p>

<h2> Filtering Comprehensions </h2>
</br>
<p> If the end expression is True then that particular item is collected </p>

```
[ expr(item) for item in iterable if bool_expr(item) ]
```

<h1> Core Language </h1> 

<h2> Nonlocal Keyword </h2> 
<p> The nonlocal keyword is used to work with variables inside nested functions, where the variable should not belong to the inner function. Use the keyword nonlocal to declare that the variable is not local. </p>

<h2> Strings <h2/>
    <p> The repr() function returns a printable representational string of the given object </p>
    

<h2> Standard Exception Hierarchy </h2>
<p> <a href="https://docs.python.org/3/library/exceptions.html#exception-hierarchy">Exception Hierarchy </a></p> 


<h2> Other Nuggets </h2>
    <ul>
        <li>A dict is a structure like hash map. It stores key-value pairs, where keys are unique and it has O(1) access time. The most important limitation for a dict is that keys must be hashable/immutable. Meaning we can use tuple as key, but not a list </li>
        <li>A callable is an object we can call - function or an object implementing the __call__ sepcial method. Any object can be made callable. </li>
    <li> Pickling is converting an object to a string representation in python. Generally used for caching and transferring objects between hosts/processes. </li> 
    <li> A generator is a callable object that acts as an iterable ( object you can iterate in for cycles etc ) </li> 
    <li> Decorators in Python are used to modify or inject code in functions or classes. Using decorators, you can wrap a class or function method call so that a piece of code can be executed before or after the execution of the original code. Decorators can be used to check for permissions, modify or track the arguments passed to a method, logging the calls to a specific method, etc.</li>
    <li> Lambda in python is an anonymous function created at runtime. </li>
    <li> `*` unpacks a tupe and `**` upacks a dict </li>
  <li> Introspection is the ability to examine an object at runtime. Example "dir()" , "type()". While introspection is passive examination of the objects, reflection is a more powerful tool where we could modify objects at runtime and access them dynamically. E.g "setattr()", "getattr()". </li>
    <li> As python OOP doesn't support true private attributes/methods we circumvent this limitation by using a name prefix with underscore which is as a convention considered private. </li>
    <li> Mixin is a concept in Programming in which the class provides functionalities but it is not meant to be used for instantiation. The main purposeo of the Mixin is to provide functionalities which are standalone and it would be best if the mixins themselves do nto have inheritance with other mixins and also avoid state. </li>
    <li> In Python, everything is an object, including classes. And just like any other object, classed are instances of something - a metaclass. The default metaclass is "type". </li>
    <li> A virtualenv is what Python developers call an isolated environment for development, running, debugging Python code. It is used to isolate a Python interpreter together with a set of libraries and settings. Together with pip, it allows us to develop, deploy and run multiple applications on a single host, each with their own version of the Python interpreter, and seperate set of libraries. </li>
<li> A module in Python is any file with *.py extension. A package is a set of modules - a directory that contains one or many .py files, one of which is __init__.py. Both modules and packages define functions, classes or any kind of software functionality. When we import something in Python, we import from packages and modules. </li> 
    <li> PEP8 is a generally recognized style guide for programming in Python. It not only convers formatting, comments, naming convention, but also programming recommendations as well as useful tips on various topics. The main aim of PEP8 is to help developers improve code readability, reliability and maintainability. </li> 
    <li> Ternary operator in python looks like `[on_true] if [expression] else [on_false]` , example : " x if x<y else y " </li>
    <li> Python has a inbuilt garbage collector, which recycles all the unused memory and frees the memory and makes it available to the heap space </li> 
    <li> Python memory is managed by Python private heap space. All Python objects and data structures are located in a private heap. The programmer does not have an access to this private heap, and the interpreter takes care of this Python private heap. The allocation of Python heap space for Python objects is done by the Python memory manager. The core API gives access to some tools for the programmer to code </li> 
    <li> Everything in Python is an object, all the variables hold references to the objects. The reference values are according to the functions. Therefore, you cannot change the value of the references. However, you can change the objects if it is mutable. </li> 
    <li> Python provied two built-in types 1) Mutable and 2) Immutalbe. </br> Mutable built-in types are : </br> 
        <ul> 
        <li> List </li> 
        <li> Sets </li> 
        <li> Dictionaries </li> 
        <li> Immutalbe built-in types</li>
        <li> Strings </li>
        <li> Tuples </li>
        <li> Numbers </li> 
        </ul>
        </br>
        Immutable built-in types are : 
        </br> 
        <ul> 
        <li> Strings </li>
        <li> Tuples </li> 
        <li> Nubmers </li>
        </ul>
        </li>
<li> A Python documentation string is known as docstring, it is a way of documenting Python functions, modules, and classes. </li>
<li> Xrange returns the xrange object while range returns the list and uses the same memory and no matter what the range size is. </li> 
<li> To make a python script executable on Unix , you'll need to set file's mode to executable and first line must begin with # ( #!/usr/local/bin/python ) </li>
        <li> Comparing Flask/Pyramids/Django : Flask is a microframework primarily build for a small application with simpler requirements. In flask you don't have to use external libraries. Flask is ready to use. Pyramids are built for larger applications. It provides flexibility and lets the developer use the right tools for their project. The developer can choose the datbase, URL structure, templating style, and more. Like pyramid, Django can also be used for larger applications. It includes an ORM.  </li> 
        <li> "Exception" can server as the base for other custom defined exceptions </li>
        <li> "None" keyword is frequently used to represent the absence of a value, as when default arguments are not passed to a function </li>
        <li> Two kinds of errors that can occur in pytho are : a. Syntax errors b. Exception <li>
        <li> "from math import sqrt" , a function named "sqrt" is imported from math module to global namespace </li>
        <li> When an assertion test passes for a Python program it means : All the assumed bugg, or sources of bugs were tested and none were found. </li>
        <li> How would you create a function that takes a value and refers to it by its assigned name? : Kwargs are like a dictionary, the most convenient way in Python when you want to pass a key-value based argument or arguments to a function.
        "pythondef function(**kwargs):        return kwargs['value1'] * kwargs['value2']" </li>
    <li> • A function should traverse a two dimensional array
• A True boolean should be returned if the inner traversal's value matches a specified string.  : • When the outside traversal begins
• When the inside traversal begins
• When the conditional is run
• When the return statement is invoked
        </li> 
        <li> What are two ways to include double quotation marks within literal strings? :  insert a backslash before the character(s) • open and close the string with single quotation marks
        </li>
