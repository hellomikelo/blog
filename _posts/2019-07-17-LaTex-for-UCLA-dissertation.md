---

layout: post
title: LaTex Formatting for UCLA Dissertation Using uclathe 
description: 
published: true
excerpt_separator: <!--more-->
categories: [Research]

---

I'm currently writing my PhD dissertation using the [uclathe](https://github.com/uclathes/uclathes) style. Below are notes and tips on my writing process using LaTex:

<!--more-->

* For references, the template includes a **uclathe** bibliographystyle. However, that style follows BibTex's default **alpha** style, which uses author abbreviations and years rather than numbers to denote each citation. I personally like to enumerate my references, so I opted to use the **ieeetr** style, which enumerates and sorts the references automatically
* If you are using TexStudio as your editor, it is recommended that you use the following `Build & View` (`Preferences` -> `Build` -> `Build & View`) order of commands: **PdfLaTex** - **BibTex** - **PdfLaTex** - **PdfLaTex**. I think this has to do with how the bibliography is processed with LaTex
* For some reason sometimes .bbl does not update from .bib when compiling. In that case, delete the .bbl file and re-compile
* If you try to compile a document containing a bibliography without actually citing anything, there will be a "something's wrong--perhaps a missing \item \end{thebibliography}" error. In this case, actually cite something, delete .bbl file then recompile. UPDATE [4/4/2020]: Per Junhyung's suggestion, "you can actually include the command `\nocite{*}` in the file and it will print everything in your .bib file in the bibliography and not give you the error you mention here."









