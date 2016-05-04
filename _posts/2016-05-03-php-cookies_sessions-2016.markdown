---
layout:     post
title:      "PHP：cookies & sessions"
subtitle:   " \"PHP：cookies & sessions\""
date:       2016-05-03 8:00:00
author:     "Wenlh"
header-img: "img/myson.jpg"
catalog: true
tags:
    - PHP
---

## cookies & sessions

#### [cookies](http://www.w3school.com.cn/php/php_cookies.asp)

* setcookie() 函数必须位于 <html> 标签之前
* setcookie()函数用于设置 cookie,setcookie(name, value, expire, path, domain);


```php
<?php 
setcookie("user", "Alex Porter", time()+3600);
?>

<html>
<body>

</body>
</html>
```

* 使用 isset() 函数来确认是否已设置了 cookie, $_COOKIE 变量用于取回 cookie 的值

```php
<html>
<body>

<?php
if (isset($_COOKIE["user"]))
  echo "Welcome " . $_COOKIE["user"] . "!<br />";
else
  echo "Welcome guest!<br />";
?>

</body>
</html>
```

* 当删除 cookie 时，您应当使过期日期变更为过去的时间点

```php
<?php 
// set the expiration date to one hour ago
setcookie("user", "", time()-3600);
?>
```

#### [sessions](http://www.w3school.com.cn/php/php_sessions.asp)

* session_start() 函数必须位于 <html> 标签之前

```php
<?php session_start(); ?>

<html>
<body>

</body>
</html>
```

* 存储和取回 session 变量的正确方法是使用 PHP $_SESSION 变量

```php
<?php
session_start();
// 存储session计数器
if(isset($_SESSION['views']))
  $_SESSION['views']=$_SESSION['views']+1;
else
  $_SESSION['views']=1;
?>

<html>
<body>

<?php
//retrieve session data
echo "Pageviews=". $_SESSION['views'];		\\输出:Pageviews=1
?>

</body>
</html>
```

- 结束session
  - unset() 函数用于释放指定的 session 变量
  - session_destroy() 函数彻底终结 session
> session_destroy() 将重置 session，您将失去所有已存储的 session 数据

```php
\\释放views的session
<?php
unset($_SESSION['views']);
?>

\\释放全部session
<?php
session_destroy();
?>
```

—— Wenlh
