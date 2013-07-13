---
layout: post
title: '开始阅读SICP及用Racket完成练习题'
tags: 
- Scheme
- SICP
- Racket
---
在[大熊](http://gigix.thoughtworkers.org/)的倡议和[校长](http://dreamhead.blogbus.com/)的怂恿下，我也下血本购买了SICP的英文版 [<<Structure and Interpretation of Computer Programs>>](http://www.amazon.cn/gp/product/0262510871)和中文版[<<计算机程序的构造和解释>>](http://www.amazon.cn/gp/product/B0011AP7RY)，并开始了阅读此书的不归路。

开始阅读以前就听各位前辈说此书易读难懂，并建议完成课后习题来加强理解，所以在读完1.1.6节时我就开始寻找能用来帮助做习题的工具。 我先试了一下校长提过的[Clojure](http://clojure.org/)，但因为书中描述的例子不能直接用Clojure来实验，我最后还是转向了[Racket](http://racket-lang.org/)。 Racket不仅提供了REPL(read-eval-print loop)窗口和简单的IDE，也提供了直接执行源代码文件的功能。 下载安装Racket后，你就可以使用GRacket或DrRacket来编写程序了。 为了从命令行直接运行Racket，我们需要把Racket的Bin目录加到环境变量里。 在Mac上，把下列两行加到.bash_profile文件并source .bash_profile就可以了。

{% highlight bash %}
export RACKET_HOME="/Applications/Racket v5.3.5"
export PATH="$RACKET_HOME/bin:$PATH"
{% endhighlight %}

设置好后，我们创建一个Scheme源代码文件test.scm:

{% highlight scheme %}
#lang racket
(define (squre x) (* x x))
(squre 3)
{% endhighlight %}

注意第一行的"#lang racket"是让Racket识别我们所选择的语言。 保存后从命令行执行"racket test.scm"应该能得到输出结果是9。
这样我们就可以轻松的实验书中所描述的例子以及完成习题了。 我也创建了一个Git Repo [sicp-solutions](https://github。com/ryandjf/sicp-solutions)来保存习题的答案。