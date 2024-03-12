---
draft: true 
date:
  created: 2024-01-07 
  updated: 2024-01-17 
slug: mkdoclearn
authors:
  - skyhigh
categories:
  - 学习
  - 分享
  - 日常
  - 自我
  - 年度
  - 音乐
---

# Mkdoc Test
MKdoc主题测试档案  
这里用来放置摘要，可有可无  
<!-- uptoc -->
## 代码块
``` title="这是标题"
markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.superfences
```

## 警告框
```
markdown_extensions:
  - admonition
  - pymdownx.details
  - pymdownx.superfences
```

!!! note "这里是标题"
    以 !!! 开头,两TAb书写，标题在“”中。
???+ note "可折叠"
    以？？？开头的是可折叠，？？？+是默认展开的折叠

!!! info "info 信息"
    When forty winters shall besiege thy brow,And dig deep trenches in thy beauty's field,Thy youth's proud livery so gazed on now,Will be a tattered weed of small worth held
!!! tip "tip 提示"
    When forty winters shall besiege thy brow,And dig deep trenches in thy beauty's field,Thy youth's proud livery so gazed on now,Will be a tattered weed of small worth held
!!! warning "warning 警告"
    When forty winters shall besiege thy brow,And dig deep trenches in thy beauty's field,Thy youth's proud livery so gazed on now,Will be a tattered weed of small worth held
!!! quote "quote 引用"
    When forty winters shall besiege thy brow,And dig deep trenches in thy beauty's field,Thy youth's proud livery so gazed on now,Will be a tattered weed of small worth held

## 按钮
```
markdown_extensions:
  - attr_list
----------------------
[Subscribe to our newsletter](#){ .md-button }
```
[Aboout :fontawesome-solid-paper-plane:](#){ .md-button }  
可添加icon或css

## 脚注
Lorem ipsum[^1] dolor sit amet, consectetur adipiscing elit.[^2]  

## 格式化
可以{--删除--}文本并{++添加++}替换文本。这也可以合并为一个操作。{>>并且可以内嵌添加注释<<}，还可以突出显示，如下：

{==

Formatting can also be applied to blocks by putting the opening and closing
tags on separate lines and adding new lines between the tags and the content.

==}

- ==This was marked==
- ^^This was inserted^^
- ~~This was deleted~~
- __加粗__

++ctrl+alt+del++

## 列表
#### 无序列表
```
- a
- b
  * c
  * d
```

- a  
- b  
  - c  
  - d  

- [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
- [ ] Vestibulum convallis sit amet nisi a tincidunt
    * [x] In hac habitasse platea dictumst
    * [x] In scelerisque nibh non dolor mollis congue sed et metus
    * [ ] Praesent sed risus massa
- [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque

## 图片
etc。。

## 网格
<div class="grid cards" markdown>

- [:fontawesome-brands-html5: __HTML__ for content and structure](https://a.com)
- :fontawesome-brands-js: __JavaScript__ for interactivity
- :fontawesome-brands-css3: __CSS__ for text running out of boxes
- :fontawesome-brands-internet-explorer: __Internet Explorer__ ... huh?

</div>

<div class="grid cards" markdown>

-   :material-clock-fast:{ .lg .middle } __Set up in 5 minutes__

    ---

    Install [`mkdocs-material`](#) with [`pip`](#) and get up
    and running in minutes

    [:octicons-arrow-right-24: Getting started](#)

-   :fontawesome-brands-markdown:{ .lg .middle } __It's just Markdown__

    ---

    Focus on your content and generate a responsive and searchable static site

    [:octicons-arrow-right-24: Reference](#)

-   :material-format-font:{ .lg .middle } __Made to measure__

    ---

    Change the colors, fonts, language, icons, logo and more with a few lines

    [:octicons-arrow-right-24: Customization](#)

-   :material-scale-balance:{ .lg .middle } __Open Source, MIT__

    ---

    Material for MkDocs is licensed under MIT and available on [GitHub]

    [:octicons-arrow-right-24: License](#)

</div>
























[^1]: Lorem ipsum dolor sit amet, consectetur adipiscing elit.  
[^2]:
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.