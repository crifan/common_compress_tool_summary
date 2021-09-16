# tar

与压缩和解压缩相关的常见格式还有：

* tar 打包
  * 常常与gz和bz2搭配使用

## tar

Linux系统自带tar工具，无需单独安装

### 创建tar打包文件

```bash
tar cf tar_filename.tar folder_or_file_to_package
```

参数解释：

* `c`=`create`：**创建**打包文件
* `f`=`file`：处理的是**文件**


### 解压tar打包文件

```bash
tar xf to_unpackage_tar_filename.tar
```

参数解释：

* `f`=`file`：处理的是**文件**
* `x`=`extract`：**提取**，解包，解开之前的打包

注：

* 如果想要看到**详细过程**，可以加上`-v`=`--verbose`参数
  * `v`=`verbose`：显示详细过程信息
    ```bash
    tar cvf tar_filename.tar folder_or_file_to_package
    tar xvf to_unpackage_tar_filename.tar
    ```
* 想要进一步再去压缩时，可以加上额外压缩的参数：`z`/`j`/`J`/`lzma`
  * `-z, -j, -J, --lzma`  Compress archive with `gzip`/`bzip2`/`xz`/`lzma`

至此，需要详细总结一下：

### tar支持的常见压缩格式和相关用法对比

Linux系统中，tar命令中常见压缩格式和相关用法对比：

| 常见后缀 | 压缩算法 | tar的参数 | 压缩比例 | 压缩(/解包)速度 | 用法举例
| ------ | ----------- | -------- | ------- | ------- | ----- |
| `.tar` | 无 | 无 | 无 | 最快 | 压缩：<br>`tar cf output.tar inputFileOrFolder`<br><br>解压缩：<br>`tar xf input.tar` |
| `.tar.gz` | `gzip` | `z` | 低 | 非常快 | 压缩：<br>`tar czf output.tar.gz inputFileOrFolder`<br><br>解压缩：<br>`tar xzf input.tar.xz` |
| `.tar.bz2` | `bzip2` | `j` | 中 | 慢 | 压缩：<br>`tar cjf output.tar.bz2 inputFileOrFolder`<br><br>解压缩：<br>`tar xjf input.tar.xz`<br>或：<br>`bzip2 -dk input.tar.bz2`<br>`tar xf input.tar` |
| `.tar.xz` | `xz` | `J` | 高 | 快 | 压缩：<br>`tar cJf output.tar.xz inputFileOrFolder`<br><br>解压缩：<br>`tar xJf input.tar.xz`<br>或：<br>`xz -d input.tar.xz`<br>`tar xf input.tar`|
| `.tar.lama` | `lzma` | `--lzma` | 非常高 | 快 | 压缩：<br>`tar cf --lzma output.tar.lama inputFileOrFolder`<br><br>解压缩：<br>`tar --lzma xf input.tar.lama`<br>或：<br>`lzma -d input.tar.lama`<br>`tar xf input.tar`|

举例：

之前解压python的xz源码：

```bash
tar xJf Python-3.7.3.tar.xz
```
