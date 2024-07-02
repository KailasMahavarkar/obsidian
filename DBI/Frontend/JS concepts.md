
# What is callback Hell ?
when we nest multiple callbacks within a function is called a callback hell.

```js
getArticles(20, (user) => {
  console.log("Fetch articles", user);
  getUserData(user.username, (name) => {
    console.log(name);
    getAddress(name, (item) => {
      console.log(item);
      // this goes on and on...
    }
})
```

getUserData takes in an argument that is dependent or needs to be extracted from the result produced by getArticles which is inside user. The same dependency can be observed with getAddress also. This scenario is termed callback hell.



# What are Promises ?
A promise in JavaScript is asynchronous, meaning it takes time to resolve or finish
The promise constructor takes one argument, a callback with two parameters, resolve and reject. Do something within the callback, perhaps async, then call resolve if everything worked, otherwise call reject

```js
const cookMePizza = (pizzaSize) => {
    return new Promise((resolve, reject) => {
        if (pizzaSize > 7) {
            console.log('cooking pizza');
            setTimeout(() => {
                resolve('done cooking pizza for you 💫');
            }, 3000)
        } else {
            reject('error cooking pizza');
        }
    });
}

cookMePizza(4) // 4 is size of pizza
    .then((result) => {
        // result will become whatever we pass in resolve
        // in this case 'done cooking pizza'
        console.log(result);
    })
    .catch((error) => {
        // error will become whatever we pass in reject
        // in this case 'error cooking pizza'
        console.log(error);
    })


```



# What is Event Loop?

A must watch video (26mins) on event loop (official JS conference 2014)
[(13) What the heck is the event loop anyway? | Philip Roberts | JSConf EU - YouTube](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

If you wish to skip and want to read instead:

![](https://i.imgur.com/g1RqTv8.png)

Just remember: 
1. Its a lie when people say javascript is a single threaded programming language
2. Main thread of JS is single threaded but it also has internal webAPIs which execute code in parallel, in a essence its single threaded but its actually NOT.

```js
console.log("One")
setTimeout(()=>{
	console.log("Happy")
}, 2000)
console.log("Two")
```

How is the code above processed?
1. "One" will be added to call stack then processed and removed
2. "setTimeout" will be added to call stack, but processing is done via WebAPI (setTimeout is an WebAPI), thus setTimout WebAPI will execute code in background for next 2 second meanwhile JS engine will go and execute next line
3. "Two" will be added to call stack then processed and removed
4. once timer is completed it will push result in CallbackQueue



# What is hoisting

JavaScript is the behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase. However, it's important to note that only the declarations are hoisted, not the initializations.

>  deep dive for  hoisting:
>  The internal reason why we have function hoisting is simple, JS works in two phases its goes through the code two times
>  1. In first phase JS engine builds memory! when we say memory it means variables declaration are moved at top of the code.
>  2. In second phase JS engine executes code! at very beginning of this stage we already have information about all variables used in program (declaration were hoisted not initialzed).

```
console.log(x); // undefined
var x = 5;

// is translated to 

var x; // declaration is hoisted
console.log(x); // undefined
x = 5; // initialization

```



# What is Closures in JS?

![](https://i.imgur.com/BvOR4ci.png)

*Closures are **functions** that **refer to** independent (free) variables. In other words, the function defined in the closure ‘**remembers**’ the environment in which it was created.*



# What is Async/Await ?
Async/Await is special syntax to work with promises in a more comfortable fashion, called “async/await”.

```js

// note we have added async keyword
const cookMePizza = async (pizzaSize) => {
    return new Promise((resolve, reject) => {
        if (pizzaSize > 7) {
            console.log('cooking pizza');
            setTimeout(() => {
                resolve('done cooking pizza for you 💫');
            }, 3000)
        } else {
            reject('error cooking pizza');
        }
    });
}

const result = await cookMePizza(4);
try{
	console.log("result -->", result);
}catch(error){
	console.log("error -->", error);
}
```




# What Is Method Chaining?

Method chaining, or simply chaining, in JavaScript can be defined as when one or more sequential methods get invoked from an object without the introduction of unnecessary variables.

```js

const galaxy = ['rick','morty','summer','rick','kate','jerry']

// chaining result of map to filter
galaxy.map((x)=>x + ' heya').filter((x)=> x == 'rick heya');

```



