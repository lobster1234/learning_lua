# Learning Lua 

1. Download dpkg file from http://rudix.org/packages/lua.html and install Lua. Its in /usr/local/bin
2. Install lua plugin for IntelliJ
3. In IntelliJ, create new Lua Project. When asked where Lua is, point to ```/usr/local/bin``` and it will do the rest.
4. Pick "Create new Lua script" in IntelliJ and type stuff in the file. Click "Run" to execute the script. This will be our little playground aside the interpreter.
5. To run the interpreter, type ```lua``` on a new Mac Terminal.
6. Feel free to type code in the script file in the IDE, alongside the interpreter. The IDE will do syntax highlighting and you can always keep adding more code to the bottom while keeping the old.

-------------

### Hello World

```print ("Hello World")```

If you're in the interpreter, you can also type ```="Hello World"``` as the interpreter takes anything after = as if its a part of print with brackets.  Note that this will only work in the interpreter, and not in the little script file we have going in IntelliJ.

You can also say ```return "Hello World"``` in the interpreter.

```_VERSION``` will print the version number of Lua you have.
```print(_VERSION``` will output ```Lua 5.3```

### Comments
Lua uses ```--``` to comment lines and ```--[[  --]] ```for blocks.
```
-- This is a line comment
```
```
--[[ 
 This is a block comment 
 ]]
```
```
 --[[ 
  This is also a block Comment 
 --]]
```
IntelliJ will syntax highlight all this for you.

### Identifier Names
Method and variable names are the standard fair as other languages, cant start with a number. Also, _ is the only legit special character allowed, not $ or @ etc. Oh and its all case sensitive.

```foo, Foo, _FOO, F00, f_0o``` are all good.

* ```null``` is ```nil```

* Lua is cool with whitespaces and indentation

### Declarations

* You've to explicitly declare a variable to be ```local```, otherwise its global. You can declare multiple variables in one line. They get initialized as ```nil``` unless you do.

```local a, b
print (a)``` will print nil. 

* You can do multiple initializations - this is the best part!

```local a,b = 10``` will initialize ```a``` as ```10``` and leave ```b``` as ```nil```

```local a,b = 10,1``` will initialize ```a``` as ```10``` and ```b``` as ```1```

* If you do not explicitly say local, it becomes global
```
 a = 10
 a,b = 10,2
 ```

* No error if you put more values in the value list

```local a,b = 1,2,3,4,5``` will not give any error. ```a``` will be ```1``` and ```b``` will be ```2```

* Swapping is super easy - no need for temp variables.
```local a,b = 1,2```
```print (a,b)``` will print ```1 2```
```a,b = b,a`
```print (a,b)``` will print ```2 1```

* This is awesome to not worry about floating point. 10/3 will not give 3 like Java, but 3.333. 
* Undeclared variables are _considered_ declared and have a value of ```nil```.  For instance, ```print(some_identifier_never_seen_before)```, it will be printed as ```nil```.
* Lua is a dynamically typed language (Javascript, python, ruby), so the type is not associated with the variable, but with the value that it refers to. Also these types can change anywhere, at any point, in the program with the same variable name. There is a function called ```type()``` which will print the type at that moment of the variable. 
```
 a = 10
 print(type(a)) --> prints number
 a = "Manish"
 print(type(a)) --> prints string
 ```
 
### Strings

You can use double or single quotes. Whatever you do, stick to it. Use single quotes only when your string has double quotes in it, unless you want to escape characters.
```"Hello, it's awesome"```
```'I said, "Hello!"'```
If you want a string thats a mix and match of all sorts of characters and quotes, use the ```[[``` to enclose the string.
```
[[
In this string I can do whatever, have a " with a ' and also
a new line all living happily.
]]
```
String concatenation is simple too. Use a comma for that. The whitespace feels a bit odd though.
```print("Hello","Manish")``` outputs ```Hello	Manish```

Another way to concatenate two strings is ```..``` which does not add any extra whitespace.
```
a = "Hello " <-- Notice the space after hello
b = "World"
print(a .. b)
```
will output ```Hello World```.

The operator  ```#``` will print the size of the string.
```print(#"I am a string")``` outputs 13, which is the length of this string.

The ```string``` class(?) has many standard utility functions, although not as rich as other languages, but they do the basic stuff like upper, lower, reverse, substring, etc. Sample usage -
```print(string.reverse("Reverse Me")```  outputs  ```eM esreveR```.

 
