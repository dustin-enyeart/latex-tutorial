# Latex Template

This is the template from [this](https://latex-tutorial.readthedocs.io/en/latest/) Latex tutorial.

To compile the file `main.tex`, run the following shell command. 

``` bash
    latexmk -pdf main.tex
```

On Ubuntu, the program `latexmk` can be install with the following shell command. 

``` bash
    sudo apt install texlive-full
```

The command `latexmk -c` will remove the auxiliary files. 