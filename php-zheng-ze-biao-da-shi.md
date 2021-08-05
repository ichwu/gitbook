# PHP正则表达式



```php
// 正则匹配
echo preg_match('/a/', 'abcdef1123');

// 拆分与合并
$str = "1.jpg@b.jpn*c.jpg";
$next = preg_split('/[*@#]/', $str);
echo implode('-', $next);

// 边界限度
$reg = '/^12$/';  // ^ 限定开头  $ 限定结尾

// 原子组
$str = "1.phg 2.png 3.jpg 4.git";
echo preg_match('/(png)/', $str);

$a = "bing: bing.com google: google.com ";
$reg = '/(com)/';
echo preg_replace($reg, '<h1>\1</h1>', $a);

$str = "12bing:12 com bing.com google: google.com";
$reg = '/(bing|google)\./';
$to = '\1.';
echo preg_replace($reg, $to, $str);

// \1代表第一个 \2代表第二个 \0代表全部
```

### 重复匹配 

```php
'/^.$/'       .     匹配[0,∞]   如 eior
'/^\d+$/'     +     匹配[1,∞]   如 2 34
'/^\d?$/'     ?     匹配[0,1]   如 4
'/^\d{4}$/'   {n}   匹配n次     如 3435
'/^\d{3,}$/'  {n,}  匹配n次以上  如 333
'/^\d{2,5}$/' {n,m} 匹配[n,m]   如 333
```

### 网址匹配

```php
$str = "http://www.ichwu.com";
$reg = '/http:\/\/[0-9a-zA-Z.-]+\.(com|net|org|cn)/';
echo preg_match($reg, $str);
```

### 标签匹配

```php
$str = "dsfd<h1>ichwu</h1>fdkf";
$replace = "<h1><a href='https://ichwu.com'>\\1</a></h1>";
$reg = '/<h1>(.+)<\/h1>/';
$next = preg_replace($reg, $replace, $str);
echo $next;
```

### 贪婪匹配

```php
// 默认贪婪匹配
$str = "hei <h1>first</h1> next <h1>second</h1> ";
$reg = '/<h1>(.+)<\/h1>/';
$replace = '<a><h1>\1</h1></a>';
echo preg_replace($reg, $replace, $str);
preg_match($reg, $str, $next);
print_r($next);

// 非贪婪匹配
$str = "hei <h1>first</h1> next <h1>second</h1> ";
$reg = '/<h1>(.+?)<\/h1>/';
$replace = '<a><h1>\1</h1></a>';
echo preg_replace($reg, $replace, $str);

preg_match($reg, $str, $next);       // 单次匹配
print_r($next);
preg_match_all($reg, $str, $next);   // 匹配全部
print_r($next);
```

### 基础匹配符

```php
元字符
\d 0～9
\D ^0~9
\w a~zA~Z0~9
\W ^a~zA~Z0~9

空白符
\s 任意空白
\S 非任意空白
\n 换行
\t 制表符

原子表
[abd] 相互独立
[0-9]
[a-z]
. 任意字符（除换行符）
^ 除了
[^678] 除了678
```

### 模式修饰符

```php
// i 模式修饰符：忽略大小写
$str = "hei <h1>first</h1> next <H1>second</H1> ";
$reg = '#<h([1-6])>(.*?)</h\1>#i';    // \1代表第一个括号
$replace = '\2';
echo preg_replace($reg, $replace, $str);

// s 模式修饰符：使.能匹配包括换行符的任意字符
$str = "hei <h1>first
</h1> 
next <H1>second
</H1> ";
$reg = '#<h([1-6])>(.*?)</h\1>#is';   // \1代表第一个括号
$replace = '\2';
echo preg_replace($reg, $replace, $str);

// m 模式修饰符：多行处理
$str = <<<html
hei 
<h1>first</h1> next 
@<H1>second</H1> 
<H1>second</H1> 
html;

$reg = '#^<h([1-6])>(.*?)</h\1>#im';
$replace = '\2';
echo preg_replace($reg, $replace, $str);

// x 模式修饰符：忽略空白及# 可用于在表达式中添加注释
$str = "acb";
$reg = "@acb  
#这是一个注释@x";
echo preg_match($reg, $str);

// U 模式匹配符：最小匹配 类似与?
$str = "<h1>fd</h1><h1>ne</h1>";
$reg = '#<h1>(.+)</h1>#U';
preg_match_all($reg, $str, $matchs);
print_r($matchs);

// A 模式修饰符：代表开头 类似与^
$str = "dd@ichwu@outlook.com";
$reg = "#^(\w+)@(\w)+\.(com|net|org)#";
$reg = "#(\w+)@(\w)+\.(com|net|org)#A";
echo preg_match($reg, $str);

// D 模式匹配符：当用$限定结尾时 不允许有换行符
$str = "13243a\n";
$reg = "#\d+a$#D";
echo preg_match($reg, $str);
```

### 常用函数

```php
// 匹配
$str = "1@2#5";
$reg = '/\d/';
echo preg_match($reg, $str);

// 拆分
$str = "1@2#5";
$reg = '/@|#/';
$split = preg_split($reg, $str);
print_r($split);

// 替换
$str = "1@2#5";
$reg = '/@|#/';
$replace = '-';
$replace = preg_replace($reg, $replace, $str);
echo $replace;

// 替换 callback
$str = "1@2#5";
$reg = '/\d/';
$replace = preg_replace_callback($reg, function ($matchs) {
    print_r($matchs);
    if ($matchs[0] > 2) $matchs[0] += 200;
    return $matchs[0];
}, $str);
echo $replace;
```

