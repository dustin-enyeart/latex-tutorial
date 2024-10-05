*****
Files
*****

========
Software
========

This tutorial uses the program ``latexmk``. 
On `Ubuntu <https://ubuntu.com/>`_, this program comes with ``texlive-full``, which can be installed with the following shell command. 


.. code-block:: shell

   sudo apt install texlive-full


The program ``latexmk`` is a shell program that simplifies using Latex by helping with file management and automatically making as many compiling passes are need. 
Using such a shell program instead of GUI allows the user to use his editor of choice. 
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


Everything before ``\begin{document}`` is the *preamble*, which is where formatting, packages and command definitions are done. 
Everything between ``\begin{document}`` and ``\end{document}`` is the *body*. 

Every latex document requires a document class. 
In this example, the document class is ``article``. 
The document class ``book`` could be used for a book. 
And, the class ``beamer`` is used for presentations.
These three document classes are sufficient for the personal needs for most people.
Some people may prefer the document classes ``amsart`` and ``amsbook`` from AMS instead of ``article`` and ``book``.

When publishing in a journal, the journal will provide a document class. 
Such a file is denoted by the extension ``.cls``.
Most people will never have to write their their own document class. 
The command ``texdoc <class>`` will bring up the documentation for the document class ``<class>``.


=========
Compiling
=========

If the above minimal working example is saved as ``main.tex``, then the the following command will compile the document. 


.. code-block:: latex

    latexmk -pdf file.tex


The option ``-pdf`` means that the compiler ``pdflatex`` is used. 
This is compiler is normally sufficient.
But, some packages may require a the compilers ``xelatex`` or ``lualatex``, which are selected with the options ``-xelatex`` and ``-lualatex``, respectively. 

This will make several files in the directory. 
The main output is the file ``main.pdf``.
The other files are saved to help the compiler. 
The following command will remove these other files. 


.. code-block:: latex

    latexmk -c


Sometimes, a failed compilation will alter these files in a way that will prevent later compilations. 
Thus, this command is useful to run when debugging. 


======
Titles
======

The following expands the minimal working example above by adding a title, data and author.
Each is optional, and the the command ``\maketitle`` formats them in the body.


.. code-block:: latex

    \documentclass[12pt]{article}
    
    \title{My First Document}
    \author{Dustin Enyeart}
    \date{5 October 2024}

    \begin{document}
    \maketitle

    This is the body text. 


    \end{document}


Other document classes may have additional items that are formatted with ``\maketitle``, such as something along the lines of ``\institution{}`` or ``\affliation{}`` to add this information.
In the document class ``article``, the command ``\date{}`` can be hijacked to add such additional information, as the following example demonstrates. 


.. code-block:: latex

    \documentclass[12pt]{article}
    
    \title{My First Document}
    \author{Dustin Enyeart}
    \date{5 October 2024 \\ \vspace{1em} 
          MA 341 \\ \vspace{1em}
          University of Nowhere}

    \begin{document}
    \maketitle

    This is the body text. 


    \end{document}


The command ``\maketitle`` is not necessary. 
Instead, this information can be formatted directly in the body, as the following example demonstrates. 


.. code-block:: latex

    \documentclass[12pt]{article}

    \begin{document}
    
    \begin{center}
        \textbf{My First Document} \\
        Dustin Enyeart \\
        5 October 2024 \\
        MA 341 \\
        University of Nowhere \\
    \end{center}

    This is the body text. 


    \end{document}


=========
Divisions
=========

Sections and subsections can be added with the commands ``\section{}`` and ``\subsection{}``, respectively. And, in books, chapters can be added with the command ``\chapter{}``. These are automatically numbered. Using an asterisk ``*``, such as in ``\section*{}``, will make the section unnumbered. 


.. code-block:: latex

    \documentclass[12pt]{article}

    \begin{document}

    \section{First section}

    Some text. 


    \section{Second section}

    Some text. 


    \end{document}


The command ``\tableofcontents`` would put in a table of contents. 
Bibliographies are explained in the chapter :ref:`References <refs>`.


========
Packages
========

A package can be included with the command ``\usepackage{}`` in the preamble.
A common package is ``amsmath``, which is used for formatting mathematical equations. 
The following expands the example above to include this package. 

.. code-block:: latex

    \documentclass[12pt]{article}

    \usepackage{amsmath}

    \title{My First Document}
    \author{Dustin Enyeart}
    \date{5 October 2024}

    \begin{document}
    \maketitle

    \section{First section}


    This is the body text. 


    \end{document}


===============
Some Formatting
===============

The output so far may look poorly formatted on normal A1 paper.
The following example adjusts the margins. 


.. code-block:: latex

    \documentclass[12pt]{article}

    \usepackage[letterpaper, margin=1.0in, footskip=30pt]{geometry}
    \renewcommand{\baselinestretch}{1.0}

    \usepackage{amsmath}

    \title{My First Document}
    \author{Dustin Enyeart}
    \date{5 October 2024}

    \begin{document}
    \maketitle

    \section{First section}


    This is the body text. 


    \end{document}


The package ``geometry`` is used to set the margins, and the ``1.0`` or ``30pt`` can be changed to whatever is desired. 
The command ``\renewcommand{\baselinestretch}{1.0}`` redefines ``\baselinestretch``, which is used as the spacing between lines, and the ``1.0`` can be changed to whatever is desired. 


======
Inputs
======

The command ``\input{}`` can be used to included another file. 
For example, ``\input{otherfile}`` will include the file ``otherfile.tex``.
This directly copies the contents of the file, and it can be used anywhere in the document. 
The file must be in the same directory. 
For example, this can be used to have each section in a separate file.
It could also be useful to put a large table in a different file.
If ``\input`` is used in the preamble for formatting, then the inputted file is called a *style* file and has the extension ``.sty`` is used.


========
Template
========

There is a template as ``template`` in the `git repository <https://github.com/dustin-enyeart/latex-tutorial>`_ for this tutorial. 
The user can copy this file and modify it as needed.