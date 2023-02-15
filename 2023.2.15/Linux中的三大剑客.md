---
title: Linux中的三大剑客
icon: note
category:
  - Linux
tag:
  - Linux
sticky: false
star: false
article: true
timeline: true
---

## 前言

* `Linux`三剑客：**`grep`、`awk`、`sed`**
* `Linux` 三剑客以**正则表达式**作为基础，而在`Linux`系统中，支持两种正则表达式，**分别为“`标准正则表达式`”和“`扩展正则表达式`”。**
* 三剑客的**特点及应用场景**

| 命令   | 特点     | 应用场景                                                     |
| ------ | -------- | ------------------------------------------------------------ |
| `grep` | 文本过滤 | 包括**从文件中进行过滤**和**从标准输入进行过滤**，其过滤速度**最快** |
| `sed`  | 取行     | 文件内容**新增、删除、替换、取出**某个范围的内容             |
| `awk`  | 取列     | **编写`awk`脚本对文本进行格式化输出（可进行统计计算）**      |

## 正则表达式

通过特定的**字符串匹配模板**，来获取到所需的内容。

### 元字符

`.`：匹配**任意单个字符；**

`[]`：匹配**指定范围内**的任意单个字符；

`[^]`：匹配**指定范围外**的任意单个字符；

### 字符集合

`[[:digit:]]`：匹配单个数字；

`[[:lower:]]`：匹配单个小写字母；

`[[:upper:]]`：匹配单个大写字母；

`[[:punct:]]`：匹配单个标点字符；

`[[:space:]]`：匹配单个空白字符；

`[[:alpha:]]`：匹配单个字母；

`[[:alnum:]]`：匹配单个字母或数字；

### 匹配次数-贪婪模式

`*`：匹配其前面的字符任意次

`?`：匹配其前面的字符0次或者1次

`+`：匹配其前面的字符至少1次

`.*`：任意长度的任意字符

### 位置锚定

`^`: 锚定行首，此字符后面的任意内容必须出现在行首

`$`: 锚定行尾，此字符前面的任意内容必须出现在行尾

`^$`: 空白行

### Linux实际使用

由于`Linux`系统`Shell`解释器的特殊处理，某些元字符在`Linux`下具有展开式等特殊含义，在实际的使用过程中我们需要添加`\`进行转义。

`\?`：匹配其前面的字符1次或0次；

`\+`：匹配其前面的字符至少1次；

`\{m,n\}`：匹配其前面的字符至少m次，至多n次；
`\{1,\}`：匹配前面的字符至少1次；
`\{0,3\}`：匹配前面的字符0次至3次均可；

## 扩展正则表达式











## 正则表达式辅助工具

* [any-rule](https://github.com/any86/any-rule)
  * 常用正则大全, 支持`web` / `vscode` / `idea` / `Alfred Workflow`多平台。
  * `Gitee`地址：https://gitee.com/mirrors/any-rule
  * 在`IDEA`的插件市场中搜索`any-rule`进行安装，重启生效，在需要使用正则表达式的地方可`右键`或者使用`option+a`调出窗口。
  * 在`IDEA`偏好设置中搜索`any-rule`，可以随时`更新官网收集的正则表达式规则`，除此之外，还可以`查看、添加、编辑、删除`所有的正则表达式规则。
* [Expressions](https://apps.apple.com/cn/app/expressions/id913158085?mt=12)
  * `Mac`上的正则表达式测试工具，支持语法高亮。
  * `a.*z`是贪婪模式。【默认是贪婪匹配，正则表达式引擎会尽可能地匹配满足条件的最大区间】
  * `a.*?z`是非贪婪模式。【在贪婪量词后面加`?` 即可实现非贪婪匹配】

* [菜鸟在线工具](https://c.runoob.com/front-end/854/)
  * 网址：https://c.runoob.com/front-end/854/


::: tip 参考

https://www.jianshu.com/p/10823e81f327

https://blog.csdn.net/qq_41622282/article/details/109242131

:::

## 常用的正则表达式

* 经常使用该正则表达式来**校验**一条数据的正确性，即是否为一条手机号数据？是否为一条身份证号数据？

<PDF url="/books/正则表达式速查备忘手册.pdf" :zoom="90"/>

## Java中使用正则表达式

* `Pattern` 类：
  * `Pattern` 对象是一个**正则表达式的编译表示**。`Pattern` 类没有公共构造方法。要创建一个 `Pattern` 对象，你必须首先调用其公共静态编译方法，它返回一个 `Pattern` 对象。该方法接受一个正则表达式作为它的第一个参数。
* `Matcher` 类：
  * `Matcher` 对象是**对输入字符串进行解释和匹配操作的引擎**。与`Pattern` 类一样，`Matcher` 也没有公共构造方法。你需要调用 `Pattern` 对象的 `matcher` 方法来获得一个 `Matcher` 对象。
  * `匹配器（Matcher）`对象可以执行三种不同的匹配操作
    *  `matches` 方法尝试**将整个输入序列与该模式匹配。**
    *  `lookingAt` 方法尝试**将输入序列从头开始与该模式匹配。**
    * `find` 方法**扫描输入序列以查找与该模式匹配的下一个子序列。**
* `PatternSyntaxException`：
  * `PatternSyntaxException` 是一个非强制异常类，它**表示一个正则表达式模式中的语法错误**。
* `Java`中使用正则表达式的**场景**
  * **场景一**：拿到一条数据，使用正则表达式进行校验，通过校验，返回`true`，反之，返回`false`。
  * **场景二**：给一条文本数据（字符串），从头到尾使用正则表达式进行匹配，例如给一条包含众多手机号的文本，打印该文本中手机号的所有个数及每一条手机号。

```java
/**
 * @Description: 正则表达式使用场景-校验
 * @Author: Mr.Tong
 */
@Test
public void testRegex() {
    // 1、使用方法一
    String str1 = "http://www.mysite.com/category/231";
    Pattern pattern = Pattern.compile("^https?://.*$");
    Matcher matcher = pattern.matcher(str1);
    System.out.println("str1 is match with pattern ? " + matcher.matches());
    // 2、使用方法二
    System.out.println("str1 is match with pattern ? " + Pattern.matches("^https?://.*$", "http://www.mysite.com/category/231"));
}

/**
 * @Description: 正则表达式使用场景-查找符合条件的子串个数及每一个子串
 * @Author: Mr.Tong
 */
@Test
public void testMatcher() {
    String str = "You may be out of my sight, but never out of my mind.";
    // 查找my的个数
    matchStringByRegularExpression(str, "my");
}

// 打印str中符合regex的字符串个数及每一个符合的字符串
private void matchStringByRegularExpression(String str, String regex) {
    int count = 0;
    Pattern p = Pattern.compile(regex);
    Matcher m = p.matcher(str);
    while (m.find()) {
        count++;
        System.out.println("匹配项" + count + "：" + m.group()); //group方法返回由以前匹配操作所匹配的输入子序列。
    }
    System.out.println("匹配个数为" + count);                              //结果输出
}

```

* 查找一个字符串中的所有身份证号个数，并打印每个身份证号

```java
@Test
public void testIdCardNumber() {
    String text = "371421199612340256english325632145231245632身份证号测试123456789123456789";
    Pattern pattern = Pattern.compile("\\d{18}|\\d{15}");
    Matcher matcher = pattern.matcher(text);

    int phoneNumberCount = 0;
    while (matcher.find()) {
        phoneNumberCount++;
        System.out.println(matcher.group());
    }
    System.out.println("====" + phoneNumberCount + "====");
}
```

::: tip 用于提取的正则表达式总结

```
提取信息中的网络链接:(h|H)(r|R)(e|E)(f|F) *= *('|")?(\w|\\|\/|\.)+('|"| *|>)?
提取信息中的邮件地址:\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*
提取信息中的图片链接:(s|S)(r|R)(c|C) *= *('|")?(\w|\\|\/|\.)+('|"| *|>)?
提取信息中的IP地址:(\d+)\.(\d+)\.(\d+)\.(\d+)
提取信息中的中国手机号码:(86)*0*13\d{9}
提取信息中的中国固定电话号码:(\(\d{3,4}\)|\d{3,4}-|\s)?\d{8}
提取信息中的中国电话号码（包括移动和固定电话）:(\(\d{3,4}\)|\d{3,4}-|\s)?\d{7,14}
提取信息中的中国邮政编码:[1-9]{1}(\d+){5}
提取信息中的中国身份证号码:\d{18}|\d{15}
提取信息中的整数:\d+
提取信息中的浮点数（即小数）:(-?\d*)\.?\d+
提取信息中的任何数字:(-?\d*)(\.\d+)?
提取信息中的中文字符串:[\u4e00-\u9fa5]*
提取信息中的双字节字符串 (汉字):[^\x00-\xff]*
```

:::

::: tip 参考

https://www.runoob.com/java/java-regular-expressions.html

https://blog.csdn.net/daguanjia11/article/details/78753072

https://blog.csdn.net/taotao12312/article/details/71330815

:::

## grep

* `grep`命令家族由`grep`、`egrep`、`fgrep` 三个子命令组成，适用于不同的场景。
  * `grep`：原生的`grep`命令，使用“**标准正则表达式**”作为匹配标准。【🔥】
  * `egrep`：扩展的`grep`命令，相当于`grep -E`，使用“**扩展正则表达式**”作为匹配标准。
  * `fgrep`：简化版的`grep`命令，相当于`grep -F`，不支持正则表达式，**只支持固定的字符串**，但搜索速度快，系统资源使用率低。

* `grep`常用方法【🔥】

```shell
- 【重要】Search for a pattern within a file:
    grep "search_pattern" path/to/file

- 【重要】Search for an exact string (disables regular expressions):
    grep --fixed-strings "exact_string" path/to/file

- Search for a pattern in all files recursively in a directory, showing line numbers of matches, ignoring binary files:
    grep --recursive --line-number --binary-files=without-match "search_pattern" path/to/directory

- 【重要】Use extended regular expressions (supports `?`, `+`, `{}`, `()` and `|`), in case-insensitive mode:
    grep --extended-regexp --ignore-case "search_pattern" path/to/file

- 【重要】Print 3 lines of context around, before, or after each match:
    grep --context|before-context|after-context=3 "search_pattern" path/to/file

- 【重要】Print file name and line number for each match with color output:
    grep --with-filename --line-number --color=always "search_pattern" path/to/file

- 【重要】Search for lines matching a pattern, printing only the matched text:
    grep --only-matching "search_pattern" path/to/file

- 【重要】Search stdin for lines that do not match a pattern:
    cat path/to/file | grep --invert-match "search_pattern"
```

* `egrep`常用方法

```shell
- 【重要】Search for a pattern within a file:
    egrep "search_pattern" path/to/file

- 【重要】Search for a pattern within multiple files:
    egrep "search_pattern" path/to/file1 path/to/file2 path/to/file3

- 【重要】Search stdin for a pattern:
    cat path/to/file | egrep search_pattern

- 【重要】Print file name and line number for each match:
    egrep --with-filename --line-number "search_pattern" path/to/file

- Search for a pattern in all files recursively in a directory, ignoring binary files:
    egrep --recursive --binary-files=without-match "search_pattern" path/to/directory

- 【重要】Search for lines that do not match a pattern:
    egrep --invert-match "search_pattern" path/to/file
```

* `fgrep`常用方法

```shell
- 【重要】Search for an exact string in a file:
    fgrep search_string path/to/file

- Search only lines that match entirely in files:
    fgrep -x path/to/file1 path/to/file2

- 【重要】Count the number of lines that match the given string in a file:
    fgrep -c search_string path/to/file

- Show the line number in the file along with the line matched:
    fgrep -n search_string path/to/file

- Display all lines except those that contain the search string:
    fgrep -v search_string path/to/file

- 【重要】Display filenames whose content matches the search string at least once:
    fgrep -l search_string path/to/file1 path/to/file2
```

::: tip 参考

https://www.cnblogs.com/zimskyzeng/p/11630071.html

https://www.runoob.com/linux/linux-comm-grep.html

:::

## sed

* `sed`全称为`Stream EDitor`，`sed`是一个流编辑器，在处理**行内容**时功能十分强大。
* 利用**脚本**来处理**文本文件或者是标准输入（`stdin`）。**
* 使用语法

```shell
sed [-hnV][-e<script>][-f<script文件>][文本文件]
```

* 常用**参数介绍**
  * `-e<script>`或`--expression=<script>` 以选项中指定的`script`来处理输入的文本文件。
  * `-f<script文件>`或`--file=<script文件>` 以选项中指定的`script文件`来处理输入的文本文件。
  * `-n`或`--quiet`或`--silent` 仅显示`script`处理后的结果，包含`-e`。
  * `-i`代表修改文件内容，包含`-e`。
* 动作说明
  * `a`：**新增**，`a` 的后面可以接字串，而这些字串会在新的一行出现（**目前的下一行**）
  * `c`：**取代**，`c` 的后面可以接字串，这些字串可以取代 `n1,n2` 之间的行【取代选择的行】
  * `d`：**删除**，因为是删除，所以 `d` 后面通常不接任何东西
  * `i`：**新增**，`i` 的后面可以接字串，而这些字串会在新的一行出现（**目前的上一行**）
  * `p`：**打印**，将某个选择的数据印出，通常 `p` 会与参数 `sed -n` 一起运行
  * `s`：**取代**，可以直接进行取代的工作，通常这个 `s` 的动作可以搭配正则表达式【对每行中查找到的数据进行替换，粒度更细】

* `sed`基本使用（`Mac`与`Linux`中的用法 ==稍有差别== ，以`Linux`为例）

创建的`sedtest.txt`的内容如下：

```shell
HELLO LINUX!  
Linux is a free unix-type opterating system.  
This is a linux testfile!  
Linux test 
Google
Taobao
Runoob
Tesetfile
Wiki
```

```shell
# 创建一个文件
touch sedtest.txt
# 将上述文件内容拷贝进去
# 查看文件内容方式1-纯粹打印
cat sedtest.txt
# 查看文件内容方式2-带行号显示
nl sedtest.txt

# 向文件新增一行内容-【不会改变原文件内容】
sed -e '4anewLine' ./sedtest.txt

# 以行为单位进行新增/删除，在知道行号的情况下使用-【不会改变文件内容】
# 第 2~5 行删除，两个边界都包括
nl ./sedtest.txt | sed -e '2,5d'
# 只删除第2行
nl ./sedtest.txt | sed -e '2d'
# 删除3到最后一行，两个边界都包括
nl ./sedtest.txt | sed -e '3,$d'
# 第二行后加上drink tea
nl ./sedtest.txt | sed -e '2adrink tea'
# 第二行前加上drink tea
nl ./sedtest.txt | sed -e '2idrink tea'
# 增加两行以上，在第二行后面加入两行字
nl ./sedtest.txt | sed -e '2adrink tea\
drink beer'# 每一行之间都必须要以反斜杠 \ 来进行新行标记。

# 以行为单位的替换和显示-【不会改变文件内容】
# 将第 2-5 行的内容取代成为 No 2-5 number
nl ./sedtest.txt | sed -e '2,5cNo 2-5 number'
# 列出文件内的第 5-7 行
nl ./sedtest.txt | sed -n '5,7p'

# 数据的搜寻并显示，在不知道行号的情况下使用-【不会改变文件内容】
# 搜索文件中有 oo 关键字的行
nl ./sedtest.txt | sed -n '/oo/p'

# 数据的搜寻并删除，在不知道行号的情况下使用-【不会改变文件内容】
# 删除文件中所有包含 oo 的行
nl ./sedtest.txt | sed -e '/oo/d'

# 数据的搜寻并新增，在不知道行号的情况下使用-【不会改变文件内容】
# 找到文件中所有包含 oo 的行，并在其后面一行新增加内容xiaotong
nl ./sedtest.txt | sed -e '/oo/axiaotong'# 向后新增
nl ./sedtest.txt | sed -e '/oo/ixiaotong'# 向前新增

# 数据的搜寻并执行命令，在不知道行号的情况下使用-【不会改变文件内容】
# 搜索文件，找到 oo 对应的行，执行后面花括号中的一组命令，每个命令之间用分号分隔，这里把 oo 替换为 kk
nl ./sedtest.txt | sed -n '/oo/{s/oo/kk/;p;q}'  # 最后的 q 是退出

# 数据的查找与替换-【不会改变文件内容】
# 除了整行的处理模式之外， sed 还可以行为单位进行部分数据的查找与替换
# 将文件中每行第一次出现的 oo 用字符串 kk 替换
nl ./sedtest.txt | sed -e 's/oo/kk/'
# g 标识符表示全局查找替换，使 sed 对文件中所有符合的字符串都被替换
nl ./sedtest.txt | sed -e 's/oo/kk/g'
# 选项 i 使 sed 修改文件-【会修改文件内容】
sed -i 's/oo/kk/g' ./sedtest.txt

# 多点编辑-【不会改变文件内容】
# 一条 sed 命令，删除文件第三行到末尾的数据，并把 HELLO 替换为 TONG
nl ./sedtest.txt | sed -e '3,$d' -e 's/HELLO/TONG/g'

# 直接在一个文件的末尾添加一行新的数据-【会修改文件内容，在大文件下非常有效】
sed -i '$aThis is a test' ./sedtest.txt
# 对于大文件特别有效，这是因为其他的文本处理程序直接将文件读入内存，内存如果不是很大，处理起来就会很慢，但是sed是按照行将文件读入内存，速度快
```

::: warning 注意

* `Mac`系统与`Linux`系统下`sed`用法的**差异**
  * 参考：https://www.cnblogs.com/exmyth/p/14582067.html
* **下达 `sed -e` 命令**，虽然没有 `-e` 也是可以的
* 动作请务**必以 `'...'` 两个单引号**括住
* 只要用**到了动作`p`，参数就使用`n`，只要涉及到修改文件，就用参数`i`，其他情况全部使用参数`e`**

:::

* `sed`常用方法（`Mac`与`Linux`中的用法 ==稍有差别== ，以`Mac`为例）

```shell
- 【重要】Replace the first occurrence of a string in a file, and print the result:
    sed 's/find/replace/' filename

- 【重要】Replace all occurrences of an extended regular expression in a file:
    sed -E 's/regular_expression/replace/g' filename

- 【重要】Replace all occurrences of a string [i]n a file, overwriting the file (i.e. in-place):
    sed -i '' 's/find/replace/g' filename

- 【重要】Replace only on lines matching the line pattern:
    sed '/line_pattern/s/find/replace/' filename

- 【重要】Print only text between n-th line till the next empty line:
    sed -n 'line_number,/^$/p' filename

- 【重要】Apply multiple find-replace expressions to a file:
    sed -e 's/find/replace/' -e 's/find/replace/' filename

- 【重要】Replace separator `/` by any other character not used in the find or replace patterns, e.g. `#`:
    sed 's#find#replace#' filename

- 【重要】[d]elete the line at the specific line number [i]n a file, overwriting the file:
    sed -i '' 'line_numberd' filename
```

::: tip 参考

https://www.cnblogs.com/zimskyzeng/p/11630071.html

https://www.runoob.com/linux/linux-comm-sed.html

:::

## awk

* `awk`是发明该工具三个作者姓名的首字母简称，`awk`是一个**报表生成器**，主要用于**格式化输出。**
  * `Alfred Aho`
  * `Peter Weinberger` 
  * `Brian Kernighan`
* `awk`按照行来读取文档，根据输入分隔符切分成小部分，用内建变量来表示，例如`$1`，`$2`，`$3`等，`$0`表示整行。
* 常用参数
  * `-F`：指定分割符
  * `-v`：定义变量
  * `-f`：指定`awk`脚本文件

* 新建`log.txt`

```shell
2 this is a test
3 Do you like awk
This's a test
10 There are orange,apple,mongo
```

* 用法一

```shell
awk '{[pattern] action}' {filenames}   # 行匹配语句 awk '' 只能用单引号
```

```shell
# 每行按空格或TAB分割，输出文本中的1、4列
awk '{print $1,$4}' log.txt
# 格式化输出
awk '{printf "%-8s %-10s\n",$1,$4}' log.txt
```

* 用法二

```shell
awk -F  #-F相当于内置变量FS, 指定分割字符
```

```shell
# 使用","分割
awk -F , '{print $1,$2}' log.txt
# 或者使用内建变量
awk 'BEGIN{FS=","} {print $1,$2}' log.txt
# 使用多个分隔符。先使用空格分割，然后对分割结果再使用","分割
awk -F '[ ,]' '{print $1,$2,$5}' log.txt
```

* 用法三

```shell
awk -v  # 设置变量
```

```shell
awk -v a=1 '{print $1,$1+a}' log.txt
awk -v a=1 -v b=s '{print $1,$1+a,$1b}' log.txt
```

* 用法四

```shell
awk -f {awk脚本} {文件名}
```

```shell
awk -f cal.awk log.txt
```

* 此工具在运维工作中可以极大提高效率，比如可以**对日志文件的有效内容进行统计计算后格式化输出**，但是**该工具在开发中很少进行使用**，而且该工具居然有自己的语言设计，基于该语言可以编写`awk`脚本，其三位创建者已将它正式定义为“样式扫描和处理语言”。
  * 学习该语言可以参考：https://awk.readthedocs.io/en/latest/index.html
* **举个例子：统计每个学生的总分和平均分**

`student.txt`数据如下：

```shell
cc 90 98 98 96 96 92
ll 70 77 85 83 70 89
ss 85 92 78 94 88 91
nn 89 90 85 94 90 95
bb 84 88 80 92 84 82
gg 64 80 60 60 61 62
```

`script.txt`脚本如下：

```c
# BEGIN模块
BEGIN {
    printf "姓名\t总分\t平均分\n"
}
# 代码块1-依次执行
{
    sum=0
    # NF表示每一行的字段数量
    for(i=2;i<=NF;i++)
        sum+=$i
}
# 代码块2-依次执行
{
    avg=sum/(NF-1)
    printf("%s\t%s\t%s\n", $1,sum,avg)
}
# END模块
END {
    printf "统计工作完成啦！\n"
}
```

运行命令：

```shell
awk -f script.txt student.txt
姓名	总分	平均分
cc	570	95
ll	474	79
ss	528	88
nn	543	90.5
bb	510	85
gg	387	64.5
统计工作完成啦！
```

此时还可以模式匹配行，也就是选择特定的行进行统计计算，修改`script.txt`脚本：

```c{7,14}
# BEGIN模块
BEGIN {
    printf "姓名\t总分\t平均分\n"
}
# 代码块1-依次执行
/ss/ {# 模式匹配行ss
    sum=0
    # NF表示每一行的字段数量
    for(i=2;i<=NF;i++)
        sum+=$i
}
# 代码块2-依次执行
/ss/ {# 模式匹配行ss
    avg=sum/(NF-1)
    printf("%s\t%s\t%s\n", $1,sum,avg)
}
# END模块
END {
    printf "统计工作完成啦！\n"
}
```

执行结果如下：

```shell
awk -f script.txt student.txt
姓名	总分	平均分
ss	528	88
统计工作完成啦！
```

* **`awk`的工作流程**

![image-20221031230011530](https://my-knowledge-web.oss-cn-qingdao.aliyuncs.com/my-img1/awk%E5%B7%A5%E4%BD%9C%E6%B5%81%E7%A8%8B.png)

::: tip 参考

https://www.cnblogs.com/zimskyzeng/p/11630071.html

https://www.runoob.com/linux/linux-comm-awk.html

https://blog.csdn.net/yetugeng/article/details/86634957

https://www.runoob.com/w3cnote/awk-work-principle.html

:::

