S3.FMA
======

Amazon S3 File Manager API in Python. S3.FMA is a thin wrapper around boto to perform specific high level file management tasks on an AWS S3 Bucket.

## **Requirements**

You must have **boto** installed to use S3.FMA. For directions to installing boto see [this post](http://stackoverflow.com/questions/2481287/how-do-i-install-boto)


## Usage
The S3.FMA programming model looks like this:

### **Creating an instance of S3FileManager**
```python
from S3FMA import *
 
AWS_KEY = 'my key'
AWS_SECRET = 'my secret'
s3FileManager = S3FileManager(AWS_KEY, AWS_SECRET, use_ssl = True)
```

### **List all files in an S3 bucket**
```python
# returns a list of files stored in bucket 'mybucket'
fileNames = s3FileManager.getFileNamesInBucket('mybucket')
    for f in filenames:
        print f
```

### **Download a file from a bucket**
```python
# download a file named 'fileToDownload.txt' from bucket 'mybucket' to '~/Downloads/download_to_here/'
s3FileManager.downloadFileFromBucket('mybucket', 'fileToDownload.txt', '~/Downloads/download_to_here/')
```

### **Download all files from a bucket**
```python
# download all of the files in bucket 'mybucket' to the '~/Downloads/download_to_here/'
s3FileManager.downloadAllFilesFromBucket('mybucket', '~/Downloads/download_to_here/')
```

### **Download all files from a bucket who's filename satisfy a predicate**
```python
# download files that contain the word 'foo' in their name from 'mybucket' to '~/Downloads/download_to_here/'
s3FileManager.downloadFilesInBucketWithPredicate('mybucket', lambda filename: 'foo' in filename, '~/Downloads/download_to_here/')
```

### **Delete all files from a bucket**
```python
# delete all files in bucket 'mybucket'
s3FileManager.deleteAllFilesFromBucket('mybucket')
```

### **Delete all files from a bucket who's filename satisfy a predicate**
```python
# delete files that contain the word 'foo' in their name from 'mybucket'
s3FileManager.deleteFilesInBucketWithPredicate('mybucket', lambda filename: 'foo' in filename)
```
