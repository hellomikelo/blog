=================

Tip: When Jupyter notebooks are converted to .md for publishing on the blog, if the HTML table is wide and extends beyond screen resolution, you can make table overflow and scroll in x by replacing 

<div>

with 

<div style="overflow-x:auto;>

=================

If you want to add images, add "/static/imgs/" to the beginning of the image path, e.g.

![png](/static/imgs/output_44_0.png)

=================

You can edit style sheets css and scss at 

blog/css/main.scss 

and 

blog/_sass/_base.scss

if you make changes to the configuration or css, remember to 

jekyll build

before pushing to Github, or else the changes won’t be reflected online.

=================

You can edit Jekyll blog's configuration at 

_config.yml 

in the blog's root directory

