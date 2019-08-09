## পাইথনে একাধিক ডিরেক্টরি নিয়ে যেভাবে কাজ করবেন

পাইথনে একাধিক ফোল্ডার বা ডিরেক্টরি নিয়া কাজ করা একটা মহা ঝামেলার কাজ।
এই ঝামেলার কাজ পাইথন `os` মডিউল দিয়ে সমাধান করা যায়। নিচে উদাহরণ সহ তলে ধরা হলো।

## `os.getcwd()` ব্যবহার করে বেজপাথ ডিফাইন করা

আমরা আমাদের বর্তমান কর্মরত ফোল্ডারকে বেজপাথ হিসেবে ডিফাইন করবো।
উদাহরণ হিসাবে আমাদের বর্তমান কর্মরত পাথ/ফোল্ডার হলোঃ `home/sagor/Desktop/hello`

```py
import os

BASE_PATH = os.getcwd()
print(BASE_PATH)
# output: home/sagor/Desktop/hello

```
বেজপাথ ইনিশিয়ালাইজেশন হয়ে গেছে।

`hello` ফোল্ডারে ভীতর আমাদের তিনটি সাবফোল্ডার আছে। 

* src (contains source script)
* data (contains data files)
* logs (contains our logs file)

## `os.path.join` ব্যবহার করে এই তিন সাবফোল্ডারকে বেজপাথে যুক্ত করা

এখন আমরা এই তিন সাবফোল্ডারকে আমাদের বেজপাথে যুক্ত করবো।

```py
SRC_PATH = os.path.join(BASE_PATH, 'src')
DATA_PATH = os.path.join(BASE_PATH, 'data')
LOGS_PATH = os.path.join(BASE_PATH, 'logs')


# ধরি, 'extra' নামে আরেকটি ফোল্ডার 'hello' ফোল্ডারের একধাপ বাইরে আছে। মানে 'Desktop' এ আছে। 
# আমরা 'extra' কেও বেজপাথে যুক্ত করতে পারি।

EXTRA_PATH = os.path.join(BASE_PATH, '../hello')


```


এখন এই সব ডিফাইন পাথ নিয়ে আপনি যেকোন কাজ করতে পারেন। 

## উদাহরণ

`os.listdir` ব্যবহার করে 'DATA_PATH' এর ভীতর যত ফাইল আছে তা আমরা প্রিন্ট করবো।

```py

files = os.listdir(DATA_PATH)

for file in files:
    print(file)
    
# output: 'hello.png''hello1.png'


```
