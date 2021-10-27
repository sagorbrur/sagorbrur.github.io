# Downloading and Inspecting Huggingface Datasets

## Downloading and Loading data
Here is an example of downloading and loading [`conll2003`](https://huggingface.co/datasets/conll2003) datasets
Below code will download `conll2003` datasets in default `~/.cache/huggingface/datasets` directory.

```py
from datasets import load_dataset

dataset = load_dataset("conll2003")
print(dataset)
```
`load_dataset` important argument listed below:

- __path(str)__ - path or name of the datasets. You can download by the datasets name like above or provide a data path to load. You can find any datasets name in hf.com/datasets with username.
-  
