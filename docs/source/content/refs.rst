.. _refs:

**********
References
**********

===================
Internal References
===================


The command ``\label{}`` can be used to specify a numbered object, and the command ``\ref{}`` can be used to reference it. The label ``label{}`` can be put after anything that is automatically numbered and a descriptive string is its input. This descriptive string is then the input of ``ref{}``, which returns the number of the object.  


.. code-block:: Latex

    \documentclass[12pt]{article}

    \usepackage{amsthm}
    \newtheorem{theorem}{Theorem}

    \begin{document}

    \section{First section}\label{sec:first}

    Some stuff. 

    \begin{theorem}
    A theorem.
    \end{theorem}
    \label{thm:a-theorem}


    \section{Second section}

    In Section \ref{sec:first}, some stuff was done. 
    Theorem \ref{thm:a-theorem} was especially interesting. 


    \end{document}


The package ``hyperref`` will make add clickable links to such internal references. 


===================
External References
===================


For, external references, first they need to be defined in a separate Bibtex file. Such files are denoted by the extension ``.bib``. In a Bibtex, an entry is denoted by ``@`` followed by its type and then its formation. Anything outside of this environment is a comment. 

.. code-block:: Bibtex

    Book
    @article{feynman2014qed,
        title={QED: The strange theory of light and matter},
        author={Feynman, Richard P},
        year={2014},
        publisher={Princeton University Press}
        }
    Article
    @article{vaswani2017attention,
        title={Attention is all you need},
        author={Vaswani, A},
        journal={Advances in Neural Information Processing Systems},
        year={2017}
        }
    Miscellaneous
    @misc{enyeart2024latex,
        title={Latex Tutorial}, 
        year={2024},
        url={https://github.com/dustin-enyeart/latex-tutorial}
        }

`Google Scholar <https://scholar.google.com/>`_ will provide the bibtex format for most references. 

Then, the package ``biblatex`` is used to include the bibliography. 
If above code block is saved as ``refs.bib``, then it can be included with ``\addbibresource{refs.bib}``. Citations are done with ``\cite{}``, and the bibliography is printed with ``\printbibliography``. 


.. code-block:: Latex

    \documentclass[12pt]{article}

    \usepackage[backend=biber]{biblatex}
    \addbibresource{refs.bib}

    \begin{document}

    Quantum electrodynamics is cool \cite{feynman2014qed}. 

    \printbibliography

    \end{document}
