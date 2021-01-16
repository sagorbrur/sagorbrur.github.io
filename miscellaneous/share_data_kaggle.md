# Sharing Dataset Using Kaggle API
After creating a large beautiful dataset or corpus we all want to share with the large beautiful community.

Here is a step by step approach to share your dataset using kaggle api

## Creating Dataset in Kaggle
* Download kaggle api and keep it inside `C:\Users\username\.kaggle` in windows and `/home/username/.kaggle` in linux </br>
  if you don't know how to download kaggle api json please check [here](https://github.com/sagorbrur/sagorbrur.github.io/blob/master/miscellaneous/kaggle_data_colab.md)
* Install kaggle api by `pip install kaggle`
* Create a directory and keep your data inside that directory
* Create dataset metadata by
  `kaggle datasets init -p /path/your_directory`
* Fill the dataset metadata file according to your information and [template](https://github.com/Kaggle/kaggle-api/wiki/Dataset-Metadata)
* Now create your dataset in kaggle by `kaggle datasets create -p /path/your_direcotory`
* To make this dataset public you can use `-u` or can change in kaggle profile `share setting` option

## Updating your dataset
* Run `kaggle datasets init -p /path/to/dataset` to generate a metadata file if you don't already have one
* Make sure the id field in datapackage.json points to your dataset
* Run kaggle datasets version -p /path/your_directory -m "Your message here"

## References
* [https://www.kaggle.com/product-feedback/52640](https://www.kaggle.com/product-feedback/52640)
* [https://www.kaggle.com/docs/api](https://www.kaggle.com/docs/api)
* [https://github.com/Kaggle/kaggle-api#create-a-new-dataset](https://github.com/Kaggle/kaggle-api#create-a-new-dataset)
