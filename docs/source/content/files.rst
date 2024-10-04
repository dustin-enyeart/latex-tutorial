*****
Files
*****

========
Software
========

This tutorial uses the program ``latexmk``. 
On `Ubuntu <https://ubuntu.com/>`_, this program comes with ``texlive-full``, which can be install with the following shell command. 

.. code-block:: shell

   sudo apt install texlive-full


The program ``latexmk`` is a shell program that simplifies using Latex by helping with file management and being able to determine how many compiling passes are needed. 
It is better to use such a shell program than a GUI so that the user's editor of choice can be used. 
The command ``latexmk -h`` prints its options.


===============
Minimal Example
===============

The following in a minimal working example. 

.. code-block:: latex

    \documentclass[12pt]{article}
    \begin{document}

    This is the body text. 


    \end{document}

Everything before ``\begin{document}`` is the preamble, which includes formatting, packages and definitions. 
Everything between ``\begin{document}`` and ``\end{document}`` is the body. 

Every latex document requires a document class. 
In this example, the document class ``article`` is used. 
The article class ``book`` could be used for a book. 
And, the class ``beamer`` is used for presentations.
These three document classes are sufficient for personal needs for most people.
Although, some people may prefer the document classes ``amsart`` and ``amsbook`` from AMS instead of ``article`` and ``book``.

When publishing in a journal, the journal will provide a document class. 
Such a file is denoted by the extension ``.cls``.
Most people will never have to make their their own document class. 


.. The document class ``beamer`` is used for presentations
.. It is much better than something like Powerpoint
.. After this tutorial, the specifics of Beamer can be learned from [here] or [here]. 
.. https://www.overleaf.com/learn/latex/Beamer%23Creating_a_table_of_contents
.. https://latex-beamer.com/quick-start/


=========
Compiling
=========

If the above minimal working example is saved as ``main.tex``, then the command 

.. code-block:: latex

    latexmk -pdf file.tex

will compile the document. 
If ``latexmk`` is not installed, then see the :ref:`start page <start_page>` of this tutorial. 

The option ``-pdf`` means that the compiler ``pdflatex`` is used. 
This is compiler is sufficient for most of the time. 
Some packages may require a different compiler. 
The other compiler options are ``-xelatex`` and ``-lualatex``.

This will make several files in the directory. 
The most important is the PDF file ``main.pdf``, which is the desired end. 
The other files are saved by the compiler for later runs. 
One reason for this is to make later compilations faster, which is useful for large documents. 
The command 

.. code-block:: latex

    latexmk -c

will remove these other files. 
Sometimes, a failed compilation will alter these files in a way that will prevent later compilations. 
Thus, this command is useful to run when debugging. 


======
Titles
======

The following expands the minimal working example above. 


.. code-block:: latex

    \documentclass[12pt]{article}
    
    \title{My First Document}
    \author{Dustin Enyeart}
    \date{17 September 2024}

    \begin{document}
    \maketitle

    This is the body text. 


    \end{document}


The title, author and date are added in the preamble. Then, the command ``\maketitle`` formats them and add them in the body.
The title, author and date are all optional. 
Furthermore, a quick fix to add more information, such as intuition or course number, is to hijack the ``\date`` command.


.. code-block:: latex

    \documentclass[12pt]{article}
    
    \title{My First Document}
    \author{Dustin Enyeart}
    \date{17 September 2024 \\ \vspace{1em} 
          MA 341 \\ \vspace{1em}
          University of Nowhere}

    \begin{document}
    \maketitle

    This is the body text. 


    \end{document}


Other document classes may have something along the lines of ``\institution{}`` or ``\affliation{}`` to add this information.

The header can also be formatted and added in directly. 

.. code-block:: latex

    \documentclass[12pt]{article}

    \begin{document}
    
    \begin{center}
        \textbf{My First Document} \\
        Dustin Enyeart \\
        17 September 2024 \\
        MA 341 \\
        University of Nowhere \\
    \end{center}

    This is the body text. 


    \end{document}


=========
Divisions
=========

Sections and subsections can be added with the command ``\section{}`` and ``\subsection{}``. And, in books, chapters can be added with the command ``\chapter{}``. These are automatically numbered. Using a start ``*``, such as in ``\section*{}``, will make the section unnumbered. 


.. code-block:: latex

    \documentclass[12pt]{article}

    \begin{document}

    \section{First section}

    Some text. 


    \section{Second section}

    Some text. 


    \end{document}


Such sections will automatically be numbered. 
The command ``\section*{First section}`` would make the section unnumbered.
Similarly, the command ``\subsection{}`` would make a subsection, and, in a book, the command ``\chapter{}`` would make a chapter.

The command ``\tableofcontents`` would put in a table of contents. 
Bibliographies are explained in the chapter :ref:`References <refs>`.


========
Packages
========

A package can be included with the command ``\usepackage{}`` in the preamble.
A common packages is ``amsmath``, which is used for formatting mathematical equations. 
The following expands the example above to include this package. 

.. code-block:: latex

    \documentclass[12pt]{article}

    \usepackage{amsmath}

    \title{My First Document}
    \author{Dustin Enyeart}
    \date{17 September 2024}

    \begin{document}
    \maketitle

    \section{First section}


    This is the body text. 


    \end{document}


===============
Some Formatting
===============

The output so far may look a poorly formatted.
The following will have better margins. 

.. code-block:: latex

    \documentclass[12pt]{article}

    \usepackage[letterpaper, margin=1.0in, footskip=30pt]{geometry}
    \renewcommand{\baselinestretch}{1.0}

    \usepackage{amsmath}

    \title{My First Document}
    \author{Dustin Enyeart}
    \date{17 September 2024}

    \begin{document}
    \maketitle

    \section{First section}


    This is the body text. 


    \end{document}


The package ``geometry`` is used to set the margins, and the ``1.0`` or ``30pt`` can be changed to whatever is desired. 
The command ``\renewcommand{\baselinestretch}{1.0}`` redefines ``\baselinestretch``, which is used as the spacing between lines, and the ``1.0`` can be changed to whatever is desired. 

It may be useful to save this as a template as a minimal. 
It can then be expanded according to the user's wants as they go through this tutorial. 
There is a slightly more elaborate template as ``template.tex`` in the `git repository <https://github.com/dustin-enyeart/latex-tutorial>`_ for this tutorial


======
Inputs
======

The command ``\input{}`` can be used to included another file. 
For example, ``\input{otherfile}`` will include the file ``otherfile.tex``.
This directly copies the contents of the file, and it can be used anywhere in the document. 
The file must be in the same directory. 
For example, this can be used to have each section in a separate file.
It could also be useful to put a large tables in a different file.

If ``\input`` is used in the preamble for formatting, then the inputted file is called a *style* file and has the extension ``.sty`` is commonly used, although the extension ``.tex`` could also be used. 