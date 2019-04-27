# A Gentle Introduction to Google Colaboratory([Colab](https://colab.research.google.com))

You are an enthusiastic learner on Machine Learning but you have no capability to purchase a big machine to train and test your model.

## Don't worry! 

Google Colab is a perfect solution for you. Google Colab(Colaboratory) is a free cloud service to encourage machine learning research.

Here is a simple introduction how you start google colaboratory. 

# STEPS

## Account

* Create a google account(Hope you all have a gmail)
* Log in to your gmail
* Goto [https://colab.research.google.com](https://colab.research.google.com) and sign in with your gmail account

## Opening a new Notebook

* Now you can create a jupyter Notebook with python 2 or 3 just clicking 'New Notebook'
* To run any cell click shift+enter

## Download anything from web and cloning git

* To Download anything from web just run the following command inside notebook

```!wget url```

You can download dataset from website with no time(12mbps or more google speed)

You can unzip anything just running the following command

```!unzip file.zip```  [Here file is your filename]

* To clone a git just run the following command

```!git clone git_url```

## Installing libraries
Although google colab has all the dependencies library installed, you can install any library just running the command you run on bash

```!pip install library_name```

## Activating GPU
* You can activate GPU from ```Edit>Notebook Settings>Hardware Accelerator>GPU```

## Upload local file

*You can upload local file by clicking the upload button which exist in your left side inside Files
*Check and upload your local file

```NB: file will automatically deleted after you closing the browser```

## Run full project as python scripts
Suppose we have directory with files, data , config

```
----Contents

    ------train.py
    
    ------test.py
    
    ------data
    
          -----train.csv
          
          -----test.csv
          
    ------config
    
          ------config.config
          
    -------logs
```

Our config.config looks like

```
train_data = "data/train.csv"
test_data = "data/test.csv"
log_dir = "logs"
epoch = 10
mode = train

```

Our train command is 

```python train.py --config_file config/config.config```

and Test command is 

```python test.py --config-file config/config.config```

To train the project in colab write the commnad inside notebook

```!python train.py --config_file config/config.config```

It will train the model and save the checkpoint inside logs directory. From where you can download the checkpoint. 

To test the project in colab write the command inside notebook

```!python test.py --config-file config/config.config```

That's the easiest way to train model from project scripts. 



