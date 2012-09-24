R�������ܣ�merge()
========================================================

### ��������;
�������data frame ����ͬ���л����У���ϣ����������data frameͨ��������ͬ���л�������ϳ�һ��data frame�����γɵ����data frame��ǰ����data frame�������е���Ϣ��ֻ��������ͬ�����ں�Ϊһ����
> �ںϣ��ϲ�Ҳ��merge���ʵı��塣


### �����Ĳ���

```r
merge(x, y, by = intersect(names(x), names(y)), by.x = by, by.y = by, all = FALSE, 
    all.x = all, all.y = all, sort = TRUE, ...)
```

���õľ�����Щ����:
* x��y������������Ҫ�ںϺϲ������ݿ�
* by��x��y���ں�����Ҫ����ͬ���У�����һ�£�
* by.x,by.y������x��y����1��������һ���ģ������������е�������һ�µ�ʱ��x��y�ں���x�е�by.x�к�y�е�by.y���ںϣ�
* all:Ĭ��ֵΪFALSE����ֻ��ʾx��y���ں��ж��еĲ��֣����������x����һ��y��û�У��򶼲���ʾ��ͬ��y����һ��x��û�У�Ҳ����ʾ����all=TRUE,����ʾx��y���ںϵ������У�ȱʧ����NA��ʾ��
* all.x,all.y:all.x��ΪTRUE��ʱ����ʾ�ں�����x�������У�ͬ��all.y;
* sort:Ĭ��ΪTRUE���������γɵ����ݿ��е�һ�е���������ĸ˳�������ֵ˳�����򣬿�����ԭ���ݿ��˳��һ�£������all�ĳ�FALSE������x����˳��Ϊ�����ݿ����˳��

### ʵ������
1��x��y�ں�������ͬ������k1

```r
x <- data.frame(k1 = c("A", "B", "E", "D", "C"), names = c("Tukey", "Venables", 
    "Tierney", "Ripley", "Ripley"))

y <- data.frame(k1 = c("A", "G", "C", "D", "B"), nationality = c("US", "Australia", 
    "US", "UK", "Australia"))
merge(x, y, by = "k1")
```

```
##   k1    names nationality
## 1  A    Tukey          US
## 2  B Venables   Australia
## 3  C   Ripley          US
## 4  D   Ripley          UK
```

���Կ��������������ݿ��ں�Ϊһ��������allĬ��ΪFALSE������ֻ��ʾx��k1��y��k2���еĲ���A��B��C��D�У�����sortĬ��ΪTRUE�����������ɵ����ݿ�ĵ�һ�а�����ĸ˳�����У�
�������sort�ı䣺

```r
merge(x, y, by = "k1", sort = FALSE)
```

```
##   k1    names nationality
## 1  A    Tukey          US
## 2  B Venables   Australia
## 3  D   Ripley          UK
## 4  C   Ripley          US
```

���Կ����ǰ���x��k1�е�˳�����С�
�������ٿ�����ں��е�������һ�£�

```r
x <- data.frame(k1 = c("A", "B", "E", "D", "C"), names = c("Tukey", "Venables", 
    "Tierney", "Ripley", "Ripley"))

y <- data.frame(l1 = c("A", "G", "C", "D", "B"), nationality = c("US", "Australia", 
    "US", "UK", "Australia"))
merge(x, y, by = "k1")
```

```
## Error: 'by' must specify uniquely valid column(s)
```

```r
merge(x, y, by.x = "k1", by.y = "l1")
```

```
##   k1    names nationality
## 1  A    Tukey          US
## 2  B Venables   Australia
## 3  C   Ripley          US
## 4  D   Ripley          UK
```


�����all�ı仯��

```r
x <- data.frame(k1 = c("A", "B", "E", "D", "C"), names = c("Tukey", "Venables", 
    "Tierney", "Ripley", "Ripley"))

y <- data.frame(k1 = c("A", "G", "C", "D", "B"), nationality = c("US", "Australia", 
    "US", "UK", "Australia"))
merge(x, y, by = "k1")
```

```
##   k1    names nationality
## 1  A    Tukey          US
## 2  B Venables   Australia
## 3  C   Ripley          US
## 4  D   Ripley          UK
```

```r
merge(x, y, by = "k1", all = T)
```

```
##   k1    names nationality
## 1  A    Tukey          US
## 2  B Venables   Australia
## 3  C   Ripley          US
## 4  D   Ripley          UK
## 5  E  Tierney        <NA>
## 6  G     <NA>   Australia
```

```r
merge(x, y, by = "k1", all.x = T)
```

```
##   k1    names nationality
## 1  A    Tukey          US
## 2  B Venables   Australia
## 3  C   Ripley          US
## 4  D   Ripley          UK
## 5  E  Tierney        <NA>
```

������Ĵ���ͽ�������Ŵ�ҿ��������all�Ĺ��ܡ�
