R函数介绍：colsplit()
========================================================

### 函数的用途
如果我们需要将一些有规律的变量名拆分开，colsplit()将会方便的完成任务，并且将拆分好的数据分别放在不同的列中。常见的篮球数据中的投篮数据，比如12/20，我们需要将12和20分离开，来分析该球员的投篮次数和投中的次数，再比如时间数据类型，2012/10/17，还有变量名a_1等。

### 函数的参数


```r
colsplit(string, pattern, names)
```

* string :需要拆分的字符向量或者因子
* pattern ：拆分的依据或者方式，正则形式
* names:输出列的列名

> colsplit函数位于reshape2包中。

### 实例分析
1、分离变量名，并保存在各列中

```r
library(reshape2)
x <- c("a_1", "a_2", "b_2", "c_3")
vars <- colsplit(x, "_", c("trt", "time"))
vars
```

```
##   trt time
## 1   a    1
## 2   a    2
## 3   b    2
## 4   c    3
```

```r
str(vars)
```

```
## 'data.frame':	4 obs. of  2 variables:
##  $ trt : chr  "a" "a" "b" "c"
##  $ time: int  1 2 2 3
```

2、分离投篮数据

```r
x <- c("10/20", "5/8", "12/24")
vars <- colsplit(x, "/", c("success", "shots"))
vars
```

```
##   success shots
## 1      10    20
## 2       5     8
## 3      12    24
```

```r
str(vars)
```

```
## 'data.frame':	3 obs. of  2 variables:
##  $ success: int  10 5 12
##  $ shots  : int  20 8 24
```

3、分离时间数据

```r
x <- c("2010-10-11", "2012-11-11", "2012-10-17")
vars <- colsplit(x, "-", c("year", "month", "day"))
vars
```

```
##   year month day
## 1 2010    10  11
## 2 2012    11  11
## 3 2012    10  17
```

```r
str(vars)
```

```
## 'data.frame':	3 obs. of  3 variables:
##  $ year : int  2010 2012 2012
##  $ month: int  10 11 10
##  $ day  : int  11 11 17
```

……
