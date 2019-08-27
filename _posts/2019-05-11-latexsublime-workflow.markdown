---
layout: post
title: Latex+Sublime+MathJax+Jekyll workflow
tags: [distill]
mathjax: true
---

So basically to make heavy math websites faster, use the workflow as below:

1. Have the pre-requisites installed first i.e. latex using miktex and Sublime text 3.
2. Make sure you have Perl also on your system.
3. Add "latexindent.pl" package from miktex.
4. Now set-up your sublime text as follows:
    * First things first: install 'package control'
    * Then add the following packages: LaTexTools, LateXYZ, Jekyll, BeautifyLatex
    * Optionally add these packages just to make your experience better: materialtheme, side bar, advanced new file, file icon and GitGutter.
5. If needed, use Pandoc to convert tex file to html 
{% highlight python %}
pandoc -s name_of_tex_file.tex --mathjax -o name_of_ex_file.html 
{% endhighlight %}
That's it. Your set-up is done!

To work faster with Sublime, learning keybindings (a.k.a keyboard shortcuts) is a must.