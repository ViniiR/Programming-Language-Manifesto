# Concept Language

It aims to provide a language without many syntax quirks, relying more on method calls

## Rules

<ul>
    <li>Every statement must end with a semicolon(;)</li>
    <li>Avoid quirky operators, prefer method calls and properties</li>
</ul>


## Planned "features"

<ul>
    <li>Async/Suspend</li>
</ul>



### Keywords

func, fun, return
let, mut
while, break, continue
if, else
type, enum, struct // TODO:
true, false
public



### Operators

->
==, ===, <=, >=
!=, !==
!, ||, &&
(), [], {}
+, -, *, /, %
=, +=, -=, *=, =/, %=
:, ;
,, .



### Blocks

// Blocks automatically return their last expression
let hello: String = {
    "Hello"
};

let none: Void = {};



### Variables

// Specify types
let name: Type = value;
mut name: Type = value;

// Infer types
let name = value;
mut name = value;

// Reassign
name = newValue;

// No immediate assign (cannot use without reassignment)
let name: Type;
mut name: Type;



### Functions

// Types must be defined
func name(param: Type): ReturnType {

};

// Calling functions
name(value);


## Lambdas

(param: Type) -> {
    "Hello, world!"
};

// They are expressions
let function: Function<Type1, Type2, ..., String> = 
(param: Type1, param2: Type2, ...): String -> {
    "Hello, world!"
};

// Lambdas that only receive one or no parameters can be shortened to 
fun {
    // you can access the parameter using 'it'
    println(it);
};
// Is equivalent to
(val: String) -> {
    println(val);
};

value.methodWithFun(fun {
    // 
});



### Loops


## While

while true {
    println("Hello");
    break;
};


## Foreach

let iterator: Iterator = Vec::from(0, 1, 2).iter();

iterator.foreach(fun {
    println("Value is ${it}");
});

let range: Rage = Range::from(0, 10); 0 to 10
let exclusiveRange: Rage = Range::from_exclusive(0, 10); // 0 to 9

Range::from(0, 100).foreach(...);



### Conditionals

if true {
    // ...
} else if true {
    // ...
} else {
    // ...
}

// Ifs are expressions too
let integer: Int = if true {0} else if true {1} else {2};
// Also with a simpler syntax
let integer: Int = if true then 0 else if true then 1 else 2;



### Built-in Types

Void
represents nothing: {}; // empty block

Bool
true, false

Int, Int64
10, 10i, 10i64, 100_000

Float, Float64
10.0, 10f, 10f64, 100_00.0, 1., .1

String
"Hello, ${"world"}!", 'Hello, ${'world'}!' (allows interpolation with ${})

Function&lt;T, ..., R&gt;
(T, ...): R -> {...}

Vec&lt;T&gt;
Vec::from(value, ...);

Option&lt;T&gt;
Option::Some(value);
Option::None;

Result&lt;T&gt;
Result::Ok(value);
Result::Error;


PROPOSED TYPES


Iterator



### Custom Types

TODO:
type Name = Type;

// Default option implementation for example
enum Option<T> {
    Some(T),
    None,
};

// Structs
// structs are much like classes TODO: maybe not
struct Name {
    field: String,
    public func name() {

    },
};
let str: Name = {
    field = "",
};



### Comments

// Normal comment

/* Inline comment */

/// Doc comment
/// @param hello_world: String
/// @return Void



# Usage

You are free to implement this document's features on the condition that you credit this repository.
