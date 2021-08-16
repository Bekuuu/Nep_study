# misc

## 图片隐写

### 工具

010editor（winhex）

kali(可用ubuntu替代)

llinx中先装一下需要的工具

```
sudo apt install binwalk
sudo apt install foremost
```



### 分类

#### 1）右键属性

#### 2）文件藏字符串

1.010

2.strings

3.grep（正则表达匹配输出行）

4.file（查看文件类型）

#### 3）文件包含

1.010editor



2.binwalk

```bash
$ binwalk file
$ binwalk -e file //输出为文件夹
```



3.foremost

```bash
$ foremost fire
```



4.dd

```bash
$ dd if=filein of=fileout bs=? skip=?
```



#### 4）修改文件头

010editor



#### 5）gif

1.特殊帧（ps,ulead gif,stegsolve）

2.帧长度

#### 6）png(bmp)

1.lsb（stegsolve，zsteg一把梭）

<img src="https://segmentfault.com/img/bVbgeGG?w=865&h=331" alt="lsb" style="zoom:80%;" />

安装：

```bash
$ git clone https://github.com/zed-0xff/zsteg
$ cd zsteg/
$ gem install zsteg
```



```bash
$ zsteg lsb.png
$ zsteg -a lsb.png     //尝试所有组合
$ zsteg zsteg -e "b1,rgb,lsb,xy" lsb.png > out.png  //输出
```

2.zlib(pngcheck,010,jio本,binwalk)

头：0x789c

```bash
$ sudo apt intall pngcheck
$ pngcheck -v file.png
```

3.IHDR,IDAT

4.wbstego4.3open(bmp、pdf)

#### 7）jpg

jphide (jphs)



steghide

```sh
steghide extract -sf .jpg -p 123456
```



outguess

```bash
 su root git clone https://github.com/crorvick/outguess ./configure && make && make install  outguess -k "key" -r 文件名 -t 保存的文件名
```



f5：

```sh
$ git clone https://github.com/matthewgao/F5-steganography$ java Extract .jpg -p pwd
```

#### 奇奇怪怪

1.双图

2.stegpy

3.盲水印（jio本）

··············

