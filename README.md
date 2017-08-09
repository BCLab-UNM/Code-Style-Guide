# Code Style Guide
This is the coding style guide for NASA-Swarmathon programmers. Feel free to make suggestions for additions to this style guide via pull requests. Be sure to include a category for the rule (try to match existing rule categories if possible), a rationale, a description of the rule and an example of the rule in practice, and any exceptions.

The purpose of this guide is to standardise the look of code written by our teams. Consistently formatted code is easier to read and compare then code written with a diverse set of styles. 

Imposing constraints on the format of syntactic elements makes source code easier to read due to consistency in form and appearance. Note that automatic code generators should be configured to produce code that conforms to the style guidelines where possible. However, an exception is made for code generators that cannot be reasonably configured to comply with should or will style rules. For example most code editors allow you to replace tabs with spaces. 

This style guide does not claim that these are the best rules to use in all circumstances. That's why it is a *style* guide not a *coding standards* guide. We do claim that consistency is often more desirable than the perfect style for each block of code. This style guide does not reflect the *personal* coding style of any of the team members. Instead this guide draws from the JOINT STRIKE FIGHTER AIR VEHICLE C++ CODING STANDARDS, 2005 with updates for more recent additions to the language. For example we introduce style guidlines for use use of the `auto` keyword.

## Typesetting

## Rule 1
**Rule:** Code indentation will be 2 spaces.

**Rationale:** Consistency. Two spaces is enough to make the indentation obvious without making lines too long.

### Rule 2  
**Rule:** Source lines will be kept to a length of 120 characters or less. 

**Rationale:** Readability and style. Very long source lines can be difficult to read and understand. 

### Rule 3  
**Rule:** Each expression-statement will be on a separate line. All expressions in an expression-statement are evaluated and all side effects are completed before the next statement is executed. 

**Rationale:** Simplicity, readability, and style.  
**Example 1** 

```C++
x = 7; y=3; // Incorrect: multiple expression statements on the same line.
a[i] = j[k]; i++; j++; // Incorrect: multiple expression statements on the same line.
a[i] = k[j]; // Correct.
i++;
j++;
```
Note that a `for` statement is a special case where conditionopt and expressionopt may appear on the same line as expression-statement.
iteration-statement:

**Example 2**
```C++
while ( condition ) statement
do statement while ( expression ) ;
for ( for-init-statement condition-opt ; expression-opt ) statement
for-init-statement:
expression-statement
simple-declaration
```
**Example 3**
```C++
for( i = 0 ; i < max ; ++i) fun(); // Incorrect: multiple expression statements on the same line.
for(i = 0 ; i < max ; ++i) // Correct
{
  foo();
}
```
### Rule 4 
**Rule:** Tabs should be avoided. 

**Rationale:** Tabs are interpreted differently across various editors and printers. 

**Note:** many editors can be configured to map the ‘tab’ key to a specified number of spaces. 

### Rule 5
**Rule:** All indentations will be at least two spaces and be consistent within the same source file. 

**Rationale:** Readability and style. 

## Naming Identifiers 

### Overview
The choice of identifier names should: 
• Suggest the usage of the identifier. 
• Consist of a descriptive name that is short yet meaningful. 
• Be long enough to avoid name conflicts, but not excessive in length. 
• Include abbreviations that are generally accepted. 

Note: In general, the above guidelines should be followed. However, conventional usage of simple identifiers (i, x, y, p, etc.) in small scopes can lead to cleaner code and will therefore be permitted. 

Additionally, the term ‘word’ in the following naming convention rules may be used to refer to a word, an acronym, an abbreviation, or a number. 

### Rule 6 

**Rule:** User-specified identifiers (internal and external) will not rely on significance of more than 64 characters. 
Note: The C++ standard suggests that a minimum of 1,024 characters will be significant. [10] 

### Rule 7 
**Rule:** Identifiers will not begin with the underscore character ‘_’. 

**Rationale:** ‘\_’ is often used as the first character in the name of library functions (e.g. _main, _exit, etc.) In order to avoid name collisions, identifiers should not begin with ‘\_’. 

### Rule 8 
**Rule:** We will not use Hungarian naming (prefixing type information) or any other naming convention that encodes intended type into the variable name. 

**Rationale:** This notation does not allow for a variable to have its type easily changed.

**Example**
```C++
float ftime = 0; //Incorrect
float time_f = 0; //Incorrect
float time = 0; //Correct
```
### Rule 9 

**Rule:** Identifiers will not differ by: 
• Only a mixture of case 
• The presence/absence of the underscore character 
• The interchange of the letter ‘O’, with the number ‘0’ or the letter ‘D’ 
• The interchange of the letter ‘I’, with the number ‘1’ or the letter ‘l’ 
• The interchange of the letter ‘S’ with the number ‘5’ 
• The interchange of the letter ‘Z’ with the number 2 
• The interchange of the letter ‘n’ with the letter ‘h’. 

**Rationale:** Readability.

**Example**

```C++
// Incorrect
float time0 = 0;
float timeO = 0; 

// Correct
float timeZero = 0;
float timeOpen = 0;
```

### Rule 10 
**Rule:** All acronyms in an identifier will be composed of uppercase letters. 

**Note:** An acronym will always be in upper case, even if the acronym is located in a portion of an identifier that is specified to be lower case by other rules. 

**Rationale:** Readability. 

## Naming Classes, Structures, enumerated types and typedefs 
### Rule 11 
**Rule:** The name of a class, structures, namespace, enumeration, or type created with typedef will begin with an uppercase letter. Each word will begin with an upper case letter. All other letters will be lower case alphanumeric (sometimes called Snake case). 

**Rationale:** Style, easy differentiation of functions, type definitions, and variables. 

**Example**
```C++
class DiagonalMatrix { // Only first letter of each word is capitalized
… 
};  
enum RGBColors {RED, GREEN, BLUE}; // RGB is an acronym so all letters 
                                   // are in upper case
```
**Exception:** The first letter of a typedef name may be in lowercase in order to conform to a standard library interface or when used as a replacement for fundamental types.
```C++
typename C::value_type s=0; // value_type of container C begins with a lower case 
                            //letter in conformance with standard library typedefs 
```

## Naming Functions, Variables and Parameters 
### Rule 12 

**Rule:** Variable names will be composed entirely of lowercase letters with underscores ("\_") separating words (sometimes known as "COBOL case".) 

**Rationale:** Style, easy differentiation of functions, type definitions, and variables.  
**Example 1**
```C++
class ExampleClassName { 
private: 
  uint16 example_variable_name; 
}; 
```
### Rule 13 
**Rule:** Functions names will be composed entirely of alphanumeric symbols. Each word, except the first, will start with a capital letter (sometimes known as “camel case.”).  

**Rationale:** Style, easy differentiation of functions, type definitions, and variables. 

**Example 1** 
```C++
class ExampleClassName { 
public: 
  uint16 exampleFunctionName(void); 
private: 
  uint16 example_variable_name; 
}; 
```

## Naming Constants and Enumerators 
### Rule 14 
**Rule:** Identifiers for constant and enumerator values shall be uppercase. 

**Rationale:** It is an accepted convention to use uppercase letters for constants and enumerators. An argument is sometimes made that macro substitution is easier if enum values are lower case. We will avoid macro substitutions.

**Example: **
```C++
const uint16 max_pressure = 100; 
enum Switch_position {UP, DOWN}; 
```

## Naming Files 
Naming files should follow the same guidelines as naming identifiers with a few additions. 
### Rule 15 
**Rule:** Header files will always have a file name extension of ".h". 
### Rule 16 
**Rule:** The following character sequences shall not appear in header file names: ‘, \, /*, //, or ". 

**Rationale:** If any of the character sequences ‘, \, /*, //, or " appears in a header file name (i.e. <h-char-sequence>), the resulting behavior is undefined. [10], 2.8(2) Note that relative pathnames may be used. However, only “/” may be used to separate directory and file names. 

**Examples**
```C++
#include <foo /* comment */ .h> // Bad: “/*” prohibited 
#include <foo’s .h> // Bad: “’” prohibited 
#include <dir1\dir2\foo.h> // Bad: “\” prohibited 
#include <dir1/dir2/foo.h> // Good: relative path used 
```
### Rule 17 
**Rule:** Implementation files will always have a file name extension of ".cpp". 

### Rule 18 
**Rule:** The name of a header file should reflect the logical entity for which it provides declarations. 

**Example:** 
For the Matrix entity, the header file would be named: 
*Matrix.h* 

### Rule 19 
**Rule:** The name of an implementation file should reflect the logical entity for which it provides definitions and have a “.cpp” extension (this name will normally be identical to the header file that provides the corresponding declarations.) 

**Exception:** At times, more than one .cpp file for a given logical entity will be required. In these cases, a suffix should be appended to reflect a logical differentiation. 

**Example 1**
One .cpp file for the Matrix class: 
Matrix.cpp 

**Example 2**
Multiple files for a math library: 

MathSqrt.cpp 

MathSin.cpp 

MathCos.cpp 

## Classes 
### Rule 20 
**Rule:** The public, protected, and private sections of a class will be declared in that order (the public section is declared before the protected section which is declared before the private section). 

**Rationale:** By placing the public section first, everything that is of interest to a user is gathered in the beginning of the class definition. The protected section may be of interest to designers when considering inheriting from the class. The private section contains details that should be of the least general interest. 

### Rule 21
**Rule:** Class constructors will always appear at the top of the list of functions in their respective sections (private, protected, or public). 

**Rationale:** Consistency. 

### Rule 22
**Rule:** Class destructors will always appear at the end of the list of functions in their respective sections (private, protected, or public). 

**Rationale:** Consistency.

### Functions 
## Rule 23 
**Rule:** When declaring and defining functions with more than two parameters, the leading parenthesis and the first argument will be written on the same line as the function name. Each additional argument will be written on a separate line (with the closing parenthesis directly after the last argument). Arguments will be indented so the argument name starts on the same column.

**Rationale:** Readability and style. 

**Examples** 
The following examples illustrate the proper way to declare functions with multiple arguments.
```C++
int32 max (int32 a, int32 b) // Correct: two parameters may appear on the
{ // same line. Order is easily understood.
…
}
// Incorrect: too many parameters on the same line.
// Difficult to document parameters in this form
msg1_in (uint16 msg_ID, float32 rate_IO, uint32 msg_size, uint16 rcv_max_instances)
{
…
}
// Correct form.
msg1_in ( uint16 msg_ID, // Unique identifier that is the label for the message
          float32 rate_IO, // The desired rate for the message distributed
          uint32 msg_size, // Size in bytes of the message
          uint16 rcv_max_instances) // The maximum number of instances of this
// message expected in a processing frame
{
…
}
```

## Blocks

### Rule 24
**Rule:** The statements forming the body of an ``if``, ``else if``, ``else``, ``while``, ``do…while`` or for statement shall always be enclosed in braces, even if the braces form an empty block. 

**Rationale:** Readability. It can be difficult to see “;” when it appears by itself. 

### Rule 25
**Rule:** Braces ("{}") which enclose a block will be placed in the same column, on separate lines directly before and after the block. 
**Example*
```C++
if (var_name == true) 
{ 
} 
else 
{ 
} 
```

### Rule 26
**Rule:** Braces ("{}") which enclose a block will have nothing else on the line except comments (if necessary). 

## Pointers and References

### Rule 27
**Rule:** The dereference operator ‘*’ and the address-of operator ‘&’ will be directly connected with the type-specifier. 

**Rationale:** The ``int32* p;`` form emphasizes type over syntax while the ``int32 *p;`` form emphasizes syntax over type.
Although both forms are equally valid C++, the heavy emphasis on types in C++ suggests that ``int32* p;`` is the preferable form. 

**Examples**
```C++
int32* p; // Correct 
int32 *p; // Incorrect 
int32* p, q; // Probably error. However, this declaration cannot occur 
// under the one name per declaration style required by AV Rule 152. 
```
### Rule 28
**Rule:** Spaces will not be used around ‘.’ or ‘->’, nor between unary operators and operands. 

**Rationale:** Readability and style. 

