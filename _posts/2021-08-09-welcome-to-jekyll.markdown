---
layout: post
title:  "Welcome to Jekyll!"
date:   2021-08-09 14:24:06 +0800
categories: jekyll update
---

### Jephian's testing area

#### Inline math:

- `$$x^2$$`: $$x^2$$ (the only correct way for kramdown...)
- `$x^2$`: $x^2$ (content might be parsed by kramdown)
- `\\(x^2\\)`: \\(x^2\\) (content might be parsed by kramdown)
- `<span markdown=0>$x^2$</span>`: <span markdown=0>$x^2$</span> (passing raw code)

or `<div display="inline" markdown=0>$x^2$</div>` to make
<div display="inline" markdown=0>$x^2$</div>
(which is not necessary).


#### Display math:

`blank line + $$display math$$ + blank line` (kramdown way)

$$A = \begin{bmatrix}
 1 & 2 \\
 3 & 4
\end{bmatrix}.$$

at the beginning of a line do `<div>\[display math\]</div>` (row code)
<div>\[A = \begin{bmatrix}
 1 & 2 \\
 3 & 4
\end{bmatrix}.\]</div>

- inside a list: at the beginning of a line do `indent <div>\[display math\]</div>` (row code)
    <div>\[A = \begin{bmatrix}
 1 & 2 \\
 3 & 4
\end{bmatrix}.\]</div>

Anywhere do `<span display:"block" markdown=0>\[display math\]</div>` (row code, faked inline element)  
Consider the matrix <span display="block" markdown=0>\[A = \begin{bmatrix}
 1 & 2 \\
 3 & 4
\end{bmatrix}.\]</span>


#### Macro:

- defined by `macros` in the head tag: $\R$
- defined by `$\gdef\teste{\mathbf{e}}$`: $\gdef\teste{\mathbf{e}}$ $\teste$
- defined by `$\newcommand{\testf}{\mathbf{f}}$`: $\newcommand{\testf}{\mathbf{f}}$ $\testf$  
(This part need to set `globalGroup: true` in KaTeX setting.)


#### Code block

```python
from manim import *
class Test(Scene):
    square = Square()
    self.play(Create(square))
```

#### Line wrap

(no space after)
(one space after) 
(two space after)  
last line

沒空格
一個空格 
兩個空格  
最後一行

### Original content of this page

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
