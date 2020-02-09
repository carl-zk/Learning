# sprintf

- 把百分号（%）符号替换成一个作为参数进行传递的变量：
- [PHP sprintf() 函数 | 菜鸟教程](https://www.runoob.com/php/func-string-sprintf.html)

## Demo

```php
<?php
$number = 9;
$str = "RUNOOB";
$txt = sprintf("%s 每天有 %u 万人在访问！", $str, $number);
echo $txt;
?>
// 执行输出结果如下：
RUNOOB 每天有 9 万人在访问！
```

```c#

参数 描述
format 必需。规定字符串以及如何格式化其中的变量。
可能的格式值：

%% - 返回一个百分号 %
%b - 二进制数
%c - ASCII 值对应的字符
%d - 包含正负号的十进制数（负数、0、正数）
%e - 使用小写的科学计数法（例如 1.2e+2）
%E - 使用大写的科学计数法（例如 1.2E+2）
%u - 不包含正负号的十进制数（大于等于 0）
%f - 浮点数（本地设置）
%F - 浮点数（非本地设置）
%g - 较短的 %e 和 %f
%G - 较短的 %E 和 %f
%o - 八进制数
%s - 字符串
%x - 十六进制数（小写字母）
%X - 十六进制数（大写字母）
附加的格式值。必需放置在 % 和字母之间（例如 %.2f）：

+ （在数字前面加上 + 或 - 来定义数字的正负性。默认情况下，只有负数才做标记，正数不做标记）
' （规定使用什么作为填充，默认是空格。它必须与宽度指定器一起使用。例如：%'x20s（使用 "x" 作为填充））
- （左调整变量值）
[0-9] （规定变量值的最小宽度）
.[0-9] （规定小数位数或最大字符串长度）
注释：如果使用多个上述的格式值，它们必须按照上面的顺序进行使用，不能打乱。

arg1 必需。规定插到 format 字符串中第一个 % 符号处的参数。
arg2 可选。规定插到 format 字符串中第二个 % 符号处的参数。
arg++ 可选。规定插到 format 字符串中第三、四等等 % 符号处的参数。
技术细节
返回值： 返回已格式化的字符串。
PHP 版本：	4+
```