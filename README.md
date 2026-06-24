This README contains all of the information needed to create a blog post on the Formula uOttawa site and technical data on how it works.

- **To see your blog online after committing changes**: https://formula-uottawa.github.io/uOpenBlog/posts/(name-of-post-no-capilization)/

# Creating a blog post

Blog posts are written in Markdown; a text file with syntax to format text (similar to Discord's bolding and italicizing). Follow the steps below when writing your first post, or refer back to specific steps as needed.

## First Step: Creating Your Work Space

1. Go to https://github.com/Formula-uOttawa/uOpenBlog (where we are right now).
   
2. Click in this exact order: content -> posts -> Add file (top right of page) -> create new file
   
3. You'll see an empty text screen. Look at the top and you'll see: uOpenBlog/content/posts/Name your file... Click "Name your file" and type "(name-Of-Your-Post)**/**" to create the folder. Remember the forward slash.
   
4. Click "Name your file" again and type "index.md". This will be where you write your blog post.

5. Copy and paste the metadata below into index.md, replacing the values in ( ):

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

Anytime you want to make changes to your post, you will click: content → posts → post-name → index.md. Use Preview to see how it looks, and Commit changes to save. Note: to properly see how images look, go to the uploading images section for instructions. The metadata at the top of your posts will take the form of:

<img width="873" height="100" alt="image" src="https://github.com/user-attachments/assets/9063ddad-08e2-4c39-8caf-23684ea6b4d6" />

## Markdown Syntax

Sourced from [markdownguide.org](https://www.markdownguide.org/cheat-sheet/)(link to their cheat sheet). Hugo does not support the highlight, subscript, superscript elements.

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
| Heading ID           | IGNORE FOR NOW                                                                                                  | IGNORE FOR NOW                                  |
| Definition List      | Voltage<br>: The potential difference between two points                                                                       | <dl><dt><b>Voltage</b></dt><dd>The potential difference between two points</dd></dl>     |

## Uploading Images

Images must be placed in the same folder as their post (uOpenBlog/content/posts/post-name/). Keywords can be used to render images in different ways.

### Current Keyword Table:

| Keyword | Renders                                                                                     | Syntax                    |
| ------- | ------------------------------------------------------------------------------------------- | ------------------------- |
|  | Default — resizes image to 600px wide                                                       | \!\[alt](image.jpg)         |
| "small" | Resizes image to 400px wide, displays as a small thumbnail                                  | \!\[alt](image.jpg "small") |
| "full"  | No resizing — image displays at its original size, stretched to 100% of the container width | \!\[alt](image.jpg "full")  |

### Seeing Your Rendered Images

Github doesn't render images the same way that Hugo does, our site generator. When you are making adjustments to your images, such as changing the keyword, you will need to go to the url: https://formula-uottawa.github.io/uOpenBlog/posts/x/ , where x is the name of your post folder with no capitilization.


# Software Team Section
