# Notes on Regular Expressions

Using regular expressions is great when you want to match patterns, aka find something that matches a pattern you're looking for.

For me, the pattern I'm looking for at the moment is a book's publication date so I can calculate how many days it's been since a book came out.

So take these two date strings for instance:

  April 4, 1900
  December 25, 1984

They're different lengths. Have different values and mean different things.

But they're both dates.

Each string will compute as date and parse out to a time code using Date.parse()

  var time1 = Date.parse(April 4, 1900);
  console.log(time1);

  var tim2 = Date.parse(December 25, 1984);
  console.log(time2);

But if we think about what each of these date strings specifically have in common we can create a pattern we can search for using RegEx.

Each date string is a word, followed by a space, followed by an either 1 or 2-digit number, followed by a comma character, followed by a space character, followed by a 4-digit number.

By looking at our RegEx snippets, we can see that this pattern would use snippets to find word characters (\w), an imprecise number of them `(*)`, a space (\s), a digit (\d), that's either a 1 or two-digit number ({1,2}) a comma ([,]), another space (\s), and a exact number of digits (\d{4}).

Using these RegEx snippets, we can simply combine these to find any date strings matching this pattern on our page.

  \w*\s\d{1,2}[,]\s\d{4}

## Replacing text using Regex

You can replace groups of text uisng Regex when you group your RegEx expressions.

You form groups of RegEx expressions by adding parentheses around RegEx snippets.

Groups of regex expressions can be called using the "$" symbol and indexed using integers starting with 1.

For instance if you wanted to replace a 10-digit phone number such as 1-212-555-1234 with a 7-digit number such as 555-1234, you could match the RegEx pattern using:

    (\d[-]\d{3}[-.])(\d{3}[-.])(\d{4})

And then you could replace this string using second and third RegEx groups:

  $2$3
