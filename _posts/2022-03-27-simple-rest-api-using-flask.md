---
title: "Simple REST API using Flask"
date: 2022-03-27
categories:
  - web
  - python
classes: wide
excerpt: This blog describes about simple REST API using Flask.
---

In this tutorial we will learn a simple REST API using Flask.
We will learn mostly two methods (GET and POST) of HTTP request.

## Content
- [Dependencies](#dependencies)
- [Creating a flask app](#creating-a-flask-app)
- [GET Method](#get-method)
- [POST Method](#post-method)

## Dependencies
To start with this tutorial, let's import the required packages.
```bash
pip install flask
```

## Creating a flask app
Creating a flask app is quite simple.
```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello World!'

if __name__ == "__main__":
    app.run(debug=True)
```
run following command to test

```bash
python app.py
```

## GET Method
The GET method is used to retrieve data from a server. Here we will retrive simple message from our local server. Modify the above code with a new route and a new function with GET method.

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello World!'

@app.route('/get_message', methods=['GET'])
def get_message():
    return jsonify({'message': 'Hello World!'})

if __name__ == "__main__":
    app.run(debug=True)
```
To get the message we will use python `requests` module to retrive the message.

```python
import requests

response = requests.get('http://localhost:5000/get_message')
print(response.json())
# output: {'message': 'Hello World!'}
```

## POST Method
The POST method is used to send data to a server. Here we will send text to our local server, our server will tokenize it and return tokenized data. Modify the above code with a new route and a new function with POST method.

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello World!'

@app.route('/get_message', methods=['GET'])
def get_message():
    return jsonify({'message': 'Hello World!'})

@app.route('/tokenize', methods=['POST'])
def tokenizer():
    if request.method == 'POST':
        text = request.form['text']
        tokens = text.split()
        return jsonify({'tokens': tokens})

if __name__ == "__main__":
    app.run(debug=True)
```

To send the text we will use python `requests` module to send the text.

```python
import requests

response = requests.post('http://localhost:5000/tokenize', data={'text': 'Hello World!'})
print(response.json())
# output: {'tokens': ['Hello', 'World!']}
```



