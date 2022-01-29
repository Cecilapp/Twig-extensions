# The Intl Extension

The *Intl* extensions provides the `localizeddate`, `localizednumber` and `localizedcurrency` filters.

## Installation

First, install the Extensions library. Next, add the extension to Twig:

```php
use Twig\Extensions\IntlExtension;

$twig->addExtension(new IntlExtension());
```

## `localizeddate`

Use the `localizeddate` filter to format dates into a localized string representating the date.

```twig
{{ post.published_at|localizeddate('medium', 'none', locale) }}
```

The `localizeddate` filter accepts strings (it must be in a format supported by the [`strtotime`] function), [`DateTime`] instances, or [`Unix timestamps`].

> Internally, Twig uses the PHP [`IntlDateFormatter::create()`]function for the date.

## Arguments

* `date_format`: The date format. Choose one of these formats:

  * `none`: [`IntlDateFormatter::NONE`]
  * `short`: [`IntlDateFormatter::SHORT`]
  * `medium`: [`IntlDateFormatter::MEDIUM`]
  * `long`: [`IntlDateFormatter::LONG`]
  * `full`: [`IntlDateFormatter::FULL`]

* `time_format`: The time format. Same formats possible as above.
* `locale`: The locale used for the format. If `NULL` is given, Twig will use [`Locale::getDefault()`]
* `timezone`: The date timezone
* `format`: Optional pattern to use when formatting or parsing. Possible patterns are documented in the [`ICU user guide`].
* `calendar`: Calendar to use for formatting. The default value is `gregorian`, which corresponds to [`IntlDateFormatter::GREGORIAN`]. Choose one of these formats:

  * `gregorian`: [`IntlDateFormatter::GREGORIAN`]
  * `traditional`: [`IntlDateFormatter::TRADITIONAL`]

For the following calendars should use 'traditional':

 * Japanese
 * Buddhist
 * Chinese
 * Persian
 * Indian
 * Islamic
 * Hebrew
 * Coptic
 * Ethiopic

Also for non-Gregorian calendars need to be specified in locale.  
Examples might include `locale="fa_IR@calendar=PERSIAN"`.

## `localizednumber`

Use the `localizednumber` filter to format numbers into a localized string representating the number.

```twig
{{ product.quantity|localizednumber }}
```

> Internally, Twig uses the PHP [`NumberFormatter::create()`] function for the number.

## Arguments

* `style`: Optional number format (default: `decimal`). Choose one of these formats:

  * `decimal`: [`NumberFormatter::DECIMAL`]
  * `currency`: [`NumberFormatter::CURRENCY`]
  * `percent`: [`NumberFormatter::PERCENT`]
  * `scientific`: [`NumberFormatter::SCIENTIFIC`]
  * `spellout`: [`NumberFormatter::SPELLOUT`]
  * `ordinal`: [`NumberFormatter::ORDINAL`]
  * `duration`: [`NumberFormatter::DURATION`]

* `type`: Optional formatting type to use (default: `default`). Choose one of these types:

  * `default`: [`NumberFormatter::TYPE_DEFAULT`]
  * `int32`: [`NumberFormatter::TYPE_INT32`]
  * `int64`: [`NumberFormatter::TYPE_INT64`]
  * `double`: [`NumberFormatter::TYPE_DOUBLE`]
  * `currency`: [`NumberFormatter::TYPE_CURRENCY`]

* `locale`: The locale used for the format. If `NULL` is given, Twig will use `Locale::getDefault()`

## `localizedcurrency`

Use the `localizedcurrency` filter to format a currency value into a localized string.

```twig
{{ product.price|localizedcurrency('EUR') }}
```

> Internally, Twig uses the PHP [`NumberFormatter::create()`] function for the number.

## Arguments

* `currency`: The 3-letter ISO 4217 currency code indicating the currency to use.
* `locale`: The locale used for the format. If `NULL` is given, Twig will use `Locale::getDefault()`

[`strtotime`]: http://php.net/strtotime
[`DateTime`]: http://php.net/DateTime
[`Unix timestamps`]: http://en.wikipedia.org/wiki/Unix_time
[`IntlDateFormatter::create()`]: http://php.net/manual/en/intldateformatter.create.php
[`IntlDateFormatter::NONE`]: http://php.net/manual/en/class.intldateformatter.php#intldateformatter.constants.none
[`IntlDateFormatter::SHORT`]: http://php.net/manual/en/class.intldateformatter.php#intldateformatter.constants.short
[`IntlDateFormatter::MEDIUM`]: http://php.net/manual/en/class.intldateformatter.php#intldateformatter.constants.medium
[`IntlDateFormatter::LONG`]: http://php.net/manual/en/class.intldateformatter.php#intldateformatter.constants.long
[`IntlDateFormatter::FULL`]: http://php.net/manual/en/class.intldateformatter.php#intldateformatter.constants.full
[`IntlDateFormatter::GREGORIAN`]: http://php.net/IntlDateFormatter#intldateformatter.constants.gregorian
[`IntlDateFormatter::TRADITIONAL`]: http://php.net/IntlDateFormatter#intldateformatter.constants.traditional
[`ICU user guide`]: http://userguide.icu-project.org/formatparse/datetime
[`NumberFormatter::create()`]: http://php.net/manual/en/numberformatter.create.php
[`NumberFormatter::DECIMAL`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.decimal
[`NumberFormatter::CURRENCY`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.currency
[`NumberFormatter::PERCENT`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.percent
[`NumberFormatter::SCIENTIFIC`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.scientific
[`NumberFormatter::SPELLOUT`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.spellout
[`NumberFormatter::ORDINAL`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.ordinal
[`NumberFormatter::DURATION`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.duration
[`NumberFormatter::TYPE_DEFAULT`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.type-default
[`NumberFormatter::TYPE_INT32`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.type-int32
[`NumberFormatter::TYPE_INT64`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.type-int64
[`NumberFormatter::TYPE_DOUBLE`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.type-double
[`NumberFormatter::TYPE_CURRENCY`]: http://php.net/manual/en/class.numberformatter.php#numberformatter.constants.type-currency
