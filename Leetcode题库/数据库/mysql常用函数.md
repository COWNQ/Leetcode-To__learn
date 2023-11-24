

# 常用

## 执行顺序

推荐链接：https://developer.aliyun.com/article/1131899

```
//从上到下依次执行
from
on/using
join
where
group by
having
select
distinct
union
order by
limit
```

## 表连接方式

```mysql
inner join 
left join
right join
cross join  //交叉连接
```

## 聚合函数

| 函数    | 使用一                                           |      |
| ------- | ------------------------------------------------ | ---- |
| count() | **count( distinct  xxx)** <br />分组后去重再统计 |      |
| sum()   |                                                  |      |
| avg()   |                                                  |      |
| max()   |                                                  |      |
| min()   |                                                  |      |



##  常用关键字

| distinct                  | 过滤                              |
| ------------------------- | --------------------------------- |
| **union  \|   union all** | 拼接两个表（不带all，会自动去重） |
|                           |                                   |
|                           |                                   |
|                           |                                   |
|                           |                                   |
|                           |                                   |
|                           |                                   |



## 函数

| 函数                            | 说明                                                         | 其他 |
| ------------------------------- | ------------------------------------------------------------ | :--- |
| round( xxx , 2 )                | 保留小数点后两位                                             |      |
| if ( **xxx> 10** , 1,0 )        | 满足条件为1 否则为 0                                         |      |
| ifnull( **xxx** , 0)            | 用零替换null值                                               |      |
| group_concat                    | 分组后进行合并                                               |      |
| xxx  REGEXP  ' '                | 对xxx使用正则表达式                                          |      |
| mod( xxx, 2 ) = 1               | 找奇数（1为余数，xxx与 2取余 ）                              |      |
| concat( str1, str2 )            | 将字符串str1与str2合并                                       |      |
| left( xxx, 1 ) = "M"            | 左数第一位是M的数据                                          |      |
| substring_index( xxx ,'  ' , 1) | 以空格分隔，选第一个                                         |      |
| replace( str,  " , "  , "  ")   | 将字段中的逗号用空格替换                                     |      |
| substring( str,  1 , 3 )        | 截取字段str 从1到3的字符（非下标）    substring( str,  2)     截取字段str 从2以后 |      |
| upper(xxx)                      | 字符串转为大写                                               |      |
| lower(xxx)                      | 字符串转为小写                                               |      |
| length(xxx)                     | 查看长度                                                     |      |
| char_length(xxx)                | 查看字符长度                                                 |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |
|                                 |                                                              |      |

# 日期

> 以下xxx，xxxx均为 日期值    例如 ' 2019-07-27 '

| 函数                              | 说明                                   | 其他 |
| --------------------------------- | -------------------------------------- | ---- |
| date_format( **xxx** , '%Y-%m'  ) | 格式化日期                             |      |
| datediff ( xxx , xxxxx)  < 30     | 计算两日期差（**前大后小，所得为正**） |      |
| year( xxx )='2020'                | 格式化日期为年                         |      |
|                                   |                                        |      |
|                                   |                                        |      |
|                                   |                                        |      |
|                                   |                                        |      |
|                                   |                                        |      |
|                                   |                                        |      |



# 经验

1、**行转列** 使用union，**列转行**用if/case,记得要max与sum

2、关键字**in** | **not in** 的使用

```markdown
# 例子：select user_id from user where user_id in (1,2,3,4,5,6); 
逐步分析：可以看出上方sql想要找出 user表中user_id在1~6的id，可以理解为，查询user_id等于1~6的值；
		反之，`not in`的意思是查询user_id不等于1~6的值
```

