# Deep Learning Steps

## Define your model
```py
import torch
import torch.nn as nn

class Model(nn.Module):
    def __init__(self, input_size, output_size):
        super(Model, self).__init__()
        self.linear = nn.Linear(input_size, output_size)
    def forward(self, input):
        logits = self.linear(input)

model = Model(input_size=30, output_size=20)
print(model)
```

## Define your datasets

data = torch.tensor([[1,2,3],[2,3,4],[3,4,5]])
