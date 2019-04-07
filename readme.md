# javascript的正则表达式

**RegExp 对象用于规定在文本中检索的内容。**

## 什么是 RegExp？

RegExp 是正则表达式的缩写。

当您检索某个文本时，可以使用一种模式来描述要检索的内容。RegExp 就是这种模式。

简单的模式可以是一个单独的字符。

更复杂的模式包括了更多的字符，并可用于解析、格式检查、替换等等。

您可以规定字符串中的检索位置，以及要检索的字符类型，等等。

## 创建对象

```javascript
//JS风格
let re=new RegExp('\\d+', 'g');
//perl风格
let re=/\d+/g;
```

## 修饰符

| 修饰符                                                   | 描述                                                     |
| :------------------------------------------------------- | :------------------------------------------------------- |
| i | 执行对大小写不敏感的匹配。                               |
| g | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
| m                                                        | 执行多行匹配。                                           |

方括号用于查找某个范围内的字符：

| 表达式             | 描述                               |
| :----------------- | :--------------------------------- |
| [abc]              | 查找方括号之间的任何字符。         |
| [^abc\]            | 查找任何不在方括号之间的字符。     |
| [0-9]              | 查找任何从 0 至 9 的数字。         |
| [a-z]              | 查找任何从小写 a 到小写 z 的字符。 |
| [A-Z]              | 查找任何从大写 A 到大写 Z 的字符。 |
| [A-z]              | 查找任何从大写 A 到小写 z 的字符。 |
| [adgk]             | 查找给定集合内的任何字符。         |
| [^adgk]            | 查找给定集合外的任何字符。         |
| (red\|blue\|green) | 查找任何指定的选项。               |

## 元字符

元字符（Metacharacter）是拥有特殊含义的字符：

| 元字符 | 描述                                        |
| :----- | :------------------------------------------ |
| .      | 查找单个字符，除了换行和行结束符。          |
| \w     | 查找单词字符。[a-z0-9_]                     |
| \W     | 查找非单词字符。                            |
| \d     | 查找数字。[0-9]                             |
| \D     | 查找非数字字符。[ ^0-9 ]                    |
| \s     | 查找空白字符。                              |
| \S     | 查找非空白字符。                            |
| \b     | 匹配单词边界。                              |
| \B     | 匹配非单词边界。                            |
| \0     | 查找 NUL 字符。                             |
| \n     | 查找换行符。                                |
| \f     | 查找换页符。                                |
| \r     | 查找回车符。                                |
| \t     | 查找制表符。                                |
| \v     | 查找垂直制表符。                            |
| \xxx   | 查找以八进制数 xxx 规定的字符。             |
| \xdd   | 查找以十六进制数 dd 规定的字符。            |
| \uxxxx | 查找以十六进制数 xxxx 规定的 Unicode 字符。 |

## 量词

| 量词   | 描述                                        |
| :----- | :------------------------------------------ |
| +      | 匹配任何包含至少一个 的字符串。{ 1, }       |
| *      | 匹配任何包含零个或多个  的字符串。          |
| ?      | 匹配任何包含零个或一个  的字符串。{0 , 1}   |
| n{X}   | 匹配包含 X 个 n 的序列的字符串。            |
| n{X,Y} | 匹配包含 X 至 Y 个 n 的序列的字符串。       |
| n{X,}  | 匹配包含至少 X 个 n 的序列的字符串。        |
| n$     | 匹配任何结尾为 n 的字符串。                 |
| ^n     | 匹配任何开头为 n 的字符串。                 |
| ?=n    | 匹配任何其后紧接指定字符串 n 的字符串。     |
| ?!n    | 匹配任何其后没有紧接指定字符串 n 的字符串。 |

## 支持正则表达式的 String 对象的方法

| 方法    | 描述                             |
| :------ | :------------------------------- |
| search  | 检索与正则表达式相匹配的值。     |
| match   | 找到一个或多个正则表达式的匹配。 |
| replace | 替换与正则表达式匹配的子串。     |
| split   | 把字符串分割为字符串数组。       |

match

```javascript
let str='f34rrfsdf 45tsdgsrdg 5terg56456fdghdr675 dsf3434535645645645674567';
let re=/\d+/g;

alert(str.match(re));
```

search

```javascript
    let str='Aweqesdfaerq';
    let re=/a/i;

    alert(str.search(re));
```

replace

```javascript
  let str='asdfde we fsadfas weAr efAf';

    alert(str.replace(/a/gi, '*'));
```

split

```javascript
window.onload=function (){
let oDiv=document.getElementById('div1');
let str='sdfsf##dfasderferfef##dfdfsgdsgf##dgdfbfdghg';
oDiv.innerHTML=str.split(/##/g).map(item=>{
return `<p>${item}</p>`;
	}).join('');
};
```

## RegExp 对象方法

| 方法    | 描述                                               |
| :------ | :------------------------------------------------- |
| compile | 编译正则表达式。                                   |
| exec    | 检索字符串中指定的值。返回找到的值，并确定其位置。 |
| test    | 检索字符串中指定的值。返回 true 或 false。         |

```javascript
window.onload=function (){
      let oTxt=document.getElementById('txt1');
      let oBtn=document.getElementById('btn1');

      oBtn.onclick=function (){
        let re=/\.(jpg|gif|png)$/i;

        if(re.test(oTxt.value)){
          alert('通过');
        }else{
          alert('不对');
        }
      };
};
```

