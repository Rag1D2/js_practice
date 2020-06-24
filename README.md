# What is JS?

- JavaScript is a browser language. There is no company called JavaScript.
  The language is monitored by a TC39 council. People can submit proposals for new features and standards to JS.
  If the proposal is accepted, that new feature is added to the latest ECMAscript standards.

- JS is ALWAYS backwards compatible. So if you ran JS code written 20 years ago, it would still run perfectly in the browser today.
  Modern JS is written on the back of the original.
  Advanced and modern features were simply added to the old standards along the way.

# Compiler vs Polyfill

If you write more modern (newer) JavaScript, there is no guarantee that every browser would be able to read the code. Some browsers may not have implemented the newer features yet. (Then your breaks, which sucks)

#### Compiler

Compilation allows you to write modern JS (including the latest and greatest features) and it "compiles" the code into an older version of the code so that it can be read by all browsers.

- Babel is a JS compiler

It allows you use the most modern features of JS (even some that have not yet been fully implemented into standard JS)

#### Polyfill

Polyfill is new code that is imported into your code to give you that specific feature in old code.

- npm promise-polyfill is an example.
  This would allow you to use Promises in older JS where it may not normally be recognized.

---

# What is "use strict"

Strict mode allows you to place a program or function in a "strict operating context"

Code errors that would normally be ignored, or fail silently will generate errors or throw exceptions

to implement type:

```
"use strict";
```

The command is in a string because older browsers would not support it.
this would cause the code to fail. So putting "use strict"; in a string makes older browsers ignore it, but newer browsers that recognize it implement strict mode.

Strict mode can also be implemented into a singular function in JS without using the "strict operating context" throughout the entire JS file:

```
// Not strict mode...

function newCode() {
    "use strict";
    //Strict mode...
}
```

In a nutshell, strict mode makes debugging waaaay easier.

One example of this is variable declaration

```
matt = 1
```

This would normally create the global variable: "matt" within the window object of the browser and assign its value: "1"

if we run

```
"use strict";

matt = 1
```

We get back an error because "matt" has not been defined

"use strict"; will also not allow you to use words that are reserved for future versions of JS

```
"use strict";
var let = 1;
```

this will return an error "Unexpected strict mode reserved word"
This means that we can use the word "let" because it is reserved for a future version of JS.

# Value or Reference Passing?

```
"use strict";

var a;

function foo(a){

}
```

In the above code, does JS pass "a" by its value or by its reference?

- Primitive types (Strings, numbers, booleans) are passed by value.
- Objects are passed by reference.

#### So what do these mean?

Passed by value means that if we change the value of a primitive type inside a function, it does not effect the value of the variable outside of that function scope.

Passed by reference we are pointing to something else instead of making a copy of that thing.
So if we change a property in an object in a function, the change will be reflected in the outer scope.

```
"use strict";

var a = {};
function foo() {
    a.moo = false;
}
foo(a);
console.log(a)
```

The console logs "Object {moo: false}"
So we added the property and its value to the object and that property now exists within that object even outside of the function scope.
