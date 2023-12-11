---
title: "Minimal API using FastAPI"
date: 2023-12-11
categories:
  - api
  - python
  - deployment
classes: wide
excerpt: In this blog I will share how to build a minimal API using FastAPI to deploy your python app
---

In this blog I will show how to build a minimal API using __FastAPI__ to deploy any python app.
We will build a simple tokenizer API that can take input text and return list of tokens. 

## Installation
```bash
pip install fastapi
pip install "uvicorn[standard]"
```

## API Example

```py
from pydantic import BaseModel
from fastapi import FastAPI, HTTPException

app = FastAPI()

class RequestModel(BaseModel):
  text: str

class ResponseModel(BaseModel):
    tokens: list

def tokenize(text: str):
    return text.split()

@app.post("/tokenizer", response_model=ResponseModel)
async def tokenization(request_data: RequestModel):
    try:

        tokens = tokenize(request_data.text)

        return ResponseModel(
            tokens=tokens
        )
    except Exception as e:
        traceback.print_exc()
        raise HTTPException(status_code=500, detail=str(e))

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)

```

Now save this codes as `myapp.py` and directly run `pythonn myapp.py` or you can run `uvicorn myapp:app --reload`

## API Testing
- You can test this API using FastAPI doc `http://127.0.0.1:8000/docs`
- Here is request method to test your app

```py
import requests

# Define the API base URL
api_base_url = "http://localhost:8000"  # Replace with your API URL if it's different

# Sample input data
input_data = {
    "text": "This is a sample text for tokenization."
}

# Make a POST request to the API
response = requests.post(f"{api_base_url}/tokenizer", json=input_data)

# Check if the request was successful
if response.status_code == 200:
    # Parse the JSON response
    response_data = response.json()
    
    # Extract the tokens from the response
    tokens = response_data.get("tokens", [])
    
    # Print the tokens
    print("Tokens:", tokens)
else:
    # Handle error responses
    print(f"Error: {response.status_code}")
    print(response.text)

```