**标题前面加 # 号，有多少个#就代表几级标题**  
# 这是一级标题
## 这是二级标题
### 三级标题
等等...

# 段落语法
插入一个空白行即可分段

这是第一段

这是第二段

这是第三段

# 换行语法
在文本的结尾插入两个空格即可  
这是第二行
这是不加两个空格的情况

# 强调语法
在要**加粗**的文字两端分别加两个*  
要*斜体*只要加一个星号  
三个\*代表同时***加粗和斜体***  

# 引用语法
> 在段落前面加上>代表块引用  
> 
> 块引用中间加入一个包含>的空白行，代表多个段落  
>> 块引用可以嵌套，多加一个>即可
>>> 第三层嵌套

# 列表语法
## 有序列表
1. First Item
2. Second Item
3. Third Item
    1. Intented Item
    2. Second Intented Item
4. Fourth Item

## 无序列表
- First Item
- Second Item
- Third Item
    - Intented Item
    - Second Intented Item
- Fourth Item

**用'-', "+", "*" 都可以**

**要在保留列表连续性的同时在列表中添加另一种元素，请将该元素缩进四个空格或一个制表符**

### 段落
*   This is the first list item.
*   Here's the second list item.

    I need to add another paragraph below the second list item.

*   And here's the third list item.

### 引用块
*   This is the first list item.
*   Here's the second list item.

    > A blockquote would look great below the second list item.

*   And here's the third list item.

### 代码块
代码块通常采用四个空格或一个制表符缩进。当它们被放在列表中时，请将它们缩进八个空格或两个制表符。
1.  Open the file.
2.  Find the following code block on line 21:

        <html>
          <head>
            <title>Test</title>
          </head>

3.  Update the title to match the name of your website.

### 图片
1.  Open the file containing the Linux mascot.
2.  Marvel at its beauty.

    ![Tux, the Linux mascot](image.png)

3.  Close the file.

### 列表
1. First item
2. Second item
3. Third item
    - Indented item
    - Indented item
4. Fourth item

# 代码语法
把代码包裹在`反引号`中即可

## 转义反引号
如果你要表示为代码的单词或短语中包含一个或多个反引号，则可以通过将单词或短语包裹在双反引号(``)中。

``Use `code` in your Markdown file.``

## 代码块
要创建代码块，请将代码块的每一行缩进至少四个空格或一个制表符。

    <html>
      <head>
      </head>
    </html>

# 分割线语法
要创建分隔线，请在单独一行上使用三个或多个星号 (***)、破折号 (---) 或下划线 (___) ，并且不能包含其他内容。

***

---

___

以上三个分割线的渲染效果看起来都一样

为了兼容性考虑，建议分割线的前后都插入空白行

# 链接语法
This is my [blog](https://xxx.top "Kevin的blog").

使用<>可以直接将链接变为可点击状态

<https://xxx.top>

<xxx@gmail.com>

## 带格式化的链接
强调链接, 在链接语法前后增加星号。

要将链接表示为代码，请在方括号中添加反引号。

I love supporting the **[EFF](https://eff.org)**.  
This is the *[Markdown Guide](https://www.markdownguide.org)*.  
See the section on [`code`](#code).

## 引用类型链接
[这是第一段引用的话][1]

## 兼容性建议
不同的 Markdown 应用程序处理URL中间的空格方式不一样。为了兼容性，请尽量使用%20代替空格。  
例如：<https://www.example.com/my%20great%20page>

# 图片语法
插入图片Markdown语法代码：`![图片alt](图片链接 "图片title")`

![沙漠中的岩石图片](image-1.png "Shiprock")

要给图片增加链接，将图像的Markdown 括在方括号中，然后将链接添加在圆括号中。
[![沙漠中的岩石图片](image-1.png "Shiprock")](https://markdown.com.cn)

# 转义字符
要显示markdown中的特殊字符，使用反斜杠\\即可


[1]: https://en.wikipedia.org/wiki/Markdown "Markdown Wikipedia"