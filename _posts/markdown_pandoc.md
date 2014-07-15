---
　　layout: default
　　title: 你好，世界
---

#*如何在code中加粗字体*


###安装pandoc
***
### macos下的安装
通过homebrew安装pandoc  
搜索homebrew库，可以看到有pandoc命令，如下：

    [carlshen@Carl ~]$brew search pandoc
    pandoc       pandoc-citeproc
    [carlshen@Carl ~]$

进行安装：

    [carlshen@Carl ~]$brew install pandoc
    ==> Downloading https://downloads.sf.net/project/machomebrew/Bottles/pandoc-1.12.4.2.mavericks.bottle.tar.gz
    Already downloaded: /Library/Caches/Homebrew/pandoc-1.12.4.2.mavericks.bottle.tar.gz
    ==> Pouring pandoc-1.12.4.2.mavericks.bottle.tar.gz
    ==> Caveats
    Bash completion has been installed to:
      /usr/local/etc/bash_completion.d
    ==> Summary
    🍺  /usr/local/Cellar/pandoc/1.12.4.2: 45 files, 52M
    [carlshen@Carl ~]$

安装完毕，就可以使用pandoc了。  

### pandoc文档转换常用命令
*** 
####常用参数
* -f 输入格式
* -t 输出格式
* -o 输出文件
-f和-t参数可以省略，如果省略，pandoc会自动根据后缀名进行判断

####pandoc格式转换命令例子
以下两个命令效果完全一样

    pandoc -f markdown -t html hello.md -o hello.html
    pandoc hello.md -o hello.html


###macos下使得pandoc支持pdf格式
安装完毕后，pandoc默认不支持转为pdf格式。如果尝试将md文件转为pdf，会报错，如下：

    [carlshen@Carl ~]$pandoc file.md -o file.pdf
    pandoc: pdflatex not found. pdflatex is needed for pdf output.
    [carlshen@Carl ~]$

提示需要安装pdflatex。

安装macos下的latex组件。
参照如下网址
[http://guides.macrumors.com/Installing_Latex_on_a_Mac](http://guides.macrumors.com/Installing_Latex_on_a_Mac)  
步骤如下:  
* 打开网址，下载MacTeX.pkg(文件大小2.51G, 安装需要4.62G的空间)  
* 点击安装  
等待N分钟后，提示安装完成。安装完后的bin路径为/usr/texbin, 程序会自动添加该路径到$PATH中  
terminal中重新起一个tab，输入pdflatex -v,确认pdflatex正确被安装。
  
    [carlshen@Carl ~]$echo $PATH
    /usr/local/sbin:/usr/local/bin:/Users/carlshen/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/opt/X11/bin:/usr/texbin
    [carlshen@Carl ~]$pdflatex -v
    pdfTeX 3.14159265-2.6-1.40.15 (TeX Live 2014)
    kpathsea version 6.2.0
    Copyright 2014 Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
    There is NO warranty.  Redistribution of this software is
    covered by the terms of both the pdfTeX copyright and
    the Lesser GNU General Public License.
    For more information about these matters, see the file
    named COPYING and the pdfTeX source.
    Primary author of pdfTeX: Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
    Compiled with libpng 1.6.10; using libpng 1.6.10
    Compiled with zlib 1.2.8; using zlib 1.2.8
    Compiled with xpdf version 3.03
    [carlshen@Carl ~]$
    
安装完pdflatex后，尝试进行转换markdown为pdf，成功,不再报错了

    [carlshen@Carl 03_markdown]$pandoc file.md -o file.pdf
    [carlshen@Carl 03_markdown]$








