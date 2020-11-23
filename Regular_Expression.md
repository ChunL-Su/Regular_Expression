# Regular Expression符号含义
- __规定0、. (规定.为除\n,\r的任意字符)__
- __规定1、()  小括号用于‘提取’括号中表达式匹配到的字符串__
- __规定2、[]  中括号用于‘标定’其中表达式的取值‘范围’__
- __规定3、{}  大括号一般用于‘限定字符串长度’__
- __规定4、匹配字符串从"^开始，$结束"。若^在[]中，则表示非__

- **1、+ (>=1个某字符)**
    - run+d  -->  'rund',''runnd','runnnd'...

- __2、* (>=0个某字符)__
    - run*d  -->  'rud','rund','runnd'...

- **3、? (0/1个某字符)**
    - run?d  -->  'rud','rund'
- __4、[...] (匹配[]中存在的某个字符)__
    - 目标文本：我是来自月亮der
    - [我dz]  -->  '我','d'
- __5、[^...] (返回除了[]中存在的字符的所有字符)__
    - 目标文本：我是来自月亮der
    - [^我dz] -->  '是','来','自','月','亮','e','r'
- __6、[A-Z],[a-z] (你懂的)__

- __7、\\s,\\S__
    - \s: (匹配所有空白符，以及换行符)
    - \S: (匹配非空白符)

- __8、\w  (匹配字母、数字、下划线)__
    - 等价于[A-Za-z0-9_]
- __9、限定符{}的使用__
    - {n,} : 匹配>=n个某字符
    - {n,m} : 匹配>=n,<=m个某字符
- __10、非捕获元__
    - ?= : exp1(?=exp2) 查找exp2前面的exp1
    - ?<= : (?<=exp1)exp2  查找exp1后面的exp2
    - ?! : exp1(?!exp2)  找后面不是exp2的exp1
    - ?<! : (?<!exp1)exp2  找前面不是exp1的exp2

## 先消化一下上面的内容，反向引用之后再总结...


# Python中使用 regular expression
- 1、re.match() 仅在字符串起始位置匹配字符串
```python
import re
str = 'An apple and an pear.'
result = re.match('([Aa]n+)', str, flags=0).span()
# 只会返回开头的‘An’的位置(0,3)
# 注：match方法的文档还是很简洁的....
```
```
help(re.match)
>>>
Help on function match in module re:

match(pattern, string, flags=0)
    Try to apply the pattern at the start of the string, returning
    a Match object, or None if no match was found.
```

- 2、re.search() 从左向右找整个串，返回第一个遇到的符合的串的位置
```python
import re
str = 'The apple and an pear.'
result = re.search('([Aa]n+)', str, flags=0).span()
# 只会返回'an'的位置(10,12)
# 注：search方法的文档同样简洁....
```
```
help(re.search)
>>>
Help on function search in module re:

search(pattern, string, flags=0)
    Scan through string looking for a match to the pattern, returning
    a Match object, or None if no match was found.
```