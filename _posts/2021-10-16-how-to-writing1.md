---
title: 写作教程1
author: dinger0
date: 2021-10-16 16:10:00 +0800
categories: [博客, 教程]
tags: [教程]
render_with_liquid: false
image:
  src: /pics/0.jpg
  width: 1024   # in pixels
  height: 768   # in pixels
  alt: image alternative text
---

## 写作文件命名与存放路径

在 `_post/` 目录下，创建一个文件，按照如下格式命名： `YYYY(年)-MM(月)-DD(日)-TITLE(标题).EXTENSION(扩展名)`。注意：文件扩展名 `.md` 和 `.markdown` 二选一即可。

## Front Matter配置

你可以根据Jekyllrb网站的 [Front Matter](https://jekyllrb.com/docs/front-matter/)定义进行配置。

一个标准的配置文件格式如下：

```yaml
---
title: TITLE
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [TAG]     # TAG names should always be lowercase
---
```

> **注意**：文章的 ***layout*** 字段默认设置为 `post`，不需要在**Front Matter**中重复添加***layout***字段。

### 时区设置

为了准确记录文章发布时间，你不仅需要设置 `_config.yml` 文件中的 `timezone` 字段，还要配置 `Front Matter` 的 `date` 字段，另外，时区的配置需要遵循以下格式：`+0800`，代表东8区。

### 分类与标签

每篇文章的 `categories` 包含两个元素，分别对应大分类与小分类， `tags` 可以任意多个，逗号隔开。举个例子：

```yaml
categories: [动物, 昆虫]
tags: [蜜蜂]
```

## 文章目录(Table of Contents)

默认情况下，目录(TOC)显示在博文的右侧。如果你想关闭该功能，请把 `_config.yml` 文件中的 `toc` 字段设置为 `false`，注意，这会关闭所有博文的目录显示功能，如果你只想关闭某篇博文的目录显示功能，可以在 [Front Matter](https://jekyllrb.com/docs/front-matter/)中添加以下配置：

```yaml
---
toc: false
---
```

## 评论

与TOC功能类似,你可以在 `_config.yml` 文件中修改 `comments` 字段达到全局关闭评论的目的。若是单独关闭某一篇文章的评论，只需在**Front Matter**配置中添加以下信息：

```yaml
---
comments: false
---
```

## 数学

为了加快访问，该功能默认关闭，需要打开的话，请在**Front Matter**配置文件中添加：

```yaml
---
math: true
---
```

## 框图工具(Mermaid)

[**Mermaid**](https://github.com/mermaid-js/mermaid) 是一个很好的框图生成工具，如果需要，可以添加该功能字段：

```yaml
---
mermaid: true
---
```

Then you can use it like other markdown languages: surround the graph code with ```` ```mermaid ```` and ```` ``` ````.

## 图片

### 图片预览

需要在文章的顶部添加图片的话，请在 **Front Matter** 中新增以下信息：


```yaml
---
image:
  src: /path/to/image/file
  width: 1000   # in pixels
  height: 400   # in pixels
  alt: image alternative text
---
```

除了 `alt` 字段是可选，其它为必填。

### 图片说明

在图片的下一行添加斜体字，图片下方就会出现说明文字。

```markdown
![img-description](/pics/0.jpg){: width="1024" height="768" }
_This is image caption_
```
{: .nolineno}

举个例子：
![Desktop View](/pics/0.jpg){: width="1024" height="768" }
_这是图片的文字说明_

### 图片尺寸

为了防止图片页面布局偏移，应该按照以下格式，为每张图片设置像素尺寸。

```markdown
![Desktop View](/assets/img/sample/mockup.png){: width="700" height="400" }
```
{: .nolineno}

### 图片位置

图片默认居中，当然，你也可以设置为以下任意一种： `normal` ， `left` ， `right`。

举个例子：

- **Normal**

  ```markdown
  ![Desktop View](/pics/0.jpg){: .normal width="1024" height="768" style="max-width: 50%"}
  ```

  实际效果👇👇👇👇👇👇👇👇：
  
  ![Desktop View](/pics/0.jpg){: .normal width="1024" height="768" style="max-width: 50%"} repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space.
  
  {: .nolineno}

- **Float to the left**

  ```markdown
  ![Desktop View](/pics/0.jpg){: .left width="1024" height="768" style="max-width: 50%"}
  ```
  
  实际效果👇👇👇👇👇👇👇👇：
  
  ![Desktop View](/pics/0.jpg){: .left width="1024" height="768" style="max-width: 50%"}  repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space.
  
  {: .nolineno}

- **Float to the right**

  ```markdown
  ![Desktop View](//pics/0.jpg){: .right width="1024" height="768" style="max-width: 50%" }
  ```
  
  实际效果👇👇👇👇👇👇👇👇：
  
  ![Desktop View](/pics/0.jpg){: .right width="1024" height="768" style="max-width: 50%" } repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space.

  {: .nolineno}
  
> **局限**: 指定图片位置后，不应该再添加文字说明。

### 图片阴影

你可以给图片加上那个阴影，但是该功能只在 `light` 模式下生效。

```markdown
![Desktop View](/pics/0.jpg){: .shadow }
```
{: .nolineno}

![Desktop View](/pics/0.jpg){: .shadow }

### CDN URL

如果你把图片托管在CDN，可以通过修改 `_config.yml` 文件的 `img_cdn` 字段，节省重复填写地址的时间。

```yaml
img_cdn: https://cdn.com
```
{: file='_config.yml' .nolineno}

只要 `img_cdn` 字段赋值，cdn前缀地址会自动添加到所有图片的路径前。

举个例子：

```markdown
![The flower](/path/to/flower.png)
```
{: .nolineno}

解析结果会自动转换为下面的地址:

```html
<img src="https://cdn.com/path/to/flower.png" alt="The flower">
```
{: .nolineno}

## 文章置顶

支持在主页置顶一篇或多篇文章，置顶的文章根据发布日期倒序排序。开启如下：


```yaml
---
pin: true
---
```

## 代码块

使用markdown```` ``` CODE ``` ```` 符号可以轻易实现下面的代码块:

```
This is a plaintext code snippet.
```

### 指定编程语言

使用 ```` ```{language} ``` ```` 即可达到指定语言的语法高亮:

````markdown
```yaml
key: value
```
````

> **Limitation**: The Jekyll style `highlight` tag is not compatible with this theme.

### 行号

默认情况下，除了纯文本、控制台和终端，其他所有语言都会显示行号。如果你不想显示行号，可以在代码块的下一行添加 `{: .nolineno}` 进行取消。

````markdown
```shell
echo 'No more line numbers!'
```
{: .nolineno}
````
{: .nolineno}

### 指定文件名

既然代码块的左上角会显示编程语言，那能不能显示文件名呢，当然可以，只需要添加 `file` 属性即可：

````markdown
```bash
# content
```
{: file="path/to/file" }
````

实际效果如下：

```bash
code
```
{: file="path/to/file.sh" }

### Liquid Codes

If you want to display the **Liquid** snippet, surround the liquid code with `{% raw %}` and `{% endraw %}`:

````markdown
{% raw %}
```liquid
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack.
{% endif %}
```
{% endraw %}
````

Or adding `render_with_liquid: false` (Requires Jekyll 4.0 or higher) to the post's YAML block.

## Learn More

For more knowledge about Jekyll posts, visit the [Jekyll Docs: Posts](https://jekyllrb.com/docs/posts/).
