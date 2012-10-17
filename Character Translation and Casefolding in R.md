Character Translation and Casefolding in R——R中的字符转换和大小写转换
========================================================

### 需求分析
* 在R的使用中，有可能之前输入的字符中有输入的字母或者颠倒了顺序的字母。如果数量一多，一个一个改总会觉得有些耗时，还好R中有chartr()函数可以解决这样的问题。
* 而有时，我们时常会遇到一些数据框的列名或者行名的首字母是大写，而其他字母是小写的，有的时候为了统一，我们总是希望将列名全转换成小写或者全转换成大写。而R中也提供了对应的函数。

> 以下函数全都来源自base包中。

### 函数的用途和参数
* chartr(old,new,x),就是讲x中需要改正的字母写在old中，更正过的字母写在new中，就可以将x中的字母快速的修正过来。
* tolower(x)：是将x中的大写改成小写，小写字母不变;
* toupper(x)：是将x中的小写改成大写，大写字母不变；
* casefold(x,upper = FALSE)：是将上述两个函数通过一个函数来实现了，当upper = T的时候，输出的全部为大写字母，反之为小写字母，默认的为输出小写字母。

### 实例分析
我们来处理字符“"MiXeD cAsE 123"”，如果这里的i要更正为w，X更正为h，s更正为y,然后再大小写统一格式。就可以如下操作：

```r
# 处理对象只能是字符
x <- "MiXeD cAsE 123"
# 更正字母
x
```

```
## [1] "MiXeD cAsE 123"
```

```r
chartr("iXs", "why", x)
```

```
## [1] "MwheD cAyE 123"
```

```r

tolower(x)
```

```
## [1] "mixed case 123"
```

```r
toupper(x)
```

```
## [1] "MIXED CASE 123"
```

```r
casefold(x, upper = FALSE)
```

```
## [1] "mixed case 123"
```

```r
casefold(x, upper = TRUE)
```

```
## [1] "MIXED CASE 123"
```

如果需要改正的字母在字母表的位置是挨着的，就可以用简化的形式来完成更正：



```r
y = "abondon relaX"
# 需要将a-D,b-E,c-F,X-w
y
```

```
## [1] "abondon relaX"
```

```r
chartr("a-cX", "D-Fw", y)
```

```
## [1] "DEondon relDw"
```



