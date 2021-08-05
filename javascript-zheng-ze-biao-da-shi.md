# JavaScript正则表达式

通过使用regex101网站匹配举例：

```javascript
const regex = /<([^>]*)>\(([^\)]*)\)/gm;
const str = `  <ichwu>(a) <wuchi>(b) <57>(c) <der>(d) dksafjl kkdjfsjeiafjdsi`;
let m;

while ((m = regex.exec(str)) !== null) {
    // This is necessary to avoid infinite loops with zero-width matches
    if (m.index === regex.lastIndex) {
        regex.lastIndex++;
    }
    
    // The result can be accessed through the `m`-variable.
    m.forEach((match, groupIndex) => {
        console.log(`Found match, group ${groupIndex}: ${match}`);
    });
}
```

#### node index.js 

通过while循环几次输出结果如下：

```bash
Found match, group 0: <ichwu>(a)
Found match, group 1: ichwu
Found match, group 2: a
Found match, group 0: <wuchi>(b)
Found match, group 1: wuchi
Found match, group 2: b
Found match, group 0: <57>(c)
Found match, group 1: 57
Found match, group 2: c
Found match, group 0: <der>(d)
Found match, group 1: der
Found match, group 2: d
```

通过while循环几次并单独输出m结果如下：

```bash
[
  '<ichwu>(a)',
  'ichwu',
  'a',
  index: 2,
  input: '  <ichwu>(a) <wuchi>(b) <57>(c) <der>(d) dksafjl kkdjfsjeiafjdsi',
  groups: undefined
]
[
  '<wuchi>(b)',
  'wuchi',
  'b',
  index: 13,
  input: '  <ichwu>(a) <wuchi>(b) <57>(c) <der>(d) dksafjl kkdjfsjeiafjdsi',
  groups: undefined
]
[
  '<57>(c)',
  '57',
  'c',
  index: 24,
  input: '  <ichwu>(a) <wuchi>(b) <57>(c) <der>(d) dksafjl kkdjfsjeiafjdsi',
  groups: undefined
]
[
  '<der>(d)',
  'der',
  'd',
  index: 32,
  input: '  <ichwu>(a) <wuchi>(b) <57>(c) <der>(d) dksafjl kkdjfsjeiafjdsi',
  groups: undefined
]

```







