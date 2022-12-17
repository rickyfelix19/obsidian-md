# JavaScript

_source: [The Modern JavaScript](https://javascript.info/)_

## JavaScript Fundamentals

### Variables

-   let (modern variable declatration)
    
-   var ("old way", normally it is not use anymore)
    
-   const (unchanging variable)
    

#### Limitations of (Naming) Variables

1.  The name must only contain letters, digits, or the symbols `$` and `_`
    
2.  The first character must not be a digit
    
3.  Variables named `apple` and `AppLE` are two different variables.
    
4.  Non-Latin letters are allowed, but not recommended
    
5.  There is a list of [reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords). For example: `let`, `class`, `return`, and `function` are reserved.
    
    // Examples  
    let userName;  
    let test123;  
    ​  
    // these names are valid:  
    let $ = 1;  
    let _ = 2;  
    ​  
    alert ($ + _); // 3  
    ​  
    // Examples of incorrect variable names  
    ​  
    let 1a; // rule 1 -> not start with a digit  
    let my-name; // rule -> hyphens '-' arent allowed 
    

### Constant (Unchanging Variable)

Variables declared using `const` are called “constants”. They cannot be reassigned. An attempt to do so would cause an error

const myBirthday = '18.04.1982';  
myBirthday = '01.01.2001'; // error, can't reassign the constant!

There is a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution. Such constants are named using capital letters and underscores.

const COLOR_RED = "#F00";  
const COLOR_GREEN = "#0F0";  
const COLOR_BLUE = "#00F";  
const COLOR_ORANGE = "#FF7F00";  
  
// ...when we need to pick a color  
let color = COLOR_ORANGE;  
alert(color); // #FF7F00  
  
/*  
	Benefits:  
    - COLOR_ORANGE is much easier to remember than "#FF7F00".  
    - It is much easier to mistype "#FF7F00" than COLOR_ORANGE.  
    - When reading the code, COLOR_ORANGE is much more meaningful than #FF7F00.  
*/

#### UPPERCASE Constant vs camelCase Constant (TL;dR)

When should we use capitals for a constant and when should we name it normally? -> **Capital-named constants are only used as aliases for “hard-coded” values.**

> There are constants that are known prior to execution (like a hexadecimal value for red) and there are constants that are _calculated_ in run-time, during the execution, but do not change after their initial assignment.
> 
> const pageLoadTime = /* time taken by a webpage to load */;  
>   
> /*   
> 	The value of `pageLoadTime` is not known prior to the page load, so it’s named 		normally. But it’s still a constant because it doesn’t change after assignment.  
> */

#### Name Things Right

General Rule of Thumb:

-   A variable name should have a clean, obvious meaning, describing the data that it stores.
    
-   A good variable name differentiate if it's done by a beginner vs experienced programmers
    
-   Use human-readable names like `userName` or `shoppingCart`.
    
-   Stay away from abbreviations or short names like `a`, `b`, `c`, unless you really know what you’re doing. **(NOT RECOMMENDED)**
    
-   Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. Such names say nothing. It’s only okay to use them if the context of the code makes it exceptionally obvious which data or value the variable is referencing.
    
-   Agree on terms within your team and in your own mind. If a site visitor is called a “user” then we should name related variables `currentUser` or `newUser` instead of `currentVisitor` or `newManInTown`.
    

#### Reuse or Create

> An extra variable is good, not evil.
> 
> Some programmers kept on re-using the same variable to the point they dont know what the value of a variable is anymore which results in a waste of time and leads on debugging

### Data types

There are 8 basic data types in JavaScript:

-   `number` for numbers of any kind:
    
    -   integer or floating-point,
        
    -   integers are limited by `±(253-1)`
        
    -   besides regular number, this data type belong to: `Infinity`, `-Infinity` and `NaN`.
        
        -   Infinity (is the math infinity) represents greater than any number
            
        -   NaN represents a computational error
            
-   `bigint` is for integer numbers of arbitrary length.
    
    -   A `BigInt` value is created by appending `n` to the end of an integer: `const bigInt: 9007199254740991n;`
        
    -   represent integer values larger than `(253-1)` that’s `9007199254740991`
        
        -   or less than `-(253-1)` for negatives that’s `-9007199254740991`
            
    -   For most purposes that’s quite enough, but sometimes we need really big numbers, e.g. for cryptography or microsecond-precision timestamps.
        
-   `string` for strings. A string may have zero or more characters, there’s no separate single-character type.
    
    -   In JavaScript, there are 3 types of quotes.
        
        -   Double quotes: `"Hello"`, Single quotes: `'Hello'` (practically the same)
            
        -   Backticks: `Hello` (extended functionality; wrapping `${…}`)
            
            > let name = "John";  
            >   
            > // embed a variable  
            > alert( `Hello, ${name}!` ); // Hello, John!  
            >   
            > // embed an expression  
            > alert( `the result is ${1 + 2}` ); // the result is 3  
            >   
            > alert( "the result is ${1 + 2}" ); // the result is ${1 + 2} (double quotes do nothing)
            
-   `character type` doesnt exist in JavaScript, there is one type `string`
    
    -   zero, one, or many characters
        
-   `boolean` for `true`/`false`.
    
-   `null` for unknown values – a standalone type (or does not belong to any data types) that has a single value `null`.
    
    -   In JavaScript, `null` is not a “reference to a non-existing object” or a “null pointer” like in some other languages.
        
    -   It’s just a special value which represents “nothing”, “empty” or “value unknown”.
        
        let age = null; // simply means, age is unknown
        
-   `undefined` for unassigned values – a standalone type that has a single value `undefined`.
    
    -   similar to `null`; `undefined` is "value not assigned"
        
        let age;  
        alert(age); // shows "undefined"  
          
        /*  
        	not recommended  
        */  
          
        let age = 100;  
          
        // change the value to undefined  
        age = undefined;  
        alert(age); // "undefined"
        
-   `object` for more complex data structures.
    
    -   The `object` type is special.
        
    -   Objects are used to store collections of data and more complex entities.
        
-   `symbol` for unique identifiers.
    

#### Null vs Undefined

> Normally, one uses `null` to assign an “empty” or “unknown” value to a variable, while `undefined` is reserved as a default initial value for unassigned things.

#### Object and Symbols

> All other types are called “primitive” because their values can contain only a single thing (be it a string or a number or whatever) but `object` type is special
> 
> The `symbol` type is used to create unique identifiers for objects.

#### typeof

The `typeof` operator allows us to see which type is stored in a variable.

-   Two forms:
    
    -   `typeof x` (as an operator)
        
    -   `typeof(x)` (as an function)
        
-   `typeof x` will returns the name of the type, in this case, it's a `"string"`.
    
-   For `typeof null` returns `"object"` – this is an error in the language, it’s not actually an object.
    
-   For `typeof alert` returns `"function"` - cause it's a function
    

### Interaction: alert, prompt, confirm

All these methods are **modal**: they pause script execution and don’t allow the visitor to interact with the rest of the page until the window has been dismissed.

#### alert

This one we’ve seen already. It shows a message and waits for the user to press “OK” The mini-window is called a _modal window_. The word modal means user can't interact with it, unless they press "OK"

`alert("Hello World!")`

#### prompt

The function `prompt` accepts two arguments:

result = prompt(title, [default]);  
  
// title -> the text to show the visitor  
// default -> an optional second parameter, the initial value for the input field  
  
// The square brackets in syntax [...]  
// in this case, [default] denote that the parameter is optional, not required.

The visitor can type something in prompt input field and press OK. Then will get input in the result. Or they can cancel by hitting Cancel or `esc`, then we will get `null` as the result

let age = prompt('How old are you?', 100);  
  
alert(`You are ${age} years old!`); // You are 100 years old!

#### confirm

The function `confirm` shows a modal window with a `question` and two buttons: OK and Cancel. The result is `true` if OK is pressed and `false` otherwise.

// Syntax  
result = confirm(question);  
  
// Example  
let isBoss = confirm("Are you the boss?");  
alert (isBoss); // true if OK is pressed

#### Limitations

1.  The exact location of the modal window is determined by the browser. Usually, it’s in the center.
    
2.  The exact look of the window also depends on the browser. We can’t modify it.
    

> That is the price for simplicity.
> 
> There are other ways to show nicer windows and richer interaction with the visitor, but if “bells and whistles” do not matter much, these methods work just fine.

### Type Conversions

Most of the time, operators and functions automatically convert the values given to the right type.

#### String Conversion

String conversion happens when we need the string form of a value String conversion is mostly obvious

> `false` becomes `"false"` and `null` becomes `"null"`

// For example  
alert(value); // this alert will show value  
  
// we can also use String(value) function to convert a value to a string  
let value = true;  
alert(typeof value); // boolean  
  
value = String(value); // now value is a string "true"  
alert(typeof value); // string

#### Numeric Conversion

Numeric conversion happens in mathematical functions and expressions automatically

alert("6" / "2"); // 3, strings are automatically converted to numbers  
  
// we can also use Number(value) function to explicitly convert a value to a number  
// Explicit conversion is usually required when we read a value from a string-based source like a text form but expect a number to be entered.  
let str = "123";  
alert(typeof str); // string  
  
let num = Number(str); // becomes a number 123  
  
alert(typeof num); // number  
  
// if string is not a valid number, the result will returns NaN  
let age = Number("an arbitrary string instead of a number");  
  
alert(age); // NaN, conversion failed

##### Number Conversion rules:

Value

Becomes

undefined

NaN

null

0

true and false

1 and 0

string

Whitespaces from the start and end are removed. If the remaining string is empty, the result is `0`. Otherwise, the number is “read” from the string. An error gives `NaN`.

alert( Number("   123   ") ); // 123  
alert( Number("123z") );      // NaN (error reading a number at "z")  
alert( Number(true) );        // 1  
alert( Number(false) );       // 0  
  
// Please note that null and undefined behave differently here: null becomes zero while undefined becomes NaN.

#### Boolean Conversion

The conversion rule:

-   Values that are intuitively “empty”, like `0`, an empty string, `null`, `undefined`, and `NaN`, become `false`.
    
    -   Some languages (like PHP) treat `"0"` as `false`
        
-   Other values become `true`.
    
    -   In Javascript, **a non-empty string** is always `true`
        

// It happens in logical operations (later we’ll meet condition tests and other similar things) but can also be performed explicitly with a call to Boolean(value).  
  
alert( Boolean(1) ); // true  
alert( Boolean(0) ); // false  
  
alert( Boolean("hello") ); // true  
alert( Boolean("") ); // false  
  
alert( Boolean("0") ); // true  
alert( Boolean(" ") ); // spaces, also true (any non-empty string is true)

### Basic operators, maths

-   an _operand_ (arguments) is what operators are applied to
    
-   _an operator_ is unary if it has a single operand
    
-   _the unary negation_ `-` reverses the sign of a number
    
-   _an operator_ is binary if it has two operands
    

#### Maths

The following math operations are supported:

-   Addition `+`,
    
-   Subtraction `-`,
    
-   Multiplication `*`,
    
-   Division `/`,
    
-   Remainder `%`, (not related to percents)
    
-   Exponentiation `**` (a^b)
    

#### String concatenation with binary +

let s = "my" + "string";  
alert(s); // mystring  
  
alert( '1' + 2 ); // "12"  
alert( 2 + '1' ); // "21"  
  
alert(2 + 2 + '1' ); // "41" and not "221"  
  
alert('1' + 2 + 2); // "122" and not "14"  
  
alert( 6 - '2' ); // 4, converts '2' to a number  
alert( '6' / '2' ); // 3, converts both operands to numbers

#### Numeric conversion, unary +

// No effect on numbers  
let x = 1;  
alert( +x ); // 1  
  
let y = -2;  
alert( +y ); // -2  
  
// Converts non-numbers  
alert( +true ); // 1  
alert( +"" );   // 0  
  
// It actually does the same thing as Number(...), but is shorter.  
  
let apples = "2";  
let oranges = "3";  
  
alert( apples + oranges ); // "23", the binary plus concatenates strings  
  
let apples = "2";  
let oranges = "3";  
  
// both values converted to numbers before the binary plus  
alert( +apples + +oranges ); // 5  
  
// the longer variant  
// alert( Number(apples) + Number(oranges) ); // 5

#### Operator precedence

If an expression has more than one operator, the execution order is defined by their _precedence_, or, in other words, the default priority order of operators. (just like maths). For more information, check [precedence table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

##### Assignment `=`

-   returns a value
    
-   chaining assignments
    
-   modify-in-place
    

let x = 2 * 2 + 1;  
alert(x);  
  
// returns a value   
let a = 1;  
let b = 2;  
  
let c = 3 - (a = b + 1);  
  
alert( a ); // 3  
alert( c ); // 0  
  
// chaining assignments  
let a, b, c;  
  
a = b = c = 2 + 2;  
  
alert( a ); // 4  
alert( b ); // 4  
alert( c ); // 4  
  
c = 2 + 2; // for the sake easy readability  
b = c;  
a = c;  
  
// modify-in-place  
let n = 2;  
n = n + 5;  
n = n * 2;  
  
let n = 2;  
n += 5; // now n = 7 (same as n = n + 5)  
n *= 2; // now n = 14 (same as n = n * 2)  
  
alert( n ); // 14  
  
  
let n = 2;  
  
n *= 3 + 5;  
  
alert( n ); // 16  (right part evaluated first, same as n *= 8)

#### Increment / Decrement

Increasing or decreasing a number by one is among the most common numerical operations.

##### Increment

`++` increases a variable by 1 ( var a = a+1 )

##### Decrement

`--` decreases a variable by 1 ( var a = a-1 )

// styling -> one line - one action  
  
let counter = 1;  
alert( 2 * counter );  
counter++;

##### counter++ or ++counter

The operators `++` and `--` can be placed either before or after a variable.

-   When the operator goes after the variable, it is in “postfix form”: `counter++`.
    
-   The “prefix form” is when the operator goes before the variable: `++counter`.
    

// prefix form - use it if we'd like to increase the value and use the result immediately  
let counter = 1;  
let a = ++counter; // (*)  
  
alert(a); // 2  
  
// postifx form - use it if we'd like to use its previous value  
let counter = 1;  
let a = counter++; // (*) changed ++counter to counter++  
  
alert(a); // 1  
  
// Both of these statements do the same thing: increase counter by 1.

#### Bitwise operators

Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation. The list of operators:

-   AND ( `&` )
    
-   OR ( `|` )
    
-   XOR ( `^` )
    
-   NOT ( `~` )
    
-   LEFT SHIFT ( `<<` )
    
-   RIGHT SHIFT ( `>>` )
    
-   ZERO-FILL RIGHT SHIFT ( `>>>` )
    

It is not JavaScript-specific

##### Comma

The comma operator `,` is one of the rarest and most unusual operators.

-   Sometimes, it’s used to write shorter code, so we need to know it in order to understand what’s going on.
    
-   The comma operator allows us to evaluate several expressions, dividing them with a comma `,`.
    
-   Each of them is evaluated but only the result of the last one is returned.
    

let a = (1 + 2, 3 + 4); // it's like (a = 1 + 2), 3 + 4.  
  
alert( a ); // 7 (the result of 3 + 4)  
  
// Here, the first expression 1 + 2 is evaluated and its result is thrown away.   
// Then, 3 + 4 is evaluated and returned as the result.  
  
// Sometimes we need it for 3 operations in one line  
for (a = 1, b = 3, c = a * b; a < 10; a++) {  
 ...  
}

### Comparisons

In JavaScript they are written like this:

-   Greater/less than: `a > b`, `a < b`.
    
-   Greater/less than or equals: `a >= b`, `a <= b`.
    
-   Equals: `a == b`, please note the double equality sign `==` means the equality test, while a single one `a = b` means an assignment.
    
-   Not equals. In maths the notation is `≠`, but in JavaScript it’s written as `a != b`.
    

#### Boolean comparisons

All comparison operators return a boolean value:

-   `true` – means “yes”, “correct” or “the truth”.
    
-   `false` – means “no”, “wrong” or “not the truth”.
    

#### String comparison

To see whether a string is greater than another, JavaScript uses the so-called “dictionary” or “lexicographical” order. In other words, strings are compared letter-by-letter.

alert( 'Z' > 'A' ); // true  
// the comparison 'Z' > 'A' gets to a result at the first step.  
  
alert( 'Glow' > 'Glee' ); // true  
// compare character-by-character  
// G == G  
// l == l  
// o < e (stop, first string is greater)  
  
alert( 'Bee' > 'Be' ); // true

> The algorithm to compare two strings is simple:
> 
> 1.  Compare the first character of both strings.
>     
> 2.  If the first character from the first string is greater (or less) than the other string’s, then the first string is greater (or less) than the second. We’re done.
>     
> 3.  Otherwise, if both strings’ first characters are the same, compare the second characters the same way.
>     
> 4.  Repeat until the end of either string.
>     
> 5.  If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.
>     
> 
> The comparison is done not based on dictionary, but Unicode order

### Comparison of different types

When comparing values of different types, JavaScript converts the values to numbers.

alert( '2' > 1 ); // true, string '2' becomes a number 2  
alert( '01' == 1 ); // true, string '01' becomes a number 1

For boolean values, `true` becomes `1` and `false` becomes `0`.

alert( true == 1 ); // true  
alert( false == 0 ); // true

It is possible that at the same time:

-   Two values are equal.
    
-   One of them is `true` as a boolean and the other one is `false` as a boolean.
    

let a = 0;  
alert( Boolean(a) ); // false  
  
let b = "0";  
alert( Boolean(b) ); // true  
  
alert(a == b); // true!

### Strict equality `===`

A regular equality check `==` has a problem. It cannot differentiate `0` from `false`:

alert( 0 == false ); // true  
  
// same thing happen with an empty string  
alert( '' == false ); // true  
  
// What to do if we’d like to differentiate 0 from false?  
// === checks the equality without type conversion  
  
alert( 0 === false ); // false, because the types are different

#### Comparison with `null` and `undefined`

alert( null === undefined ); // false  
  
alert( null == undefined ); // true

For maths and other comparisons `< > <= >=`

`null/undefined` are converted to numbers: `null` becomes `0`, while `undefined` becomes `NaN`.

#### Strange result: null vs 0

// let's compare null with a zero  
  
alert( null > 0 );  // (1) false  
alert( null == 0 ); // (2) false  
alert( null >= 0 ); // (3) true

> The reason is that an equality check `==` and comparisons `> < >= <=` work differently. Comparisons convert `null` to a number, treating it as `0`. That’s why (3) `null >= 0` is true and (1) `null > 0` is false.
> 
> On the other hand, the equality check `==` for `undefined` and `null` is defined such that, without any conversions, they equal each other and don’t equal anything else. That’s why (2) `null == 0` is false.

#### An incomparable undefined

// The value undefined shouldn’t be compared to other values:  
alert( undefined > 0 ); // false (1)  
alert( undefined < 0 ); // false (2)  
alert( undefined == 0 ); // false (3)

We get these results because:

-   Comparisons `(1)` and `(2)` return `false` because `undefined` gets converted to `NaN` and `NaN` is a special numeric value which returns `false` for all comparisons.
    
-   The equality check `(3)` returns `false` because `undefined` only equals `null`, `undefined`, and no other value.
    

#### Avoid problems

-   Treat any comparison with `undefined/null` except the strict equality `===` with exceptional care.
    
-   Don’t use comparisons `>= > < <=` with a variable which may be `null/undefined`, unless you’re really sure of what you’re doing. If a variable can have these values, check for them separately.
    

### Conditional branching: if, '?'

// single statement   
let year = prompt('In which year was ECMAScript-2015 specification published?', '');  
if (year == 2015) alert( 'You are right!' );  
  
// multiple statements  
if (year == 2015) {  
  alert( "That's correct!" );  
  alert( "You're so smart!" );  
}

#### else if

let year = prompt('In which year was the ECMAScript-2015 specification published?', '');  
  
if (year < 2015) {  
  alert( 'Too early...' );  
} else if (year > 2015) {  
  alert( 'Too late' );  
} else {  
  alert( 'Exactly!' );  
}

#### Conditional Operator `?`

let accessAllowed;  
let age = prompt('How old are you?', '');  
  
if (age > 18) {  
  accessAllowed = true;  
} else {  
  accessAllowed = false;  
}  
  
alert(accessAllowed);  
  
// shorthand  
// let result = condition ? value1 : value2;  
let accessAllowed = (age > 18) ? true : false;  
  
// the comparison operator "age > 18" executes first anyway  
// (no need to wrap it into parentheses)  
let accessAllowed = age > 18 ? true : false;  
  
// the same  
let accessAllowed = age > 18;

#### Multiple '?'

if (age < 3) {  
  message = 'Hi, baby!';  
} else if (age < 18) {  
  message = 'Hello!';  
} else if (age < 100) {  
  message = 'Greetings!';  
} else {  
  message = 'What an unusual age!';  
}  
  
// shorthand  
let age = prompt('age?', 18);  
  
let message = (age < 3) ? 'Hi, baby!' :  
  (age < 18) ? 'Hello!' :  
  (age < 100) ? 'Greetings!' :  
  'What an unusual age!';  
  
alert( message );

#### Non-traditional use of `?`

let company = prompt('Which company created JavaScript?', '');  
  
(company == 'Netscape') ?  
   alert('Right!') : alert('Wrong.');  
  
// It’s not recommended to use the question mark operator in this way.  
// the example above makes it hard to read  
  
// here's the same code using if for comparison:  
let company = prompt('Which company created JavaScript?', '');  
  
if (company == 'Netscape') {  
  alert('Right!');  
} else {  
  alert('Wrong.');  
}

### Logical Operators

1.  `||` OR
    
    result = value1 || value2 || value3;  
      
    alert( true || true );   // true  
    alert( false || true );  // true  
    alert( true || false );  // true  
    alert( false || false ); // false
    
    alert( 1 || 0 ); // 1 (1 is truthy)  
      
    alert( null || 1 ); // 1 (1 is the first truthy value)  
    alert( null || 0 || 1 ); // 1 (the first truthy value)  
      
    alert( undefined || null || 0 ); // 0 (all falsy, returns the last value)
    
    1.  Getting the first truthy value from a list of variables or expressions
        
        let firstName = "";  
        let lastName = "";  
        let nickName = "SuperCoder";  
          
        alert( firstName || lastName || nickName || "Anonymous"); // SuperCoder
        
    2.  Short-circuit evaluation
        
        true || alert("not printed");  
        false || alert("printed")
        
2.  `&&` AND
    
    result = a && b;  
      
    alert( true && true );   // true  
    alert( false && true );  // false  
    alert( true && false );  // false  
    alert( false && false ); // false
    
    let hour = 12;  
    let minute = 30;  
      
    if (hour == 12 && minute == 30) {  
      alert( 'The time is 12:30' );  
    }  
      
    if (1 && 0) { // evaluated as true && false  
      alert( "won't work, because the result is falsy" );  
    }
    
3.  AND `&&` finds the first falsy value
    
    The AND `&&` operator does the following:
    
    -   Evaluates operands from left to right.
        
    -   For each operand, converts it to a boolean. If the result is `false`, stops and returns the original value of that operand.
        
    -   If all operands have been evaluated (i.e. all were truthy), returns the last operand.
        
    
    In other words, AND returns the first falsy value or the last value if none were found.
    
    > The rules above are similar to OR. The difference is that AND returns the first _falsy_ value while OR returns the first _truthy_ one.
    

result = value1 && value2 && value3;  
  
// if the first operand is truthy,  
// AND returns the second operand:  
alert( 1 && 0 ); // 0  
alert( 1 && 5 ); // 5  
  
// if the first operand is falsy,  
// AND returns it. The second operand is ignored  
alert( null && 5 ); // null  
alert( 0 && "no matter what" ); // 0  
  
// We can also pass several values in a row. See how the first falsy one is returned:  
alert( 1 && 2 && null && 3 ); // null  
  
// When all values are truthy, the last value is returned:  
alert( 1 && 2 && 3 ); // 3, the last one

4.  `!` NOT
    
    The operator accepts a single argument and does the following:
    
    1.  Converts the operand to boolean type: `true/false`.
        
    2.  Returns the inverse value.
        
        alert( !true ); // false  
        alert( !0 ); // true  
           
        // a double NOT !!  
        alert( !!"non-empty string" ); // true  
        alert( !!null ); // false  
          
        // There’s a little more verbose way to do the same thing – a built-in Boolean function:  
        alert( Boolean("non-empty string") ); // true  
        alert( Boolean(null) ); // false
        

> The precedence of AND `&&` operator is higher than OR `||`.
> 
> Don't replace `if` with `||` or `&&`
> 
> The precedence of NOT `!` is the highest of all logical operators, so it always executes first, before `&&` or `||`.

### Nullish coalescing operator `??`

This is a recent addition to the language. Old browsers may need polyfills.

As it treats `null` and `undefined` similarly, we’ll use a special term here, in this article. We’ll say that an expression is “defined” when it’s neither `null` nor `undefined`. The result of `a ?? b` is:

-   if `a` is defined, then `a`,
    
-   if `a` isn’t defined, then `b`.
    

In other words, `??` returns the first argument if it’s not `null/undefined`. Otherwise, the second one.

// We can rewrite   
// result = a ?? b   
// using the operators that we already know, like this:  
result = (a !== null && a !== undefined) ? a : b;  
  
let user;  
alert(user ?? "Anonymous"); // Anonymous (user not defined)  
        
let user = "John";  
alert(user ?? "Anonymous"); // John (user defined)

We can also use a sequence of `??` to select the first value from a list that isn’t `null/undefined`.

let firstName = null;  
let lastName = null;  
let nickName = "Supercoder";  
  
// shows the first defined value:  
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder

#### Comparison with ||

The OR `||` operator can be used in the same way as `??`

let firstName = null;  
let lastName = null;  
let nickName = "Supercoder";  
  
// shows the first truthy value:  
alert(firstName || lastName || nickName || "Anonymous"); // Supercoder

##### The important difference between `||` and `??` is that:

-   `||` returns the first _truthy_ value.
    
    -   doesn’t distinguish between `false`, `0`, an empty string `""` and `null/undefined`
        
    -   They are all the same – falsy values.
        
-   `??` returns the first _defined_ value.
    
    -   we’ll get the second argument as the result.
        
    
    In practice though, we may want to use default value only when the variable is `null/undefined`. That is, when the value is really unknown/not set.
    

let height = 0;  
  
alert(height || 100); // 100, check for a falsy value. falsy indeed  
alert(height ?? 100); // 0, check for being null/undefined, it's not

#### Precedence `??` same with `||`

// without parentheses  
let area = height ?? 100 * width ?? 50;  
  
// ...works the same as this (probably not what we want):  
let area = height ?? (100 * width) ?? 50;

#### Using `??` with `&&` or `||`

Due to safety reasons, JavaScript forbids using `??` together with `&&` and `||` operators, unless the precedence is explicitly specified with parentheses.

> let x = 1 && 2 ?? 3; // Syntax error  
>   
> // Use explicit parantheses  
> let x = (1 && 2) ?? 3; // Works  
> alert(x); // 2

The limitation is surely debatable, it was added to the language specification with the purpose to avoid programming mistakes, when people start to switch from `||` to `??`

### Loops: while and for

#### While

while (condition) {  
  // code  
  // so-called "loop body"  
}  
  
let i = 0;  
while (i < 3) { // shows 0, then 1, then 2  
  alert( i );  
  i++;  
}  
  
// For instance, a shorter way to write while (i != 0) is while (i):  
let i = 3;  
while (i) { // when i becomes 0, the condition becomes falsy, and the loop stops  
  alert( i );  
  i--;  
}  
  
// Curly braces are not required for a single-line body  
let i = 3;  
while (i) alert(i--);

##### do...while

do {  
  // loop body  
} while (condition);  
  
// The loop will first execute the body, then check the condition, and, while it’s truthy, execute it again and again.  
let i = 0;  
do {  
  alert( i );  
  i++;  
} while (i < 3);

#### For

for (begin; condition; step) {  
  // ... loop body ...  
}  
  
for (let i = 0; i < 3; i++) { // shows 0, then 1, then 2  
  alert(i);  
}

part

code

definition

begin

`i = 0`

Executes once upon entering the loop.

condition

`i < 3`

Checked before every loop iteration. If false, the loop stops.

body

`alert(i)`

Runs again and again while the condition is truthy.

step

`i++`

Executes after the body on each iteration.

#### The general loop algorithm works like this:

> Run begin  
> → (if condition → run body and run step)  
> → (if condition → run body and run step)  
> → (if condition → run body and run step)  
> → ...  
>   
> That is:  
> begin executes once, and then it iterates:   
> after each condition test,   
> body and step are executed.

##### Inline variable declaration (For)

for (let i = 0; i < 3; i++) {  
  alert(i); // 0, 1, 2  
}  
alert(i); // error, no such variable  
  
// Instead of defining a variable, we could use an existing one:  
let i = 0;  
  
for (i = 0; i < 3; i++) { // use an existing variable  
  alert(i); // 0, 1, 2  
}  
  
alert(i); // 3, visible, because declared outside of the loop

##### Skipping parts (For)

Any part of `for` can be skipped

// remove begin part  
let i = 0; // we have i already declared and assigned  
for (; i < 3; i++) { // no need for "begin"  
  alert( i ); // 0, 1, 2  
}  
  
// remove step part  
let i = 0;  
for (; i < 3;) { // makes the loop identical to while (i < 3).  
  alert( i++ );   
}  
  
// remove everything - creating an infinity loop  
for (;;) {  
  // repeats without limits  
  // the two for semicolons ; must be present. Otherwise, there would be a syntax error.  
}

#### Breaking the loop

let sum = 0;  
  
while (true) {  
  let value = +prompt("Enter a number", '');  
  if (!value) break; // (*)  
  sum += value;  
}  
  
alert( 'Sum: ' + sum );

#### Continue to the next irritation

The `continue` directive is a “lighter version” of `break`. It doesn’t stop the whole loop. Instead, it stops the current iteration and forces the loop to start a new one

for (let i = 0; i < 10; i++) {  
  
  // if true, skip the remaining part of the body  
  if (i % 2 == 0) continue;  
  
  alert(i); // 1, then 3, 5, 7, 9  
}

> For even values of `i`, the `continue` directive stops executing the body and passes control to the next iteration of `for` (with the next number). So the `alert` is only called for odd values.

-   The `continue` directive helps decrease nesting
    
    for (let i = 0; i < 10; i++) {  
      if (i % 2) {  
        alert( i );  
      }  
    }
    
-   No `break/continue` to the right side of `?` Please note that syntax constructs that are not expressions cannot be used with the ternary operator `?`. In particular, directives such as `break/continue` aren’t allowed there.
    
    if (i > 5) {  
      alert(i);  
    } else {  
      continue;  
    }  
      
    // rewrite it  
    (i > 5) ? alert(i) : continue; // continue isn't allowed here
    

#### Labels for Break / Continue

Sometimes we need to break out from multiple nested loops at once.

for (let i = 0; i < 3; i++) {  
  for (let j = 0; j < 3; j++) {  
    let input = prompt(`Value at coords (${i},${j})`, '');  
    // what if we want to exit from here to Done (below)?  
  }  
}  
  
alert('Done!');  
  
// use label  
labelName: for (...) {  
  ...  
}  
      
outer: for (let i = 0; i < 3; i++) {  
  for (let j = 0; j < 3; j++) {  
    let input = prompt(`Value at coords (${i},${j})`, '');  
    // if an empty string or canceled, then break out of both loops  
    if (!input) break outer; // (*)  
    // do something with the value...  
  }  
}  
alert('Done!');

> `break outer` breaks the loops and immediately jump to `alert('Done!')`
> 
> // this is also okay to do  
> outer:  
> for (let i = 0; i < 3; i++) { ... }

##### Labels does not jump anywhere

It will only work when a break is inside a code block. Any labelled code block will do

break label; // jump to the label below (doesn't work)  
label: for (...)  
              
// use this:  
label: {  
  // ...  
  break label; // works  
  // ...  
}

### Switch Statement

// syntax  
let a = 2 + 2;  
  
switch (a) {  
  case 3:  
    alert( 'Too small' );  
    break;  
  case 4:  
    alert( 'Exactly!' );  
    break;  
  case 5:  
    alert( 'Too big' );  
    break;  
  default:  
    alert( "I don't know such values" );  
}

#### Switch / Case Allows Aribtrary Expressions

let a = "1";  
let b = 0;  
  
switch (+a) {  
  case b + 1:  
    alert("this runs, because +a is 1, exactly equals b+1");  
    break;  
  
  default:  
    alert("this doesn't run");  
}

#### Grouping Case

let a = 3;  
  
switch (a) {  
  case 4:  
    alert('Right!');  
    break;  
  
  case 3: // (*) grouped two cases  
  case 5:  
    alert('Wrong!');  
    alert("Why don't you take a math class?");  
    break;  
  
  default:  
    alert('The result is strange. Really.');  
}

### Functions (Function Declaration)

// A function declaration looks like this:  
function name(parameters, delimited, by, comma) {  
  /* code */  
      let message = "Hello, I'm JavaScript!"; // local variable	    
}  
  
name(); // call function; will show message  
alert( message ); // <-- Error! The variable is local to the function  
  
// outer variable  
  
let userName = 'John';  
  
function outer() {  
    userName = 'Bob';  
      
    let message = 'Hello ' + userName;  
    alert(message);  
}  
  
alert(userName); // John  
showMessage(); // Hello Bob (call the local variable)  
alert(userName); // Bob (if outer variablel isnt call. it will return John)

-   Values passed to a function as parameters are copied to its local variables.
    
-   A function may access outer variables. But it works only from inside out. The code outside of the function doesn’t see its local variables.
    
-   A function can return a value. If it doesn’t, then its result is `undefined`.
    
-   To make the code clean and easy to understand, it’s recommended to use mainly local variables and parameters in the function, not outer variables.
    
-   It is always easier to understand a function which gets parameters, works with them and returns a result than a function which gets no parameters, but modifies outer variables as a side-effect.
    

#### Function Naming

-   A name should clearly describe what the function does. When we see a function call in the code, a good name instantly gives us an understanding what it does and returns.
    
-   A function is an action, so function names are usually verbal.
    
-   There exist many well-known function prefixes like `create…`, `show…`, `get…`, `check…` and so on. Use them to hint what a function does.
    
    -   `"get…"` – return a value,
        
    -   `"calc…"` – calculate something,
        
    -   `"create…"` – create something,
        
    -   `"check…"` – check something and return a boolean, etc.
        
    -   Use the rule, `one function - one action`
        
-   Ultrashort function names
    

#### Parameters

In other words, to put these terms straight:

-   A parameter is the variable listed inside the parentheses in the function declaration (it’s a declaration time term)
    
-   An argument is the value that is passed to the function when it is called (it’s a call time term).
    
-   We declare functions listing their parameters, then call them passing arguments.
    

function showMessage(from, text) { // parameters: from, text  
  alert(from + ': ' + text);  
}  
  
showMessage('Ann', 'Hello!'); // Ann: Hello! (*)  
showMessage('Ann', "What's up?"); // Ann: What's up? (**)  
  
// another example  
function showMessage(from, text) {  
  from = '*' + from + '*'; // make "from" look nicer  
  alert( from + ': ' + text );  
}  
  
let from = "Ann";  
showMessage(from, "Hello"); // *Ann*: Hello  
  
// the value of "from" is the same, the function modified a local copy  
alert( from ); // Ann

##### Parameters: Default Value

function showMessage(from, text = "no text given") {  
  alert( from + ": " + text );  
}  
  
showMessage("Ann"); // Ann: no text given

##### Alternative Default Parameters

function showMessage(text) {  
  // ...  
  
  if (text === undefined) { // if the parameter is missing  
    text = 'empty message';  
  }  
  alert(text);  
}  
  
showMessage(); // empty message  
  
// use OR `||` as default  
function showMessage(text) {  
  // if text is undefined or otherwise falsy, set it to 'empty'  
  text = text || 'empty';  
  ...  
}  
    
function showCount(count) {  
  // if count is undefined or null, show "unknown"  
  alert(count ?? "unknown");  
}  
  
// using nullish coalescing operator `??`  
      
showCount(0); // 0  
showCount(null); // unknown  
showCount(); // unknown

#### Returning a value

// simple return  
function sum(a, b) {  
  return a + b;  
}  
  
let result = sum(1, 2);  
alert( result ); // 3  
  
// multiple return value  
function checkAge(age) {  
  if (age >= 18) {  
    return true;  
  } else {  
    return confirm('Do you have permission from your parents?');  
  }  
}  
  
let age = prompt('How old are you?', 18);  
  
if ( checkAge(age) ) {  
  alert( 'Access granted' );  
} else {  
  alert( 'Access denied' );  
}  
  
// returning without a value  
function showMovie(age) {  
  if ( !checkAge(age) ) {  
    return;  
  }  
  
  alert( "Showing you the movie" ); // (*)  
  // ...  
}

1.  A function does not return a value is the same as undefined
    
    function doNothing() { /* empty */ }  
      
    alert( doNothing() === undefined ); // true
    
2.  An empty return is also the same as return undefined
    
    function doNothing() {  
      return;  
    }  
      
    alert( doNothing() === undefined ); // true
    
3.  Never add a newline between `return` and the value - JavaScript assumes a semicolon after `return`
    
    return; // ; is automatic // automatically becomes an empty return  
     (some + long + expression + or + whatever * f(a) + f(b))   
      
    // write it this way instead  
    return (  
      some + long + expression  
      + or +  
      whatever * f(a) + f(b)  
      )
    

### Function Expressions

// Function Declaration  
function sayHi() {  
  alert( "Hello" );  
}  
  
// Function Expressions  
let sayHi = function() { // "create a function and put it into the variable sayHi".  
  alert( "Hello" );  
};  
  
alert( sayHi ); // shows the function expression code code

#### Copy a function to another variable

function sayHi() {   // (1) create  
  alert( "Hello" );  
}  
  
let func = sayHi;    // (2) copy  
  
func(); // Hello     // (3) run the copy (it works)!  
sayHi(); // Hello    //     this still works too (why wouldn't it)  
  
/*  
	1) Function Declaration -> creates the function and puts it into var `sayHi`  
    2) Copies the var `func`  
	if written sayHi() -> will show "Hello" in modal box  
	3) Now the function can be called as both sayHi() and func()  
*/  
  
let sayHi = function() {  
  alert( "Hello" );  
};  
  
let func = sayHi;  
// ...

#### Callback Functions

1.  questions = text of the question
    
2.  yes = function to run if the answer is `yes`
    
3.  no = function to run if the answer is `no`
    

The function should ask the `question` and, depending on the user's answer, call `yes()` and `no()` The arguments `showOk` and `showCancel` of `ask` are called _callback functions_ or just _callbacks_

1.  Function Declaration:
    
    function ask(question, yes, no) {  
      if (confirm(question)) yes()  
      else no();  
    }  
      
    function showOk() {  
      alert( "You agreed." );  
    }  
      
    function showCancel() {  
      alert( "You canceled the execution." );  
    }  
      
    // usage: functions showOk, showCancel are passed as arguments to ask  
    // The arguments showOk and showCancel of ask are called callback functions or just callbacks.  
    ask("Do you agree?", showOk, showCancel);
    
2.  Function Expression:
    
    function ask(question, yes, no) {  
      if (confirm(question)) yes()  
      else no();  
    }  
      
    ask(  
      "Do you agree?",  
      function() { alert("You agreed."); },  
      function() { alert("You canceled the execution."); }  
    );  
      
    // function without names are called anonymous, and such functions are not accessible outside of ask (because they are not assigned to any variables)
    
    #### Function Expression vs Function Declaration
    
    Function Expression
    
    Function Declaration
    
    a function, declared as a separate statement, in the main code flow.
    
    created inside an expression or inside another syntax construct. Here, the function is created at the right side of the “assignment expression” `=`
    
    created when the execution reaches it and is usable only from that moment
    
    can be called earlier than it is defined a global Function Declaration is visible in the whole script, no matter where it is.
    
    -
    
    In strict mode, it is visible everywhere inside code block, but not outside of that code block
    
    only use it when it does not fit the task
    
    preferable - flexibility in code organization, and more readable
    
    // Function Expression - will work  
    sayHi("John"); // Hello, John  
      
    function sayHi(name) {  
      alert( `Hello, ${name}` );  
    }  
      
    // Function Declaration - this wont work  
    sayHi("John"); // error!  
      
    let sayHi = function(name) {  // (*) no magic any more  
      alert( `Hello, ${name}` );  
    };
    
    // Function Declaration  
    let age = prompt("What is your age?", 18);  
      
    // conditionally declare a function  
    if (age < 18) {  
      function welcome() {  
        alert("Hello!");  
      }  
      
    } else {  
      function welcome() {  
        alert("Greetings!");  
      }  
    }  
      
    // ...use it later  
    welcome(); // Error: welcome is not defined  
      
    // Function Declaration  
    let age = 16; // take 16 as an example  
      
    if (age < 18) {  
      welcome();               // \   (runs)  
                               //  |  
      function welcome() {     //  |  
        alert("Hello!");       //  |  Function Declaration is available  
      }                        //  |  everywhere in the block where it's declared  
                               //  |  
      welcome();               // /   (runs)  
      
    } else {  
      
      function welcome() {  
        alert("Greetings!");  
      }  
    }  
      
    // Here we're out of curly braces,  
    // so we can not see Function Declarations made inside of them.  
      
    welcome(); // Error: welcome is not defined  
      
    // Function Expression  
    let age = prompt("What is your age?", 18);  
    let welcome;  
      
    if (age < 18) {  
      welcome = function() {  
        alert("Hello!");  
      };  
      
    } else {  
      welcome = function() {  
        alert("Greetings!");  
      };  
    }  
      
    welcome(); // ok now  
      
    // using ? operator  
    let age = prompt("What is your age?", 18);  
      
    let welcome = (age < 18) ?  
      function() { alert("Hello!"); } :  
      function() { alert("Greetings!"); };  
      
    welcome(); // ok now
    

##### When to choose Function Declaration versus Function Expression

> As a rule of thumb, when we need to declare a function,
> 
> 1.  the first to consider is Function Declaration syntax. It gives more freedom in how to organize our code, because we can call such functions before they are declared.
>     
>     That’s also better for readability, as it’s easier to look up `function f(…) {…}` in the code than `let f = function(…) {…};`.
>     
>     Function Declarations are more “eye-catching”.
>     
> 2.  …But if a Function Declaration does not suit us for some reason, or we need a conditional declaration (we’ve just seen an example), then Function Expression should be used.
>     

### Arrow functions, the basics

Two types of arrow functions:

1.  Without curly braces: `(...args) => expression` – the function evaluates it and returns the result.
    
2.  With curly braces: `(...args) => { body }` – to write multiple statements inside the function, but we need an explicit `return` to return something
    

let func = function(arg1, arg2, ..., argN) {  
  return expression;  
};  
  
// shorter version (arrow function)  
let func = (arg1, arg2, ..., argN) => expression  
  
// example  
let sum = (a, b) => a + b;  
  
/* This arrow function is a shorter form of:  
	let sum = function(a, b) { return a + b; };  
*/  
  
alert( sum(1, 2) ); // 3

1.  If we have only one argument, then parentheses around parameters can be omitted, making that even shorter
    
    let double = n => n * 2;  
    // roughly the same as: let double = function(n) { return n * 2 }  
      
    alert( double(3) ); // 6
    
2.  If there are no arguments, parentheses will be empty (but they should be present)
    
    let sayHi = () => alert("Hello!");  
      
    sayHi();
    
3.  Arrow functions can be used in the same way as `Function Expressions`
    
    let age = prompt("What is your age?", 18);  
      
    let welcome = (age < 18) ?  
      () => alert('Hello') :  
      () => alert("Greetings!");  
      
    welcome();
    

#### Multiline arrow functions

For multiple statement or expression

let sum = (a, b) => {  // the curly brace opens a multiline function  
  let result = a + b;  
  return result; // if we use curly braces, then we need an explicit "return"  
};  
  
alert( sum(1, 2) ); // 3

---

## Recap of JS Fundamentals

1.  Code Structure
    
    -   automatic `;` if not placed
        
    -   better to put it
        
    -   no need `;` after a function declaration
        
2.  Strict Mode `use strict`
    
    -   put on top of a script / beginning of a functio
        
    -   needed in old browsers / pages for it to run
        
3.  Variables
    
    -   let
        
    -   const
        
    -   var
        
    -   eight types of data types
        
4.  Interactions
    
    -   prompt(question, default)
        
    -   confirm(question)
        
    -   alert(message)
        
5.  Operators
    
    -   Arithmetical `+ = - * /`
        
    -   Assignments `=`
        
    -   Bitwise
        
    -   Conditional `if` (`cond ? resultA : resultB`)
        
    -   Logical Operators `&&` `||`
        
    -   Nullish coalescing operator `??`
        
    -   Comparisons `==`
        
6.  Loops
    
    -   while `while(condition){...};`
        
    -   do `do{...} while (condition);`
        
    -   for `for (let...)`
        
7.  The "switch" construct
    
8.  Functions
    
    -   Function Declaration
        
        function sum(a, b) {  
          let result = a + b;  
          return result;  
        }
        
    -   Function Expression
        
        let sum = function(a, b) {  
          let result = a + b;  
          return result;  
        };
        
    -   Arrow Functions
        
        // expression at the right side  
        let sum = (a, b) => a + b;  
          
        // or multi-line syntax with { ... }, need return here:  
        let sum = (a, b) => {  
          // ...  
          return a + b;  
        }  
          
        // without arguments  
        let sayHi = () => alert("Hello");  
          
        // with a single argument  
        let double = n => n * 2;
        

# JavaScript cont'd

## Data Types

### Numbers

1.  To write numbers with many zeroes:
    
    -   ###### Underscore `_` is used as a separator and Javascript simply ignores it. It also plays the role of the "syntactic sugar" (makes the number more readable)
        
        `let billion = 1_000_000_000;`
        
    -   Append `"e"` with the zeroes count to the number. Like: `123e6` is the same as `123` with 6 zeroes `123000000`
        
    -   A negative number after `"e"` causes the number to be divided by 1 with given zeroes. E.g. `123e-6` means `0.000123` (`123` millionths).
        
2.  For different numeral systems:
    
    -   Can write numbers directly in hex (`0x`), octal (`0o`) and binary (`0b`) systems.
        
    -   `parseInt(str, base)` parses the string `str` into an integer in numeral system with given `base`, `2 ≤ base ≤ 36`.
        
    -   `num.toString(base)` converts a number to a string in the numeral system with the given `base`.
        
        -   base = 16, used for hex colors, character encodings, digits
            
        -   base = 2, debugging bitwise operations
            
        -   base = 36
            
        -   if we want to directly call, the method we can use
            
            alert( 123456..toString(36) ); // 2n9c  
            (123456).toString(36) // alternative  
              
            // 123456.toString(36) // error
            
3.  For converting values like `12pt` and `100px` to a number:
    
    -   You can use `+` or `Number()` for number conversion and is strict, if a value is not a number, it will result it `NaN`, Hence why we use `parseInt/ parseFloat`
        
    -   Use `parseInt/parseFloat` for the “soft” conversion, which reads a number from a string and then returns the value they could read before the error.
        
4.  For fractions:
    
    -   Round using `Math.floor`, `Math.ceil`, `Math.trunc`, `Math.round` or `num.toFixed(precision)`
        
    -   Make sure to remember there’s a loss of precision when working with fractions
        
        -   If a number too big (> 64 bit) it will results in `Infinity`
            
        -   Create a "falsy" result
            
            alert( 0.1 + 0.2 == 0.3 ); // false  
            alert( 0.1 + 0.2 ); // 0.30000000000000004  
              
            // to fix  
            let sum = 0.1 + 0.2;  
            alert( sum.toFixed(2) ); // 0.30  
            // alternatively  
            alert( +sum.toFixed(2) ); // 0.3
            
5.  isFinite and isNaN
    
    -   `Infinity` (and `-Infinity`) is a special numeric value that is greater (less) than anything.
        
        -   `isFinite(value)` converts its argument to a number and returns `true` if it’s a regular number, not `NaN/Infinity/-Infinity`:
            
            alert( isFinite("15") ); // true  
            alert( isFinite("str") ); // false, because a special value: NaN  
            alert( isFinite(Infinity) ); // false, because a special value: Infinity  
              
              
            // check to validate a string value is a regular number  
            let num = +prompt("Enter a number", '');  
              
            // will be true unless you enter Infinity, -Infinity or not a number  
            alert( isFinite(num) );
            
    -   `NaN` represents an error.
        
        -   `isNaN(value)` converts its argument to a number and then tests it for being `NaN`
            
        -   The value `NaN` is unique in that it does not equal anything, including itself:
            
            alert( isNaN(NaN) ); // true  
            alert( isNaN("str") ); // true  
            alert( NaN === NaN ); // false
            
6.  Object.is (internally called `SameValue`)
    
    -   is identical to `===` , `Object.is(a,b) is the same as a ===b`
        
        -   It works with `NaN`: `Object.is(NaN, NaN) === true`, that’s a good thing.
            
        -   Values `0` and `-0` are different: `Object.is(0, -0) === false`, technically that’s true, because internally the number has a sign bit that may be different even if all other bits are zeroes.
            
7.  Other Math Functions
    
    -   `Math.random()`
        
    -   `Math.max(a, b, c, ...)` or `Math.min(a, b, c, ...)`
        
    -   `Math.pow(n, power)`
        

### Strings

-   There are 3 types of quotes. Backticks ` allow a string to span multiple lines and embed expressions ${…}.
    
    // embed expression into the string by wrapping ${...}  
    function sum(a, b) {  
      return a + b;  
    }  
      
    alert(`1 + 2 = ${sum(1, 2)}.`); // 1 + 2 = 3.  
      
    // allow a string to span multiple lines  
    let guestList = `Guests:  
     * John  
     * Pete  
     * Mary  
    `;  
      
    alert(guestList); // a list of guests, multiple lines
    
-   We can use special characters like `\n` and insert letters by their Unicode using `\u...`
    
    Character
    
    Description
    
    `\n`
    
    New line
    
    `\r`
    
    Carriage return: not used alone. Windows text files use a combination of two characters `\r\n` to represent a line break.
    
    `\'`, `\"`
    
    Quotes
    
    `\\`
    
    Backslash
    
    `\t`
    
    Tab
    
    `\b`, `\f`, `\v`
    
    Backspace, Form Feed, Vertical Tab – kept for compatibility, not used nowadays.
    
    `\xXX`
    
    Unicode character with the given hexadecimal Unicode `XX`, e.g. `'\x7A'` is the same as `'z'`.
    
    `\uXXXX`
    
    A Unicode symbol with the hex code `XXXX` in UTF-16 encoding, for instance `\u00A9` – is a Unicode for the copyright symbol `©`. It must be exactly 4 hex digits.
    
    `\u{X…XXXXXX}` (1 to 6 hex characters)
    
    A Unicode symbol with the given UTF-32 encoding. Some rare characters are encoded with two Unicode symbols, taking 4 bytes. This way we can insert long codes.
    
-   To get a character, use: `[]`
    
    let str = `Hello`;  
      
    // the first character  
    alert( str[0] ); // H  
    alert( str[1000] ); // undefined  
    alert( str.charAt(0) ); // H  
    alert( str.charAt(1000) ); // '' (an empty string)  
      
    // the last character  
    alert( str[str.length - 1] ); // o  
      
    // to iterate through character  
    for (let char of "Hello") {  
      alert(char); // H,e,l,l,o (char becomes "H", then "e", then "l" etc)  
    }  
      
    // strings are immutable, so to replace, call old and replace it  
    let str = 'Hi';  
    str = 'h' + str[1]; // replace the string  
    alert( str ); // hi
    
-   To get a substring, use: `slice` or `substring`.
    
      
    
-   To lowercase/uppercase a string, use: `toLowerCase/toUpperCase`.
    
    alert( 'Interface'.toUpperCase() ); // INTERFACE  
    alert( 'Interface'.toLowerCase() ); // interface  
    alert( 'Interface'[0].toLowerCase() ); // 'i'
    
-   To look for a substring, use: `indexOf`, or `includes/startsWith/endsWith` for simple checks.
    
-   To compare strings according to the language, use: `localeCompare`, otherwise they are compared by character codes.
    

There are several other helpful methods in strings:

-   `str.trim()` – removes (“trims”) spaces from the beginning and end of the string.
    
-   `str.repeat(n)` – repeats the string `n` times.
    
-   …and more to be found in the [manual](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).
    

### Arrays

Array is a special kind of object, suited to storing and managing ordered data items.

-   The declaration:
    
    // square brackets (usual)  
    let arr = [item1, item2...];  
      
    let fruits = ["Apple", "Orange", "Plum"];  
      
    alert( fruits[0] ); // Apple  
    alert( fruits[1] ); // Orange  
    alert( fruits[2] ); // Plum  
      
    // replace  
    fruits[2] = 'Pear'; // now ["Apple", "Orange", "Pear"]  
      
    // add  
    fruits[3] = 'Lemon'; // now ["Apple", "Orange", "Pear", "Lemon"]
    

The call to `new Array(number)` creates an array with the given length, but without elements.

-   The `length` property is the array length or, to be precise, its last numeric index plus one. It is auto-adjusted by array methods.
    
-   If we shorten `length` manually, the array is truncated.
    
      
    // new Array (exceptionally rare)  
    let arr = new Array(item1, item2...);  
      
    let arr = new Array("Apple", "Pear", "etc");  
      
      
    // if array is called with a single argument which is a number, then it creates an array without items, but with given length  
      
    let arr = new Array(2); // will it create an array of [2] ?  
    alert( arr[0] ); // undefined! no elements.  
    alert( arr.length ); // length 2
    

We can use an array as a deque with the following operations:

-   #### queue
    
    -   `push(...items)` adds `items` to the end.
        
    -   `shift()` removes the element from the beginning and returns it.
        
    -   `unshift(...items)` adds `items` to the beginning.
        
-   #### stack
    
    -   `push(...items)` adds `items` to the end.
        
    -   `pop()` removes the element from the end and returns it.
        

To loop over the elements of the array:

-   `for (let i=0; i<arr.length; i++)` – works fastest, old-browser-compatible.
    
-   `for (let item of arr)` – the modern syntax for items only,
    
-   `for (let i in arr)` – never use.
    

To compare arrays, don’t use the `==` operator (as well as `>`, `<` and others), as they have no special treatment for arrays. They handle them as any objects, and it’s not what we usually want.

Instead you can use `for..of` loop to compare arrays item-by-item.

### Array Methods

A cheat sheet of array methods:

-   #### To add/remove elements:
    
    -   `push(...items)` – adds items to the end,
        
    -   `pop()` – extracts an item from the end,
        
    -   `shift()` – extracts an item from the beginning,
        
    -   `unshift(...items)` – adds items to the beginning.
        
    -   `splice(pos, deleteCount, ...items)` – at index `pos` deletes `deleteCount` elements and inserts `items`.
        
    -   `slice(start, end)` – creates a new array, copies elements from index `start` till `end` (not inclusive) into it.
        
    -   `concat(...items)` – returns a new array: copies all members of the current one and adds `items` to it. If any of `items` is an array, then its elements are taken.
        
-   #### To search among elements:
    
    -   `indexOf/lastIndexOf(item, pos)` – look for `item` starting from position `pos`, return the index or `-1` if not found.
        
    -   `includes(value)` – returns `true` if the array has `value`, otherwise `false`.
        
    -   `find/filter(func)` – filter elements through the function, return first/all values that make it return `true`.
        
    -   `findIndex` is like `find`, but returns the index instead of a value.
        
-   #### To iterate over elements:
    
    -   `forEach(func)` – calls `func` for every element, does not return anything.
        
-   #### To transform the array:
    
    -   `map(func)` – creates a new array from results of calling `func` for every element.
        
    -   `sort(func)` – sorts the array in-place, then returns it.
        
    -   `reverse()` – reverses the array in-place, then returns it.
        
    -   `split/join` – convert a string to array and back.
        
    -   `reduce/reduceRight(func, initial)` – calculate a single value over the array by calling `func` for each element and passing an intermediate result between the calls.
        
-   #### Additionally:
    
    -   `Array.isArray(arr)` checks `arr` for being an array.
        

Please note that methods `sort`, `reverse` and `splice` modify the array itself.

These methods are the most used ones, they cover 99% of use cases. But there are few others:

-   [arr.some(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)/[arr.every(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) check the array.
    
    The function `fn` is called on each element of the array similar to `map`. If any/all results are `true`, returns `true`, otherwise `false`.
    
    These methods behave sort of like `||` and `&&` operators: if `fn` returns a truthy value, `arr.some()` immediately returns `true` and stops iterating over the rest of items; if `fn` returns a falsy value, `arr.every()` immediately returns `false` and stops iterating over the rest of items as well.
    
    We can use `every` to compare arrays:
    
    function arraysEqual(arr1, arr2) {  
      return arr1.length === arr2.length && arr1.every((value, index) => value === arr2[index]);  
    }  
      
    alert( arraysEqual([1, 2], [1, 2])); // true
    
-   [arr.fill(value, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill) – fills the array with repeating `value` from index `start` to `end`
    
-   [arr.copyWithin(target, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin) – copies its elements from position `start` till position `end` into _itself_, at position `target` (overwrites existing).
    
-   [arr.flat(depth)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)/[arr.flatMap(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap) create a new flat array from a multidimensional array.
    

### Map and Set

`Map` – is a collection of keyed values.

Methods and properties:

-   `new Map([iterable])` – creates the map, with optional `iterable` (e.g. array) of `[key,value]` pairs for initialization.
    
-   `map.set(key, value)` – stores the value by the key, returns the map itself.
    
-   `map.get(key)` – returns the value by the key, `undefined` if `key` doesn’t exist in map.
    
-   `map.has(key)` – returns `true` if the `key` exists, `false` otherwise.
    
-   `map.delete(key)` – removes the value by the key, returns `true` if `key` existed at the moment of the call, otherwise `false`.
    
-   `map.clear()` – removes everything from the map.
    
-   `map.size` – returns the current element count.
    

The differences from a regular `Object`:

-   Any keys, objects can be keys.
    
-   Additional convenient methods, the `size` property.
    

`Set` – is a collection of unique values.

Methods and properties:

-   `new Set([iterable])` – creates the set, with optional `iterable` (e.g. array) of values for initialization.
    
-   `set.add(value)` – adds a value (does nothing if `value` exists), returns the set itself.
    
-   `set.delete(value)` – removes the value, returns `true` if `value` existed at the moment of the call, otherwise `false`.
    
-   `set.has(value)` – returns `true` if the value exists in the set, otherwise `false`.
    
-   `set.clear()` – removes everything from the set.
    
-   `set.size` – is the elements count.
    

Iteration over `Map` and `Set` is always in the insertion order, so we can’t say that these collections are unordered, but we can’t reorder elements or directly get an element by its number.

### Object.keys, values, entries

-   [Object.keys(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) – returns an array of keys.
    
-   [Object.values(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values) – returns an array of values.
    
-   [Object.entries(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries) – returns an array of `[key, value]` pairs.
    

Map

Object

Call syntax

`map.keys()`

`Object.keys(obj)`, but not `obj.keys()`

Returns

iterable

“real” Array

`Object.*` methods return “real” array objects, not just an iterable

let user = {  
  name: "John",  
  age: 30  
};  
  
// Object.keys(user) = ["name", "age"]  
// Object.values(user) = ["John", 30]  
// Object.entries(user) = [ ["name","John"], ["age",30] ]  
  
let user = {  
  name: "John",  
  age: 30  
};  
  
// loop over values  
for (let value of Object.values(user)) {  
  alert(value); // John, then 30  
}

#### Transforming objects

To use other methods that Object doesnt have but exists within arrays, use `Object.entries` followed by `Object.fromEntries`

1.  Use `Object.entries(obj)` to get an array of key/value pairs from `obj`.
    
2.  Use array methods on that array, e.g. `map`, to transform these key/value pairs.
    
3.  Use `Object.fromEntries(array)` on the resulting array to turn it back into an object.
    

let prices = {  
  banana: 1,  
  orange: 2,  
  meat: 4,  
};  
  
let doublePrices = Object.fromEntries(  
  // convert prices to array, map each key/value pair into another pair  
  // and then fromEntries gives back the object  
  Object.entries(prices).map(entry => [entry[0], entry[1] * 2])  
);  
  
alert(doublePrices.meat); // 8

### Destructuring assignment

_Destructuring assignment_ is a special syntax that allows us to “unpack” arrays or objects into a bunch of variables, as sometimes that’s more convenient. The two most used data structures in JavaScript are `Object` and `Array`.

-   Objects allow us to create a single entity that stores data items by key.
    
-   Arrays allow us to gather data items into an ordered list.
    

#### Array destructuring

// we have an array with the name and surname  
let arr = ["John", "Smith"]  
  
// destructuring assignment  
// sets firstName = arr[0]  
// and surname = arr[1]  
let [firstName, surname] = arr;  
  
alert(firstName); // John  
alert(surname);  // Smith  
  
// using split, it creates variables intead of array members  
let [firstName, surname] = "John Smith".split(' ');  
alert(firstName); // John  
alert(surname);  // Smith

#### The rest '...'

let [name1, name2] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];  
  
alert(name1); // Julius  
alert(name2); // Caesar  
// Further items aren't assigned anywhere  
  
// using ...  
let [name1, name2, ...rest] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];  
  
// rest is array of items, starting from the 3rd one  
alert(rest[0]); // Consul  
alert(rest[1]); // of the Roman Republic  
alert(rest.length); // 2  
  
let [name1, name2, ...titles] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];  
// now titles = ["Consul", "of the Roman Republic"]

#### Default values

// default values  
let [name = "Guest", surname = "Anonymous"] = ["Julius"];  
  
alert(name);    // Julius (from array)  
alert(surname); // Anonymous (default used)  
  
// runs only prompt for surname  
let [name = prompt('name?'), surname = prompt('surname?')] = ["Julius"];  
  
alert(name);    // Julius (from array)  
alert(surname); // whatever prompt gets

#### Object destructuring

let options = {  
  title: "Menu",  
  width: 100,  
  height: 200  
};  
  
let {title, width, height} = options;  
  
// setting a property to another variabble { sourceProperty: targetVariable }  
let {width: w, height: h, title} = options;  
  
alert(title);  // Menu  
alert(width);  // 100  
alert(height); // 200

let options = {  
  title: "Menu"  
};  
  
// default values  
let {width = 100, height = 200, title} = options;  
  
alert(title);  // Menu  
alert(width);  // 100  
alert(height); // 200  
  
// ask for prompt  
let {width = prompt("width?"), title = prompt("title?")} = options;  
  
alert(title);  // Menu  
alert(width);  // (whatever the result of prompt is)

// complex object  
  
let options = {  
  title: "Menu",  
  width: 100,  
  height: 200  
};  
  
// only extract title as a variable  
let { title } = options;  
  
alert(title); // Menu

// ...rest  
  
let options = {  
  title: "Menu",  
  height: 200,  
  width: 100  
};  
  
// title = property named title  
// rest = object with the rest of properties  
let {title, ...rest} = options;  
  
// now title="Menu", rest={height: 200, width: 100}  
alert(rest.height);  // 200  
alert(rest.width);   // 100

#### Nested destructuring

let options = {  
  size: {  
    width: 100,  
    height: 200  
  },  
  items: ["Cake", "Donut"],  
  extra: true  
};  
  
// destructuring assignment split in multiple lines for clarity  
let {  
  size: { // put size here  
    width,  
    height  
  },  
  items: [item1, item2], // assign items here  
  title = "Menu" // not present in the object (default value is used)  
} = options;  
  
alert(title);  // Menu  
alert(width);  // 100  
alert(height); // 200  
alert(item1);  // Cake  
alert(item2);  // Donut

## Promises, async/wait

### Callbacks

# JSON

-   JSON is a data format that has its own independent standard and libraries for most programming languages.
    
-   JSON supports the following:
    
    -   plain objects,
        
    -   arrays,
        
    -   primitives: strings, numbers, booleans, and `null`.
        
        // a number in JSON is just a number  
        alert( JSON.stringify(1) ) // 1  
          
        // a string in JSON is still a string, but double-quoted  
        alert( JSON.stringify('test') ) // "test"  
          
        alert( JSON.stringify(true) ); // true  
          
        alert( JSON.stringify([1, 2, 3]) ); // [1,2,3]
        
-   Syntax: `let json = JSON.stringify(value[, replacer, space])`
    
    -   value = a value to encode
        
    -   replacer = an array or mapping function `function(key, value)`
        
    -   space = amount of space to use for formatting ; its for pretty formatting
        
-   `JSON .stringify` will ignore the following
    
    -   Function properties (methods)
        
    -   Symbolic keys and values
        
    -   Properties that store `undefined`
        
    -   Nested objects are supported and converted automatically
        
    -   No circular references ()
        
        let user = {  
          sayHi() { // ignored  
            alert("Hello");  
          },  
          [Symbol("id")]: 123, // ignored  
          something: undefined // ignored  
        };  
          
        alert( JSON.stringify(user) ); // {} (empty object)  
          
        // nested objects  
        let meetup = {  
          title: "Conference",  
          room: {  
            number: 23,  
            participants: ["john", "ann"]  
          }  
        };  
          
        alert( JSON.stringify(meetup) );  
        /* The whole structure is stringified:  
        {  
          "title":"Conference",  
          "room":{"number":23,"participants":["john","ann"]},  
        }  
        */  
          
        JSON.stringify(meetup); // Error: Converting circular structure to JSON
        
-   [JSON.stringify](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) to serialize into JSON (can be applied to primitive)
    
    let student = {  
      name: 'John',  
      age: 30,  
      isAdmin: false,  
      courses: ['html', 'css', 'js'],  
      wife: null  
    };  
      
    let json = JSON.stringify(student);  
      
    alert(typeof json); // we've got a string!  
      
    alert(json);  
    /* JSON-encoded object:  
    {  
      "name": "John",  
      "age": 30,  
      "isAdmin": false,  
      "courses": ["html", "css", "js"],  
      "wife": null  
    }  
    */
    
-   [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) to read from JSON.
    
    -   Syntax: `let value = JSON.parse(str, [reviver]);`
        
        -   str = JSON-string to parse
            
        -   reviver = optional function(key,value) for pairing and can transform value
            
        
        // stringified array  
        let numbers = "[0, 1, 2, 3]";  
          
        numbers = JSON.parse(numbers);  
          
        alert( numbers[1] ); // 1  
          
        let userData = '{ "name": "John", "age": 35, "isAdmin": false, "friends": [0,1,2,3] }';  
          
        let user = JSON.parse(userData);  
          
        alert( user.friends[1] ); // 1
        
-   Using `reviver`
    
    // title: (meetup title), date: (meetup date)  
    let str = '{"title":"Conference","date":"2017-11-30T12:00:00.000Z"}';  
      
    let meetup = JSON.parse(str);  
    alert( meetup.date.getDate() ); // Error!  
      
    // working version  
      
    let str = '{"title":"Conference","date":"2017-11-30T12:00:00.000Z"}';  
      
    let meetup = JSON.parse(str, function(key, value) {  
      if (key == 'date') return new Date(value);  
      return value;  
    });  
      
    alert( meetup.date.getDate() ); // now works!  
      
    // nested object   
      
    let schedule = `{  
      "meetups": [  
        {"title":"Conference","date":"2017-11-30T12:00:00.000Z"},  
        {"title":"Birthday","date":"2017-04-18T12:00:00.000Z"}  
      ]  
    }`;  
      
    schedule = JSON.parse(schedule, function(key, value) {  
      if (key == 'date') return new Date(value);  
      return value;  
    });  
      
    alert( schedule.meetups[1].date.getDate() ); // works!
    
-   Both methods support transformer functions for smart reading/writing.
    
-   If an object has `toJSON`, then it is called by `JSON.stringify`.
    

# ReactJS

source: [learn-react-app (forked)](https://github.com/tyroprogrammer/learn-react-app)

## Ways to use React Components

The two approaches are identical except there are certain things that `React.Component` can do that the `function` cannot do

### React.Component

> One way is to create a `ES6` class and extend `React.Component`
> 
> Each component using this method should have a `render` function that returns what the DOM should look like if this component is rendered on the browser

import React from 'react';  
  
class Component extends React.Component {  
    //needs render function  
    render() {  
        return (  
            //return should tell React what the DOM should look like  
            //if this component is rendered in the browser  
        );  
    }  
}

### function

> Another common way to create a React component is to create a simple function that takes in a parameter (we call `props`) and returns the exact same thing as above - what the DOM should look like if this component is rendered on the browser.

function Component(props) {  
    return (  
        //return should tell React what the DOM should look like  
        //if this component is rendered in the browser  
    );  
}

## Hello World in React.js

import React from 'react';  
  
function HelloWorld(props){  
    //function must return something  
    return (  
        //return should tell React to render Hello World in the browser  
          
        React.createElement('div', null, 'Hello World')  
        // First arg -> is the element you want to render   
        // Sec arg -> any properties you want to pass to the element  
        // Trd arg -> children for this component  
          
        // which is basically the same as: // <div>Hello World</div>  
    );  
}  
  
const Usage = (props) => {  
    return <HelloWorld />  
}  
  
const default Usage;

#### Comparing Hello World in Javascript

<html>  
    <head></head>  
    <body>  
        <div id="root"></div>  
    </body>  
</html>  
  
<script>  
    //Create a div node and append Hello World text  
	const helloWorldDiv = document.createElement('div');  
	helloWorldDiv.append('Hello World');  
  
	//Select the root node and append the div created above  
	const root = document.getElementById('root');  
	root.appendChild(helloWorldDiv);  
</script>

## Introduction to JSX

// under .JSX, React will automatically compiled  
	<div>Hello World</div>  
// into React.createElement('div', null, 'Hello World')    

## Power of JSX

<script>  
    function CompanyProfile(props) {  
        const stockTicker = 'AAPL';  
        const companyProfileInfo = {  
            'Company Name': 'Apple Inc.',  
            Price: 150,  
            Exchange: 'Nasdaq Global Select',  
            Industry: 'Computer Hardware',  
            CEO: 'Timothy D. Cook'  
        };  
        return (  
            <div>  
            	<div>  
            		<div>Profile of: {stockTicker}</div>  
        			<hr />  
        		<div>  
          			{Object.keys(companyProfileInfo).map((key, index) => {  
                        return (  
                         <div>  
                            {key}: {companyProfileInfo[key]}  
    					 </div>  
						);  
    				   })}  
    			</div>  
    			</div>  
		</div>  
    );      
}  
</script>  
  
<!-- HTML outputs: -->  
<html>  
    <head></head>  
    <body>  
        <div>  
            <div>Profile of: AAPL</div>  
    		<div>  
        		<div>Company Name: Apple Inc</div>  
                <div>Price: 150</div>  
                <div>Exchange: Nasdaq Global Select</div>  
                <div>Industry: Computer Hardware</div>  
                <div>CEO: Timothy D. Cook</div>  
    		</div>  
			</div>   
    </body>  
</html>

// ❌ This is illegal in React since the return has more than one tag.  
return (   
    <div></div>  
    <div></div>  
)  
  
// ✅ This is perfectly legal because there is just one enclosing tag and  
// it can have as many children as it likes  
return (  
    <div>  
        <div>  
            <div></div>  
        </div>  
        <div></div>  
    </div>  
)  
  
// ✅  If you don't want to wrap your component with some enclosing tag like `div`  
// you can wrap everything with `React.Fragment` which is an empty tag provided by React  
return (  
    <React.Fragment>  
        <div></div>  
        <div></div>  
    </React.Fragment>  
)

## Understanding Props

// parent and children concept  
import React from 'react';  
  
function CompanyProfile(props) {  
    // use props here  
  const stockTicker = props.name; //✏️ Instead of empty string we want to get this value from props  
  const companyProfileInfo = props.desc; //✏️ Instead of empty object we want to get this value from props  
  return (  
    <div>  
      <div>Profile of: {stockTicker}</div>  
      <hr />  
      <div>  
        {Object.keys(companyProfileInfo).map((info, index) => {  
          return (  
            <div key={index}>  
              {info} : {companyProfileInfo[info]}  
            </div>  
          );  
        })}  
      </div>  
    </div>  
  );  
}  
  
function FBCompanyProfile() {  
  const stockTicker = 'FB';  
  const companyProfileInfo = {  
    'Company Name': 'Facebook',  
    Price: 150,  
    Exchange: 'Nasdaq Global Select',  
    Industry: 'Computer Software',  
    CEO: 'Mark Zuckerberg'  
  };  
  /**  
   * ✏️ need to pass the props to the `CompanyProfile` component  
   * we need to pass `stockTicker` and `companyProfileInfo`  
   * */  
  return <CompanyProfile name={stockTicker} desc={companyProfileInfo} />;  
}  
  
/**  
 * 🚨 🚨 DO NOT DELETE OR CHANGE THIS.🚨 🚨  
 * This is how you would use your above component and  
 * the output of this code is displayed on the browser  
 */  
const Usage = (props) => {  
  return <FBCompanyProfile />;  
};  
  
export default Usage;