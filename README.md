S3.FMA
======

Amazon S3 File Manager API in Python. S3.FMA is a thin wrapper around boto to perform specific high level file management tasks on an AWS S3 Bucket.

The S3.FMA programming model looks like this:

**Creating an instance of S3FileManager**
```python
from S3FMA import *
 
AWS_KEY = 'my key'
AWS_SECRET = 'my secret'
s3FileManager = S3FileManager(AWS_KEY, AWS_SECRET, use_ssl = True)
```

**List all files in an S3 bucket**
```python
# returns a list of files stored in bucket 'bucket_name'
fileNames = s3FileManager.getFileNamesInBucket('mybucket')
    for f in filenames:
        print f
```

**Download a file from a bucket**
```python
# download a file named 'fileToDownload.txt' from bucket 'mybucket' to '~/Downloads/download_to_here/'
s3fileManager.downloadFileFromBucket('mybucket', 'fileToDownload.txt', '~/Downloads/download_to_here/')
```
