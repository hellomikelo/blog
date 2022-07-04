# Pro-tips for maintaining the Jekyll blog

## COMPOSING 

### Compose in Google Docs

Write the content in Google Docs, then use the "Doc to Markdown" Doc plug-in to convert the content into Markdown and paste it into the blog entry. 

### Publish jupyter notebooks as a post

When converting Jupyter notebooks Markdown format for publishing, if the HTML table is wide and extends beyond the screen frame, you can make the table overflow and scroll-able in horizontal direction by replacing `<div>` with `<div style="overflow-x:auto;>`.

### Add images to a post

If you want to add images to posts, copy the image to the directory "/static/imgs/". When inserting the image in the post, add the relative link to the file, e.g. `![png](/static/imgs/output_44_0.png)`.

## BLOG CONFIGURATION & LAYOUT

### Edit blog layout's css style 

You can edit style sheets __css__ and __scss__ at: 

* blog/css/main.scss (base CSS script)
* blog/\_sass/\_base.scss
* blog/\_sass/\_layout.scss 

If you make changes to the configuration or CSS, remember to do `jekyll build`. Before pushing to Github, or else the changes won't be reflected online.

### Test out changes before publishing

1. Go to blog home directory
2. Do `bundle exec jekyll serve`
3. Go see the blog at http://127.0.0.1:4444/
4. Make changes and see updates in browser

For more details, see [Testing your GitHub Pages site locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll).

### Edit blog configurations

You can edit the blog's configurations in \_config.yml located in the blog's root directory.
