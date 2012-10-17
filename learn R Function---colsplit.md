R�������ܣ�colsplit()
========================================================

### ��������;
���������Ҫ��һЩ�й��ɵı�������ֿ���colsplit()���᷽���������񣬲��ҽ���ֺõ����ݷֱ���ڲ�ͬ�����С����������������е�Ͷ�����ݣ�����12/20��������Ҫ��12��20���뿪������������Ա��Ͷ��������Ͷ�еĴ������ٱ���ʱ���������ͣ�2012/10/17�����б�����a_1�ȡ�

### �����Ĳ���


```r
colsplit(string, pattern, names)
```

* string :��Ҫ��ֵ��ַ�������������
* pattern ����ֵ����ݻ��߷�ʽ��������ʽ
* names:����е�����

> colsplit����λ��reshape2���С�

### ʵ������
1��������������������ڸ�����

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

2������Ͷ������

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

3������ʱ������

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

����
