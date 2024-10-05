.. _markup: 

******
Markup
******

====
Text
====

Paragraphs are separated by a blank line.
Additional white space is ignored. For example, the following two code blocks will produce the same output. 


.. code-block:: Latex

    This is a sentence.

    This is another sentence. 


.. code-block:: Latex

    This         is a          sentence.



    This is another sentence. 


Comments are denoted by a percent sign ``%``.


.. code-block:: Latex

    This is in the output. % This is a comment


Italics and bold are denoted with ``\emph`` and ``textbf``, respectively. 


.. code-block:: Latex

    This is \emph{emphasized}.

    This is \textbf{bold}.


The package ``amsthm`` is used for theorem environments that are automatically numbered. 


.. code-block:: Latex

    \documentclass[12pt]{article}

    \usepackage{amsthm}
    \newtheorem{theorem}{Theorem}

    \begin{document}

    \begin{theorem}
    This is a theorem. 
    \end{theorem}

    \begin{proof}
    This is a proof. 
    \end{proof}

    \end{document}


The following is a more simplistic way to have a theorem and proof, but the theorem will not be numbered. 


.. code-block:: Latex

    \documentclass[12pt]{article}

    \begin{document}

    \noindent \textbf{Theorem} This is a theorem. 

    \noindent \emph{Proof.}
    This is a proof. 
    \qed

    \end{document}


Accents be be added by escaping a character before the letter, such as in the following example. 


.. code-block:: latex

    Poincar\'e, G\"odel and L'H\^optial were mathematicians. 



====
Math
====

Mathematical environments are used to markup mathematical expressions. 
There are inline and out-of-line mathematical environments.
Inline mathematical environments are denoted by surround it with dollar signs ``$``, and out-of-line mathematical environments are denoted by surrounding with ``\[`` and ``\]``. 


.. code-block:: latex

    The functions $f$ and $g$ are continuous. 


.. code-block:: latex

    The relation 
    \[
        2 + 2 = 4
    \]
    holds. 


Subscripts and superscripts are indicated by an underscore ``_`` and a caret ``^``, respectively.
By default, only the next character is used as the subscript or superscript, but multiple characters can be grouped by using curly braces ``{}``.


.. code-block:: latex

    The numbers $a_1$ and $a_2$ are such that the relation
    \[
        a_1^{10} + a_2^{10}  = 100
    \]
    holds. 


In an out-of-line mathematical environment, the environment ``split`` can be used to align the lines. This is part of the package ``amsmath``. The ampersand ``&`` is used to denoted where the alignment occurs. In the following code block, the equal signs ``=`` are aligned. The double backslash ``\\`` is used to denote a new line.


.. code-block:: Latex

    The relations
    \[
    \begin{split}
        2 + 2 + 2 + 2 
        &= 2 + 2 + 4 \\
        &= 2 + 6 \\
        &= 8 \\
    \end{split}
    \]
    hold. 


Mathematical symbols and Greek letters can be inserted using a backslash ``\`` and the name of the symbol, such as ``\geq`` for the greater-than-or-equal-to symbol or ``\alpha`` for the Greek letter alpha.


.. code-block:: Latex

    Examples of trigonometric functions are $\sin(x)$, $\cos(x)$, and $\tan(x)$.


.. code-block:: Latex

    The Greek letter $\pi$ often denotes Archimedes's constant. 


.. code-block:: Latex

    The relations
    \[
    \begin{split}
        2^3
        &= 2 \cdot 2 \cdot 2 \\
        &= 2 \cdot 4 \\
        &= 8 \\
        &\geq 4 \\
    \end{split}
    \]
    hold. 


An operator takes one or multiple arguments, such as the square root operator ``\sqrt{2}`` or the fraction operator ``\frac{1}{2}``.


.. code-block:: Latex

    The relation
    \[
        \sqrt{4} \geq 2
    \]
    holds. 


Subscripts and superscript will automatically format correctly with sums :math:`\sum` and so on. 


.. code-block:: Latex

    The series
    \[
        \sum_{n=1}^{\infinity} \frac{1}{2^n} 
    \] 
    converges. 


.. code-block:: Latex

    The limit 
    \[
        \lim_{n \to \infinity} \frac{1}{n}
    \]
    is $0$. 


Text can be inserted into a mathematical environment using ``\mathrm``.


.. code-block:: Latex

    The integral 
    \[
        \int_{0}^{1} x^2 \mathrm{d}x
    \]
    is $\frac{1}{3}$. 

.. code-block:: latex

    This
    \[
        \begin{pmatrix}
        1 & 2 \\
        3 & 4 \\
        \end{pmatrix}
    \]
    is a matrix. 


The size of brackets and parentheses can automatically formatted by using commands ``\left`` and ``\right`` with their symbols. The commands ``\left.`` or ``\right.`` are placeholders for matching and will not display anything at their location. In the second following code block, the the backlash ``\`` in ``\{`` is used to escape the bracket ``{`` because it is a reserved character. 


.. code-block:: Latex

    The series
    \[
        \sum_{n=1}^{\infinity} \left( \frac{1}{2} \right)^n
    \] 
    is geometric. 


.. code-block:: Latex

    This 
    \[
        \left\{ 
            \begin{matrix}
            0 & t < 0 \\
            t & t \geq 0 \\
            \end{matrix}
        \right. 
    \]
    is a piecewise function. 


A list of some common latex symbols is `here <https://www.cmor-faculty.rice.edu/~heinken/latex/symbols.pdf>`_. 


===============
Custom Commands
===============

Custom commands can be declared in the preamble with ``\newcommand`` or ``DeclareMathOperator``. If the a command is already defined, then ``\renewcommand`` is used instead. 


.. code-block:: Latex

    \DeclareMathOperator{\grad}{\nabla}
    \newcommand{\union}{\cup}
    \renewcommand{\phi}{\varphi} 
    \newcommand{\set}[1]{\left\{ #1 \right\}}


In the above code block, the ``[1]`` means that the commands takes one argument. 
