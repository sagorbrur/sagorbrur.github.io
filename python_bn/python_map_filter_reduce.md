# পাইথনে map, filter এবং reduce

## map

map ফাংশন প্যারামিটার হিসাবে একটি ফাংশন এবং একটি লিস্ট নেয় এবং পুরা লিস্টের উপর ফাংশনটি প্রয়োগ করে।


```python
def square(x):
    return x**2

l = [1, 2, 3, 4]
list(map(square, l))
```




    [1, 4, 9, 16]



## filter

filter ফাংশনটিও map ফাংশনের মত কাজ করে। তবে এটি filter বা শর্ত হিসাবে কাজ করে। 
উদাহরণ হিসবে ধরি, আমরা একটি লিস্টের শুধুমাত্র জোড় সংখ্যাগুলো নিয়ে আরেকটি লিস্ট করতে চাচ্ছি। 
সে জন্য ফিল্টার কোড হবেঃ


```python
def even(x):
    return x%2==0

list(filter(even, l))
```




    [2, 4]



## reduce

reduce ফাংশনটি পাইথনে functools মডিউলের অন্তর্গত। এটি প্যারামিটার হিসাবে একটি ফাংশন এবং লিস্ট নেয় এবং ফলাফল হিসাবে একটি মাত্র
ভ্যালু প্রদান করে।


```python
from functools import reduce
def add(a, b):
    return a+b

reduce(add, l)
```




    10



## References

* [https://docs.python.org/3/library/functions.html](https://docs.python.org/3/library/functions.html)
* [https://towardsdatascience.com/top-3-python-functions-you-dont-know-about-probably-978f4be1e6d](https://towardsdatascience.com/top-3-python-functions-you-dont-know-about-probably-978f4be1e6d)
* [https://medium.com/@ankur.ghogle100/difference-between-map-and-filter-in-python-8c5bca11afe8](https://medium.com/@ankur.ghogle100/difference-between-map-and-filter-in-python-8c5bca11afe8)


```python

```
