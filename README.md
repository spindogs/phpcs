## PSR-1 and PSR-2

All PHP code MUST abide by the standards as described by PSR-1 and PSR-2. These recommendations can be read in full at http://www.php-fig.org/psr/.

For ease of use, a summary of these standards is described below.

### Legacy code

Whilst all new code (including new code added to old files) MUST follow these standards, you are NOT expected to convert any existing legacy code to these standards.

### Files

* All PHP files MUST use the Unix LF (linefeed) line ending

### Indenting

* Code MUST use 4 spaces for indenting, not tabs

### PHP keywords

* PHP keywords MUST be in lowercase (eg. `if`, `while`, `for`, etc)
* The PHP constants `true`, `false`, and `null` MUST be in lowercase

### Naming

PSR-1 standards do not make any recommendation regarding the naming of your code other than stating that a consistent style must be used across the board. As a result, Spindogs prefers the following naming styles:

* Constants MUST be declared in **UPPERCASE** (with underscore separators)
* Class names MUST be declared in **TitleCase**
* Method names MUST be declared in **camelCase**
* Property names MUST be declared in **snake_case**
* Variables MUST be declared in **snake_case**

### Global functions

The use of global functions SHOULD be avoided at every opportunity, instead helper functions should be encapsulated within a class

### Classes

Visibility (`public`, `protected`, `private`) MUST be declared on all properties

    <?php
    namespace Vendor\Package;

    class ClassName
    {
        public $foo = null;
    }

### Methods

* Visibility (`public`, `protected`, `private`) MUST be declared on all methods
* Hanging brace - the opening brace MUST go on its own line
* When present, the `static` declaration MUST come after the visibility

Example:

    /**
     * @param int $arg1
     * @param string $arg2
     * @param array $arg3
     * @return void
     */
    public static function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        //method body
    }

### Docblocks

All methods MUST have a docblock associated with them. At the very minimum, this docblock MUST document the `@param` types for each method parameter.

It is also recommended that every method SHOULD use the `@return` tag in order to keep docblocks consistent (use `@return void` for methods that have no return value).

### Control structures

* There MUST be one space after the control structure keyword
* The opening brace MUST be on the same line as the control structure keyword
* There MUST be one space between the closing parenthesis and the opening brace
* The keyword `elseif` SHOULD be used instead of `else if`

Example:

    if ($expr1) {
        //if body
    } elseif (isset($expr2) && isset($expr3)) {
        //elseif body
    } else {
        //else body;
    }

A `foreach` statement looks like the following:

    foreach ($iterable as $key => $value) {
        //foreach body
    }

### Variables

The variable name SHOULD accurately describe what is does. However, the following variable names are allowed in special cases:

    $q; //used for SQL queries
    $i; //used as a pointer within a loop
    $r; //used within a loop to denote a row array/object

### Strings

Variables MUST NOT be placed inside a string with double quotes:

    //incorrect
    echo "Hello world, my name is $user_name - nice to meet you";

At every opportunity, single quotes SHOULD be preferred for delimiting strings. The only exception is when displaying a special character such as a line return:

    //correct
    echo 'Hello world, nice to meet you'."\n";

### Arrays

Arrays with a small number of indices MAY be declared using the inline format (taking notice of the whitespaces):

    $arr = [1, 2, 3, 4];

For larger arrays that do not fit on one line (80 characters), the multiline format MUST be used:

    $arr = [
        'First' => 1,
        'Second' => 2,
        'Third' => 3,
        'Fourth' => 'Hello',
        'Fifth' => 'World'
    ];

### Special operators

> If you spotted the security implications in the examples below surrounding echoing variables out un-escaped then well done, give yourself a big pat on the back!

For non complicated statements, the **terniary operator** format MAY be used (taking notice of the whitespaces):

    <?= isset($variable_name) ? $variable_name : 'Default value'; ?>

In order to aid readability, the **null coalescing** operator MAY be used to provide a default value if a variable doesn't exist:

    <?= $variable_name ?? 'This variable is null'; ?>

Similarly, the **elvis operator** MAY be used to provide a default value if a variable is not truthy:

    <?= $variable_name ?: 'This variable is not truthy (ie. null/0/false)'; ?>

### Database

All database tables MUST be named using **TitleCase** and singularly (to match model name):

    Event
    EventCategory

All database columns MUST be named using **snake_case**:

    event_id
    name

## Code Editors

### Atom

You can install the Atom Beautify package and configure it to use Spindogs coding standards each time you save a PHP file https://github.com/Glavin001/atom-beautify.

1. Download latest `php-cs-fixer.phar` to your PHP directory on local machine https://github.com/FriendsOfPHP/PHP-CS-Fixer#installation

2. Clone this GIT repository to a location on your local machine https://github.com/spindogs/phpcs

2. Install `atom-beautify` package from settings screen

3.
