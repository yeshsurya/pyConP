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
