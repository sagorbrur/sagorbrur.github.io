---
title: "পাইথনে pathlib"
date: 2022-09-23
categories:
  - python
  - bangla
classes: wide
excerpt: This blog describe about path
---
আপনি যে পাইথন প্যাকেজ নিয়ে কাজ করছেন সেটা যদি অপারেটিং সিস্টেম ইন্ডেপেনডেন্ট করতে চান তবে অবশ্যই যে ঝামেলায় পড়বেন সেটা হলো ফাইল পাথ সমস্যা। আমরা যারা লিনাক্সে কাজ করি তারা মূলত ফাইল পাথ গুলো `path/mypath/file.py` এভাবে লিখে থাকি। কিন্তু একই পাথ যদি আপনি উইন্ডোজ অপারেটিং সিস্টেমে কাজ করাতে চান তবে `path\mypath\file.py` আকারে লিখতে  হবে। 
আর সমস্যা তৈরি হয় এখানেই। আমাদের প্যাকেজকে তাই OS ভিত্তিক এই সমস্যামুক্ত করতে আমাদের ব্যবহার করতে হবে __pathlib__. যেটি মূলত পাইথনে স্ট্যান্ডার্ড লাইব্রেরির অন্তর্ভুক্ত আছে।

## pathlib এর ব্যবহার
__pathlib__ এর অন্তর্ভুক্ত __Path__ ক্লাসকে কল করে যে কোন পাথ এর মধ্যে পাস করালে সেই পাথ যে কোন অপারেটিং সিস্টেম এ কাজ করবে। নিচের একটি উদাহরণ খেয়াল করুন। আমি মূলত লিনাক্স বেসড উবুন্টুতে কাজ করি। এখন আমি যে পাথ ব্যবহার করবো সেটা যদি `Path` এর মধ্যে দিয়ে পাঠাই তবে যে কোন ওএস এ সেটি কাজ করবে। সাধারণভাবে এই পাথকে আপনি `os.path` এর যত অপারেশন আছে তা এপ্লাই করতে পারবেন।

```py
from pathlib import Path

mypath = Path('./sagor/mypath/)
# mypath will work in linux as well as mac, windows also.
```

## References
1. [https://docs.python.org/3/library/pathlib.html](https://docs.python.org/3/library/pathlib.html)
2. [https://www.freecodecamp.org/news/how-to-use-pathlib-module-in-python/](https://www.freecodecamp.org/news/how-to-use-pathlib-module-in-python/)
3. [https://realpython.com/python-pathlib/](https://realpython.com/python-pathlib/)
