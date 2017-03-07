# Week 1 Class 2 #

## Class work ##

Practise in-class functions without use of a library

* Add HTML Headings + buttons that will change the colors of the headings
* Add a mouseover image to appear on hover or zoom or fade
* Add a user input field that displays a pop-up window (w/input data on submit)

This is a basic example of the following events/concepts:

1. change heading color on button click
2. pop up result of input from user      
3. dynamic use of input					
4. variables							
5. add mouseover event functions 		
6. "this" keyword						
7. JS in separate class (main.js)

We didn't get to the following parts of this demo:
8. CSS
9. if statements (if input is empty)

```
<!DOCTYPE html>
<html>
<head>
    <title>Class 2</title>

</head>
<body>
    <h1 id="myh1">Happy Thursday!</h1>
    <h2 id="myh2">This is a heading</h2>
    <h4> Input a color:
    <input id="choice" type="text"></input>
    <button id="b1">Change color</button>
    </h4>
    <p id = "joke"> Joke time! </p>
    <img id="img1" src="joke4.png">
    <!-- <script src='main.js'></script> -->

<script type="text/javascript">
        var img1 = document.getElementById("img1");
	var choice = document.getElementById("choice");

    document.getElementById('b1').addEventListener('click',function(){
    	document.getElementById("myh1").style.color='blue';
        if(choice.value != ""){
        	alert(document.getElementById("choice").value);
        	document.getElementById("myh2").style.color= document.getElementById("choice").value;
    		document.getElementById("myh2").innerText = "This is a heading in "+ choice.value;
        	choice.value="";
        }

    });
    document.getElementById("joke").addEventListener('mouseover',function(){
        img1.style.display = "block";
    });
    document.getElementById("joke").addEventListener('mouseout',function(){
        img1.style.display = "none";
    });
    img1.addEventListener("load", function(){
	this.style.display = "none";
    });

</script>

</body>
</html>
```


# Welcome to JavaScript!

## Build a simple button and a simply-styled page
(Tues)  
- Reference: variables
- Reference: arrays

(Thurs)
Review Bootstrap site reference to choose/add styling
- [Buttons](http://getbootstrap.com/javascript/#buttons)
- [Popovers](http://getbootstrap.com/javascript/#popovers)
- Reference: objects
- Reference: Booleans

## Learning Goals
- What & Why FrauenLoop?
- What is JavaScript?
- Learn about _datatypes_ and _functions_ in JS

 We are going to talk about __variables__, __datatypes__, and __functions__.

### Variables
__Declare all variables with the var operator!__

```javascript
var five = 5;
```

If you omit `var` you will get a __global__ variable, which can lead to all sorts of problems. __JUST DON'T DO IT!__

**Note** that each line of JavaScript code ends with the `;`. This is optional for the code to work (sometimes, and the rules are inconsistent) but **not** optional when taking into consideration style guidelines.

### Types
[MDN Data Types and Data Structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

JavaScript's basic _types_ are similar to Ruby's: `Boolean`, `Null`, `Undefined`, `Number`, `String`, `Array`, `Object`, and `Function`.

#### `Boolean` is `true` or `false`
```javascript
var t = true;
var f = false;
```

#### `Null` is the value null. This represents an "empty" value.
```javascript
var empty = null; // similar to Ruby's nil
```

#### `Undefined` is the value undefined.
When a variable which has not declared is accessed, JS returns undefined.

```javascript
var u;
console.log(u); //-> undefined
```

#### `Number` is a numeric value
It includes integers (1, 2, 3, etc.), floats (1.4, -40.1), infinity (+Infinity, -Infinity), and `NaN` which means "not a number." `NaN` is returned when you do a numeric operation on anything that's not a `Number`.

```javascript
var four = 4,     // Note the comma-separated variable declarations
    two = 2.0;

Infinity < Number.MAX_VALUE  // false
Infinity > Number.MAX_VALUE  // true

two == four / two; // true

// All JS numbers are floats, and floats are not 100% accurate...
0.1 + 0.2 == 0.3; // false!
0.1 + 0.2;

"asdf" - 5; // NaN
```

#### `Strings` are declared with "" or ''.
They're the same. Pick one and stick with it! __Note:__ One thing you cannot do in JavaScript is Ruby-style interpolation.

```javascript
var str = "This is a string";
str.length;      // 16 - access the length property
str.substr(2,5); // "is is" - call the substr function

var e = "elephant";
console.log("#{e} hotdog"); // "#{e} hotdog" js doesn't do interpolation
```

#### Arrays
[Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) are similar to Ruby arrays. They are declared and accessed with square brackets ([]).

```javascript
var arr = [1, 2, 3, 4];
arr.length;  // 4 - access the length property
             // Note this *cannot* be accessed like a method with parenthesis
arr[0];      // 1
arr.pop()    // 4 - call the pop() function
             // Note this method *cannot* be used without the parenthesis
arr;         // [1, 2, 3]; pop() mutates the array
```

#### Objects
[Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) are similar to Ruby hashes, but much more versatile. They are declared with braces(`{}`). You can access properties in an Object with bracket notation (like an array) or dot notation.

```javascript
var obj = {     // We can span lines; whitespace is mostly ignored.
  num: 5,
  str: "This is a string",
  subObject: {
    otherNum: 4
  }
};

obj.num;    // 5
obj['num']; // 5; note we use a string!
obj.subObject.otherNum; // 4
obj.foo;    // undefined

```

### [Conditionals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)
Conditional expressions are surrounded by parenthesis `()` and each block is surrounded by brackets `{}`.

```javascript
var name = "kittens";

if (name == "puppies") {
  name += "!";
} else if (name == "kittens") {
  name += "!!";
} else {
  name = "!" + name;
}

console.log("name");
```

JavaScript also has the ternary operator, which we all adore, am I right? :-)

```javascript
var adult = (age > 18) ? "yes" : "no";
```

### Iterators
#### `for` Loop
The most common iterator in Javascript is the `for` loop. It can be executed three different ways, depending on what kind of loop you need

##### [The basic `for` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)
- has three parts:
  - `var i = 0` - **starter**  
    This executes at loop start.
  - `i < 5` - **loop condition**  
    The condition to check if loop is finished. It is checked after every execution of loop body.
  - `i++` - **increment**  
    An action to perform after every iteration, but before the loop condition is checked.
-
  ```javascript
  for (var i = 0; i < 5; i++) {
    // Will execute 5 times
  }
  ```

##### [The `for...of` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)
The `for...of` loop works like the `for` loop above, but is optimized for iterating ordered collections. Mos of the time this is an array, but it could also be a JavaScript Map, Set, or even String!

```javascript
var arr = [1,2,3]
for (var val of arr) {
  console.log("val is " + val);
}
// the val is 1
// the val is 2
// the val is 3

for (var letter of "bark") {
  console.log("letter is " + letter);
}
// letter is b
// letter is a
// letter is r
// letter is k
```

##### [The `for...in` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in)
The `for...in` loop works very much the same as `for...of`, but it _does not guarantee the order of iteration_. We use it primarily to loop through the _iterable_ properties of an object, including the properties it inherited. Use `for...in` to iterate objects.

```javascript
var obj = {a:1, b:2, c:3};
for (var prop in obj) {
  console.log("obj." + prop + " = " + obj[prop]);
}
// obj.a = 1
// obj.b = 2
// obj.c = 3
```


#### `while` Loop
JavaScript also uses the `while` loop in a similar way to the way we use it in Ruby.

```javascript
var i = 0;
while (i < 10) {
    text += "The number is " + i;
    i++;
}
console.log(text);
```

### Functions
Functions in JavaScript are __awesome__. Rather than using the `def` keyword like definition, JavaScript uses the `function` keyword to declare a function. They can be put in variables, and passed around like any other type. We will spend a lot of time talking about functions as they are the cornerstone of understanding JavaScript.

```javascript
function choicier(choice1, choice2) {
  if (choice1 == choice2) {
    return "These are the same!";
  } else {
    return "These are not the same!"
  }
}

// You **must** use parens to execute a function
choicier; // this returns the function
choicier(4, 4) // "These are the same!" - execute the function and returns the result
```

```javascript
var adder = function (a, b) {
  return a + b;   // You need to explicitly call return in JavaScript
}

// You need to use parens to call your function!
adder;        // this returns the function that you just declared
adder(1, 2);  // 3 - this executes the function and returns the result
```

#### A note about `this`
The keyword `this` is probably the most misunderstood concept in JavaScript. At its core, `this`, when invoked inside a function, refers to the invocation _context_ of the containing function (wat). Essentially, `this` is kinda like `self` in Ruby (this object, right here), but it is more common in JavaScript for functions to be executed in contexts beyond where they were declared.

As we explore how functions work, we will also discover the ins and outs of `this`. For now, we can think of `this` to mean _this object, right here_.

```javascript
  var repeater = function(word) {
    console.log(this);
    return word + word;
  };

  var repeater_object = {
    dog: " bark bark ",
    repeater: function(word) {
      console.log(this);
      return word + word;
    },
    repeat_dog: function(word) {
      // `this` refers to the current object in context
      // most of the time, this will be repeater_object
      return word + this.dog + word + this.dog;
    }
  };

  repeater("cat"); //omg so much stuff
  repeater_object.repeater("cat"); //lots less stuff; why?
  repeater_object.repeat_dog("cat"); //cat bark bark cat bark bark
```

# JavaScript Exercises

## Exercise #1: Create a ToDo object, with the following properties:
- a task (string) - a description of the thing to do
- assignee (string) - the name of a person to do it
- done (boolean) - is the task done or not?
- getDone (function) - get the value of done, use "this" in the body of the function.
- setDone (function) - set the value of done, use "this" in the body of the function.

### Exercise #2: Find the biggest number in the array
- Utilize the stub code below to complete the problem:
- `getBiggest` should accept an array as a parameter and return a the largest number in the array

```javascript
var arrayOfNums = [2, 7, 7, 3, 9, 0, 1, 6, 8, 3, 8, 4, 7, 9];

function getBiggest(array) {
  // your code goes here!!
}

//
// pass an array to getBiggest;
// get a return value that is the biggest number in the array
//
var biggest = getBiggest(arrayOfNums);
console.log("The biggest is: ", biggest);
```
