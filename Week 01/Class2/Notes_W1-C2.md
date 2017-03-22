# Week 1 Class 2 #


## Class work ##

Practise in-class functions without use of a library


* Add variables

```javascript
    //Declare variables
    var b1 = document.getElementById('b1');
    var colorchange = document.getElementById('colorchange');
    var myh1 = document.getElementById('myh1');
    var myh2 = document.getElementById('myh2');
    var choice = document.getElementById('choice');
    var joke = document.getElementById('joke');
    var img1 = document.getElementById('img1');
   
```

* Add a button function

```javascript
    //Alert button from first class
    b1.addEventListener('click',function(){
        alert("You clicked a button on the page");  
    });
```


* Add button function that will change the color of one heading

```javascript
    // Change color on click event 
    colorchange.addEventListener('click',function(){
        // Change color to predefined value
        myh1.style.color='blue';
        // Use the color that is input
        myh2.style.color= choice.value;
    });
```

* Add a mouseover image to appear on hover or zoom or fade

```javascript
            // hide image on load
            img1.addEventListener("load", function(){
                img1.style.display = "none";
            });

            // Show image on mouse over
            joke.addEventListener('mouseover',function(){
                img1.style.display = "block";
            });
            // Hide image on mouse out 
            joke.addEventListener('mouseout',function(){                    
                img1.style.display = "none";
            });
```


This is a basic example of the following events/concepts:

1. change heading color on button click 
2. pop up result of input from user      
3. dynamic use of input                 
4. variables                            
5. add mouseover event functions        