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
    <li> </li> 
