## The Open Manual Repository

Our software manuals are maintained as open-source and be able to be updated/translated on GitHub.



### How to Update

Document is written in Markdown and deployed with Jekyll.

[Markdown Reference](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
|
[Basic Tutorial on GitHub](https://docs.github.com/en/get-started/quickstart/contributing-to-projects)
|
[GitHub Pages and Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll)



### Template for New Page

File extension must be `.md`.
It's good to have additional language extension before file extension. ex: `FileName.en.md`

```yaml
---
title: "Page Title"
lang: en
date: 2021-12-02
author:
- "You"
- "Prior to You"
---

# Contents written in Markdown
```



### Controls for PDF Output

You can use `class="print--hidden"` to hide content from "Print to PDF" output.  
`class="print--d-none"` is also available, note that this will change page layout.

If you want to add page break for PDF explicitly, use: `<div class="print--page-break"></div>`

#### Note for HTML in Markdown

Page break using HTML tag and you need to have attention to use it in Markdown format.
> Page break HTML tag must be in independent HTML block, because of that page break uses CSS and it will hide rest of inline contents in same HTML block. In Markdown context, it requires empty line before and after.

See Markdown source of this page for example.
<div class="print--page-break"></div><strike>THIS TEXT IS SHOWN
IN MARKDOWN PREVIEW BUT NOT IN RESULTING PAGE</strike>



### Customize Directory Label in Index Page

Search with `// SP: update directory display label` and update JavaScript.
https://github.com/SatorImaging/OpenManual/blob/master/_layouts/default.html

> [!WARNING]
> DO NOT change directory name. it will make existing URL unreachable.


### About Jekyll Theme

Theme was designed by Sator Imaging.


### Tests

> [!TIP]
> TIP

> [!NOTE]
> NOTE

> [!IMPORTANT]
> IMPORTANT

> [!WARNING]
> WARNING

> [!CAUTION]
> CAUTION
