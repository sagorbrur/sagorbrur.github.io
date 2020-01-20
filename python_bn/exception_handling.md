# পাইথনে Exception Handling

**Exceptions(এক্সেপশন):** পাইথন কোড এক্সিকিউশনের সময় যে ভুল/ত্রুটি উৎপন্ন হয় তাকে  Exceptions বলে।


**Handling Exception(এক্সেপশন হ্যান্ডলিং):** সাধারণত যখন কোন ত্রুটি বা এক্সেপশন উৎপন্ন হয় পাইথন কোড এক্সিউশন বন্ধ করে দেয় এবং একটি ত্রুটি বার্তা দেখায়। </br>
Exception Handling এক্সিউশন বন্ধ করা রোধ করে এবং বার্তা দেখিয়ে `try` এবং `except` এর মাধ্যমে এক্সিউশনকে হ্যান্ডল করে বা চালু রাখে।

## উদাহরণ:

নিচের উদাহরণটি লক্ষ্য করুন, যেটি যতক্ষণ পর্যন্ত ইউজার সঠিক পুর্নসংখ্যা ইনপুট না দিচ্ছে তখনক্ষণ পর্যন্ত কোডটি চালু থাকবে 
এবং ইউজারকে একটি ত্রুটি বার্তা দেখিয়ে যাবে। 


```py
while True:
    try:
        a = int(input("please enter an integer value: "))
        print(a)
        break
    except:
        print("Ops! Please enter a valid integer value.")

```

আরো জানতেঃ [https://docs.python.org/3/tutorial/errors.html](https://docs.python.org/3/tutorial/errors.html)
