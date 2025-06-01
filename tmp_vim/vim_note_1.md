# vim note

1. 单词移动
w 跳到下一处单词的开头
b 跳到上一处单词的开头
e 跳到下一处单词的结尾
ge 跳到上一处单词的结尾


2. 查找
2.1 本行查找
f{char}  跳转到本行下一个 char 出现处
t{char}  跳转到本行下一个 char 出现前

2.2 文件
/{pattern} 跳转到本文中下一个 pattern 出现的地方
?{pattern} 跳转到本文中上一个 pattern 出现的地方

n 用于快速查找下一个，比如记住了匹配规则，n  就可以查找下一个匹配的地方
N 用于快速查找上一个，比如记住了匹配规则，N  就可以查找上一个匹配的地方

3. 基于标记的移动
3.1 m{mark} 把当前位置标记为 mark  一般习惯标记为m  所以具体操作就是 mm
    具体的要跳转回 m{mark} 执行操作 `{mark}，比如上面的标记为 m ，那么跳转回标记处m 就是执行操作 `m

`` 连按两下 ` 就是跳转上一个位置
`. 按一下 ` 和 .  就是跳转到上一次修改的位置
`^ 按一下 ` 和 ^ 就是跳转到上一次插入的位置

^ 跳到行首
$ 跳到行尾

% 跳转到匹配的配对符处。比如 {xxxxx} 光标在左打括号处，可以通过 % 快速跳转到 右大括号处。扩展，可以使用 d% 快速删除 {xxxxx} /* xxxx */  等内容

4. Action = OPerator + Motion
> 一次编辑动作
>> {operator}{motion}

常见的操作符
c 代表 change 修改，删除内容，并进入插入模式
d 代表 delete 删除
y 代表 yank 复制
v 代表 visual 选中文本，进入可视模式

---
连续按两次：
    cc  对整行操作  修改
    dd  对整行操作  删除
    yy  对整行操作  复制
---
举例说明(常见场景)：
    dgg     删除到第一行
    ye      复制到单词结尾
    dw      删除当前的单词
    d$      删除到行尾
    dt;     删除到分号为止的内容
    d /int  删除两次int 之间的内容。在第一次出现int 之后，执行 d /int 可以删除下一次出现int 之间的所有内容

5. 批量操作

>针对上面的 Action

5.1 初级
. 重复上一次的修改
u 撤销上一次的修改
ctrl + r 重做上一次的修改  有点类似于 ctrl + y

5.2 高级

{count}{action} 重复 count 次 action 动作

---
> 数字+动作需要预先知道动作的次数
> 注意，多次操作之后，如果撤销，会回到多次操作前的状态(而不是多次操作的最后一个子动回退，注意批量操作，是一次性全部操作，把批量的动作当成一个整体。)

    4j  向下移动4行
    3dw 删除3个单词
    2yy 复制两行
    4p  粘贴4次

查看当前行就其他行号的相对偏移量
set rnu     全量 set relativenumber   set nonu
set nornu   全量 set norelativenumber

6. 文本对象操作 
> textobjects 语义化的文本片段

格式： i/a + 对象


[参考源01](https://www.bilibili.com/video/BV1s4421A7he?spm_id_from=333.788.videopod.episodes&vd_source=185f80d453b08f4c6ad76d3216e073b8&p=3)
[参考源02](https://share.weiyun.com/XNxSRe9o)
