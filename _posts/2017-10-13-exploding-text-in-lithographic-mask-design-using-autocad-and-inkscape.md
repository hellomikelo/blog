---

layout: post
title: Exploding Text in Lithographic Mask Design Using AutCAD and Inkscape
published: true
categories: [Guides]
excerpt_separator: <!--more-->

---

This post will explain how I created exploding text inside AutoCAD for lithography mask design using Inkscape. Normally, the text you enter in AutoCAD is automatically hatched, which for some reason cannot be read correctly by mask fracturing software. I've tried the text explode tool (**TXTEXP**) in Express Tools, but at least in the Mac version of AutoCAD it does not work. Maybe it works in the Windows version, I don't know. Anyway, in order to properly incorporate text into your design, you must create outlined versions of your text. For this workaround I'm using AutoCAD 2017 Mac edition. 

<!--more--> 

1. To begin, open Inkscape and create text using whichever font and font size you'd like. 
2. **Path** -> **Object to Path**. If you double click the text now you will see that each character is now its own object and has its own path. 
3. **Save as** -> *your_file_name.dxf*. A pop-up window will show up. You can keep the default options and save. 
4. Go into AutoCAD and open *your_file_name.dxf*
5. When you first see your text, you will most likely see a crude outline of the text, with lots of unwanted lines everywhere, and most lines will not be joined so they do not represent a closed loop. For instance, 

From here I will offer several ways in which you can clean up the text to be in its final form. 

* To get rid of unwanted lines, you can select the polyline and use **BREAKUP (EXPLODE)** command. This will separate individual line segments within the polyline. Then select the line you don't want and delete. 
* If you select all the lines in one character and **JOIN**, you will find that some line segments become spline, while others remain line or polyline. Because of the difference in line type, not all segments will be joined. A somewhat tedious task is to check different line segments and convert them all to polyline. You can convert splines to polylines by selecting splines and **PEDIT**. You will be ask "Do you want to turn it into one?". Enter "Y" and specify the precision (1-10) of the conversion. 
* After all lines in a character are in polyline, select all the lines and **JOIN** again, and you should be able to join all the line segments of a character together. Sometimes a curved and straight segment cannot be joined (e.g. at sharp corners of "r", for instance), so I'd select the straight segment and **PEDIT** -> **OPEN**. After which the join should work. 
* In my case, the lithographic pattern fracturing software cannot recognize when one polyline is nested inside another (e.g. character O), so I had to find a workaround by introducing a small gap to the character to essentially joines two lines into one. You can do this by **BREAK** and clicking on one line segment. You will determine how much of a gap to create by moving the cursor along the line. Repeat the same process for the other line. Next, enable Object Snap (F3) and select the tip of one of the line segments and add a vertex. Drag that vertex to the vertex of the other line and make sure the ends join. Repeat for the other vertex. After all vertices look like they aligned well, select all the lines in the character again and try **JOIN**. 

Follow the steps above and go through iterations for each character until all the characters is a closed polyline, then you have successfully exploded text! 




