---
layout: post
keywords: ebook, crawler, wiki
description: It's often too slow to access a document online, so it should be really help to mirror it and make a ebook.
title: "make a ebook from online web pages"
categories: [work]
tags: [ebook document ]
group: archive
icon: file-alt
---
{% include site/setup %}


Make a Ebook from Online Web Pages
==================================

## Problem
It's often too slow to access a document online, so it should be really help to mirror it and make a ebook.  

When I frequently access this site, [Lemur Project and Indri Search Engine Wiki](http://sourceforge.net/p/lemur/wiki/Home/), I found it really frustrating...

## Crawling
**wget** is enough.

1. first try  

    ```sh
    wget -r -p -k -I /p/lemur/wiki http://sourceforge.net/p/lemur/wiki/Home/
    ```

    follow directory works fine!  
    but wiki contents has too much versions, History, Feeds

2. check the log  

    Check the log, find these kinds of urls :  
    http://sourceforge.net/p/lemur/wiki/search/?q=labels_t%3A%22command-line%22&parser=standard&sort=score+desc  
    http://sourceforge.net/p/lemur/wiki/browse_pages/?sort=alpha&page=0  
    http://sourceforge.net/p/lemur/wiki/browse_tags/  

    ==>they are all navigational hyperlinks outside the main text, which are not needed.  
    出现在正文外面的 导航 hyperlinks

    Check the log, find these kinds of urls :  
    --2014-10-24 11:01:27--  http://sourceforge.net/p/lemur/wiki/Indri
    正在连接 sourceforge.net (sourceforge.net)|216.34.181.60|:80... 已连接。
    已发出 HTTP 请求，正在等待回应... 302 Found
    位置：http://sourceforge.net/p/lemur/wiki/Indri/ [跟随至新的 URL]
    --2014-10-24 11:01:28--  http://sourceforge.net/p/lemur/wiki/Indri/
    正在连接 sourceforge.net (sourceforge.net)|216.34.181.60|:80... 已连接。
    已发出 HTTP 请求，正在等待回应... 200 OK
    长度： 34905 (34K) [text/html]
    正在保存至: “sourceforge.net/p/lemur/wiki/Indri.1”

    ==>such jump , it means the url are actually the same in content. faint...................  
    wget doesn't distinguish Directory and File name  Indri/ exist --> Indri.1  
    try "add -nc", but is says:  
    "Both --no-clobber and --convert-links were specified,only --convert-links will be used."  

    Check the log, find :  
    http://sourceforge.net/p/lemur/wiki/RankLib/
    it save result to file "RankLib" other than index.html under /RankLib.....  

    ==>try "-nd"  

3. at last

    ```c 
    wget -r -p -E -c -nd -k --max-redirect=3 -R history,feed*,*version=* -I /p/lemur/wiki -X /p/lemur/wiki/browse_pages,/p/lemur/wiki/search,/p/lemur/wiki/browse_tags -o lemur.log http://sourceforge.net/p/lemur/wiki/Home/
    ```

    this works fine~

## 2. ebook maker
1. Publish online.  
just upload the directory to [my online document repository](http://net.pku.edu.cn/~pb/doc)

2. Publish ebook.  
publish it to a ebook by [Calibre](http://calibre-ebook.com)~


## Reference
Useful parameters of **wget**

       -r
       --recursive
           Turn on recursive retrieving.    The default maximum depth is 5.

       -l depth
       --level=depth
           Specify recursion maximum depth level depth.

       -k
       --convert-links
           After the download is complete, convert the links in the document
           to make them suitable for local viewing.  This affects not only the
           visible hyperlinks, but any part of the document that links to
           external content, such as embedded images, links to style sheets,
           hyperlinks to non-HTML content, etc.

       --mirror
           Turn on options suitable for mirroring.  This option turns on
           recursion and time-stamping, sets infinite recursion depth and
           keeps FTP directory listings.  It is currently equivalent to -r -N
           -l inf --no-remove-listing.

       -p
       --page-requisites
           This option causes Wget to download all the files that are
           necessary to properly display a given HTML page.  This includes
           such things as inlined images, sounds, and referenced stylesheets.


       -L
       --relative
           Follow relative links only.  Useful for retrieving a specific home
           page without any distractions, not even those from the same hosts.

       -I list
       --include-directories=list
           Specify a comma-separated list of directories you wish to follow
           when downloading.  Elements of list may contain wildcards.

       -nc
       --no-clobber
           If a file is downloaded more than once in the same directory,
           Wget's behavior depends on a few options, including -nc.  In
           certain cases, the local file will be clobbered, or overwritten,
           upon repeated download.  In other cases it will be preserved.

       -o logfile
       --output-file=logfile
           Log all messages to logfile.  The messages are normally reported to
           standard error.
       -nd
       --no-directories
           Do not create a hierarchy of directories when retrieving
           recursively.  With this option turned on, all files will get saved
           to the current directory, without clobbering (if a name shows up
           more than once, the filenames will get extensions .n).

       -E
       --adjust-extension
           If a file of type application/xhtml+xml or text/html is downloaded
           and the URL does not end with the regexp \.[Hh][Tt][Mm][Ll]?, this
           option will cause the suffix .html to be appended to the local
           filename.  This is useful, for instance, when you're mirroring a
           remote site that uses .asp pages, but you want the mirrored pages
           to be viewable on your stock Apache server.  Another good use for
           this is when you're downloading CGI-generated materials.  A URL
           like http://site.com/article.cgi?25 will be saved as
           article.cgi?25.html.

       --max-redirect=number
           Specifies the maximum number of redirections to follow for a
           resource.  The default is 20, which is usually far more than
           necessary. However, on those occasions where you want to allow more
           (or fewer), this is the option to use.

       -U agent-string
       --user-agent=agent-string
           Identify as agent-string to the HTTP server.

       -k
       --convert-links
           After the download is complete, convert the links in the document
           to make them suitable for local viewing.  This affects not only the
           visible hyperlinks, but any part of the document that links to
           external content, such as embedded images, links to style sheets,
           hyperlinks to non-HTML content, etc.

