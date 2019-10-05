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

