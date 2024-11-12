## Ruby Attributes
- Imperative
- Object-oriented
- Strongly-typed
- Interpreted
- Dynamically-typed
- Everything is an object
- Platform-independent
- Later error detection

>[!Built-in Data Types]
>Numbers - Integers, Floats, Rationals, Complex
>Strings - "Mutable" and 'Immutable'
>Ranges - \[a..b]
>Arrays and Hashes

## Syntax

__Comments:__ begin with \#, for multiline use =begin, =end
To indicate a result within a comment, use =>
e.g. `"Hi #{name}" + "!" #=> "Hi Liam!"`

__Operators:  \+, \-, \*, \/, \%, \*\*, \<, \>, \<\=, \>\=, \<\=\>__, \&\&, \|\|, \!, \a\n\d, \o\r, \n\o\t

__Pseudo Variables:__ 
 - self - refers to the object that the method is called from
 - nil - null
 - true, false
 - \_\_FILE\_\_ - the current source file name
 - \_\_LINE\_\_ - the current line number

__Naming Schemes__
Local variable - starts with lowercase letter or \_
Global - starts with \$
Instance - starts with @
Class - starts with @@
Constant - starts with uppercase
Idiom - all uppercase

__Conditionals__
```
if (condition) [then] # parenthesis and then may be omitted
  ...
else
  ...
end
``` 

```
unless condition # equivalent to if not
  ...
end
```
__Statement Modifiers__
`unless` and `if` can be added to the end of a statement so that that line only runs if condition is met. e.g. `x = x + 1 unless condition`

>[!INFO]
>Conditionals do not create nested lexical scope. If a variable is defined within a conditional it is now available outside conditional scope. 

__Case Statements__

```
[var = ] case expression
when case1
  ...
when case2
  ...
else
  ...
end
```

>[!INFO]
>Avoid basic iteration. Instead, do 
>```
>array.each do |item|
>  ...
>end
>```

__Functions__
```
def func (x, y)
  x + y
end
```

>[!INFO]
>All functions return something. The last object executed will be returned

Functions do not have types in signature

To access a class or module within another class, use `Class::class2`
Omit parenthesis in functions with no parameters. They can also be omitted in any function calls. 


# Objects and Dynamic Types

Everything in Ruby is an object. All variables map to objects. 

An object's reference value is called an *object ID*. It is 4 or 8 bytes and stored in the variable slot. Call object ID with obj.object_id

### Immediates
Small integers have mathematical value encoded into its reference value. (e.g. `0.object_id = 0b00000001` where LSB is 1 and remaining bits encode B2T value)
This results in better performance. 

### Methods
Objects all have methods and since everything is an object, everything has methods. Unlike Java, the == operator compares *object value* and .equal? compares reference value. Assignments and parameters are all passed by reference, not value. This can result in aliasing. 

>[!INFO]
>Even though there are no variable types, you can't call any method on any variable. 

### Strings
Ruby strings are mutable, but can be *frozen*. 

### Assignment Operators
Ruby supports parallel assignment:
```
x,y,z = " ", 1, other_var
```
This can be used to swap variables:
```
x,y=y,x
```
Ruby also supports arithmetic contraction: 
```
+= -= *= /= %= **=
```
And logical contraction: 
```
||= &&=
||= is also used for initializing potentially nil variables
```

### Function Signatures
Ruby does not have variable types defined in method parameters. You can pass any type as a parameter for any function. 
Variable Types can change at any time during runtime. 

# Useful Classes and Methods

## Ranges

```
Range.new(a,b) # => returns a range class with the range of values from a to b

```

However, the more common use is to use its literal syntax: 
```
a..b # => returns range a to b inclusive
a...b # => returns range a to b end-exclusive
```

We can cast a range to a list with `[a..b].to_a`
Range can also return first and last with 
```
[a..b].first x #=> returns first x elements in range
[a..b].last x #=> returns last x elements in range
```

Range can also check inclusion and cover with:
```
[a..b].include? x # => returns true if x in [a..b]
[a..b].cover? x # => checks if x would fit between a and b
```

## Strings
Strings have 100+ methods, but some common ones are:
Methods with suffx ? should return boolean
Methods with suffix ! should change receiver
```
empty? # if string empty
start_with? x # if string starts with x
include?
length
to_f
to_i
split
upcase
downcase
capitalize
clear # no !
replace # no !
chomp
chop
slice
sub
gsub
```

## Arrays

Arrays are an instance of the Array Class
```
Array.new x # => array with x nil elements
Array.new x,y # => array with x elements of y
```

Literal notation is more common:
```
[1, 1.0, " ", []]
```

Array methods:
```
length
a[0] # => first element
a[-1] # => last element
a[x,y] # => elements from range x to y
```

>[!INFO]
>Accessing the index of an array past the end will extend it

Arrays have the properties of other data structures: 
```
a.pop
a.push x,...
a << x # => pushes x
a.shift # => pops from front
a.unshift # => pushes to front
```

Arrays also have the following methods:
```
.concat x # => concats with x array
a - b # => removes elements b from a
.reverse
.rotate
.shuffle
.sort
.find_index
.rindex
.include?
.uniq
.fill
.join
.product
.transpose
```

### Splat operator

When used on arrays: 
If splat is on right side, the array is generalized/split
If splat is used on left side, gathers all extra vars
Can work similar to ... parameter in Java

# Blocks, Hashes, Symbols

### Blocks

A [[Block Statement]] may have parameters. `5.times  {|n| puts n**2}`

We can write `yield` in a function, which will replace that yield with the block passed in as an argument. NOT PASSING IN A BLOCK INTO A FUNCTION THAT CONTAINS YIELD WILL ERROR OUT. 

Blocks can also be written by using 
```
do |var|
	code
end
```
and can be used to execute code on arrays like this:
```
arr.each {|var| code}
arr.each_index {|index| code}
arr.fill {|initial| code} #=> will replace with new val
arr.index { |var| condition}
arr.select! {|var| condition}
arr.reject! {|var| condition}
a.sort! {|var1,var2| condition <=> condition}
```

We can also transform an array into a new array with `arr.map {|var| code to transform}` which will return the new array. 

`arr.reduce(initial value) {|accumulated, item| code to reduce}`

### Enumerable

The enumerable module contains these methods:
```
arr.all? {|var| condition}
arr.any? {|var| condition}
arr.none? {|var| condition}
words.max_by {|var| condition}
arr.find_all {|var| condition}
arr.map {}
arr.reduce {}
```

### Hashes



### Usage



### Blocks with Hashes



### Keys




### Symbols



### Operational View



### Symbols as Keys



### Keyword Arguments







# Object-Oriented Concepts

### Classes


### Visibility


### Getters Setters



### Class Extensions



### No overloading



### Classes as object instances



### Instance, Class, Class Instance



### Inheritance



### Modules



### Namespaces



### Modules



### Mixins