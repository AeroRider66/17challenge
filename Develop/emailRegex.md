# Decoding a Regex Tutorial with Example

At its most basic definition, a Regular Expression (regex) is a sequence of characters that define a specific search pattern.  
The purpose of this tutorial is to show the methodology of breaking an existing regex down to its piece parts, and providing a sample breakdown of an example regex.  Doing this exercise actually serves 2 purposes; the breakdown, but the other purpose is to comprehend a toolset that will also allow the user CREATE a regex.  There is so much data in today's world that it can often be overwhelming just trying to describe what we're looking for, let alone figuring out where that data might be. 

## Summary

This tutorial will provide a breakdown of a specific regex aimed at matching an email.  The regex we will decode is below, and we will describe the elements and meaning of the various parts of a regex.  One note as we start; regex is mostly not dependent on specific single characters.  It is the combinations, and sequences that hold the real power of regex.

'Match an email' regex:
### /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

As we go through this tutorial, we will begin find the meanings we need to decrypt our mystery regex. This tutorial will not cover ALL possible reqex expressions, but we will touch on the ones that we need for our 'mystery regex'.  In order to identify specific characters or groups, I will use the method of splitting apart the regex to focus.

NOTE:  Because of the interactivity of symbols, characters, combinations, sequences and so on, there in not a clear path from start to finish on how to succinctly define how regex's work.  So if it seems I'm jumping around that is true (sort of), but there really is not completely correct sequence to teach regex.

NOTE:  In order to clearly show what is punctuation, and what are actual characters and/or expressions, we will use the format of ('  +  '), that is

open parentheses,apostrophe  <mark>target</mark>   apostrophe, close parentheses 

to indicate the target term/character.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

<mark>+</mark>

### Anchors
Before defining a regex, one piece of knowledge is key.  The forward slash ('  /  ') at the beginning and end are the 'delimiter' that says "everything between us is a regex".  However the 'anchor points'
 are the start and end of a regex...literally - as in the case of our regex. But anchors do not only indicate the beginning and end for the whole regex, they can also be used as anchor points for specific uses within the regex They are the characters that indicate where the beginning and end of a regex are, but not JUST for the entire regex.  They are also used as anchors in the content of a regex as well, sort of indicating the start and end of other things, such as a string that is a specific word. Additionally, in combination with other characters they can be used for other defining expressions. They are called metacharacters, and there are many of those in regex. (   . $ ^ { [ ( | ) * + ? \    )

### Quantifiers
In regex, a quantifier is an expression that tells how many times a previous character or group of characters can or must be matched.  There are a few quantifiers that exist in our expression so lets look at them:
###       /^([a-z0-9_\.-] <mark>+</mark> )@([\da-z\.-]   <mark>+</mark>   )\.([a-z\.]   <mark>{2,6}</mark>    )$/
In our regex we have 2 addition ('  +  ') signs, and a set of curly bracket with numbers inside of them ('  {2,6}  ').  The (' + ') sign says that the previous character must occur at least 1 or more times. The (' {2,6} ') is saying that the previous character must occur at least 2 times, but no more than 6 times.  Notice that all three of these quantifiers follow a (' ] ') symbol.   

### Grouping Constructs
Grouping is very important in regex, and provides for clear delineation of a mix of symbols or a sequence that must occur (or not occur).  Groups are enclosed patterns within a set of parentheses.  For example:
#### <mark>(xyz)</mark> 
is a group of the letters x,y,z and specifically in that order.  So the grouping 'xyz' meets that criteria, whereas 'yz' or 'zxy' do not.

### Bracket Expressions
Bracket expressions are a list of characters enclosed within square brackets (' [ ' and ' ] '), and are used to compare a single character and check if it matches. 
The expression here is looking for any of the characters within the bracket: 
### <mark>[abcd]</mark>
so, an 'a', 'b', 'c' or 'd' , and specifically the lower case letters would satisfy that expression. 
Many other bracket expressions exist, such as those that indicate a character within a range of characters (' [1-7] ') = numbers between 1 and 7, inclusive.

### Character Classes
Character classes are a subset of the bracket expressions, and consist of sets of predefined expressions.  Examples of this are 
### <mark>[:lower:]</mark>  
which indicates alphabetic characters that are lower case, or
### <mark>[:digit:]</mark>
which indicates numerical characters.

### The OR Operator
As one might expect, regex offers logical operators and operations as well. A specific operator (' | ' sometimes called the 'pipe' operator) is contained in the regex symbols, but there are many ways to perform the logical OR operation.  Here are a couple of examples:

a|b|c
can also be represented as
[abc]

Both of the above expressions are interpreted as "a OR b OR c". Depending on the complexity of the expression will help show what is the better (more efficient) method

### Flags
Regex also uses special parameters to modify the regex searches. These parameters are called flags, and there are only 6 of them in regex in general, but regex used in programming languages may have additional flags available, but in general those are for very specific cases.  Defining how each flag works is beyond the scope of this tutorial. 
Flags are added at the end of a regex expression, and come after the final ('  /  ') symbol.  As one of the most used of the flags, the letter ('  i  ') is well known and almost everyone has used it (even though you may not have recognized it).  
The ('  i  ') flag is used to make the preceding expression case insensitive.  Letters that are contained in the expression are treated the same, regardless of whether they are upper- or lower-case.  The most common usage of this flag are email addresses.  
From an email address point, the email MyNameIsFred@gmail.com will be read the same as MYNAMEISFRED@gmail.com which will be read the same as mynameisfred@gmail.com.  

### Character Escapes
Escaped characters in regular expressions are used for specific characters that have special meanings.  In the case of the special characters used in regex expressions, there are times when we need the actual literal of the character.  Character escapes are managed by add the backslash ('  \  ') symbol. So, in the case of the arithmetic plus sign, we have seen above that it is used to indicate that the previous character must occur one or more times.  However, there are times when we want to used the literal plus sign.  In order to do that, we use a character escape.  
In an expression:
...[f]+... is indicating that the letter ('  f  ') must occur one or more times.  
As a escape character, we would use:
...[\+] to show that we are looking for the use of the literal plus sign.
There are several common escaped characters in REGEX. These include \., \\, \+, \*, \?, \^, \$, \(, \), \[, \], \{, and \}. Each of these characters has a special meaning within a regular expression, and escaping them allows for their literal use.

## Our Mystery Redex
So what does our mystery redex say?  Let's see:

### /^ (  [a-z0-9_\.-] + )  @ ( [\da-z\.-]  +) \.([a-z\.] {2,6}) $/

Our first grouping is:
#### ( [a-z0-9_\.-] + )
within this group we have a character set  
#### [a-z0-9_\.-]
This can be decoded to say in words "Match any character in the set"  of a-z == 0-9 == _ == \. == -  (separated by ==)

followed by the plus character
#### ( [...] + )
which adds the quantifier of "match ONE OR MORE of the preceding"

the 
#### @
adds on the caveat of "and exactly match @" for that character

the next grouping is
#### ( [\da-z\.-]  +)

the character set is
#### [\da-z\.-]
and is once again followed by the
#### +
So we can read that as "match"




## Author

As I grew up, I noticed that I didn't see the world the same as many others did.  I saw cause-effect, I analyzed criteria of events around me, I even looked at math as 'fun'!  I think that seeing the world and its associated connectivity led me down the road to become an engineer, and now someone who is becoming a developer.  I'm looking forward to a bright future, and I hope you have enjoyed this brief look at this key aspect that every coder will use.
Drop by and visit me at
