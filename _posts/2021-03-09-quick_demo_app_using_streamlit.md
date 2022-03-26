---
title: "Streamlit ব্যবহার করে তাৎক্ষনিক ডেমো ওয়েব অ্যাপ তৈরি"
date: 2021-03-09
categories:
  - demo
  - web
  - msc
classes: wide
excerpt: This blog describe how to prepare a simple demo app using streamlit
---

মেশিন লার্নিং কিংবা ডিপ লার্নিং দিয়ে পাইথনে অ্যাপ তৈরি করে সেই অ্যাপ খুব সহজে ওয়েব ভার্সনে ডিস্প্লে করার সহজ উপায় হলো Streamlit

Streamlit ব্যবহার করে মাত্র কয়েক লাইনে একটি ডেমো অ্যাপ তৈরি করা সম্ভব। নিচে স্টেপ বাই স্টেপ তুলে ধরা হলো।

## Installation
```pip install streamlit```

### Creating Demo App
আমরা একটি ডেমো অ্যাপ তৈরি করবো যেটি ইনপুট টেক্সট নিয়ে সেটার টোকেনাইজ ভ্যালু দেখাবে।

* প্রথমেই নিজের পছন্দ মত নাম দিয়ে একটি ফাঁকা ডিরেক্টরি তৈরি করবো।
  ```
    mkdir tokenizer
    cd tokenizer
  ```
* আমার অ্যাপ ডিরেক্টরিতে `app.py` নামে একটি স্ক্রিপ্ট তৈরি করি।
* স্ক্রিপ্টে নিচের কোড পেস্ট করি।

  ```py
  import streamlit as st

  def tokenize(text):
      tokens = text.split()
      return tokens

  def run():
      st.title("Tokenizer")
      st.header("A simple web tokenizer")
      text = st.text_area("Enter your text here")
      if st.button("Tokenize"):
          output = tokenize(text)
          st.success(f"{output}")

  if __name__=="__main__":
      run()
  ```
* এখন অ্যাপ ডিরেক্টরিতে টার্মিনাল ওপেন করে নিচের কম্যান্ড রান করালেই ব্রাউজারে ওপেন হবে আমাদের টোকেনাইজার অ্যাপ।

  ```streamlit run app.py```
  
  ![streamlit demo 1](https://raw.githubusercontent.com/sagorbrur/sagorbrur.github.io/master/assets/images/streamlit_demo_1.png)