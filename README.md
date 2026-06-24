**CHANGES ARE BEING MADE TO THIS README**

This README contains all of the information needed to create a blog post on the Formula uOttawa site and technical data on how it works.

# Creating a blog post

  The website builds your blog post using a language called **markdown**, it is basically just an upgraded text file with syntax to change how text appears. Discord uses a simplified version, such as for **bolding** or *italicizing*. 

  This section is separated into steps to follow along with as you make your post, but you may naturally find yourself returning to only look at certain steps to see things such as markdown syntax or how to upload images.

## First Step: Creating Your Work Space

  Things need to be organized in a specific way to allow the website to pull your blog post and its associated images correctly. 

  For each blog post, all of the content (markdown file, images), needs to be contained in its own unique folder under content/posts/(post-Name). You will create a file in this folder and name it "index.md", then whenever you want to have an image in your post, you will place the image directly into this folder as well. Here are the steps to do all of this:

1. Go to https://github.com/Formula-uOttawa/uOpenBlog (where we are right now).
   
2. Click in this exact order: content -> posts -> Add file (top right of page) -> create new file
   
3. You'll see an empty text screen. Look at the top and you'll see: uOpenBlog/content/posts/Name your file... Click "Name your file" and type "(name-Of-Your-Post)**/**" to create the folder. Remember the forward slash.
   
4. Click "Name your file" again and type "index.md". This will be where you write your blog post.

5. in index.md you will copy and paste the follow code/metadata, replace the information in (), and then delete the (). Remember: title, date, tags, authors. You can put as few or as many authors/tags as you want:

```
---
title: "(Name of Post)"
date: 2026-(MM)-(DD)T02:00:00-04:00
draft: false
_build:
  list: never
  render: always
unlisted: true
tags: ["(subteam)","(tag)","(tag)"]
authors: ["(author)", "(author)", "(author)"]
---
```

It should look like this:
<img width="1564" height="718" alt="image" src="https://github.com/user-attachments/assets/6ca4c8a0-2647-429b-b5b1-f38c6506d932" />

6. Press the green "Commit changes..." top right, then click the green "Commit changes" in the popup.

Anytime you want to work on your post, you'll click content->posts->post-Name->index.md, and then type into that text file. To see how the text will look you'll click preview, and to save your work you'll commit your changes again. Ignore how the metadata tables looks in preview, it will look like this on the site:

<img width="873" height="100" alt="image" src="https://github.com/user-attachments/assets/9063ddad-08e2-4c39-8caf-23684ea6b4d6" />

## Markdown Syntax

We generate our site using Hugo, a static site generator. It supports most markdown syntax. Here is a list of elements and the syntax to use them in order of usefulness. Sourced from [markdownguide.org](https://www.markdownguide.org/cheat-sheet/)(link to their cheat sheet). Hugo does not support the highlight, subscript, superscript elements.

### Commonly Used
| Element              | Markdown Syntax                                                                                                                 | Visually                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Title/Headings       | \# Title<br>\#\# Heading<br>\#\#\# Subheading                                                                                  | <h1>Title</h1><h2>Heading</h2><h3>Subheading</h3>                                        |
| Bold                 | \*\*bold text\*\*                                                                                                               | **bold text**                                                                            |
| Italic               | \*italicized text\*                                                                                                             | *italicized text*                                                                        |
| Link                 | \[title](https://www.example.com)                                                                                               | [title](https://www.example.com)                                                         |
| Image                | \!\[alt text](image.jpg)                                                                                                        | (displays an image) Please see image uploading section for more information.                                                                     |
| Ordered List         | 1\. First item<br>2\. Second item<br>3\. Third item                                                                             | <ol><li>First item</li><li>Second item</li><li>Third item</li></ol>                      |
| Unordered List       | \- First item<br>\- Second item<br>\- Third item                                                                                | <ul><li>First item</li><li>Second item</li><li>Third item</li></ul>                      |
| Code (inline)        | \`code\`                                                                                                                        | `code`                                                                                   |
| Code (fenced block)  | \`\`\`toml<br>[taxonomies]<br>&nbsp;&nbsp;tag = "tags"<br>&nbsp;&nbsp;author = "authors"<br>\`\`\`  | <img width="723" height="78" alt="image" src="https://github.com/user-attachments/assets/0d20ee9d-3726-431f-8927-51ec12525ccc" /> Note: toml is the coding language



### Uncommonly Used

| Element              | Markdown Syntax                                                                                                                 | Visually                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Blockquote           | \> "The only way to do great work<br>\> is to love what you do."<br>\> — Steve Jobs                                            | <blockquote>"The only way to do great work<br>is to love what you do."<br>— Steve Jobs</blockquote> |
| Horizontal Rule      | \-\-\-                                                                                                                          | <hr>                                                                                     |
| Strikethrough        | \~\~The world is flat.\~\~                                                                                                      | <s>The world is flat.</s>                                                                |
| Table                | \| Syntax \| Description \|<br>\| --- \| --- \|<br>\| Header \| Title \|<br>\| Paragraph \| Text \|                            | <table><tr><th>Syntax</th><th>Description</th></tr><tr><td>Header</td><td>Title</td></tr><tr><td>Paragraph</td><td>Text</td></tr></table> Note: recommended to use AI for tables. |
| Task List            | \- \[x] Write the press release<br>\- \[ ] Update the website<br>\- \[ ] Contact the media                                     | &#9745; Write the press release<br>&#9744; Update the website<br>&#9744; Contact the media |
| Footnote             | Voltage is measured in volts. \[^1]<br><br>\[^1]: Named after Alessandro Volta.                                                | Voltage is measured in volts. <sup>1</sup><br><br><sub><sup>1</sup> Named after Alessandro Volta.</sub> |
| Heading ID           | \#\#\# Introduction \{#intro}                                                                                                  | <b>Introduction</b> — link to it with \[click\](#intro)                                  |
| Definition List      | Voltage<br>: The potential difference between two points                                                                       | <dl><dt><b>Voltage</b></dt><dd>The potential difference between two points</dd></dl>     |

## Uploading Images

All images need to be in the same folder as the markdown post that is using them. Meaning all of your images need to be in uOpenBlog/content/posts/name-Of-Post/.

\!\[alt text](image.jpg) is the standard way to insert images in markdown, where image.jpg should be the exact name and filetype of your image. However, because Hugo has built in image rendering, we can adjust the sizing and other details of the image using keywords. For example: \!\[alt text](image.jpg "(keyword)"), where (keyword) is any keyword from the table below. Without a keyword, the image will be rendered as default.

Current Keyword Table:

| Keyword | Renders                                                                                     | Syntax                    |
| ------- | ------------------------------------------------------------------------------------------- | ------------------------- |
|  | Default — resizes image to 600px wide                                                       | \!\[alt](image.jpg)         |
| "small" | Resizes image to 400px wide, displays as a small thumbnail                                  | \!\[alt](image.jpg "small") |
| "full"  | No resizing — image displays at its original size, stretched to 100% of the container width | \!\[alt](image.jpg "full")  |
