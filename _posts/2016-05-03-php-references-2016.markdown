---
layout:     post
title:      "PHP 引用"
subtitle:   " \"PHP引用\""
date:       2016-05-03 8:00:00
author:     "Wenlh"
header-img: "img/myson.jpg"
catalog: true
tags:
    - PHP
    - PHP基础
---

## [引用](http://www.w3school.com.cn/php/php_file_upload.asp)  

#### 变量引用
```php
<html>
    <body>
        <?php
            $a="A"; 
            $b =&$a; 				//$b是$a的引用,即$a和$b使用同一个内容,
            echo $a .'<br>';//这里输出:A 
            echo $b .'<br>';//这里输出:A  
            $b="B"; 
            echo $a .'<br>';//这里$a的值变为B 所以输出B
            echo $b .'<br>';//这里输出B
            
            $a = 'C';
            echo $a .'<br>';//这里$a的值变为C 所以输出C 
            echo $b .'<br>';//这里输出C
        ?>
    </body>
</html>
```

#### 函数的传址调用

```php
<?php 
	function test(&$a) 
	{ 
		$a=$a+100; 
	} 
	$b=1; 
	echo $b;//输出１ 
	test($b); //这里$b传递给函数的其实是$b的变量内容所处的内存地址，通过在函数里改变$a的值　就可以改变$b的值了 
	echo "<br>"; 
	echo $b;//输出101
?>
```

#### 函数的引用返回,即变量的返回值被引用,可直接修改函数中static变量的值

```php
<?php 
	function &test() 
	{ 
		static $b=0;//申明一个静态变量 
		$b=$b+1; 
		echo $b; 
		return $b; 
	} 
	$a=test();//这条语句会输出　$b的值　为１ 
	$a=5; 
	$a=test();//这条语句会输出　$b的值　为2 
	$a=&test();//这条语句会输出　$b的值　为3 
	$a=5; 
	$a=test();//这条语句会输出　$b的值　为6
?>
```

#### 对象的引用,对象通过等号复制是按引用复制,如果想新创建一个对象副本需要使用__clone

```php
	<?php
	class a{ 
		var $abc="ABC"; 
	} 
	$b=new a; 
	$c=$b; 
	echo $b->abc;//这里输出ABC 
	echo $c->abc;//这里输出ABC 
	$b->abc="DEF"; 
	echo $c->abc;//这里输出DEF 
	?>
```

### 取消引用

```php
<?php 
	$a = 1; 
	$b =& $a; 
	unset ($a); //只是断开变量名$a与变量值的关系,并未清除变量值
	echo($b);		//输出:1
?> 
```
—— Wenlh
