# All About RegEx

Introductory paragraph (replace this with your text)

Regular Expressions (RegEx) are objects in js that match character combinations in a string to create search patterns which can be used for search and replace functionalities.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

I will be explaining and demoing a replace regex. Please see my code below.

<!--
<!DOCTYPE html>
<html>

<body>

<h2>RegEx Replace</h2>

<p>Replace "Replaceable" with "Valuable" below</p>

<button onclick="myFunction()">Replace!</button>

<p id="demo">You are Replaceable!</p>

<script>
function myFunction() {
  let text = document.getElementById("demo").innerHTML;
  document.getElementById("demo").innerHTML =
  text.replace(/Replaceable/i, "Valued");
}
</script>

</body>
</html>
-->

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

anchors allow you to match a position before or after characters. Use "^" to match a position at the beginning of the string and "$" to match a position at the end of the string, you can use "m" to match the beginning or the end of the string as well as the beginning or the end of lines.

EXAMPLE:

<!--
let str = 'You Are Cute';
console.log(/$e/.test(str));
-->

this will be true because my last character in my string is "e" you can use these beginning and ending anchors to ensure that your string fully matches the desired pattern.

### Quantifiers

Quantifiers in RegEx match the number of instances or a character, group, or character class within a string. See below for a table from www.javascripttutorial.net laying out the most commonly used quantifiers in regards to RegEx + some others I found useful and have added to the table below

<!--
Quantifier Description
*         Match zero or more times.
+          Match one or more times.
?          Match zero or one time.
{ n }      Match exactly n times.
{ n ,}     Match at least n times.
{ n , m }  Match from n to m times.
/\d{2}/    Match a 2 digit number (can be any digit number)
-->

### OR Operator

The OR Operator is shown using a vertical line "|" and represents an or statement.

EXAMPLE (using time):
accepts multiple time values but makes sure fake times are not logged

<!---
let regexp = /([01]\d|2[0-3]):[0-5]\d/g;
console.log("00:00 11:11 23:59 26:99 1:2".match(regexp)); // 00:00,10:10,23:59
--->

### Character Classes

Character classes are specific notation that match all symbols of a certain set.
Please see some common uses below

<!---
table from https://docs.oracle.com/javase/tutorial/essential/regex/char_classes.html
Construct	Description
[abc]	a, b, or c (simple class)
[^abc]	Any character except a, b, or c (negation)
[a-zA-Z]	a through z, or A through Z, inclusive (range)
[a-d[m-p]]	a through d, or m through p: [a-dm-p] (union)
[a-z&&[def]]	d, e, or f (intersection)
[a-z&&[^bc]]	a through z, except for b and c: [ad-z] (subtraction)
[a-z&&[^m-p]]	a through z, and not m through p: [a-lq-z] (subtraction)
-->

PHONE NUMBER EXAMPLE from https://javascript.info/regexp-character-classes

<!--
let str = "+7(903)-123-45-67";

let regexp = /\d/g;

alert( str.match(regexp) ); // array of matches: 7,9,0,3,1,2,3,4,5,6,7

// let's make the digits-only phone number of them:
alert( str.match(regexp).join('') ); // 79031234567
-->

^extracts all numbres from the phone number without any other characters / symbols +() etc

### Flags

flags are optional in a RegEx function there are 6 available options in js which I have listed below
https://javascript.info/regexp-introduction
i - With this flag the search is case-insensitive: no difference between A and a (see the example below).
g - With this flag the search looks for all matches, without it – only the first match is returned.
m - Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").
s - Enables “dotall” mode, that allows a dot . to match newline character \n (covered in the chapter Character classes).
u - Enables full Unicode support. The flag enables correct processing of surrogate pairs.
y - “Sticky” mode: searching at the exact position in the text (covered in the chapter Sticky flag "y", searching at position)

EXAMPLE: (using the g flag)

<!--
let str = "she sells sea shells by the sea shore";

alert( str.match(/sea/gi) );

// sea,sea (an array of 2 substrings that match)
-->

### Grouping and Capturing

https://www.codingame.com/playgrounds/218/regular-expressions-basics/groups-capturing-groups

Groups are shown using () and are useful when creating blocks of patterns so you can apply repetitions or other modifiers to them, they are also useful for processing parts of a match like extracting or replacing data.
EXAMPLE:
pattern1(pattern2)pattern3

^you'll capture the results of pattern2 for later use but not pattern1 or pattern3. This showcases the extraction ability of this RegEx Capture/Grouping

### Bracket Expressions

https://javascript.plainenglish.io/regular-expressions-brackets-f2d6f69ffe13
Brackets indicate a set of characters to match. Any individual character between the brackets will match you can use a hyphen to define a set
EXAMPLE:
'apple'.match(/[a-d]/) // -> matches 'a'
'apple'.match(/[A-D]/) // -> no match (because no capitals)
'apple'.match(/[A-D]/i) // -> matches 'a' (becuase it is case insensitive due to the "i")

### Greedy and Lazy Match

https://javascript.info/regexp-greedy-and-lazy
In the greedy mode (by default) a quantified character is repeated as many times as possible.
The regexp engine adds to the match as many characters as it can for .+, and then shortens that one by one, if the rest of the pattern doesn’t match.

The lazy mode of quantifiers is an opposite to the greedy mode. It means: “repeat minimal number of times”.
We can enable it by putting a question mark '?' after the quantifier, so that it becomes +?

### Boundaries

https://javascript.info/regexp-boundary
Boundary represented by \b is used as a test to check that the position of the string is a word boundary
There are three different positions that qualify as word boundaries:
At string start, if the first string character is a word character \w.
Between two characters in the string, where one is a word character \w and the other is not.
At string end, if the last string character is a word character \w

### Back-references

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Groups_and_Backreferences
Backreferences refer to a previously captured group in the same regular expression.

### Look-ahead and Look-behind

https://javascript.info/regexp-lookahead-lookbehind
Look-Ahead
The syntax for a positive is: X(?=Y), it means "look for X, but match only if followed by Y". There may be any pattern instead of X and Y.
The syntax for a negative is: X(?!Y), it means "search X, but only if not followed by Y".

Look-Behind
Lookahead allows to add a condition for “what follows" while Lookbehind is similar but different in that it looks behind. Look behind allows a pattern to match only if there’s something before it.

The syntax is:
Positive lookbehind: (?<=Y)X, matches X, but only if there’s Y before it.
Negative lookbehind: (?<!Y)X, matches X, but only if there’s no Y before it.

## Author

Emily is new to web development while she has basic compsci training from college her career took her in other directions and now she is finding her way back to tech. Please check out some of her work here https://github.com/emismol
