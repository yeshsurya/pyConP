# Python Concepts
Master notes for python core concepts

<hr/>
<br/>
<p> Python is interpreted, garbage-collected and dynamically typed </p>
<h1> Datatypes </h1>
<ul> <li> A dictionary in Python is a collection of items that stores data as key-value pairs. In Python 3.7 and later versions, dictionaries are sorted by the order of item insertion. In earlier versions, they were unordered. </li> 
    </ul>
<h1> Scope </h1> 

<ul> 
    <li> LOCAL : Inside the current function </li>
    <li> ENCLOSING : Inside enclosing functions </li>
    <li> GLOBAL : At the top level of the module </li>
    <li> BUILT-IN : In the special builtins module </li>
    <li> LEGB </li>
    <li> When accessed through "self" instance attributes takes precedence over class attributes. </li>
    <li> There is no class scope. Class will not introduce any scope. </li>
</ul>
    

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
</hr>
</br>
<h2> pytest </h2>
</br>
</hr>
<ul>
	<li>Many pytest settings can be set in a configuration file, which by convention resides on the root of your repository or in your tests folder. pytest.ini files take precedence over other files, even when empty.

```
# pytest.ini
[pytest]
minversion = 6.0
addopts = -ra -q
testpaths =
    tests
    integration
```
		
	</li>
</ul>
</br> 
<h1> pip </h1>
</br>
</hr>
<ul>
	<li>pip install package_name </li>
	<li>pip install package_name1 package_name2 </li>
	<li>pip uninstall package_name</li>
	<li>pip unisntall package_name1 package_name2 </li>
	<li>pip list </li>
	<li>pip show package_name (shows details bout package)</li>
	<li>python -m pip (for python documentation) </li>
</ul>
<h1> Data Analytics </h1> 
</hr> 
<ul> 
	<li> First stage in the cross industry standard process for data mining ( CRISP-DM ) is to have understanding of the problem you are solving and the advantages it provides </li>
</ul>
<h1> Core Language </h1> 
</hr>
<h2> Organizing Larger Programs </h2>
 <ul> 
    <li> Module is a python basic tool for organizing code. Normally it is a single Python source file. 
        We can load modules with "import" keyword. Modules once imported are like any other Python 
. </li>
    <li> Package is a special type of module, which can contain other packages. Packages are generally directories, while modules are generally files. </li>
    <li> Packages will have "__path__" defined , whild modules will not have it defined. </li> 
    <li> "sys.path" controls module search, and it is initialized from PYTHONPATH </li> 
    <li> If a package is a nested one, Only first name is bound and for accessing submodules we'll need to use thier full-qualifed names for accessing them </li>
    <li> If we try to import module it and if is not present in paths of "sys.path" , then "ImportError" exception will rise </li>
    <li> Use "set PYTHONPATH = path1;path2;path3" in windows , in Linux/MacOS use "export PYTHONPATH=path1:path2:path3" </li>
    <li> A package is a directory conataining "__init__.py". This file is optional after python 3.3+. However it is still requied in earlier python versions. </li> 
    <li> Relative imports avoid specifying name of package. Example " from .. import util" , here (..) meand current or parent package. In general absolute import are preferred </li>
    <li> "__all__" it controls "import * behavior". It must be a list of strings, where each entry is a name to import. </li>
    <li> PEP 420 : Implicit Namespace Packages : "Namespace packages are a mechanish for splitting a single Python packages across multiple directories on disk" </li>
    <h2> Classes and Object-Orientation </h2> 
    <ul> 
        <li> Class attributes are those attributes whose value is shared across multiple instances of a class. </li>
        <li> A method can be made static method by static method decorator(@staticmethod)</li>
	 <li> Can we have 2 Constructors in Python?
		 Yes but the second definition will override the first definition. </li>

```python
class Student:
    def __init__(selfa):
        selfa.test = 'aa'
        selfa.testa = 'a'
        print("initiated")
    def __init__(selfa,test):
        selfa.testa = test
        print("in test initializer")
    def hello(selfa):
        print(selfa.test)

a = Student('testa')
a.hello()
```
        <li>![image](https://user-images.githubusercontent.com/9417467/118355178-58839780-b58c-11eb-95de-d30d25b1178b.png)
 </li>
        <li> General Syntax for single class Inheritance : 
            
            ```
            class Parent_class_Name:
            #Parent_class code block
            class Child_class_Name(Parent_class_name):
            #Child_class code block
            ```
            
</li>
<li> A decorator can modify the behavior of a method. </li>
        <li>Creating Decorator in python :   

```
    # importing libraries
import time
import math

# decorator to calculate duration
# taken by any function.
def calculate_time(func):
	
	# added arguments inside the inner1,
	# if function takes any arguments,
	# can be added like this.
	def inner1(*args, **kwargs):

		# storing time before function execution
		begin = time.time()
		
		func(*args, **kwargs)

		# storing time after function execution
		end = time.time()
		print("Total time taken in : ", func.__name__, end - begin)

	return inner1
# this can be added to any function present,
# in this case to calculate a factorial
@calculate_time
def factorial(num):
	# sleep 2 seconds because it takes very less time
	# so that you can see the actual difference
	time.sleep(2)
	print(math.factorial(num))

# calling the function.
factorial(10)

```

</li>
<li> Dataclass module is introduced in Python 3.7 as a utility tool to make structured classes specially for storing data. These classes hold certain properties and functions to deal specifically with the data and its representation. DataClasses in widely used Python3.6. Although the module was introduced in Python3 </li>
        <li> A decorator factory is just a callable that produces the actual decorator. It is used to make it possible to 'configure' a decorator. </li>
        <li> A dataclass if forozen like "@dataclass(eq=True,frozen=True)" then the ojbects instantiated will become hashable and then can be part of ojbects like "set" </li>
	<li> "__post_init__()" is the method where we do attribute validation for dataclass , it is not necessary to be done only here , but it is a standard practice </li>
	<li> Only equality comparable and frozen data classes are hashable </li>
    </ul>
 
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
<li> You have a nested comprehension in Python to look for the numbers divisible by three and five. Because the numbers are divisible, the if statement evaluates to true so you give the following expression: number_list = [x for x in range(100) if x % 3 if x % 5]. It still does not show the expected output. Why not? : You must evaluate if the remainder is zero so the correct expression would be: number_list = [x for x in range(100) if x % 3 == 0 if x % 5 == 0] </li>
        <li> How do you define an empty set? : x = set() </li>
        <li> How do you define a function to yield an even list_of_numbers? : python
        def my_evens(list_of_numbers): </br>
        for i in range(list_of_numbers): </br>
        if i % 2 == 0: </br>
        yield i </br>
        </li>
       <li> Can you use the unittest module to test if the script is performing the desired changes on your infrastructure while it's running? : No, the unittest is only able to verify if the given functions return the proper values on specified inputs. </li>
        <li> "locals()" prints all local variables in current scope </li>
	    <li> List of all dunder methods in Python <a href="https://www.reddit.com/r/Python/comments/br9ok2/list_of_all_python_dunder_methods/"> in reddit </a> </li>
	    <li> Pytest command list all fixtures available : ```pytest --fixtures``` </li>
	    <li> The id() function returns a unique id for the specified object. All objects in Python has its own unique id. The id is assigned to the object when it is created. The id is the object's memory address, and will be different for each time you run the program </li>
	    <li> Print is a function in Python 3 and a keyword in Python 2. </li>
	    <li> The Unicode character set in the editor should match the Unicode standard of Python 3.</li>
	    <li> `py %F` is the Komodo command that you'll use to run a Python script on windows</li>
	    <li> When you already have python 2 on your mac, you can still download pyton 3 and it'll run separately in addition to python 2</li>
	    <li> Komodo Edit is free, while Komodo IDE is a pay version </li>
	    <li> Each print statement will print its output in a separate line</li>
	    <li> A valid shebang line starts with #! / A shebang line starts with a hash mark, immediately followed by an exclamation point.  </li>
	    <li> "True" - This is an expression but not a stand-alone line of code.(statement/line of code) </li>
	    <li> In all Python loop types, the evaluation is done before the loop starts. </li>
	    <li> When a return value is not specified explicitly, a function returns a none value </li>
	    <li> The f-string version prepends 'f' before the string, and leave the variable inside curly brackets. </li>
	    <li> While <b>shutil.copy()</b> copies the file content, <b> shutil.copystat() </b> copies the file metadata. </li>
	    <li> While <b>path.exists()</b> checks whether a path exists, <b> path.isfile() </b> checks wheter a path is a file. </li>
	    <li> "urllib" provides more granular control compared to "httplib" library </li>
	    <li> <b> HTMLParser </b> is the class provided by python to parse HTML </li>
	    <li> Ternary operator in python : <b>a if condition else b</b> </li>
	    <li> <b> Beautiful Soup </b> is a python package for parsing HTML and XML, including those with malformed markup such as missing tags </li>
	    <li> The default parser of BeautifulSoup is <b> lxml</b> which is lenient and fast as compared to html. </li>
	    <li> Both str() and repr() methods in python are used for string representation of a string. Now if you go by the official python documentation – the __str__ is used to find the “informal”(readable) string representation of an object whereas __repr__ is used to find the “official” string representation of an object. </li>
	    <li> <b> Sikuli </b> is a free open-source automation software that uses image detection to automate anything you see on your screen. Sikuli is a Jython interpreter(Uses both Python and Java). SikuliX or Sikuli is a scripting/automation technology that relies on pattern matching, and is available for use via Python or Java
	    <li> Code to dump HTML  </br>
	    
```python 
import urllib.request
webUrl = urllib.request.urlopen("http://www.google.com")
results = webUrl.read()
print(results)

