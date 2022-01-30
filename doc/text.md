# The Text Extension

The Text extension provides the following filters:

* `truncate`
* `wordwrap`

## Installation

First, install the Extensions library. Next, add the extension to Twig:

```php
use Twig\Extensions\TextExtension;

$twig->addExtension(new TextExtension());
```

## Wrapping Words

Use the `wordwrap` filter to split your text in lines with equal length.

```twig
{{ "Lorem ipsum dolor sit amet, consectetur adipiscing"|wordwrap(10) }}
```

This example would print:

```
Lorem ipsu
m dolor si
t amet, co
nsectetur
adipiscing
```

The default separator is "\\n", but you can easily change that by providing one:

```twig
{{ "Lorem ipsum dolor sit amet, consectetur adipiscing"|wordwrap(10, "zz\n") }}
```

This would result in:

```
Lorem ipsuzz
m dolor sizz
t amet, cozz
nsectetur zz
adipiscing
```

## Truncating Text

Use the `truncate` filter to cut off a string after limit is reached:

```twig
{{ "Hello World!"|truncate(5) }}
```

The example would output `Hello...`, as `...` is the default separator.

You can also tell truncate to preserve whole words by setting the second parameter to `true`. If the last Word is on the separator, truncate will print out the whole Word.

```twig
{{ "Hello World!"|truncate(7, true) }}
```

Here `Hello World!` would be printed.

If you want to change the separator, just set the third parameter to your desired separator.

```twig
{{ "Hello World!"|truncate(7, false, "??") }}
```

This example would print `Hello W??`.
