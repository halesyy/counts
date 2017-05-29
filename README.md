# How to use Counts
Counts is a static class that allows you to quickly parse strings and get data on them, the data is customized to what **you** want, with no opinions.

You're able to start using the Counts class by requiring in the single file. *Composer support coming soon*.

```php
  require "Counts.php";
  // Counts::... now available.
```

Counts uses something called **indicators**, which are things you want to search for in a string. It allows you to quickly see how many *commas*, *semicolons*, or any other substring in your searching string. You can set your indicators using the appropriate function:

```php
  Counts::SetIndicator([
    ',', ':', '@', '<<'
  ]);
```

After you have the indicators you want to use when searching your string, you're able to start managing strings and writing extensive parsers!

In this example we're checking if a string contains `<<` which dictates calling a function in our parser.

```php
  // Testing if string calling a @function << method.
  $c    = Counts::count($line);
  $line = 'opt << You like Jazz, bruce?'

  if ($c['<<'] == 1) {
    $function = $c['word_0'];
    $param    = explode('<<', $line)[1];
  }
```

Using that, we've parsed a potential line using only 6 lines of code. This could be refined even further thou it's better to use a more clear representation of code than compressed jargon.

We used a key in the `$c` variable named `word_0`, this refers to being able to easily reference words from the split done to give you more ease when using a single class call and not multiple.
