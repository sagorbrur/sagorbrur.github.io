# পাইথনে Dictionary
**Dictionary** হলো আইটেমের কালেকশন যেখানে প্রতি আইটেম হলো key আর value এর পেয়ার। 
উদাহরণঃ 
```py
d = {'a': 1, 'b': 2}
```

এখানে a হলো key এবং 1 হলো value.

## Indexing a dictionary
- প্রথমে ডিকশনারির সকল আইটেমকে লিস্ট আকারে নিতে হবে।
  ```py
  d_list = list(d.items())
  # [('a', 1), ('b', 2)]
  ```
- এখন আপনি আপনার মন মত ইনডেক্স নিতে পারে। এবং সেখান থেকে key আর value ও নিতে পারবেন।
  ```py
  first_item = d_list[0]
  # ('a', 1)
  first_item_key = d_list[0][0]
  # 'a'
  first_item_value = d_list[0][1]
  ```
  
## Sorting a dictionary
উপরে যেভাবে আমরা ইনডেক্সিং করলাম এই ইনডেক্স ধরেই আমরা একটা Dictionary কে সর্ট করতে পারি।

```py
d = {'a': 1, 'b': 2}
# sort by value
# d.itmes() return a list of tuples [(key, value), (key, value), ...]
# then we take the value and sort it.
sorted_d = dict(sorted(d.items(), key=lambda x: x[1]))
# {'a': 1, 'b': 2}
# sort by key
sorted_d = dict(sorted(d.items(), key=lambda x: x[0]))
```
