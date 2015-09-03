# How to set directory-wide options in Auctex

Suppose you have these options in a file and want to set them to all files in the same directory:

    %%% Local Variables: 
    %%% mode: latex
    %%% TeX-master: "main"
    %%% End:

You should do:

Create a file `.dir-locals.el` in the current directory, with these contents:

    ((latex-mode
      (TeX-master . "main")))


Emacs manual: http://www.gnu.org/software/emacs/manual/html_node/emacs/Directory-Variables.html

Source: http://tex.stackexchange.com/questions/167327/
