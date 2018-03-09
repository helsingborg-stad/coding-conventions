# PHP coding conventions
Specifies how to write PHP. This is simply a summary of how PSR works with some small additions. You may benefit from installing a PSR-2 linter in your editor. 

The platform always requires compability with the previous stable version; For now, version 7.0 of PHP. 

## Example of a complete class
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

## Inline documentation
Inline documentation is required to be above all functions in a class. This documentation should descirbe all parameters that a function can interpret and their type (eg. bool, string). 

It should also describe allowed return values. Whenever possible, you should also define this as a function return type. At the moment, we cannot return multiple types or void due to the compability requirement of php 7.0. 

### Example code: 
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

## Public functions 
All plugins may have some functions that should be swift and easy to implement in other plugins or themes. These function should be placed in a single file called Public.php. This function is the only file containing function that doesn't have to be object orientated. They should however only be wrappers of code contained in classes. 

## Public, Private, Protected functions in classes
In contradiction to PSR coding standards private functions in classes should be prefixed with an "_" to emphasis that the function isen't intended to be used outside the present class definition. This is a relative new requirement that isen't applied in moste cases. We do however have the goal to implement this standard in all classes possible.

## Return types
Always have tha ambition to use return types in your code. We want stuff to break when stuff dosen't return variables as they wehere intended to. This minimizes the number of "wierd" errors that may appear in the platform. 

## Always return as soon as possible
You should always strive to return a result of a function as soon as possible. Also, a default last return should be defined. Eaven in cases where it's obvois that a function will not end up. 

```php
/* DO NOT DO THIS */ 
public function example(string $var) : bool
{
    if($var == "a") {
        return true; 
    } else {
        return false; 
    }
}
```

```php
/* DO LIKE THIS */ 
public function example(string $var) : bool
{
    if($var == "a") {
        return true; 
    }

    return false; 
}
```

## Vendor packages
You may use any vendor package that is required, but it should be implemented as loose as possible (eg. with wrapper functions). This is because there may be a need to replace it in the future. The formatting of vendor packages (PSR/PEAR etc) is not important, but they shoould be object orientated. 

All vendor packages should be reviewed before a requie. This is a very important aspect as they may introduce unsuspected issues in the future. 

## Omitting end tags & shorthands
The end tag ```php ?> ``` should not be used in any case. If you feel the urge to use it, you are proboly doing it wrong. 

The shorthands of php-start ```php <? ``` should not be used in any case. Always use full version of the php start tag ```php <?php ```. 

## Views 
Functions is not allowed in any views, all logic and data fething (including translations) should be done in respective view controller. Using if-statements and for loops should be avioided in views whenever possible, but is a necessety in many cases. 

In a few cases you may want to use php in a view (please don't), then use laravel's built-in php start and end tags @php and @endphp. 

## Class loader
All code should be compatbile with a PSR class loader. No classes should be included manually.

## Initilization of classes
Whenever possible, a __construct of a function should not be done before Wordpress itself has ben initialized. In other words, use a hook when running your code at all times if it dosen't affect performance or common sense. 

# WordPress hooks and filters 
All hooks and filters SHOULD be documentated when created in the readme of the relevant plugin. The should also have a logic format that is coherent with the current namespace. 

For instance, if you want to apply a filter in a controller with the namespace(and classname) "MyAwesomePlugin/Theme/Archive". Then your filer should be named "MyAwesomePlugin/Theme/Archive/varname_affected_by_filter". 

You may not use __NAMESPACE__ to achive this due to bad readability of your code. Again, do not try to be smart, try to be evident. 
