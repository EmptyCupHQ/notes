# Markdown

Markdown is a human readable plain text format for creating HTML content.

A markdown file with a `.md` extension can be converted to a `.html` file which can be rendered / viewed in a web browser. A lot of online web tools like forums, blogs, static site generators and other websites like GitHub have support for Markdown.

A block of markdown can be converted to a block of HTML. For example:

```
# Title
### Sub title
```

gets converted to:

``` html
<h1>Title</h1>
<h3>Sub title</h3>
```

!!! note "mkdocs"
    `mkdocs` the documentation generator used for this project also uses Markdown for its content. So, we can write notes in markdown and `mkdocs` will convert that note into structured HTML pages that can be read on a browser.


### Cheat sheet

A frequently used list of markdown elements

|   Element  |  Markdown Syntax  |
| ---- | ---- |
| __Heading__ | `# H1` <br> `## H2` <br> `### H3` |
| __Bold__ | __`__bold text__`__ <br> __`**bold text**`__ |
| __Italic__ | _`_italicized text_`_ <br> _`*italicized text*`_ |
| __Blockquote__ | `> blockquote` |
| __Ordered List__ |<pre><code> 1. First item <br> 2. Second item <br> 3. Third item </code></pre>|
| __Unordered List__ | <pre><code> - First item <br> - Second item <br> - Third item</code></pre>|
| __Code__ | <code>'code'</code> |
|  __Horizontal Rule__ | `---` |
| __Link__ | `[Google](https://www.google.com)` |
| __Table__ | <pre><code> \| Syntax \| Description \|<br> \| ------ \| ----------- \|<br> \| Header \| Title \|<br> \| Paragraph \| Text \| </code></pre>|
| __Task List__| <pre><code> - [x] Write code <br> - [ ] Update the website <br> - [ ] Contact the manager</code></pre> |


### References

- [Basic Writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

- [Advanced formatting](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting)

- [Writing on GitHub](https://docs.github.com/en/get-started/writing-on-github)