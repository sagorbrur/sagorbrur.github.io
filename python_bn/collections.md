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

