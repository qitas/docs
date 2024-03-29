.. _lan_compile:

编译原理
===========

* 1 编译器是一种翻译程序，它用于将源语言（即用某种程序设计语言写成的）程序翻译为目标语言（即用二进制数表示的伪机器代码写成的）程序。后者在windows操作系统平台下，其文件的扩展名通常为.obj。该文件通常还要经过进一步的连接，生成可执行文件（机器代码写成的程序，文件扩展名为.exe）。通常有两种方式进行这种翻译，一种是编译，另一种是解释。后者并不生成可执行文件，只是翻译一条语句、执行一条语句。这两种方式相编译比解释运行的速度要快得多。
* 2 编译过程的5个阶段：词法分析；语法分析；语义分析与中间代码产生；优化；目标代码生成。
* 3 在这五个阶段中，词法分析的任务是识别源程序中的单词是否有误，编译程序中实现这种功能的部分一般称为词法分析器。在编译器中，词法分析器通常仅作为语法分析程序的一个子程序以便在它需要单词符号时调用。在这一编译阶段中发现的源程序错误，称为词法错误。
* 4 语法分析阶段的目的是识别出源程序的语法结构（即语句或句子）是否错误，所以有时又常为句子分析。编译程序中负责这一功能的程序称为语法分析器或语法分析程序。在这一阶段中发现的错误称为语法错误。
* 5 C语言的（源）程序必须经过编译才能生成目标代码，再经过链接才能运行。PASCAL语言、FORTRAN语言的源程序也要经过这样的过程。通常将C、PASCAL、FORTRAN这样的语言统称为高级语言。而将最终的可执行程序称为机器语言程序。
* 6 在编译C语言程序的过程中，发现源程序中的一个标识符过长，超过了编译程序允许的范围，这个错误应在词法分析阶段发现，这种错误通常被称作词法错误。

编译过程
-----------
**预处理，编译，组装，链接**

* 预处理：gcc -E project.c -o project.i //宏展开，宏替换
* 编译：gcc -S project.i -o project.s //将目标文件编译成汇编文件
* 汇编：gcc -c project.s -o project.o //汇编成二进制文件
* 链接：gcc project.o -o project  //加载库文件，生成可执行文件

.. note::
    组装才是平台相关的，之前的操作都与平台无关

编译程序的工作过程一般也可以划分为五个阶段：词法分析、语法分析、语义分析与中间代码产生、优化、目标代码生成。


ASSERT
~~~~~~~~~~~~~~

ASSERT()是一个调试程序时经常使用的宏，在程序运行时它计算括号内的表达式，如果表达式为FALSE (0), 程序将报告错误，并终止执行。如果表达式不为0，则继续执行后面的语句。

ASSERT只有在Debug版本中才有效，如果编译为Release版本则被忽略。
