---
layout: recipe
title: Python f-string Hacks
language: python
author: Andrew Rohne
libraries-needed: 
category: Data Visualization
---

This is reformatted from a (Reddit post)[https://www.reddit.com/r/Python/comments/17hgu5o/you_should_know_these_fstring_tricks/] with some additions.

number = 150

decimal places to n -> .nf
`print(f"number: {number:.2f}") number: 150.00`

hex conversion
`print(f"hex: {number:#0x}") hex: 0x96`

binary conversion
`print(f"binary: {number:b}") binary: 10010110`

octal conversion
`print(f"octal: {number:o}") octal: 226`

scientific notation
`print(f"scientific: {number:e}") scientific: 1.500000e+02`

total number of characters
`print(f"Number: {number:09}") Number: 000000150`

number with commas
```
number = 1234567
print(f"Number: {number:,})
```

ratio = 1 / 2

percentage with 2 decimal places
`print(f"percentage = {ratio:.2%}") percentage = 50.00% `

2. Stop writing print(f”var = {var}”)
This is the debug feature with f-strings. This is known as self-documenting expression released in Python 3.8 .

```
a, b = 5, 15 print(f"a = {a}") # Doing this ? a = 5

# Do this instead.
print(f"{a = }") a = 5

# Arithmatic operations
print(f"{a + b = }") a + b = 20

# with formatting
print(f"{a + b = :.2f}") a + b = 20.00 
```

3. Date formatting
You can do strftime() formattings from f-string. 

``` 
import datetime

today = datetime.datetime.now() print(f"datetime : {today}") datetime : 2023-10-27 11:05:40.282314

print(f"date time: {today:%m/%d/%Y %H:%M:%S}") date time: 10/27/2023 11:05:40

print(f"date: {today:%m/%d/%Y}") date: 10/27/2023

print(f"time: {today:%H:%M:%S %p}") time: 11:05:40 AM ```

4. String Formatting
The string formatting specifiers are all about padding and alignment.

The specifier is :{chr}{alignment}{N}

Here, {chr} is the character to be filled with. (default = space)

alignment signs : left(<)[default], right(>), center(^)

N is the number of characters in resulting string. ```

name = 'deep' a, b, c = "-", "", 10

f"{name:10}" 'deep ' f"{name:<10}" 'deep ' f"{name:>10}" ' deep' f"{name:10}" ' deep '

f"{name:!<10}" 'deep!!!!!!' f"{name:{a}{b}{c}}" '---deep---' ```

5. Value Conversion
These modifiers can be used to convert the value.

'!a' applies ascii(), '!s' applies str(), and '!r' applies repr().
This action happens before the formatting.

Let's take a class Person. ``` class Person: def init(self, name): self.name = name

def __str__(self):
    return f"I am {self.name}."

def __repr__(self):
    return f'Person("{self.name}")'
Now if we do :

me = Person("Deep")

f"{me}" 'I am Deep.' f"{me!s}" 'I am Deep.' f"{me!r}" 'Person("Deep")'

emj = "😊"

f"{emj!a}" "'\U0001f60a'" ```