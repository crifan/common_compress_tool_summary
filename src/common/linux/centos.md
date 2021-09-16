# CentOS

此处以`CentOS`为例，来解释`Linux`中如何使用压缩和解压缩相关工具。

## 7z

CentOS的7z工具：

* `p7zip`
  * 安装
    * 通过`源码`安装`p7zip`
    * 通过`yum`安装`p7zip`

### 通过yum安装p7zip

```bash
yum install p7zip
```

注意：

安装后的不是`7z`，而是`7za`：

```bash
# which 7za
/usr/bin/7za
```

不过用法都是类似的：

详见后续章节：[7z命令行工具使用总结](../../usage/7z.md)

### 通过源码安装7z

先下载p7zip源码

比如从：

https://sourceforge.net/projects/p7zip/files/p7zip/16.02/p7zip_16.02_src_all.tar.bz2/download

找到的

https://nchc.dl.sourceforge.net/project/p7zip/p7zip/16.02/p7zip_16.02_src_all.tar.bz2

去下载：

```bash
wget https://nchc.dl.sourceforge.net/project/p7zip/p7zip/16.02/p7zip_16.02_src_all.tar.bz2
```

解压：

```bash
tar xvf p7zip_16.02_src_all.tar.bz2
```

安装：

```bash
cd p7zip_16.02
make && make install
```

确认已安装：

```bash
which 7za
```

查看语法即参数：

```bash
7za --help
```

## zip

zip：用来压缩

```bash
zip -r output_zip_filename.zip some_folder/*
```

安装：

```bash
yum -y install zip
```

## unzip

unzip：用来解压缩

```bash
unzip file_to_uncompress.zip
```

安装：

```bash
yum -y install unzip
```

## bz2

安装：

```bash
yum -y install bzip2
```

用法：

解压bz2：

```bash
bzip2 -d curl-7.64.1.tar.bz2
```

注意：

* 默认会删除`bz2`文件
  * `bzip2`解压默认会**删除**`bz2`文件，如果要保留之前的bz2文件，则加上`-k`=`--keep`参数：
    ```bash
    bzip2 -dk curl-7.64.1.tar.bz2
    ```
* 只是解压缩bz2，并没有解包tar
  * 此处
    ```bash
    bzip2 -d
    ```
  * 只是是解压了`bz2`，即，把`.tar.bz2`变成了`.tar`
  * 但只得到了tar打包文件，还没有得到源码
  * 需要再去解包：
    ```bash
    tar -xf curl-7.64.1.tar
    ```
  * 才能得到源码
