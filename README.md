# 高级计算机网络

本项目提供了西电高级计算机网络课程大作业的 Typst 模板，可供感兴趣的同学尝试。

## 环境准备

使用本模板最便捷的方式是在 VSCode 中安装相应的扩展，可以在 VSCode 的插件市场中搜索 Tinymist 或 Typst，该插件包含了 Typst 的命令行工具以及相应的语言服务器实现。

使用其他编辑器或者想对该插件深入了解的同学可参考 [Tinymist](https://myriad-dreamin.github.io/tinymist/)。

## 使用说明

根目录下的 `main.typ` 提供了一些简单的示例，要使用本模板，需要在文档开头填写以下内容：

```typ
#import "template.typ": *

#show: doc.with(bibliography: bibliography("refs.bib"))
```

其中 `refs.bib` 内容是 Latex 格式的参考文献，项目根目录下同样提供了一个示例。有关参考文献更加详细的内容，可以参考 Typst 官方文档的 [bibliography](https://typst.app/docs/reference/model/bibliography/) 部分。

如果需要添加附录，则在 `doc.with` 中填写以下内容：

```typ
#show: doc.with(
  appendix:[
    = 附录标题一

    = 附录标题二
  ],
  bibliography: bibliography("refs.bib"),
)
```

其中每个 `=` 会递增附录的编号，上述内容会渲染出“附录A 附录标题一”和“附录B 附录标题二”两节内容。

### 标题

在 Typst 中，通过 `=` 来为文档添加一个标题，其中 `=` 的数量决定了标题的级别。有关标题更加详细的内容，可以参考 Typst 官方文档的 [heading](https://typst.app/docs/reference/model/heading/) 部分。

```typ
= 这是一级标题

== 这是二级标题

=== 这是三级标题
```

注：根据模板要求，名称为“引言”的标题不会编号。

### 图片

如果要向文档中添加图片，需要使用如下形式：

```typ
#figure(
  image("/path/to/image"),
  caption: [这是图片的题注],
) <img:demo>
```

有关图片更加详细的内容，可以参考 Typst 官方文档的 [image](https://typst.app/docs/reference/visualize/image/) 和 [figure](https://typst.app/docs/reference/model/figure/) 部分。

### 表格

如果要向文档中添加表格，需要使用如下形式：

```typ
#figure(
  table(
    columns: 3,
    [A], [B], [C],
    [D], [E], [F],
  ),
  caption: [这是表格的题注],
) <tab:demo>
```

有关表格更加详细的内容，可以参考 Typst 官方文档的 [table](https://typst.app/docs/reference/model/table/) 和 [figure](https://typst.app/docs/reference/model/figure/) 部分。

### 公式

如果要向文档中添加公式，有两种形式，分别渲染为行内公式和行间公式：

```typ
$f(n)$

$ F(n) = F(n-1) + F(n-2) $ <equ:demo>
```

其中行间公式会自动编号。有关公式更加详细的内容，可以参考 Typst 官方文档的 [math](https://typst.app/docs/reference/math/) 部分。

### 脚注

如果要向文档中添加脚注，需要使用如下形式：

```typ
#footnote[脚注的示例内容]
```

有关脚注更加详细的内容，可以参考 Typst 官方文档的 [footnote](https://typst.app/docs/reference/model/footnote/) 部分。

### 引用

如果要向文档中添加元素（图片、表格、公式）的引用，需要使用如下形式：

```typ
@img:demo
@tab:demo
@equ:demo
```

该代码分别是上述示例图片、表格和公式的引用。有关引用更加详细的内容，可以参考 Typst 官方文档的 [ref](https://typst.app/docs/reference/model/ref/) 部分。

### 杂项

#### 引言和结论分点

根据模板要求，在引言和结论部分不能有子标题，需要使用分点替代。考虑到这些符号输入不是很方便，尤其是第三级分点，所以本项目提供了一些辅助函数：

```typ
#mark1(1)分点1       # （1）
#mark2(1)子分点1     # 1）
#mark3(1)子子分点1   # ①
#mark4(1)子子子分点1 # [1]
```

分别对应要求的四级分点，其中函数 `markM(N)` 输出的是第 M 级的第 N 个分点。

#### 中英文间隙

Typst 会自动在中英文间添加一定的间隙，因而普通的中英文间不需要加入额外的空格。但是对于行内公式和中文之间，不会进行这种处理。考虑到排版的美观性，本项目提供了提供了 `S` 函数用于添加一些间隙，示例如下：

```typ
这是一个行内公式#(S)$f(n)$#(S)示例。
```

#### 取消首行缩进

在编写行间公式后，通常需要对公式进行一些解释，通常的做法是该公式的下一段首行不缩进。Typst 中没有提供相关的功能，因而本项目提供了 `D` 函数用于临时取消缩进，示例如下：

```typ
#(D)这段内容不会首行缩进
```

## 参考

以下是 Typst 排版工具的一些参考资料：

[官方文档](https://typst.app/docs/)

[中文文档](https://typst-doc-cn.github.io/guide/)
