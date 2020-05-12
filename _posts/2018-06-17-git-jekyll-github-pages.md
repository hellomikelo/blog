---

layout: post
title: Short Guide to Using git with Jekyll and Github Pages
description: 
excerpt_separator: <!--more-->
categories: [Guides]

---

I've been using <a href="https://jekyllrb.com/" target="_blank">Jekyll</a> to build this blog for a while now, but since I haven't been updating this blog often, I always forget the basic git workflow for pushing updated content from my local computer onto Github. Therefore, I'm writing a short guide to quickly update a Github blog when new posts are created. 

<!--more-->

## Update blog from user computer to Github

Note: instructions here assumes you have already set up a Github blog, using static site generators such as <a href="https://jekyllrb.com/" target="_blank">Jekyll</a>. For instructions on how to do that I refer to Github's tutorial on <a href="https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/" target="_blank"> Setting up your GitHub Pages site locally with Jekyll</a>.

Assuming you've just finished creating a post on your local computer and you are ready to push the content onto Github. Navigate to your blog directory (i.e. directory that contains `.git/`) in command line, and do the following:

    git add .
    git commit -m "descriptive-message-of-changes-to-be-committed"
    git push

This will `add` all files in the directory to the staging area, then `commit` them to be submitted to Github. You will be required to include a message with the changes (this is a good practice anyway). At this step the changes you've made still only exist on the local computer. By running`push` you will send the updated files to Github and finish the update process.

So that's it! Happy blogging!

## Other tips
* To see if any other files are not updated between branches, you can check the status of file-keeping with 

		git status
 
* You can also preview the blog on your local computer by 

		jekyll serve

	The prompt will show you a server address, (e.g. http://127.0.0.1:4444) that you can then open with in a browser to see a preview of your blog.

* Sometimes if you mess with the `_config.yml` file that contains Jekyll's configuration parameters, you may introduce errors that will prevent Github from updating any changes. YAML files are very sensitive to formatting, so sometimes even missing a white space can ruin things. To check for errors, you can use the <a href="https://codebeautify.org/yaml-validator" target="_blank">YAML validator</a> from Code Beautify.






