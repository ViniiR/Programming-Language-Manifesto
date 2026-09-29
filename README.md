# Styria

An expression-based, statically typed, scripting programming language named after the Duchy of Styria
File extension: .sty

## Shebang

if the first two characters are #! the first line will be ignored by the parser

## Keywords

<table>
    <tr>
        <th>Keyword</th>
        <th>Example</th>
        <th>Type</th>
        <th>Explanation</th>
    </tr>
    <tr>
        <td>true</td>
        <td>true</td>
        <td>Expression</td>
        <td>Boolean literal of 1 variant</td>
    </tr>
    <tr>
        <td>false</td>
        <td>false</td>
        <td>Expression</td>
        <td>Boolean literal of 0 variant</td>
    </tr>
    <tr>
        <td>none</td>
        <td>none</td>
        <td>Expression</td>
        <td>Void literal (represents no value)</td>
    </tr>
    <tr>
        <th colspan="4">Conditionals</th>
    </tr>
    <tr>
        <td>if</td>
        <td>if true {}</td>
        <td>Expression</td>
        <td>Conditional statement (When used as an expression it is required to add an else branch)</td>
    </tr>
    <tr>
        <td>else</td>
        <td>else {}</td>
        <td>Expression</td>
        <td>Complementary branch of an if statement (can be followed by another if branch, e.g. else if false {})</td>
    </tr>
    <tr>
        <td>match</td>
        <td>match 10 {}</td>
        <td>Expression</td>
        <td>Branch selection based on condition, requires at least 2 branches</td>
    </tr>
    <tr>
        <td>when</td>
        <td>when 10 {}</td>
        <td>Expression</td>
        <td>Branch for a match expression</td>
    </tr>
    <tr>
        <td>or</td>
        <td>when 10 or 11 {}</td>
        <td>Expression</td>
        <td>Creates multiple entry points for when branch, can be chained</td>
    </tr>
    <tr>
        <td>and</td>
        <td>when 10 and true {}</td>
        <td>Expression</td>
        <td>Checks if condition is true before matching branch, must be used after the last or operation if any exists, cannot be chained</td>
    </tr>
    <tr>
        <td>it (match)</td>
        <td>when 10 and it != 11 {}</td>
        <td>Expression</td>
        <td>Access to the matched element in a match branch</td>
    </tr>
    <tr>
        <td>default</td>
        <td>default {}</td>
        <td>Expressio</td>
        <td>Default branch for a match expression, will always match if none of the previous when branches are matched</td>
    </tr>
    <tr>
        <th colspan="4">Loops</th>
    </tr>
    <tr>
        <td>for</td>
        <td>for let i = 0; i &lt; 10; i += 1 {}</td>
        <td>Statement</td>
        <td>Iterates for an index, checks condition and increments index</td>
    </tr>
    <tr>
        <td>in</td>
        <td>for let item in [0, 1, 2, 3] {}</td>
        <td>Expression</td>
        <td>Used in a for loop variant, iterates over an array or string</td>
    </tr>
    <tr>
        <td>while</td>
        <td>while true {}</td>
        <td>Statement</td>
        <td>Repeatedly executes block while condition is true</td>
    </tr>
    <tr>
        <td>continue</td>
        <td>continue;</td>
        <td>Statement</td>
        <td>Continues loop's execution to next iteration</td>
    </tr>
    <tr>
        <td>break</td>
        <td>break;</td>
        <td>Statement</td>
        <td>Breaks the innermost loop's execution</td>
    </tr>
    <tr>
        <th colspan="4">Variables</th>
    </tr>
    <tr>
        <td>const</td>
        <td>const VAL = 10;</td>
        <td>Statement</td>
        <td>Binds immutable value to identifier</td>
    </tr>
    <tr>
        <td></td>
        <td>const VAL: Int = 10;</td>
        <td>Statement</td>
        <td>Variant of value binding with explicit type</td>
    </tr>
    <tr>
        <td>let</td>
        <td>let var = 10;</td>
        <td>Statement</td>
        <td>Assigns mutable value to identifier</td>
    </tr>
    <tr>
        <td></td>
        <td>let var: Int = 10;</td>
        <td>Statement</td>
        <td>Variant of variable assignment with explicit type</td>
    </tr>
    <tr>
        <th colspan="4">Functions</th>
    </tr>
    <tr>
        <td>func</td>
        <td>func name(param: Int) {}</td>
        <td>Expression</td>
        <td>Declares and implements function (if return type is ommited it is implicitly Void)</td>
    </tr>
    <tr>
        <td></td>
        <td>func name(param: Int): Int {}</td>
        <td>Expression</td>
        <td>Variant of function declaration with explicit type</td>
    </tr>
    <tr>
        <td></td>
        <td>func(param: Int) {}</td>
        <td>Expression</td>
        <td>Anonymous variant of function declaration, must be used exclusively as an expression</td>
    </tr>
    <tr>
        <td></td>
        <td>func {}</td>
        <td>Expression</td>
        <td>Variant of anonymous function with zero or one parameter</td>
    </tr>
    <tr>
        <td>it (function)</td>
        <td>it</td>
        <td>Expression</td>
        <td>Implicit name of an anonymous' function only parameter if it was not specified</td>
    </tr>
    <tr>
        <td>return</td>
        <td>return true;</td>
        <td>Statement</td>
        <td>Returns an expression from a function matching its return type (if expression is ommited it implicitly returns none)</td>
    </tr>
    <tr>
        <th colspan="4">Types</th>
    </tr>
    <tr>
        <td>type</td>
        <td>type Int32 Int;</td>
        <td>Statement</td>
        <td>Creates a new type (must end with a semicolon)</td>
    </tr>
    <tr>
        <td>struct</td>
        <td>type CoolString struct { value: String }</td>
        <td>Expression</td>
        <td>Used together with the type keyword to create a new struct type</td>
    </tr>
    <tr>
        <td>enum</td>
        <td>type ThisOrThat enum { This, Or, That }</td>
        <td>Expression</td>
        <td>Used together with the type keyword to create a new enum type</td>
    </tr>
    <tr>
        <td>is</td>
        <td>10 is Int</td>
        <td>Expression</td>
        <td>Checks if left expression's type is the same as the right side's Type Identifier</td>
    </tr>
    <tr>
        <td>as (cast)</td>
        <td>10 as Float</td>
        <td>Expression</td>
        <td>Casts left expression to type</td>
    </tr>
    <tr>
        <th colspan="4">Modules</th>
    </tr>
    <tr>
        <td>export</td>
        <td>export func name() {}</td>
        <td>Statement</td>
        <td>Specifies that a function, type or constant value is exposed to module importer</td>
    </tr>
    <tr>
        <td>import</td>
        <td>import "filename" as namespace;</td>
        <td>Statement</td>
        <td>Imports all exported members of a file under a local namespace</td>
    </tr>
    <tr>
        <td>as (namespace)</td>
        <td>import "filename" as namespacename;</td>
        <td>Expression</td>
        <td>Specifies name of namespace</td>
    </tr>
    <tr>
        <th colspan="4">Other</th>
    </tr>
    <tr>
        <td>into</td>
        <td>10 into func_call(here)</td>
        <td>Expression</td>
        <td>Inserts left expression into the first here keyword it finds, inspired by Hack's pipe operator</td>
    </tr>
    <tr>
        <td>here</td>
        <td>10 into func_call(here)</td>
        <td>Expression</td>
        <td>Placeholder keyword for into operation</td>
    </tr>
</table>



## Naming rules

<table>
    <tr>
        <td>Constant values</td>
        <td>A-Z, 0-9, and underscores _, following CONSTANT_CASE</td>
    </tr>
    <tr>
        <td>Regular variables, methods, and functions</td>
        <td>a-z, 0-9, and underscores _, following snake_case</td>
    </tr>
    <tr>
        <td>Types and enum variants</td>
        <td>a-z, A-Z, 0-9, where the first character must be uppercase and followed by at least one lowercase letter, following PascalCase</td>
    </tr>
    <tr>
        <td>Namespaces</td>
        <td>a-z, 0-9, where ideally only one word should exist, if more than one exists it should simply be appended to it, following lowercase</td>
    </tr>
</table>



## Comments

<table>
    <tr>
        <td>//</td>
        <td>Normal Comment</td>
    </tr>
    <tr>
        <td>///</td>
        <td>Doc Comment</td>
    </tr>
</table>


## Symbols and Non-keyword Operators

<table>
    <tr>
        <th>Name</th>
        <th>Operator</th>
        <th>Example</th>
        <th>Explanation</th>
    </tr>
    <tr>
        <td>Negation</td>
        <td>!</td>
        <td>!false</td>
        <td>Negates value of boolean</td>
    </tr>
    <tr>
        <td>And</td>
        <td>&&</td>
        <td>true && true</td>
        <td>Logical And</td>
    </tr>
    <tr>
        <td>Or</td>
        <td>||</td>
        <td>true || false</td>
        <td>Logical Or</td>
    </tr>
    <tr>
        <td>Structural Equality</td>
        <td>==</td>
        <td>10 == 10</td>
        <td>Compares expressions by value</td>
    </tr>
    <tr>
        <td>Structural Difference</td>
        <td>!=</td>
        <td>10 != 11</td>
        <td>Negation of Structural Equality</td>
    </tr>
    <tr>
        <td>Physical Equality</td>
        <td>===</td>
        <td>array === array</td>
        <td>Checks if expressions are the same value in memory</td>
    </tr>
    <tr>
        <td>Physical Difference</td>
        <td>!==</td>
        <td>Struct1 {} !== Struct1 {}</td>
        <td>Negation of Physical Equality</td>
    </tr>
    <tr>
        <td>Greater</td>
        <td>&gt;</td>
        <td>10 &gt; 9</td>
        <td>Greater than comparison</td>
    </tr>
    <tr>
        <td>Greater-equal</td>
        <td>&gt;=</td>
        <td>10 &gt;= 10</td>
        <td>Greater or equals than comparison</td>
    </tr>
    <tr>
        <td>Lesser</td>
        <td>&lt;</td>
        <td>9 &lt; 10</td>
        <td>Lesser than comparison</td>
    </tr>
    <tr>
        <td>Lesser-equal</td>
        <td>&lt;=</td>
        <td>9 &lt;= 9</td>
        <td>Lesser or equals than comparison</td>
    </tr>
    <tr>
        <td>Addition</td>
        <td>+</td>
        <td>1 + 1</td>
        <td>Addition</td>
    </tr>
    <tr>
        <td>Subtraction</td>
        <td>-</td>
        <td>2 - 1</td>
        <td>Subtraction</td>
    </tr>
    <tr>
        <td>Division</td>
        <td>/</td>
        <td>10 / 2</td>
        <td>Division</td>
    </tr>
    <tr>
        <td>Multiplier</td>
        <td>*</td>
        <td>1 * 2</td>
        <td>Multiplication</td>
    </tr>
    <tr>
        <td>Remainder</td>
        <td>%</td>
        <td>10.2 % 2</td>
        <td>Remainder</td>
    </tr>
    <tr>
        <td>Assignment</td>
        <td>=</td>
        <td>let var = 10</td>
        <td>Assigns value to an identifier, including struct members</td>
    </tr>
    <tr>
        <td>Assignment Addition</td>
        <td>+=</td>
        <td>a += 1</td>
        <td>Adds value of variable</td>
    </tr>
    <tr>
        <td>Assignment Subtraction</td>
        <td>-=</td>
        <td>a -= 1</td>
        <td>Subtracts value of variable</td>
    </tr>
    <tr>
        <td>Assignment Division</td>
        <td>/=</td>
        <td>a /= 1</td>
        <td>Divides value of variable</td>
    </tr>
    <tr>
        <td>Assignment Multiplier</td>
        <td>*=</td>
        <td>a *= 2</td>
        <td>Multiplies value of variable</td>
    </tr>
    <tr>
        <td>Assignment Remainder</td>
        <td>%=</td>
        <td>a %= 2</td>
        <td>Assigns remainder value to variable</td>
    </tr>
    <tr>
        <td>Separator (Comma)</td>
        <td>,</td>
        <td>[10, 20]</td>
        <td>Separates values</td>
    </tr>
    <tr>
        <td>Member Access (Dot)</td>
        <td>.</td>
        <td>value.member</td>
        <td>Lets you access field, method, or type on structs and enums</td>
    </tr>
    <tr>
        <td>Namespace Resolutor (Double Colon)</td>
        <td>::</td>
        <td>namespace::Type</td>
        <td>Lets you resolve module paths and access functions, types or constants defined on them</td>
    </tr>
    <tr>
        <td>Void Coalescing</td>
        <td>??</td>
        <td>returns_option_string() ?? "Some String"</td>
        <td>If left expression is none, evaluates to the right expression (right expression can be a code block with a return statement)</td>
    </tr>
    <tr>
        <td>Try Result</td>
        <td>!!</td>
        <td>returns_result()!!</td>
        <td>If left expression is an error, immediately returns it, else unwraps its result value</td>
    </tr>
    <tr>
        <th colspan="4">Symbols</th>
    </tr>
    <tr>
        <td>Type Specifier (Colon)</td>
        <td>:</td>
        <td>let a: Int = 10</td>
        <td>Specifies type of variables, parameters, struct fields, and functions</td>
    </tr>
    <tr>
        <td>Semicolon</td>
        <td>;</td>
        <td>let b = 10;</td>
        <td>Ends specific statements</td>
    </tr>
    <tr>
        <td>Block</td>
        <td>{}</td>
        <td>let a = { let b = 10; b };</td>
        <td>Expression that contains statements and evaluates to the last statement expression inside it, as long as it does not end in a semicolon, if no ending expression is found, implicitly evaluates to none</td>
    </tr>
    <tr>
        <td>Index</td>
        <td>[]</td>
        <td>array[10]</td>
        <td>Retrieves value of array, string or tuple at certain index</td>
    </tr>
</table>



## Custom Types

type EnumType enum {
    Identifier,
    Keyword,
}

type StructType struct {
    epoch: Int64
}

type Alias OtherType;



## Types and Literals

<table>
    <tr>
        <th>Type</th>
        <th>Example</th>
        <th>Info</th>
    </tr>
    <tr>
        <td>Int</td>
        <td>10</td>
        <td>Any number from 0-9 optionally separated by underscores _</td>
    </tr>
    <tr>
        <td>Int64</td>
        <td>10i64</td>
        <td>Same as Int literal but suffixed by i64</td>
    </tr>
    <tr>
        <td>Float</td>
        <td>10.0</td>
        <td>Same as Int but with a period decimal separador ., .10 is implicitly 0.10, 10. is implicitly 10.0</td>
    </tr>
    <tr>
        <td>Float64</td>
        <td>10.0f64</td>
        <td>Same as Float but suffixed by f64</td>
    </tr>
    <tr>
        <td>Bool</td>
        <td>true</td>
        <td>Keywords true or false</td>
    </tr>
    <tr>
        <td>Void</td>
        <td>none</td>
        <td>Keyword none</td>
    </tr>
    <tr>
        <td>String</td>
        <td>"Ten!"</td>
        <td>Anything inside two double quote characters " in the same line, supports character escaping, see String Escape Characters</td>
    </tr>
    <tr>
        <td></td>
        <td>\\'Raw String</td>
        <td>Multiline or Raw String, String literal without escapable characters, only inserts newline at the end if followed by another Raw String on the next line</td>
    </tr>
    <tr>
        <td>Error</td>
        <td>!'Error message'</td>
        <td>Anything inside single quote characters ' where the first is !', in the same line, supports character escaping</td>
    </tr>
    <tr>
        <th colspan="3">Aggregate Types</th>
    </tr>
    <tr>
        <td>[] (Array)</td>
        <td>[10, 11]</td>
        <td>Comma , separated expressions inside square brackets [], with an optional comma after the final item</td>
    </tr>
    <tr>
        <td>() (Tuple)</td>
        <td>(10, "10")</td>
        <td>Comma , separated expressions inside parentheses, with an optional comma after the final item</td>
    </tr>
    <tr>
        <td>Struct</td>
        <td>Name { field = 10, name = "" }</td>
        <td>Field assignments with = inside curly braces {} prefixed by struct name, individual fields must be separated by a comma ,, with an optional comma after the final item</td>
    </tr>
    <tr>
        <td>? (Option)</td>
        <td>Has no specific literal definition</td>
        <td>Union of type Void and type defined after question mark ?</td>
    </tr>
    <tr>
        <td>! (Result)</td>
        <td>Has no specific literal definition</td>
        <td>Union of type Error and type defined after exclamation mark !</td>
    </tr>
    <tr>
        <td>Func() Void (Function)</td>
        <td>func() {}</td>
        <td>Type of a function, defined by the Func type followed by an unnamed parameter list and ending with a non optional return type</td>
    </tr>
    <tr>
        <td>Any</td>
        <td>Has no literal definition</td>
        <td>Can match any type, even custom ones</td>
    </tr>
</table>

Arrays, Options and Results can be read from left to right using the word 'of',
!?[]Int is a Result of Option of Array of Int, roughly in a generic based syntax: Result&lt;Option&lt;Array&lt;Int&gt;&gt;&gt;



## String Interpolation

Strings can have expressions embedded inside them using the ${} symbol, anything inside the curly braces will be evaluated,  
to use a literal ${} see String Escape Characters



## String Escape Characters

<table>
    <tr>
        <th>Value</th>
        <th>Symbol</th>
    </tr>
    <tr>
        <td>Newline</td>
        <td>\n</td>
    </tr>
    <tr>
        <td>Carriage Return</td>
        <td>\r</td>
    </tr>
    <tr>
        <td>Tab</td>
        <td>\t</td>
    </tr>
    <tr>
        <td>Backslash</td>
        <td>\\</td>
    </tr>
    <tr>
        <td>Double Quote</td>
        <td>\"</td>
    </tr>
    <tr>
        <td>Single Quote</td>
        <td>\'</td>
    </tr>
    <tr>
        <td>Currency Symbol</td>
        <td>\$</td>
    </tr>
</table>



## Modules

As previously mentioned, items in a file can be exposed to the outside,
modules can be structured in either of these two ways:
<pre><code>
- main.sty
- mod1.sty
- mod2/
-    mod2.sty
-    nested.sty
</code></pre>

You can import them like this:
<ul>
    <li><code>import "mod1" as mod1;</code></li>
    <li><code>import "mod2" as mod2;</code></li>
    <li><code>mod2::nested::some_func();</code></li>
</ul>
