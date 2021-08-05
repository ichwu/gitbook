# 通用正则表达式

Youtube视频：【[30分钟学会正则表达式\(看完就会\)](https://www.youtube.com/watch?v=i_rMqj-bm44)】

Youtube视频：【[5/19 Live公开课：一小时熟悉正则表达式Regular Expression](https://www.youtube.com/watch?v=fmggOEPFW2c)】

编程胶囊：【[https://codejiaonang.com/\#/courses](https://codejiaonang.com/#/courses)】

正则表达式工具：【[https://regexr-cn.com](https://regexr-cn.com)】

正则表达式工具：【[https://regex101.com](https://regex101.com)】

【[ 正则表达式 学习指南](https://fe.rualc.com/note/regexp.html#zheng-ze-biao-da-shi-jian-jie)】



正则表达式可用于：Search/Match\(Validation\)、Replace、Extract



### Special sequences

|  | Sepecial sequences |
| :--- | :--- |
| \d | digit\(0-9\) |
| \D | Not a digit\(0-9\) |
| \w | Word character\(a-z, A-Z, 0-9, \_） |
| \W | Not a word character |
| \s | Whitespace\(space, tab, blank line\) |
| \S | Non-Whitespaces |
|  |  |
| \b | Word boundary |
| \B | Not a word boundary |
| \A | Start of string  ^ |
| \Z | End of string $ |
| \g&lt;id&gt; | Matches a previously defined group |

### Special characters

|  | Sepecial characters |
| :--- | :--- |
| \ | Escape special character |
| . | Matches any character\(except for line terminators\) |
| ^ | Matches start of string |
| $ | Matches end of string |
| \[\] | Matches characters in brackets\(其中一个\) |
| \[^\] | Matches characters NOT in brackets |
| \| | Either or |
| \(\) | Group |

### Quantifiers

| Quantifiers |  |
| :--- | :--- |
| \* | 0 or more |
| + | 1 or more |
| ? | 0 or more |
| {m} | Exactly m times |
| {n,} | Min n times |
| {m, n} | From m to n times |
| {m, n}? | From m to n times, as few as possible |

### Test string

```text
abcdefghijklmnopqrstuvwxyz
ABCDEFGHIJKLMNOPQRSTUVWXYZ
0123456789
_!@#$%^&*()\{}[]
123-456-7890
987_654_3210
666 666 6666
HaHa Ha
somebody123@gmail.com
somebody@fb.com
some@yale.edu
First Last
First.Last
```



