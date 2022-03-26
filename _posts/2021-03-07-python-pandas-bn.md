---
title: "পাইথনে Pandas"
date: 2020-03-17
categories:
  - python
  - bangla
classes: wide
excerpt: পাইথনে টেবুলার ডাটা হ্যান্ডল করার জন্য Pandas একটি গুরুত্বপূর্ন টুল। নিচে Pandas এর কিছু স্পেশাল ট্রিক্স তুলে ধরা হলো। সময় অনুযায়ী ট্রিক্স এর লিস্ট বারতে থাকবে।
---

পাইথনে টেবুলার ডাটা হ্যান্ডল করার জন্য Pandas একটি গুরুত্বপূর্ন টুল। নিচে Pandas এর কিছু স্পেশাল ট্রিক্স তুলে ধরা হলো। সময় অনুযায়ী ট্রিক্স এর লিস্ট বারতে থাকবে।

## Creating DataFrame

```py
import pandas as pd

data = {
  'A': [1, 2, 3],
  'B': [4, 5, 6]
}

df = pd.Dataframe(data, columns=data.keys())
print(df.head())

"""
output:
A B
1 4
2 5
3 6
"""

```

## Create a new column from list

```py
sample_list = [7, 8, 9]
df['C'] = sample_list
print(df.head())

"""
output:
A B C
1 4 7
2 5 8
3 6 9
""""

```

## Selecting Column Tips
`df.iloc[:,:]` এই লিস্টের প্রথম `:` দ্বারা সকল row আর দ্বিতীয় `:` দ্বারা সকল column নির্দেশ করে।

এখন আমরা যদি কোন একটি টেবিলের সকল কলামের শুধু ১০ টা রো সেলেক্ট করতে চাই তবে এভাবে iloc ব্যবহার করে করতে পারি।

```py
df.iloc[:10, :]
```
একই ভাবে কোন টেবিলের যদি আমরা নির্দিষ্ট কিছু কলাম নিতে চাই তবে iloc দিয়ে নিতে পারি।

```py
# 10 row with first 2 column
df.iloc[:10, :2]
# all row with first 2 column
df.iloc[:, :2]

# all row with column 1 and 3
df.iloc[:, [0, 2]]

# and so on
```
## Saving file in pandas
পাইথনে বিভিন্ন ফরমেটে ফাইল সংরক্ষণ করা যায়। সেখানে নরমাল টেস্কুয়াল থেকে বাইনারী ফরম্যাটে ডাটা সংরক্ষণ করা যায়।

```py
# to save as csv
df.to_csv('file.csv', index=False)
# to save as tsv
df.to_csv('file.tsv', sep='\t', index=False)

```
