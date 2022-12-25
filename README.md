# Composer plugin allowing you to extend any vendor class

So.. some people might think it's easier to extend just the 10 row
method you're patching instead of copying the whole 1000+ row file over
to your local namespace and whatever else bullshit you're forced
to endure if you do not follow the OneTrueParadigm IoC.

So for real world people, with real world problems - you are welcome!


example conf (root level of any composer.json file, root or vendor):

```json
"autoload": {
    "psr-4": {
        "Buggy\\Namespace\\": "path/to/FixedNamespace/"
    }
},
"extra": {
    "composer-extend-class": {
        "path/to/BuggyClass.php": "path/to/FixedClass.php",
        "path/to/AnotherBuggyClass.php": {
            "path": "path/to/AnotherFixedClass.php",
            "createOldFile": true
        }
    }
},
```

You can now extend the original class e.g. FixedClass.php:
```php
namespace Buggy\Namespace; // Use the original namespace

class BuggyClass extends BuggyClass_0R1giN4L // Extend original class name + _0R1giN4L
{
    public function brokenFunction($payload)
    {
        return $payload * 100;
    }
}
```

Simple as that. Old class file will be copied and source altered for it to have
the new unique class name of "Class_0R1giN4L" but same old namespace.

Not quality checked code, no tests, no warranty. Copyleft KludgeWorks LLC.

# Don't forget
To gitignore the generated *_0R1giN4L.php files.php
