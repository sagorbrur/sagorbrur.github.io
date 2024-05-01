---
permalink: /llm/
title: "LLM Resources"
classes: wide
excerpt: This page contains different resource of LLM
---

## LLM Quantization
- [4-bit transformers](https://huggingface.co/blog/4bit-transformers-bitsandbytes)

    ```py
    from transformers import AutoModelForCausalLM

    model = AutoModelForCausalLM.from_pretrained("facebook/opt-350m", load_in_4bit=True, device_map="auto")
    ```

- [Intro to 8-bit transformers multiplication](https://huggingface.co/blog/hf-bitsandbytes-integration)

    ![image](https://huggingface.co/blog/assets/96_hf_bitsandbytes_integration/out-quant.gif)
