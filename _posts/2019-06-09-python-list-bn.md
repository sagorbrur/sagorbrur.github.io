---
title: "পাইথনে List"
date: 2019-06-09
categories:
  - python
  - bangla
classes: wide
excerpt: পাইথনে list এক ধরনের কন্টেইনার(পাত্র) হিসেবে কাজ করে, যা একই সঙ্গে অনেকগুলো ডাটা জমা করে রাখতে পারে। সেটের মত লিস্ট সাধারণত সাজানো এবং নির্দিষ্ট গণনাযোগ্য। লিস্ট ইন্ডেক্সিং করা থাকে এবং ইন্ডেক্স শুরু হয় শূন্য থেকে। 
---

পাইথনে list এক ধরনের কন্টেইনার(পাত্র) হিসেবে কাজ করে, যা একই সঙ্গে অনেকগুলো ডাটা জমা করে রাখতে পারে। 
সেটের মত লিস্ট সাধারণত সাজানো এবং নির্দিষ্ট গণনাযোগ্য। লিস্ট ইন্ডেক্সিং করা থাকে এবং ইন্ডেক্স শুরু হয় শূন্য থেকে। 

## List তৈরি

**ফাঁকা লিস্ট** 
```py
>>> list = [] # return an empty list
```

**লিস্টে একই সাথে একাধিক ডাটা টাইপ ভ্যালু থাকতে পারে কিংবা একই প্রকার ডাটা টাইপ থাকতে পারে।** 
```py
>>> squares = [1, 4, 9, 16, 25]
>>> squares
[1, 4, 9, 16, 25]
```
```py

>>> m = [1, 1.2, 'string']
>>> m
[1, 1.2, 'string']
```

**স্ট্রিং এর মত লিস্টকেও ইন্ডেক্সিং করা যায় এবং স্লাইচিং(নির্দিষ্ট অবস্থানে কেটে নেওয়া) করা যায়।**
```py
>>> squares[0]  # indexing returns the item
1
>>> squares[-1]
25
>>> squares[-3:]  # slicing returns a new list
[9, 16, 25]
```

**লিস্টের সাথে নতুন ভ্যালু কনক্যাট করা যায় এবং লিস্ট মিউটেবল(লিস্টের ভীতরের ভ্যালু চেঞ্জ করে দেওয়া যায়।)**
```py
>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

>>> cubes = [1, 8, 27, 65, 125]  # something's wrong here
>>> 4 ** 3  # the cube of 4 is 64, not 65!
64
>>> cubes[3] = 64  # replace the wrong value
>>> cubes
[1, 8, 27, 64, 125]
```

## ডাটা স্ট্রাকচার হিসেবে লিস্ট

ডাটা স্ট্রাকচার হিসেবে লিস্টে আরো কিছু মেথুড আছে। 

### list.append(x)
লিস্টের শেষে কোন আইটেম যোগ করে।

```py
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.append('grape')
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']

```

### list.extend(x)

লিস্টকে আরেকটি লিস্ট অনুযায়ী বর্ধিত করে। 

```py
>>> language = ['French', 'English', 'German']
>>> language1 = ['Spanish', 'Portuguese']
>>> language.extend(language1)
>>> language
['French', 'English', 'German', 'Spanish', 'Portuguese']
```

### list.insert(i, x)

লিস্টের i তম পজিশনে x ভ্যালু ইনসার্ট করার মেথুড এটি। 

```py
>>> vowel = ['a', 'e', 'i', 'u']
>>> vowel.insert(3, 'o')
>>> vowel
['a', 'e', 'i', 'o', 'u']
```

### list.count(x)

লিস্টের x আইটেম সংখ্যা কত আছে তা এই মেথুড দিয়ে বোঝা যাবে। 

```py
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.count('apple')
2
```

### list.reverse()

লিস্টের আইটেমগুলোকে রিভার্স(উল্টা দিকে থেকে) করার মেথুড। 

```py
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.reverse()
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
```
### list.index(x)

x এর অবস্থান কততম তা এই মেথুড রেটার্ন করবে। 

```py
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.index('banana')
3
```

### Stack হিসেবে লিস্টের ব্যবহার

লিস্টকে Stack হিসেবে ডাটা স্ট্রাকচারে ব্যবহার করা যাবে। মূলত স্ট্যাকে দুইটি বিষয় থাকে। **push** এবং **pop**. 
Push করার জন্য আমরা ```list.append``` ব্যবহার করতে পারি আর pop করার জন্য ```list.pop()``` করতে পারি। 

```py
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack.pop()
5
>>> stack
[3, 4]

```


## References
1. [https://docs.python.org/3/tutorial/datastructures.html](https://docs.python.org/3/tutorial/datastructures.html)
2. [https://docs.python.org/3/tutorial/introduction.html#lists](https://docs.python.org/3/tutorial/introduction.html#lists)
