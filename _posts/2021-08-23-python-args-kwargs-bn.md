---
title: "পাইথনে *args এবং **kwargs"
date: 2021-08-23
categories:
  - python
  - bangla
classes: wide
excerpt: পাইথন ফাংশনে আমরা যদি আর্গুমেন্টের সংখ্যা সম্পর্কে অবগত না থাকি তবে আমরা দুই ধরণের স্পেশাল আর্গুমেন্ট পাস করাতে পারি।
---

পাইথন ফাংশনে আমরা যদি আর্গুমেন্টের সংখ্যা সম্পর্কে অবগত না থাকি তবে আমরা দুই ধরণের স্পেশাল আর্গুমেন্ট পাস করাতে পারি।

- __*args__
- __**kwargs__

## *args
কোন ফাংশনে আমরা যদি ভেরিয়েবল সংখ্যক নন-কিওয়ার্ড আর্গুমেন্ট পাস করাতে চাই সেক্ষেত্রে *args ব্যবহার করতে হবে।

__নন-কিওয়ার্ড আর্গুমেন্ট (non-keyword argument)__: যে সকল আর্গুমেন্টের সাথে আইডেন্টিফায়ার থাকেনা সেগুলোকে নন-কিওয়ার্ড আর্গুমেন্ট বলে।
যেমনঃ 
```py 
def add(name, age): return name, age
``` 
এই ফাংশনে name, age কি ধরণের আর্গুমেন্ট আমরা জানিনা।

__*args__ উদাহরণঃ
```py
def add(*args):
  total = 0
  for arg in args:
    total += arg
  return total

total = add(1, 2, 3, 4, 5)
# output: 15

```

## **kwargs
কোন ফাংশনে আমরা যদি ভেরিয়েবল সংখ্যক কিওয়ার্ড আর্গুমেন্ট পাস করাতে চাই সেক্ষেত্রে **kwargs ব্যবহার করতে হবে।

__কিওয়ার্ড আর্গুমেন্ট(keyword argument)__: যে সকল আর্গুমেন্টের সাথে আইডেন্টিফায়ার থাকে সেগুলোকে কিওয়ার্ড আর্গুমেন্ট বলে।
যেমনঃ 
```py
def add(name="John", age=20): return name, age
```
এই ফাংশনে name, age কি ধরণের আর্গুমেন্ট আমরা জানি।

__**kwargs__ উদাহরণঃ
```py
def user(**kwargs):
    for k, v in kwargs.items():
        print(f"{k}: {v}")

user(name="John", age=22, email="example@gmail.com")
# output:
# name: John
# age: 22
# email: example@gmail.com

```


  


