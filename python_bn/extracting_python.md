# পাইথনে কম্প্রেসড ফাইল যেভাবে এক্সট্রাক্ট করবেন

## `.zip` ফাইল এক্সট্রাটিং

```py
from zipfile import ZipFile
zf = ZipFile('path_to_file/file.zip', 'r')
zf.extractall('path_to_extract_folder')
zf.close()

```

## `.tar` or `.tar.gz` ফাইল এক্সট্রাটিং

```py
import tarfile
tar = tarfile.open("file.tar.gz") # or file.tar
tar.extractall()

```

## `.bz2` ফাইল এক্সট্রাটিং

```py
import bz2
zipfile = bz2.BZ2File(filepath) # open the file
data = zipfile.read() # get the decompressed data
newfilepath = filepath[:-4] # assuming the filepath ends with .bz2
open(newfilepath, 'wb').write(data) # write a uncompressed file

```

## `.7z` ফাইল এক্সট্রাটিং(python 3 only)

```py
import lzma
with lzma.open('data.7z') as f:
    f.extractall("<output path>")

```

## রেফারেন্স
* [stackoverflow](stackoverflow.com)
