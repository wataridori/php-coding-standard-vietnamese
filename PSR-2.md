Coding Style Guide
==================

Bộ quy tắc này dựa trên và mở rộng từ [PSR-1], basic coding standard

Bộ quy tắc này được tạo ra nhằm giảm bới những khó khăn trong việc đọc code 
của người khác. Nó thực hiện điều đó bằng cách đặt ra những quy định hay gợi 
ý về việc format PHP code.

[PSR-0]: https://github.com/wataridori/php-coding-standard-vietnamese/blob/master/PSR-0.md
[PSR-1]: https://github.com/wataridori/php-coding-standard-vietnamese/blob/master/PSR-1.md


1. Overview
-----------

- Code phải tuân theo "coding style guide" PSR [[PSR-1]].

- Code không dùng tab, mà phải sử dụng 4 dấu cách làm indent. 

- Không có hard limit về độ dài của một dòng; soft limit phải là 120
  chữ. Một dòng nên có không quá 80 chữ.

- Cần phải có một dòng trống ở sau phần định nghĩa `namespace`. Ngoài ra cũng cần có 
  một dòng trống phía sau phần định nghĩa `use`.

- Dấu mở ngặc nhọn dùng khi định nghĩa class phải được viết ở dòng mới (không viết cùng dòng với phần định nghĩa tên class), 
  và dấu đóng ngoặc nhọn của một class phải được viết ở dòng mới sau khi kết thúc body của class.

- Dấu mở ngặc nhọn dùng khi định nghĩa  phải được viết ở dòng mới (không viết cùng dòng với phần định nghĩa tên method), 
   và dấu đóng ngoặc nhọn của một method phải được viết ở dòng mới sau khi kết thúc body của method.

- Phải luôn định nghĩa tính visibility (`public`, `protected` hay là `private`) của properties cũng như methods.
 `abstract` và `final` phải được định nghĩa phía trước tính visibility và `static` phải được định nghĩa sau tính visibility. 

- Cần phải có một dấu cách phía sau những từ khoá Control structure (như `if`, `else`, `for` ...).
  Không được có dấu cách phía sau tên của method khi gọi hàm.

- Dấu mở ngoặc nhọn cho control structures (như `if`, `else`, `for` ...) phải được viết cùng dòng, trong khi đó đấu đóng ngoặc
  phải được viết ở dòng mới.

- Trong câu lệnh control structures, không được phép có dấu cách ở sau dấu mở ngặc tròn cũng như ở trước dấu đóng ngoặc tròn.

### 1.1. Example

Ví dụ dưới đây bao gồm một vài quy tắc đã được đề cập ở phần trên, overview:

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

2. General
----------

### 2.1 Basic Coding Standard

Code phải tuân theo "coding style guide" PSR [[PSR-1]].

### 2.2 Files

Mọi PHP files phải dùng Unix LF (linefeed) line ending.

Mọi PHP files phải kết thúc bằng một dòng trống.

Trong một file chỉ bao gồm code PHP thì không được viết tag đóng `?>`. 

### 2.3. Lines

Không có hard limit về độ dài của một dòng.

Soft limit của độ dài một dòng phải là 120 chữ. Chương trình check style tự động phải báo warning nhưng không được báo 
error khi vượt quá soft limit.
 
Một dòng nên có không quá 80 chữ. Dòng mà dài quá 80 chữ thì nên chia nhỏ ra thành nhiều dòng với độ dài mỗi dòng 
không quá 80 chữ.

Một dòng không trống không được phép có trailing whitespace (dấu cách ở cuối dòng) 

Dòng trống có thể được thêm vào để code có thể được dễ đọc hơn và để phân cách những đoạn code.

Không được phép có quá một statement trên một dòng.

### 2.4. Indenting

Code không dùng tab, mà phải sử dụng 4 dấu cách làm indent.

### 2.5. Keywords and True/False/Null

Những [keywords] của PHP phải được viết thường. (không viết hoa)

Những constants của PHP là `true`, `false`, và `null` cũng cần phải viết thường.

[keywords]: http://php.net/manual/en/reserved.keywords.php


3. Namespace and Use Declarations
---------------------------------

Cần phải có một dòng trắng phía sau định nghĩa `namespace`.

Những phần định nghĩa `use` phải được đặt phía sau phần định nghĩa `namespace`.

Phải dùng một từ `use` cho mỗi định nghĩa.

Phải có một dòng trắng phía sau đoạn code `use`.

Ví dụ:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... additional PHP code ...

```


4. Classes, Properties, and Methods
-----------------------------------

Từ class dưới đây được hiểu là cả những class bình thường, hay cả interfaces và traits.

### 4.1. Extends and Implements

Từ khoá `extends` và `implements` phải được viết cùng dòng với tên class. 

Dấu mở ngoặc nhọn của class phải đứng trên một dòng riêng. Dấu đóng ngoặc phải được viết ở dòng sau của phần body.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

Lists of `implements` MAY be split across multiple lines, where each
subsequent line is indented once. When doing so, the first item in the list
MUST be on the next line, and there MUST be only one interface per line.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

### 4.2. Properties

Visibility MUST be declared on all properties.

The `var` keyword MUST NOT be used to declare a property.

There MUST NOT be more than one property declared per statement.

Property names SHOULD NOT be prefixed with a single underscore to indicate
protected or private visibility.

A property declaration looks like the following.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3. Methods

Visibility MUST be declared on all methods.

Method names SHOULD NOT be prefixed with a single underscore to indicate
protected or private visibility.

Method names MUST NOT be declared with a space after the method name. The
opening brace MUST go on its own line, and the closing brace MUST go on the
next line following the body. There MUST NOT be a space after the opening
parenthesis, and there MUST NOT be a space before the closing parenthesis.

A method declaration looks like the following. Note the placement of
parentheses, commas, spaces, and braces:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

### 4.4. Method Arguments

In the argument list, there MUST NOT be a space before each comma, and there
MUST be one space after each comma.

Method arguments with default values MUST go at the end of the argument
list.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

Argument lists MAY be split across multiple lines, where each subsequent line
is indented once. When doing so, the first item in the list MUST be on the
next line, and there MUST be only one argument per line.

When the argument list is split across multiple lines, the closing parenthesis
and opening brace MUST be placed together on their own line with one space
between them.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

### 4.5. `abstract`, `final`, and `static`

When present, the `abstract` and `final` declarations MUST precede the
visibility declaration.

When present, the `static` declaration MUST come after the visibility
declaration.

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```

### 4.6. Method and Function Calls

When making a method or function call, there MUST NOT be a space between the
method or function name and the opening parenthesis, there MUST NOT be a space
after the opening parenthesis, and there MUST NOT be a space before the
closing parenthesis. In the argument list, there MUST NOT be a space before
each comma, and there MUST be one space after each comma.

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Argument lists MAY be split across multiple lines, where each subsequent line
is indented once. When doing so, the first item in the list MUST be on the
next line, and there MUST be only one argument per line.

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5. Control Structures
---------------------

The general style rules for control structures are as follows:

- There MUST be one space after the control structure keyword
- There MUST NOT be a space after the opening parenthesis
- There MUST NOT be a space before the closing parenthesis
- There MUST be one space between the closing parenthesis and the opening
  brace
- The structure body MUST be indented once
- The closing brace MUST be on the next line after the body

The body of each structure MUST be enclosed by braces. This standardizes how
the structures look, and reduces the likelihood of introducing errors as new
lines get added to the body.


### 5.1. `if`, `elseif`, `else`

An `if` structure looks like the following. Note the placement of parentheses,
spaces, and braces; and that `else` and `elseif` are on the same line as the
closing brace from the earlier body.

```php
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

The keyword `elseif` SHOULD be used instead of `else if` so that all control
keywords look like single words.


### 5.2. `switch`, `case`

A `switch` structure looks like the following. Note the placement of
parentheses, spaces, and braces. The `case` statement MUST be indented once
from `switch`, and the `break` keyword (or other terminating keyword) MUST be
indented at the same level as the `case` body. There MUST be a comment such as
`// no break` when fall-through is intentional in a non-empty `case` body.

```php
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```


### 5.3. `while`, `do while`

A `while` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

```php
<?php
while ($expr) {
    // structure body
}
```

Similarly, a `do while` statement looks like the following. Note the placement
of parentheses, spaces, and braces.

```php
<?php
do {
    // structure body;
} while ($expr);
```

### 5.4. `for`

A `for` statement looks like the following. Note the placement of parentheses,
spaces, and braces.

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 5.5. `foreach`

A `foreach` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 5.6. `try`, `catch`

A `try catch` block looks like the following. Note the placement of
parentheses, spaces, and braces.

```php
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

6. Closures
-----------

Closures MUST be declared with a space after the `function` keyword, and a
space before and after the `use` keyword.

The opening brace MUST go on the same line, and the closing brace MUST go on
the next line following the body.

There MUST NOT be a space after the opening parenthesis of the argument list
or variable list, and there MUST NOT be a space before the closing parenthesis
of the argument list or variable list.

In the argument list and variable list, there MUST NOT be a space before each
comma, and there MUST be one space after each comma.

Closure arguments with default values MUST go at the end of the argument
list.

A closure declaration looks like the following. Note the placement of
parentheses, commas, spaces, and braces:

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```

Argument lists and variable lists MAY be split across multiple lines, where
each subsequent line is indented once. When doing so, the first item in the
list MUST be on the next line, and there MUST be only one argument or variable
per line.

When the ending list (whether or arguments or variables) is split across
multiple lines, the closing parenthesis and opening brace MUST be placed
together on their own line with one space between them.

The following are examples of closures with and without argument lists and
variable lists split across multiple lines.

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

Note that the formatting rules also apply when the closure is used directly
in a function or method call as an argument.

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```


7. Conclusion
--------------

There are many elements of style and practice intentionally omitted by this
guide. These include but are not limited to:

- Declaration of global variables and global constants

- Declaration of functions

- Operators and assignment

- Inter-line alignment

- Comments and documentation blocks

- Class name prefixes and suffixes

- Best practices

Future recommendations MAY revise and extend this guide to address those or
other elements of style and practice.