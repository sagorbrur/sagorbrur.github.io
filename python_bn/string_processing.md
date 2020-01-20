# Python String Processing Tricks and Tips

## Stripping Whitepsace

```py
s = '   This is a sentence with whitespace.       \n'

print('Strip leading whitespace: {}'.format(s.lstrip()))
print('Strip trailing whitespace: {}'.format(s.rstrip()))
print('Strip all whitespace: {}'.format(s.strip()))
```
```
Strip leading whitespace: This is a sentence with whitespace.       

Strip trailing whitespace:    This is a sentence with whitespace.
Strip all whitespace: This is a sentence with whitespace.
```

Striping unwanted characters

```py
s = 'This is a sentence with unwanted characters.AAAAAAAA'
print('Strip unwanted characters: {}'.format(s.rstrip('A')))
```
```
Strip unwanted characters: This is a sentence with unwanted characters.
```

## Spliting Strings

```py
s = 'KDnuggets is a fantastic resource'

print(s.split())
```
```
['KDnuggets', 'is', 'a', 'fantastic', 'resource']
```

```py
s = 'these,words,are,separated,by,comma'
print('\',\' separated split -> {}'.format(s.split(',')))

s = 'abacbdebfgbhhgbabddba'
print('\'b\' separated split -> {}'.format(s.split('b')))
```
```
',' separated split -> ['these', 'words', 'are', 'separated', 'by', 'comma']
'b' separated split -> ['a', 'ac', 'de', 'fg', 'hhg', 'a', 'dd', 'a']
```
## Joining List Elements Into a String
```py
s = ['KDnuggets', 'is', 'a', 'fantastic', 'resource']

print(' '.join(s))
```
```
KDnuggets is a fantastic resource
```

```py
s = ['Eleven', 'Mike', 'Dustin', 'Lucas', 'Will']

print(' and '.join(s))
```
```
Eleven and Mike and Dustin and Lucas and Will
```

## Reversing a String
```py
s = 'KDnuggets'

print('The reverse of KDnuggets is {}'.format(s[::-1]))
```
```
The reverse of KDnuggets is: steggunDK
```

## Converting Uppercase and Lowercase
```py
s = 'KDnuggets'

print('\'KDnuggets\' as uppercase: {}'.format(s.upper()))
print('\'KDnuggets\' as lowercase: {}'.format(s.lower()))
print('\'KDnuggets\' as swapped case: {}'.format(s.swapcase()))
```
```
'KDnuggets' as uppercase: KDNUGGETS
'KDnuggets' as lowercase: kdnuggets
'KDnuggets' as swapped case: kdNUGGETS
```

## Checking for String Membership
```py
s1 = 'perpendicular'
s2 = 'pen'
s3 = 'pep'

print('\'pen\' in \'perpendicular\' -> {}'.format(s2 in s1))
print('\'pep\' in \'perpendicular\' -> {}'.format(s3 in s1))
```
```
'pen' in 'perpendicular' -> True
'pep' in 'perpendicular' -> False
```
```py
s = 'Does this string contain a substring?'

print('\'string\' location -> {}'.format(s.find('string')))
print('\'spring\' location -> {}'.format(s.find('spring')))
```
```
'string' location -> 10
'spring' location -> -1
```

## Replacing Substrings
```py
s1 = 'The theory of data science is of the utmost importance.'
s2 = 'practice'

print('The new sentence: {}'.format(s1.replace('theory', s2)))
```
```
The new sentence: The practice of data science is of the utmost importance.
```

## Combining the Output of Multiple Lists
```py
countries = ['USA', 'Canada', 'UK', 'Australia']
cities = ['Washington', 'Ottawa', 'London', 'Canberra']

for x, y in zip(countries, cities):
  print('The capital of {} is {}.'.format(x, y))
```
```
The capital of USA is Washington.
The capital of Canada is Ottawa.
The capital of UK is London.
The capital of Australia is Canberra.
```

## Checking for Anagrams
```py
from collections import Counter
def is_anagram(s1, s2):
  return Counter(s1) == Counter(s2)

s1 = 'listen'
s2 = 'silent'
s3 = 'runner'
s4 = 'neuron'

print('\'listen\' is an anagram of \'silent\' -> {}'.format(is_anagram(s1, s2)))
print('\'runner\' is an anagram of \'neuron\' -> {}'.format(is_anagram(s3, s4)))
```
```
'listen' an anagram of 'silent' -> True
'runner' an anagram of 'neuron' -> False
```

## Checking for Palindromes
```py
def is_palindrome(s):
  reverse = s[::-1]
  if (s == reverse):
    return True
  return False

s1 = 'racecar'
s2 = 'hippopotamus'

print('\'racecar\' a palindrome -> {}'.format(is_palindrome(s1)))
print('\'hippopotamus\' a palindrome -> {}'.format(is_palindrome(s2)))
```
```
'racecar' is a palindrome -> True
'hippopotamus' is a palindrome -> False
```

# Reference
* Tips and Tricks copied from [kdnuggets](https://www.kdnuggets.com/2020/01/python-string-processing-primer.html)

