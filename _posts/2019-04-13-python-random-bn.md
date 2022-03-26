---
title: "পাইথনে Random"
date: 2019-04-13
categories:
  - python
  - bangla
classes: wide
excerpt: দৈবভাবে কোন নাম্বার চয়ন করা, দৈবভাবে কোন নাম্বার জেনারেট করা ইত্যাদি কাজের জন্য পাইথনে random মডুউলটি ব্যবহার করা হয়। এটি পাইথনের স্টানডার্ট লাইব্রেরির একটি মডুউল।
---

দৈবভাবে কোন নাম্বার চয়ন করা, দৈবভাবে কোন নাম্বার জেনারেট করা ইত্যাদি কাজের জন্য পাইথনে random মডুউলটি ব্যবহার করা হয়। 
এটি পাইথনের স্টানডার্ট লাইব্রেরির একটি মডুউল। 

# উদাহরণ

```py
>>>import random
>>> random.random()                             # Random float:  0.0 <= x < 1.0
0.37444887175646646

>>> random.uniform(2.5, 10.0)                   # Random float:  2.5 <= x < 10.0
3.1800146073117523

>>> random.expovariate(1 / 5)                   # Interval between arrivals averaging 5 seconds
5.148957571865031

>>> random.randrange(10)                        # Integer from 0 to 9 inclusive
7

>>> random.randrange(0, 101, 2)                 # Even integer from 0 to 100 inclusive
26

>>> random.choice(['win', 'lose', 'draw'])      # Single random element from a sequence
'draw'

>>> deck = 'ace two three four'.split()
>>> random.shuffle(deck)                        # Shuffle a list
>>> deck
['four', 'two', 'ace', 'three']

>>> random.sample([10, 20, 30, 40, 50], k=4)    # Four samples without replacement
[40, 10, 50, 30]

```


## রেফারেন্স লিংক
১। [https://docs.python.org/3.6/library/random.html](https://docs.python.org/3.6/library/random.html)
