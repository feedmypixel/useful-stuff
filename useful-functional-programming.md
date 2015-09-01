# Useful Functional Programming Stuff

## Links

[http://www.smashingmagazine.com/2014/07/02/dont-be-scared-of-functional-programming/](http://www.smashingmagazine.com/2014/07/02/dont-be-scared-of-functional-programming/)  
[http://reactive-extensions.github.io/learnrx/](http://reactive-extensions.github.io/learnrx/)

## Tips
- Data should be immutable.
- Should be stateless.
- When programming in a functional style, you’re always looking for simple, repeatable actions that can be abstracted out into a function.
- All of your functions must accept at least one argument.
- All of your functions must return data or another function.
- No loops!
- Notice that JavaScripts forEach let's us specify what we want to happen to each item in the array, but hides how the array is traversed. 
- Its not running items with loops it is abstracting that looping functionality away to enable the code to be cleaner and provide a higher level.
- Pure functions. 
- No side affects.
- Contained unit doesn’t presume or use anything from its environment e.g new Date() would be an outside presumption
