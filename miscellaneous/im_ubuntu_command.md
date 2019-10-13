# Important Ubuntu Command

* Installing bash file/run .sh file

```
$chmod +x file.sh
$./file.sh

```

* Download file from web with retry

```
wget -c --retry-connrefused --waitretry=1 --read-timeout=3600 --timeout=60 -t 0 file_url'

```

* Zip/Unzip file

zipping a single file

```
zip file.zip filename_with_extention

# example
zip mytext.zip text.txt

```

zipping folder

```zip -r name.zip folder
#example
zip -r myfol.zip myfolder

```


Unzip file

```unzip file.zip```


* Check GPU status

```
$nvidia-smi
# for watch live status
$watch -n0.1 nvidia-smi
```

* Check Cuda Version

```
$cat /usr/local/cuda/version.txt
```

