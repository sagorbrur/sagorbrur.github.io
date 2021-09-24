# Simple Pytorch Steps
- Import necessary modules
- Set device
- Define data
- Define model
- Define loss function
- Define optimizer
- Train model
- Eval model
- Save Model
- Load Model
- inspect model

## Import Necessary Modules
```py
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader
```

## Set Device
```py
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
print(device)
```

## Define Data
```py
# device a sample trainset
traindata = torch.tensor([[1, 2, 3], [2, 3, 4], [5, 7, 4], [9, 1, 4]], dtype=torch.float32)
# map traindata in cuda device or cpu
traindata = traindata.to(device)
# device train label
trainlabel = torch.LongTensor([0, 1, 0, 1])
# map label to cuda or cpu
trainlabel = trainlabel.to(device)
print(traindata)
print(trainlabel)

# define sample test set
testdata = torch.tensor([[1, 2, 3], [2, 3, 4], [5, 7, 4], [9, 1, 4]], dtype=torch.float32)
# map testdata in cuda device or cpu
testdata = testdata.to(device)
# device test label
testlabel = torch.LongTensor([0, 1, 0, 1])
# map label to cuda or cpu
testlabel = testlabel.to(device)

# convert traindata and label to example
def generate_data_example(data, label):
  examlpes = []
  for d, l in zip(data, label):
    data_set = (d, l)
    examples.append(data_set)
  return exampes
 
train_examples = generate_data_example(traindata, trainlabel)
test_examples = generate_data_example(testdata, testlabel)

# fit in dataloader
batch_size = 1
train_dataloader = DataLoader(train_examples, batch_size=batch_size)
test_dataloader = DataLoader(test_examles, batch_size=batch_size)
```
## Define Model
A simple one layer model

```py
class Model(nn.Module):
  def __init__(self, input_size, output_size):
    super(Model, self).__init__()
    self.input_size = input_size
    self.output_size = output_size
    self.linear = nn.Linear(input_size, output_size)

  def forward(self, x):
    out = self.linear(x)
    return out
    
input_size = traindata.shape
print(input_size[1])
model = Model(input_size[1], 2)
model.to(device)
print(model)
```

## Define Loss Function
```py
criterion = nn.CrossEntropyLoss()
```
## Define Optimizer
```py
optimizer = optim.Adam(net.parameters(), lr=0.001)
```
## Train Function
```py
def train(dataloader, model, loss_fn, optimizer):
    size = len(dataloader.dataset)
    model.train()
    for batch, (X, y) in enumerate(dataloader):
        X, y = X.to(device), y.to(device)

        # Compute prediction error
        pred = model(X)
        loss = loss_fn(pred, y)

        # Backpropagation
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

        if batch % 1 == 0:
            loss, current = loss.item(), batch * len(X)
            print(f"loss: {loss:>7f}  [{current:>5d}/{size:>5d}]")

```
## Test Function
```py
def test(dataloader, model, loss_fn):
    size = len(dataloader.dataset)
    num_batches = len(dataloader)
    model.eval()
    test_loss, correct = 0, 0
    with torch.no_grad():
        for X, y in dataloader:
            X, y = X.to(device), y.to(device)
            pred = model(X)
            test_loss += loss_fn(pred, y).item()
            correct += (pred.argmax(1) == y).type(torch.float).sum().item()
    test_loss /= num_batches
    correct /= size
    print(f"Test Error: \n Accuracy: {(100*correct):>0.1f}%, Avg loss: {test_loss:>8f} \n")

```
## Train
```py
epochs = 5
for t in range(epochs):
    print(f"Epoch {t+1}\n-------------------------------")
    train(train_dataloader, model, loss_fn, optimizer)
    test(test_dataloader, model, loss_fn)
print("Done!")
```
## Save Model
```py
torch.save(model.state_dict(), 'model.pth')
```
## Load and Inference
```py
load_model = model.load_state_dict(torch.load('model.pth'))
test_input = torch.tensor([[1, 2, 3]], dtype=torch.float32)
predict = model(test_input).data.max(1, keepdim=True)[1]
print(predict)
```
## Inspect Model
```py
# inspect parameters
params = model.parameters()
for param in parameters:
  print(param)
modules = model.named_modules()
for idx, m in enumerate(modules):
  print(idx, m)
```
