---
layout: post
title: LaTex formatting for UCLA dissertation using uclathe 
description: 
publish: true
categories: 
- misc
---

I'm currently writing my PhD dissertation using the [uclathe](https://github.com/uclathes/uclathes) style. Below are notes of some changes I've made to customize the template based on my needs.

* For references, the template includes a _uclathe_ bibliographystyle. However, that style follows BibTex's default `alpha` style, which uses author abbreviations and years rather than numbers to denote each citation. I like to enumerate my references, so I opted to use the `ieeetr` style, which enumerates and sorts the references
* If you are using TexStudio as your editor, it is recommended that you use the following Build & View (Preferences -> Build -> Build & View) order of commands: PdfLaTex - BibTex - PdfLaTex - PdfLaTex 








