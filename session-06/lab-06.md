#Module 06: JavaScript Functions

##Overview

This lab does the following:

* introduces you to JavaScript functions (more specifically):
    * declaring and calling custom functions
    * passing arguments and using function parameters
    * using return values 
    * understanding function scope


###Working files

You should try out the code in this lab using the index.html file located in the session-06/lab/ directory from the course Github repository. Remember to sync your local version of the course repository with the online version.

##Required Readings

Chapter 3 of *Eloquent JavaScript*: [Functions](http://eloquentjavascript.net/03_functions.html)

##What are functions?

So far, we've been writing JavaScript code as one big unit of statements. The program runs top to bottom (with the exception of looping structure) and as things get more complicated things are looking a bit messy. Little bits of code all over the place. This is where functions come in because they help clean things up and replace 30 lines of code with one line.  The slobs among you might be tempted to forgo cleanliness BUT it also makes it easier to program.

Functions are a fundamental building block of larger programs and act to bundle sequences of JavaScript statements together so they may run at specific times. Thus rather than have 30 lines of code mucking around your program flow and confusing you, you bundle these lines into a function, store some place more out of the way and use one line to call it.  As the reading in *Eloquent JavaScript* [notes](http://eloquentjavascript.net/03_functions.html):

> "Functions are the bread and butter of JavaScript programming. The concept of wrapping a piece of program in a value has many uses. It is a tool to structure larger programs, to reduce repetition, to associate names with subprograms, and to isolate these subprograms from each other.  The most obvious application of functions is defining new vocabulary. Creating new words in regular, human-language prose is usually bad style. But in programming, it is indispensable."

So lets create some new JavaScript functions!

##Declaring and calling custom functions

First let's cover the syntax for writing functions. We begin declaring a function with the keyword `function`, followed by the name of the function (e.g., `function jackTheIguana`). We use the camelCase naming convention for functions, similar to naming variables. 

Also required for a function are two parentheses that immediately follow the function name. More about how to use this in a bit. Following this is a block statement (similar to those used by the for, while, if and else statements, which is also known as the function's *body*. Here's an example of a very basic function declaration:

```javascript
function helloMap() {
    console.log("Hello Map");
}
```

Here's another example of a very basic function declaration that is exactly the same as the previous one but involves Igunas:

```javascript
function jackTheIguana() {
    console.log("Iguanas RULE!!!");
}
```
If you type either of these functions into your script, save your file, and refresh your browser, you will not see the "Hello Map" or "Iguanas RULE" logged to the console. This `console.log` statement, contained within the function's block statement, has not yet been executed. It is just sitting quietly waiting to be called, much like an iguana waiting for its lunch.

To get the statements within a function's block statement to run, we need to *call* or "invoke" the function. We call a function with a simple statement: the name of the function itself, including the two paretheses:

```javascript
function helloMap() {
    console.log("Hello Map");
}

helloMap(); // this statement calls or invokes the helloMap() function!
```

We can think of the function as a piece of code that is waiting, ready to be executed for whenever we wish to call it. We can call it multiple times, for example:

```javascript
function helloMap() {
    console.log("Hello Map");
}

helloMap();
helloMap();
helloMap();
```

Of course, you want to be cautious about calling/invoking to many times as that is just silly. For example, if you included a for or while loop, you could invoke this simple function any number of times. 

Also, a key thing to remember about JavaScript if that we can call the function before the function has been declared. This is *different* from other programming languages such as Python. For example, the code below invokes the function jackTheIguana before is has even been declared! 

This no doubt giving this iguana all manner of existential doubt and ennui but the JavaScript works just fine.

```javascript
jackTheIguana();

function jackTheIguana() {
    console.log("Iguanas RULE!!!");
}
```

##Passing arguments and using function parameters

So far we've declared and called the most basic type of function. Essentially, the function receives no information when it's called. It just does something, and does it once. While this is cool, functions can be much more useful when they receive information from the "caller," or the statement that calls or invokes it. So rather than just doing exactly the same thing, the function can interact and react to stimuli. 

We refer to this as *passing arguments* to the function. An argument is an expression that is passed along to the function when it is called. Remember those two parentheses we need to include when declaring and calling a function? A caller sends arguments by including them within those parentheses. The function then receives these arguments (technically known as *parameters* as they enter the function) within its parentheses. Think of arguments and parameters as types of variables that refer to values or expressions used within functions. We can name these whatever we want (as long as it is not a reserved keyword!), and they too follow the camelCase naming convention. Consider our example now:

```javascript
function saySomething(message) {
    console.log(message);
}

saySomething("Hello Map");
```

This function is far more flexible and powerful than the previous one we created above. We can now pass any message we want to it:

```javascript
function saySomething(message) {
    console.log(message);
}

saySomething("Hello Map");
saySomething("My iguana has dreamy eyes.");
saySomething("Why are these people so obsessed with iguanas?");
```

We can also pass multiple arguments to a function. We simply include them within the parentheses and separate them with commas. Let's say we want to write a function that calculates the area of a rectangle. This is actually a quasi-useful function for mapping as we often want to know the physical area of polygons. Of course the world is not made of rectangular land areas -- with the exceptions of various parts of the agricultural Midwest (we're looking at you Iowa!) -- and hence the quasi-usefulness.  Still you can begin to see how one might construct mapping functions. The function for doing this is:

```javascript
function calcAreaRect(width,height){
    var area = width * height;
    console.log(area);
}
```

We can then send two Number values to the function. Note how they are incorporated into a JavaScript expression and assigned to a variable within the function's block statement:

```javascript
function calcAreaRect(width,height){
    var area = width * height;
    console.log(area);
}

calcAreaRect(40,30);
```

Note that we often pass expressions to a function in the form of a variable:

```javascript
function calcAreaRect(width,height){
    var area = width * height;
    console.log(area);
}

var width = 40;
var height = 30;
calcAreaRect(width,height);
```

We can pass as many arguments to a function as we'd like, as long as the function's declaration (sometimes referred to as a function's "signature") specifies a parameter for each argument passed when the function is invoked. The order of the arguments passed determines which parameter they are assigned to when they "reach" the function. Huh? 

OK, you've lined up your arguments in a certain order when you send them to the function they are accessed in the same order. Computers are  completely unimaginative and no arguments will try to budge ahead of others. They know their place and are happy to stay there.  This is a ticklish part of understanding function definitions so don't worry if you don't quite get it now, move on. 

Another thing to keep in mind is that the names we use for arguments and parameters are not persistent (i.e., do not stay the same) between calling a function and passing along arguments and when they reach the function (and magically become parameters). The arguments are passed along, but the names of the arguments (in the call) and parameters (in the function) don't have to match up. After all, what is in a name?  It's only the order in which they are passed that really matters. So, we could have written:

```javascript
function calcAreaRect(width,height){
    var area = width * height; // once parameters are in the function, the names do matter
    console.log(area);
}

var peanutButter = 40;
var jelly = 30
calcAreaRect(peanutButter,jelly);
```

The value of the variable `peanutButter` (40) is passed to the `calcAreaRect` function and assigned to the parameter `width`, which is then accessible as `width` within the function's block statement. *Note* once the parameters are in the function -- in this case as width and height -- the names do matter.

However, to keep things simpler and clearer, we often use the same name for the arguments as the parameters to which they correspond. Just remember that they don't need to do so. 

##Return values

So far we've created more flexible and powerful functions by writing them to accept arguments and do something with these arguments within their body. However, this is not yet the most useful use of a function because after the function executes the statements within its body, the story ends there. 

Rather function can become more "fruitful" (or igunalicious) by sending (or "returning") information back to its caller (the statement that invoked the function).  In computer programming, this is called "returning a value" as it provides useful information to the caller.

To do so, we simply use the `return` statement at the end of the function's body; consider this example:

```javascript
function calcAreaRect(width,height){
    var area = width * height;
    return area; // statements below a `return` statement in a function will **NOT** be executed
}

var width = 40;
var height = 30;
var calculatedArea = calcAreaRect(width,height);
console.log(calculatedArea);
```

When we call the function `calcAreaRect` we are also defing a new variable `calculatedArea`.  Thus when the function returns a value it is assigned to the new variable and then output to the console.log. 

The results are similar to what we did above -- when the output to the console.log was sent within the `calcAreaRect` function -- but we can could do any number of things because the value of the area is now *outside* the function.

One thing to keep in mind with return statements is that statements within a function's body that are written below a `return` statement will not be executed. For example:

```javascript
function sayThings() {
    
    console.log("thing 1"); // will output to console
    console.log("thing 2"); // will output to console
    return;                  // returns an `undefined` value
    console.log("thing 3"); // will NOT output to console
}

sayThings(); // calls the function
```

Also note that the return statement can only return a single element. If you wish to return multiple values, you can, for example, put them in an Array and return that Array (itself being a single element):

```javascript
function getMultiValues() {
    var value1 = 5;
    var value2 = "iguana";
    return [value1, value2];
}

var values = getMultiValues();
console.log(values[0]); // output is 5
console.log(values[1]); // output is "iguana"
```

See! Arrays are really useful!

##Function scope

So far in this module we've seen how functions are used to bundle chunks of code for use and re-use. Functions also provide an additional purpose within programming: that of establishing a *local scope*. That is, the variables created within a function's body exist (and are accessible) only from within that body, or that particular function's scope. This is often returned to as *encapsulation* within computer science. 

In addition to the local scope, defined within the body of a function, there is also the wider *global scope* of the HTML document itself. 

Consider this example of code that would result in an error:

```javascript
function doVegas (){
    var iguanaGreeting = "Hi, I'm Jack the Iguana.";
    console.log(iguanaGreeting);
}

doVegas(); // function call
console.log(iguanaGreeting); // throws an error
```

While the variable `iguanaGreeting` exists and is accessible within the function `doVegas()`'s body, that variable is unknown outside of that scope, in the global scope.  In other words -- what happens in Vegas, stays in Vegas.  

This is useful, because we can define and use variables within a function scope and not have to worry about them being computationally confused with variables outside that scope. For example:

```javascript
function doVegas(){
    var iguanaName = "Jack"; // variable defined within the function scope
    console.log(iguanaName); // output is Jack
}

doVegas();

var iguanaName = "Sally"; // variable defined within the global scope
console.log(iguanaName); // output is Sally
```

**Side Note**: Toying with the affections of multiple iguanas -- in Vegas or elsewhere -- is both morally reprehensible and liable to result in an iguana bite.

##Defining and calling functions

While we won't go into this too much, there is a slightly different way of creating functions than that of function declaration prescribed above: defining functions as a variable. For example:

```javascript
var saySomething = function(message) {
    console.log(message); // output is "Hello Map, Again."
}
saySomething("Hello Map, Again.");
```

There are really only two differences between this *definition* approach and the *declaration* approach to building custom JavaScript functions. First, when we define a function as a variable, we can only call that function after the place in which the function is defined. In this way, it is more like an interpeted script such as in Python. 

For example, the code below would be incorrect and will throw an error because the function `saySomething` is not yet defined:


```javascript
saySomething("Hello Map, Again."); // throws an error

var saySomething = function(message) {
    console.log(message); // output is "Hello Map, Again."
}
```

Second, when we wish to nest a function within another one (which is quite allowable in JavaScript), we need to use the definition approach to avoid issues in some web browsers that run JavaScript within a "strict" mode. So if you find yourself needing to have a function within the body of another function, this is the appropriate way to use a function within another:

```javascript
function outerFunction(message) {
    console.log(message)
    var innerFunction = function(message) {

        console.log(message)
    }
    innerFunction("I'm inside outerFunction!");
}
outerFunction("hi there");
```
Whew! That was a lot. But well worth it!

Functions, in particular the passing of arguments, return values, and function scope, are conceptually challenge to grasp at first. With more practice reading and writing functions, we'll get the hang of them. 

##Glossary
* ****:
* **function**: a set of reusable, self-contained statements of code that perform specific tasks (such as calculating and returning a value)
* **function body**: the statements contained within the curly braces of a function, also designating the functions "local scope"
* **calling or invoking a function**: the statement that "triggers" the function, passing optional arguments along with the call
* **argument**: the value passed to a function when that function is called
* **parameter**: the variable found within a function definition (and used within the function's body) to which an argument is assigned
* **return statement**: the statement within a function's local scope that terminates the sequence of statements within a function and returns 
* **function or local scope**: cooresponds to the statements contained within a function's body. variables created within the local scope are not accessible outside of this scope (i.e., in the global scope) 
