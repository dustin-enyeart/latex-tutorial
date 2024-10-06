*******
Figures
*******

.. Mention again using -c

========
Graphics
========

The package ``graphicx`` is used to include images. 
The following code is includes the image whose filename is ``fig1`` with an image extension such as ``.png`` or ``.jpeg``. 
A caption is optional. 

.. code-block:: latex

    \usepackage{graphicx}

    ...

    \begin{figure}
        \centering
        \includegraphics[width=0.5\textwidth]{fig1}
        \caption{An example of including an image.}
    \end{figure}


For file organization, images can be stored in a subdirectory with the command ``\graphicspath``. 
Placing the following code in the header will configure it so that images can be stored in the subdirectory ``figs`` instead of the main directory. 


.. code-block:: latex
    
    \graphicspath{{figs}}



======
Tables
======

Tables can be made using the ``table`` and ``tabular`` environments.
The command ``\hline`` draws a horizontal line. 
In a row, each entry is separated by an ampersand ``&``.
And, each row is separated by a newline character ``\\``.
Each row must have the same number of columns, and this must match repetitions of ``c`` in the ``tabular`` environment.
Each vertical line ``|`` in ``c|c|c`` draws vertical lines between columns.
An entry can be blank. 


.. code-block:: latex

    \usepackage{tikz}

    ...

    \begin{table}
        \centering
        \caption{Example Table}
        \begin{tabular}{c|c|c}
            Column 1 & Column 2 & Column 3 \\ \hline
            A & B & C \\ \hline
            D & E & F \\ \hline
            G & H & I \\ 
        \end{tabular}
    \end{table}


===========
Positioning
===========

The package ``float`` help with positioning figures and table. 
For example, the ``[H]`` in the following example puts the figure directly where it appears in the text. 


.. code-block:: latex

    \usepackage{tikz-cd}

    ...

    \begin{figure}[H]
        \centering
        \includegraphics[width=0.5\textwidth]{fig1}
        \caption{An example of including an image.}
    \end{figure}


======
Shapes
======

The package ``tikz`` is used to draw shapes.
The following is an example. 
Such an example could placed in a figure environment.  


.. code-block:: latex

    \begin{center}
    \begin{tikzpicture}
        \draw (0,0) node[below]{$A$}
        -- (3,0) node[below]{$B$}
        -- (1.5,4) node[above]{$C$}
        -- cycle;
        \draw[dashed] (1.5,0) node[below]{$D$} -- (1.5, 4);
    \end{tikzpicture}
    \end{center}


====================
Commutative Diagrams
====================

The package ``tikz-cd`` is used to draw commutative diagrams.
The following code is an example of a commutative diagram. 
Such an example could placed in a figure environment.  


.. code-block:: latex

    \[
    \begin{tikzcd}
        G \arrow{dr} \arrow{rr}{f} & & G' \\
        & G/H \arrow{ur} & \\
    \end{tikzcd}
    \]


