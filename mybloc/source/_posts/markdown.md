---
title: Markdown
date: 2017-09-05 19:09:47
tags: [cheatsheet , markdown]
---
## Headers
``` markdown
# H1
### H3  
###### H6
Header 1
========

Header 2
--------
```

## Emphasis


``` markdown
*Italics* / _Italics_                       # 斜体：command + i

**Bold** / __Bold__                         # 粗体：command + b

~~Strikethrough~~                           #  删除线
```

<!--more-->
## Lists

``` markdown
1. First ordered list item
2. Another item
  * Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
  1. Ordered sub-list
4. And another item.  

   Some text that should be aligned with the above item.

* Unordered list can use asterisks
- minuses
+ pluses

```

## Links
``` markdown

https://github.com

[Inline-style](https://www.google.com)      # command + shift + k

[Reference-style][Google]
[Reference-style][1]
leave it empty  [link text]

[Google]: https://www.mozilla.org
[1]: http://slashdot.org
[link text]: http://www.reddit.com
```


## Relative links
``` markdown
[Contribution](docs/CONTRIBUTING.md)
[Contribution](./)
[Contribution](../)
```
## Images

``` markdown
![alt text](https://xxx.png)                # Inline-style

![alt text][logo]                           # Reference-style

[logo]: https://xxx.png

![Image alt text](/path/to/img.jpg)
![Image alt text](/path/to/img.jpg "title")
![Image alt text][img]

[img]: http://foo.com/img.jpg

```
## Code and Syntax Highlighting / Quoting code

``` markdown
`code`

\```somthing```\                            # ignore "\"

```

## Tables

``` markdown
| A | B | C |
|:- |:-:| -:|
| a | b | f |
| c | d | e |
| F | G | H |

A   |  B  |  C
--- | --- | ---
*a* | `b` | **c**
1   |  2  |   3

| Name     | Character |
| ---      | ---       |
| Backtick | `         |
| Pipe     | \|        |
```

## Blockquotes

``` markdown
> This is
> a blockquote
>
> > Nested
> > Blockquote

> This is
  another blockquote
```


## Inline HTML

```
<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>```



## Horizontal Rule

``` markdown
----                    # Hyphens
****                    # Asterisks
____                    # Underscores
```


## Task lists

``` markdown
- [x] Finish my changes
- [ ] Push my commits to GitHub

- [ ] \(Optional) Open a followup issu

```

More info: [About task lists](https://help.github.com/articles/about-task-lists/)

## Mentioning users and teams
``` markdown
@github/support What do you think about these updates?
```
More info: [About teams](https://help.github.com/articles/about-teams/)

## Referencing issues and pull requests

More info: [Autolinked references and URLs](https://help.github.com/articles/autolinked-references-and-urls/)

## Using emoji
``` markdown
 :+1:
 :shipit:
```
More info:[emoji-cheat-sheet.com](https://www.webpagefx.com/tools/emoji-cheat-sheet/)


## Ignoring Markdown formatting
``` markdown
Let's rename \*our-new-project\* to \*our-old-project\*.
```

More info: [Markdown Syntax](https://daringfireball.net/projects/markdown/syntax#backslash)

## YouTube Videos

``` html
<a href="http://www.youtube.com/watch?feature=player_embedded&v=YOUTUBE_VIDEO_ID_HERE
" target="_blank"><img src="http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg"
alt="IMAGE" width="240" height="180" border="10" /></a>

[![IMAGE](http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](http://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)
```

-----

## Reference
[writing-on-github](https://help.github.com/categories/writing-on-github/)
[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
[Rico's Cheatsheets](http://ricostacruz.com/cheatsheets/)
