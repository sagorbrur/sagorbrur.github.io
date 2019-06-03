# পাইথন Collections মডুইল

পাইথনে collections মডুইল মূলত বিভিন্ন ডাটা কালেকশন(তথ্য সংগ্রহ) ফাংশন নিয়ে কাজ করে। যেমনঃ

* list
* dict
* set
* tuple

এগুলো মূলত বিল্ট ইন কালেকশন। এই বিল্ট ইন কালেকশন মডুইলকে আরো শক্তিশালী করার জন্য পাইথন কালেকশন মডুইলে যুক্ত আছে এমন কয়েকটি ফাংশন নিচে বর্ননা করা হলো। 

* Counter
* DefaultDict
* OrderDict
* deque
* ChainMap
* namedtuple()

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

যেমন নিচের কোড দিয়ে হেমলেট এ সবচেয়ে বেশি আছে এমন দশটি শব্দ আমরা দেখাবো। 

```py
from collections import Counter
import re # re means regular expression

words = re.findall(r'\w+', open('hamlet.txt').read().lower())
Counter(words).most_common(10)
# [('the', 1143), ('and', 966), ('to', 762), ('of', 669), ('i', 631),
 ('you', 554),  ('a', 546), ('my', 514), ('hamlet', 471), ('in', 451)]


```
