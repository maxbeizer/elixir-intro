### Types

```
1          # integer
0x1F       # integer
1.0        # float
true       # boolean
:atom      # atom/symbol
"string"   # string
[1, 2, 3]  # list
{1, 2, 3}  # tuple
```


### Basic Arithmetic

```
1 + 2       # 3
5 * 5       # 25
10 / 2      # 5.0 returns a float
div(10, 2)  # 5

0b1010      # binary accepted, e.g. 10
0o777       # octal, e.g. 511
0x1F        # hexadecimal, e.g. 31

round 3.58  # 4 - round
trunc 3.58  # 3 - lop off the float and take the integer
```


### Booleans

```
true           # true
true == false  # false
```


### Predicate Functions

```
is_boolean(true)  # true
is_boolean(1)     # false
```


### Atoms

```
:hello            # :hello
:hello == :world  # false
true == :true     # true
is_atom(false)    # true
```


### Strings

```
"hellö #{:world}"       # hellö world
IO.puts "hello\nworld"  # IO.puts/1 will print a string and returns :ok
is_binary("hellö")      # strings are binaries, i.e. true
String.length("hello")  # 5
String.upcase("hello")  # HELLO
'hello' == "hello"      # false
```


### Anonymous Functions

```
add = fn a, b -> a + b end

is_function(add)     # true
is_function(add, 2)  # true
is_function(add, 1)  # false
add.(1, 2)           # 3, `.` required to invoke anonymous function

add_two = fn a -> add.(a, 2) end  # Anonymous functions are closures
add_two.(2)                       # 4

x = 42                # block scope
(fn -> x = 0 end).()  # 0
x                     # 42, value not affected
```

### Linked Lists

```
[1, 2, true]         # lists can contain any type
length [1, 2, true]  # 3

[1, 2, 3] ++ [4, 5, 6]                         # [1, 2, 3, 4, 5, 6] list concatenation
[1, true, 2, false, 3, true] -- [true, false]  # [1, 2, 3, true] list subtraction

list = [1, 2, 3]  # head and tail of list examples
hd(list)          # 1
tl(list)          # [2, 3]
```

### Tuples

```
tuple = {:ok, "hello"}       # can hold any type
tuple_size tuple             # 2
elem(tuple, 1)               # "hello"
put_elem(tuple, 1, "world")  # {:ok, "world"}
tuple                        # {:ok, "hello"} tuple is immutable
```


### Lists Versus Tuples
Lists are stored in memory as linked lists. This means each element in a list points to the next
element, and then to the next element, until it reaches the end of a list.

Tuples, on the other hand, are stored contiguously in memory. This means getting the tuple size or
accessing an element by index is fast. However, updating or adding elements to tuples is expensive
because it requires copying the whole tuple in memory.


