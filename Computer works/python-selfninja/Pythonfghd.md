 Topics: 
  1. Primitive datatypes & operators
  2. Variables & collections
  3. control flow & Iterables
  4. Functions
  5. Modules
  6. Class(OOPS)
	  1. Inheritance
7. Advance stuffs.

##### Intro
Its a high level and general purpose language.
Public release(1991)
created by Guido Van Rossum.
It is strongly typed

##### What is interpreter?
 Unlike a compilation process which takes the whole code and converts them into binary for execution, an interpreter will just run the code directly line by line and there is no need for compilation
##### Datatypes:
	1. Integer
	2. Float
	3. Boolean(True,False)
###### Comment

**Single line comment**:
 > In python we use # to comment the line.

**Multi line comment**:

> Double tick for the multi line comment. Eg: """dsfsadfsadf""".

###### Primitive operators:
+Addition,- - subraction,* - multiplication 

```
>>> 2+5
7
>>> 252+494
746
>>> 485-58
427
>>> 5/3 ---> this is float division or division operators
1.6666666666666667
>>> 5 // 3 ---> this is integer division
1(gives you the quotient)
>>> 5 % 3
2(gives you the reminder)
>>> 
```
/ - division (returns floating point)
// - integer division (returns integer)
% - modulo operators (returns integer)
** - exponent operator (power of )
```
2**6
64
```

###### Order of execution:
How the program runs the code line by line is order of execution.
Each and every statement or expression  that should executes line by line.

**BODMAS**:
B- brackets/functions
O-order/exponent
D-division
M-multiplication
A-Addition
S-subtraction

###### Booleans
(Case sensitive)
True carries 1. False carries 0
True\False is added with number.

Eg:
```>>> False
False
>>> True
True
>>> True + False
1
>>> True + False + True
2
>>> True + False + True + True + True + True + True
6
>>> False + False
0
```

###### Comparison operators:
It can check whether for the conditions below:
	1. ==  Equality
	2. !=  Inequality
	3. > Greater than
	4. < Less than
	5. >= Greater than or equal to
	6. <= Less than or equal to
	7. is  checks if both rars have same ref.
	   Checks of the Id.
	   Id (the address of something) same ah iruntha is true nu varum
These are all returns Boolean value

**is**:
Id is the address of the some input

So here is is used to compare the id of the input. It returns turns whether the id is same between the data or input.
```
>>> a=5
>>> b=4
>>> id(a)
139760479224176
>>> id(b)
139760479224144
>>> id(1)
139760479224048
>>> id(a)
139760479224176
>>> id(a) is id(b)(checking the address(id) of the input)
False
>>> a=5
>>> b=5
>>> a = b
>>> a == b
True
>>> id(a)
139760479224176
>>> id(b)
139760479224176
>>> id(a) is id(b)
False
>>> a is b
True
>>>
```
###### Chaining Comparisons:
To proceed for the chaining of the comparisons we need to know about the logical gates. 

Gates: 
- AND
- OR
- NOT

**AND**:
 And satisfies if the all the conditions were satisfies and gives the returns <span style="color:rgb(255, 255, 0)">TRUE</span>.
**OR**:
If any one satisfies OR returns <span style="color:rgb(255, 255, 0)">TRUE</span>.

**Memory Management:**

**Immutable** - Datatypes in python where the value assigned to a variable cannot be changed.
**Mutable**  - Datatypes in python where the value assigned to a variable can be changed without changing the address of the assigned var.

**Datatypes:

| Integer           | Float             | String                                                      | Lists              | Tuple | Dictionary | Sets |
| ----------------- | ----------------- | ----------------------------------------------------------- | ------------------ | ----- | ---------- | ---- |
| Immutable         | Immutable         | Immutable                                                   | Mutable            |       |            |      |
| Address:Immutable | Address:Immutable | Address: Mutable (Data)<br>Address: Immutable (Identifiers) | Address: Immutable |       |            |      |
| Data:Immutable    | Data:Immutable    | Data: Immutable                                             | Data:Mutable       |       |            |      |


*Mutable of lists:*
```bash
>>> a= [1,2,3,4]
>>> id(a)
139760456911488
>>> a.append(5)[value is modified]
>>> a
[1, 2, 3, 4, 5]
>>> id(a)
139760456911488(which is mutable where the value or data is append without affecting its own Id)
```

---
*Immutable of integer:*
```bash
>>> a=5
>>> id(a
... )
139760479224176
>>> a=a+1
>>> id(a)
139760479224208
>>> 
```

---

Immutable to Float:
```bash
>>> a=a+5
>>> a
6.25
>>> id(a)
139760456437328
```

---

##### Strings:
Anything which is inside a enclosed in a quotes.
"this is a string" OR 'this is a string'-- which is a single line string.
"""this is 
also a string""" -- which is also a string named as multiline string. Same as comment. 
If the multiline string was assigned to a variable, it is not consider as a comment.

```bash
a= "this is a string"
a='this is string'
a="""hello, 
this is also a string which 
is consider as the comment as well as multiline string"""
>>> print(a)
hello,
this is also a string which
is consider as the comment as well as multiline string
```


```python
even though `a` and `b` hold the **same string value**, they may have **different memory addresses (`id`)** due to Python’s optimization rules (e.g., interning isn't guaranteed for strings with spaces).
>>> a = "hello world"
>>> b = "hello world"
>>> id(a)
139760476992816
>>> id(b)
139760478451056

both `a` and `b` refer to the **same memory address**, because Python **interns** strings that:
consist of letters, digits, and underscores (like identifiers).
>>> b = "hello_world"
>>> a = "hello_world"
>>> id(a)
139760477018288
>>> id(b)
139760477018288
```
---
