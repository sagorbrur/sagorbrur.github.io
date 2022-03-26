---
title: "পাইথনে Shutil"
date: 2019-04-11
categories:
  - python
  - bangla
classes: wide
excerpt: পাইথনে ফাইল ও ফাইল কালেকশন নিয়ে কাজ করার জন্য Shutil হল খুবেই কার্যকরি একটি মডুউল।
---

পাইথনে ফাইল ও ফাইল কালেকশন নিয়ে কাজ করার জন্য Shutil হল খুবেই কার্যকরি একটি মডুউল। এটি পাইথনের স্টান্ডার্ড লাইব্রেরীর একটা মডুউল।

Shutil দিয়ে মূলত ফাইল copy, move করা যায়। 
এছাড়া পুরো ডিরেক্টরি কপি করতে কিংবা ডিলিট করতে কিংবা একই ফাইল বার বার আছে কিনা চেক করতে shutil ব্যবহার করা হয়। 

নিচে উদাহরণসহ প্রতিটি কাজ দেখানো হলোঃ

## shutil.copy(src,destination)

```py
>>> import shutil
>>> shutil.copyfile('data.db', 'archive.db')
'archive.db'
```

## shutil.move(source, destination)

```py
>>> import shutil
>>> shutil.move('file.txt','src_dir')

```

## shutil.disk_usage(path)

```py
>>> import shutil
>>>shutil.disk_usage('directory')

```

## shutil.copytree(src,dst)
Recursively copy an entire directory

```py
>>> import shutil
>>> shutil.copytree('source_dir', 'new_dir')

```

## shutil.rmtree
Delete an entire directory tree

```py
>>>import shutil
>>>shutil.rmtree('mydir')

```

এছাড়াও shutil দিয়ে ফাইল ও ডিরেক্টরি যুক্ত অনেক কাজ করা যায়। 

## রেফারেন্স লিংক
১। [https://docs.python.org/3/library/shutil.html#module-shutil](https://docs.python.org/3/library/shutil.html#module-shutil)

২। [https://docs.python.org/3/tutorial/stdlib.html](https://docs.python.org/3/tutorial/stdlib.html)