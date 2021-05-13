# Python Concepts
Master notes for python core concepts

<hr/>
<br/>
<p> Python is interpreted, garbage-collected and dynamically typed </p>


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
