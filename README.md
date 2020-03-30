## Welcome Github Pages

You can use the [editor on GitHub](https://github.com/aramisentreri/aramisentreri.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/aramisentreri/aramisentreri.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

## There is a tutorial to include Latex syntax to Github pages that I want to follow:
[Adding MathJax to a GitHub Pages Jekyll](http://sgeos.github.io/github/jekyll/2016/08/21/adding_mathjax_to_a_jekyll_github_pages_blog.html)

## Steps to get mathjax working
1. Download the theme template (in my case [minimal](https://github.com/pages-themes/minimal)) from the folder '_layouts/default.html',_ and include it in your own site repository under "_layouts/default.html"_
2. Edit that file to include in the head portion the following scrips:
```html
<head>
  ...

  <script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
    </script>
    <script type="text/javascript" charset="utf-8" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
    </script>
    <script type="text/javascript" charset="utf-8" src="https://vincenttam.github.io/javascripts/MathJaxLocal.js">
    </script>
</head>
```
3. Then on the markdown file you want to add math formulas, simply write them between $$:
```
## Example using simple mathjax

$$ r = h = \sqrt{\frac {1} {2}} = \sqrt{\frac {N} {N+1}} \sqrt{\frac {N+1} {2N}} $$
```

## Steps to add comments to blog posts using Github Issues API
1. See the tutorial from [Aristath's github page](https://aristath.github.io/blog/static-site-comments-using-github-issues-api)
