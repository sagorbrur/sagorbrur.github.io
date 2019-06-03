# পাইথন Collections মডুইল

পাইথনে collections মডুইল মূলত বিভিন্ন ডাটা কালেকশন(তথ্য সংগ্রহ) ফাংশন নিয়ে কাজ করে। যেমনঃ

* list
* dict
* set
* tuple

এগুলো মূলত বিল্ট ইন কালেকশন। এই বিল্ট ইন কালেকশন মডুইলকে আরো শক্তিশালী করার জন্য পাইথন কালেকশন মডুইলে যুক্ত আছে এমন কয়েকটি ফাংশন হলো: 

* Counter
* DefaultDict
* OrderDict
* deque
* ChainMap
* namedtuple()

নিচের Counter সম্পর্কে বিস্তারিত আলোচনা করা হলো। 

## Counter

`Counter' মূলত ডিকশনারির একটি সাবক্লাশ, যেটি বিভিন্ন অবজেক্ট কতবার আছে তা গনণা করে। 

```py
from collections import Counter

cnt = Counter()
for word in ['red', 'blue', 'red', 'green', 'blue', 'blue']:
     cnt[word] += 1
print(cnt)
# output: Counter({'blue': 3, 'red': 2, 'green': 1})
```
তাহলে এখানে দেখতে পাচ্ছি যে আমাদের লিস্টে blue আছে তিনবার, red আছে দুইবার আর green আছে একবার। এটাই মূলত `Counter` এর কাজ।

এখন আমরা যদি চাই যে একটা টেক্সট ডকুমেন্টে কতগুলো একই শব্দ আছে তা আমরা Counter ব্যবহার করে সহজে বের করতে পারবো। 

যেমন নিচের কোড দিয়ে [হেমলেট](https://gist.github.com/provpup/2fc41686eab7400b796b) এ সবচেয়ে বেশি আছে এমন দশটি শব্দ আমরা দেখাবো। 

```py
from collections import Counter
import re # re means regular expression

words = re.findall(r'\w+', open('hamlet.txt').read().lower())
Counter(words).most_common(10)
# [('the', 1143), ('and', 966), ('to', 762), ('of', 669), ('i', 631),
#('you', 554),  ('a', 546), ('my', 514), ('hamlet', 471), ('in', 451)]


```
Counter অবজেক্টের মূলত তিনটা মেথুড সাপোর্ট করে। 
* elements()
* most_common([n])
* subtract()

### elements()

লিস্টে মূলত কি কি অবজেক্ট আছে তা দেখানোই এই মেথুড এর কাজ। 

```py
>>> from collections import Counter
>>> c = Counter(a=4, b=2, c=0, d=-2)
>>> list(c.elements())
['a', 'a', 'a', 'a', 'b', 'b']
```

### most_common([n])

এই মেথুডটি কোন অবজেক্ট কতবার আছে তা গনণা করে। উপরে হেমলেট উদাহরণে আমরা দেখেছি। 

```py
>>> from collections import Counter
>>> Counter('abracadabra').most_common(3)
[('a', 5), ('r', 2), ('b', 2)]

```

### subtract()

এই মেথুডটি দুটি কাউন্টারের অন্তর্গত উপাদানসমুহ বিয়োগ করে তার ফলাফল প্রকাশ করে।

```py
>>> from collections import Counter

>>> c = Counter(a=4, b=2, c=0, d=-2)
>>> d = Counter(a=1, b=2, c=3, d=4)
>>> c.subtract(d)
>>> c
Counter({'a': 3, 'b': 0, 'c': -3, 'd': -6})
```
উপরের উদাহরণে দেখা যাচ্ছে c কাউন্টারে a আছে ৪টি এবং d কাউন্টারে a আছে ১টি। এখন এদের subtract কাউন্টারে a আছে তাদের বিয়োগফল মানে ৩টি। 

## References
1. [https://docs.python.org/2/library/collections.html](https://docs.python.org/2/library/collections.html)
2. [https://stackabuse.com/introduction-to-pythons-collections-module/](https://stackabuse.com/introduction-to-pythons-collections-module/)
