# Markdown - A Lightweight Markup Language

This is a simplified guide to some of the markdown elements. For each topic, you will see what you can do and how to do it. Interestingly enough, the whole document has been built with markdown itself. [^1]

For those who already know the basics of markdown, you can go directly to the Topic [Cheat Sheet](#cheat-sheet).

1. [Headings](#headings)
2. [Styling](#styling)
3. [Quoting](#quoting)
4. [Code](#code)
5. [Links](#links)
6. [Lists](#lists)
7. [Horizontal Rule](#horizontal-rule)
8. [Table](#table)
9. [Footnote](#footnote)
10. [Emoji](#emoji)
11. [Cheat Sheet](#cheat-sheet)
12. [Conclusion](#conclusion)
13. [References](#references)

## Headings

# ISSUE - The largest heading
## 1 Section - The second largest heading
### 1.1 Subsection - The third largest heading
#### 1.1.1 Subsubsection - The fourth largest heading
##### - The fifth largest heading
###### - The sixth largest heading

```
# ISSUE - The largest heading
## 1 Section - The second largest heading
### 1.1 Subsection - The third largest heading
#### 1.1.1 Subsubsection - The fourth largest heading
##### - The fifth largest heading
###### - The sixth largest heading
```

## Styling

**bold**: `**bold**`<br>
*italic*: `*italic*`<br>
***bold and italic***: `***bold and italic***`<br>
~~strikethrough~~: `~~strikethrough~~`

## Quoting

> This is a comment made by a user.

This is my thoughts on the previous quote comment.

```
> This is a comment made by a user.

This is my thoughts on the previous quote comment.
```

## Code

**Within a sentence**

Use `git init` to initialize a local repository.

``Use `git init` to initialize a local repository.``

**As a block**

```
git status
git add .
git commit
```

````
```
git status
git add .
git commit
```
````

**Code snippet**

```javascript
function add(x, y) {
  return x + y;
}
```

````
```javascript
function add(x, y) {
  return x + y;
}
```
````

## Links

Always use relative links when referencing an asset in your project in order to avoid problems with forked and cloned repositories.

**URL**

Much more information can be found at [GitHub Documentation](https://docs.github.com/en).

`Much more information can be found at [GitHub Documentation](https://docs.github.com/en).`

**Section**

You can click [here](#headings) to return to the Topic **Headings**.

`You can click [here](#headings) to return to the Topic **Headings**.`

You can click [here](#markdown---a-lightweight-markup-language) to return to the beginning of the document.

`You can click [here](#markdown---a-lightweight-markup-language) to return to the beginning of the document.`

**Image**

![The Octocat](https://myoctocat.com/assets/images/base-octocat.svg)

`![The Octocat](https://myoctocat.com/assets/images/base-octocat.svg)`

## Lists

**Unordered**

- Item 1
- Item 2
  - Item 2.1
  - Item 2.2
    - Item 2.2.1

```
- Item 1
- Item 2
  - Item 2.1
  - Item 2.2
    - Item 2.2.1
```

**Ordered**

1. First
2. Second
3. Third

```
1. First
2. Second
3. Third
```

**Tasks**

- [x] Review the main code
- [ ] Write the manual pages for the library
- [ ] Start the log functionality

```
- [x] Review the main code
- [ ] Write the manual pages for the library
- [ ] Start the log functionality
```

## Horizontal Rule

This is a paragraph before horizontal rule.

---

This is a paragraph after horizontal rule.

```
This is a paragraph before horizontal rule.

---

This is a paragraph after horizontal rule.
```

## Table

| Name | Age | Salary |
|:---|:---:|---:|
| John | 29 | 9,900.00 |
| Elizabeth | 30 | 19,000.00 |

```
| Name | Age | Salary |
|:---|:---:|---:|
| John | 29 | 9,900.00 |
| Elizabeth | 30 | 19,000.00 |
```

## Footnote

I think, therefore I am. [^2]

```
I think, therefore I am. [^2]

[^2]: René Descartes.
```

## Emoji

:+1: That is a good idea. :clap: Great! :smile: I am happy. :pout: We have a problem!

```
:+1: That is a good idea. :clap: Great! :smile: I am happy. :pout: We have a problem!
```

## Cheat Sheet

If you need to render some of the special markdown characters, try using a backslash (\\) to escape them.

| Element | Markdown |
|---|---|
| Heading | `# H1`<br> `## H2`<br> `### H3` |
| Bold | `**bold**` |
| Italic | `*italic*` |
| Strikethrough | `~~strikethrough~~` |
| Quote | `> original message` |
| Code | `` `code` `` |
| Code Block | ```` ```language````<br> `code block`<br> ```` ``` ```` |
| Link | `[title](url)`<br> `[title](#header-id)` |
| Image | `![alt text](url)` |
| Unordered List | `- First Item`<br> `- Second Item`<br> `- Third Item` |
| Ordered List | `1. First Item`<br> `2. Second Item`<br> `3. Third Item` |
| Task List | `- [x] Task 1`<br> `- [ ] Task 2`<br> `- [ ] Task 3` |
| Horizontal Rule | `---` |
| Table | `\| Left \| Center \| Right \|`<br> `\|:---\|:---:\|---:\|`<br> `\| x \| 1 \| 2 \|`<br> `\| y \| 3 \| 4 \|` |
| Footnote | `A sentence with a footnote. [^id]`<br><br> `[^id]: This is the footnote.` |
| Emoji | `:EMOJICODE:` |

## Conclusion

The goal of this document is not to be a comprehensive resource for the markdown language. You can check out the references for more information. Here we just simplified the use of the language by pointing out simple examples of the supposed most used features. By doing that, we consider the document as a quick refresher of how to do something.

Even though some features were not covered here, they were used in the construction of the document, so you can always look at this source file to see them yourself.

## References

- [GitHub Docs: Basic formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [GitHub Docs: Create code blocks](https://docs.github.com/en/github/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks)
- [Markdown Guide](https://www.markdownguide.org/)
- [Emojipedia](https://emojipedia.org/)

[^1]: We used some HTML \<br\> tags in some places in order to force a line break.
[^2]: René Descartes.
