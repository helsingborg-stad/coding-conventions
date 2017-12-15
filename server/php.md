# PHP coding conventions
Specifies how to write PHP. This is simply a summary of how PSR works with some small additions. You may benefit from installing a PSR-2 linter in your editor. 

The platform always requires compability with the prevois stable versoion; For now, version 7.0 PHP. 

# Example of a complete class
```php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleMethod($a, $b = null)
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

# Inline documentation
Inline documentation is required to be above all functions in a class. This documentation should descirbe all parameters that a function can interpret and their type (eg. bool, string). 

It should also describe allowed return values. Whenever possible, you should also define this as a function return type. At the moment, we cannot return multiple types or void due to the compability requirement of php 7.0. 

## Example code: 
```php
/**
 * Install procedure
 * @param  string $language Language to install
 * @return bool
 */
public static function install(string $language) : bool
{
    do_action('wp-content-translator/option/install', $language);
    return true;
}
```

# Public functions 
All plugins may have some functions that should be swift and easy to implement in other plugins or themes. These function should be placed in a single file called Public.php. This function is the only file containing function that doesn't have to be object orientated.

# Vendor packages
You may use any vendor package that is required, but it should be implemented as loose as possible (eg. with wrapper functions). This is because there may be a need to replace it in the future. 

# Omitting end tags & shorthands
The end tag ```php ?> ``` should not be used in any case. If you feel the urge to use it, you are proboly doing it wrong. 

The shorthands of php-start ```php <? ``` should not be used in any case. Always use full version of the php start tag ```php <?php ```. 

# Views 
Functions is not allowed in any views, all logic and data fething (including translations) should be done in respective view controller. Using if-statements and for loops should be avioided in views whenever possible, but is a necessety in many cases. 
