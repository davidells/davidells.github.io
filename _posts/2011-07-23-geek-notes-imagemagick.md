---
id: 37
title: 'Hacker Notes: ImageMagick'
date: 2011-07-23T03:32:34+00:00
author: dells
layout: post
guid: http://davidells.info/blog/?p=37
permalink: /2011/07/geek-notes-imagemagick/
dsq_thread_id:
  - "366348558"
categories:
  - hacker-notes
tags:
  - geek-notes
  - image-processing
---
[<img src="http://davidells.info/blog/wp-content/uploads/2011/07/wizard.jpg" alt="" title="image-magick-wizard" width="361" height="480" class="aligncenter size-full wp-image-44" />](http://davidells.info/blog/wp-content/uploads/2011/07/wizard.jpg)

Usually when I resize images, it&#8217;s on the spot for a single image I&#8217;m already looking at, but sometimes I need to resize a whole batch of photos (i.e. from a [DSLR](http://www.amazon.com/Canon-T2i-Digital-3-0-Inch-18-55mm/dp/B0035FZJHQ) on the way into [flickr](http://www.flickr.com/)). ImageMagick gives you a way to process images from the command line, hence giving you batch processing, and <a href=http://www.imagemagick.org/script/command-line-tools.php?ImageMagick=6e3cse6d86qtkn6f7qnrmcj867">lots of other interesting stuff</a>.

Either way, a mental jot in the web log, here&#8217;s the command to process the photos in the current directory (with the options set for my camera situation, changing ~5.5Mb images to around 1Mb in the output folder):

`for f in *.JPG;<br />
    do convert -verbose -resize "46%" \<br />
               -quality 94 $f output/$f;<br />
done`

If you&#8217;re processing a ton of files, you may want to watch the progress of the operation, so open up another terminal and run this (ending with CTRL + C when you&#8217;re done with it):

`while [ 0 -le 1 ];<br />
    do sleep 2;<br />
    ls -l /path/to/output/*.JPG | wc -l;<br />
done`