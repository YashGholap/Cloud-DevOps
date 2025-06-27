You probably already know what a file archive is, you've most likely encountered file types such as .rar and .zip. These are an archive of files, they contain many files inside of them, but they come in this very neat single file known as an archive.

## **Compressing the file**

gzip is program used to compress files in linux, they end in a .gz extension
To compress a file down:

```bash
$  gzip myfile
```
 
 To decompress:
 
```bash
$  gunzip myfile.gz
```

## **Compressing/uncompressing archives with tar and gzip**

Many times you'll see a tar file that has been compressed such as: mycompressedarchive.tar.gz, all you need to do is work outside in, so first remove the compression with gunzip and then you can unpack the tar file. Or you can alternatively use the **z** option with tar, which just tells it to use the gzip or gunzip utility.

- Create a compressed tar file:  

```bash
$  tar czf myfile.tar.gz myfile myfile2
```

- Uncompress and unpack:  

```bash
$  tar xzf myfile.tar [path]
$  tar xzf myfile.tar.gz [path]
```

If you need help remember this: e**X**tract all **Z**ee **F**iles!