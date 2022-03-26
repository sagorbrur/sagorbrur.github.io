---
title: "পাইথনে lambda ফাংশন"
date: 2020-01-21
categories:
  - python
  - bangla
classes: wide
excerpt: পাইথনে `lambda` ফাংশন হলো অজ্ঞাত ফাংশন যেটি একটি অবজেক্ট রিটার্ন
---

পাইথনে `lambda` ফাংশন হলো অজ্ঞাত ফাংশন যেটি একটি অবজেক্ট রিটার্ন করে। </br>
`lambda` ফাংশন যে অবজেক্টটি রিটার্ন করে সেটিকে বড় কোন ফাংশনে কিংবা ভেরিয়েবল হিসেবে ব্যবহার করা হয়।


## **উদাহরণ:**

* যে কোন আর্গুমেন্ট পাস করলে `lambda` ফাংশন সেটির সাথে ১০ যোগ করবে। 

```py
x = lambda a: a + 10
print(x(10))
```

* এডিশন ফাংশন হিসেবে

```py
addition = lambda x, y: x + y
print(addition(10, 20))
```

* স্কয়ার ফাংশন হিসেবে

```py
square = lambda x : x ** 2
print(square(5))
```

## References
1. [https://www.w3schools.com/python/python_lambda.asp](https://www.w3schools.com/python/python_lambda.asp)
2. [https://www.educative.io/edpresso/what-is-a-python-lambda-function?https://www.educative.io/courses/grokking-the-object-oriented-design-interview?aid=5082902844932096&utm_source=google&utm_medium=cpc&utm_campaign=blog-dynamic&gclid=EAIaIQobChMIgJr_4ISU5wIVAh4rCh2Yjg6jEAAYASAAEgK6TPD_BwE](https://www.educative.io/edpresso/what-is-a-python-lambda-function?https://www.educative.io/courses/grokking-the-object-oriented-design-interview?aid=5082902844932096&utm_source=google&utm_medium=cpc&utm_campaign=blog-dynamic&gclid=EAIaIQobChMIgJr_4ISU5wIVAh4rCh2Yjg6jEAAYASAAEgK6TPD_BwE)
3. [https://realpython.com/python-lambda/](https://realpython.com/python-lambda/)
