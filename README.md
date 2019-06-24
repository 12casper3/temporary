Usage
=====

Exported logos
==============
For easy use, the different versions of the logo are released in different file formats.
The possible combinations are:
Color - Black
Text - NoText

*.pdf, *.eps, *.png

Small, Medium and Large resolutions.

A vector version (*.tikz, *.pdf, *.eps) of the logo should be used where possible.

Export to EPS
-------------
EPS exports are done by converting the *.dvi from ```latex logo``` using ```dvips -E logo ```.
The exported *.pdf from pdflatex can of course also be converted to *.eps directly, by using a command like ```pdftops -eps logo.pdf```.


Installation & Dependencies
===========================
Compiling the logo requires LaTeX.

ImageMagick is used to convert the pdfs to other formats.

Ubuntu
------

```sudo apt install texlive-latex-extra```
```./compile_all.sh```

Potential problems with ImageMagick exporting GIFs:
https://stackoverflow.com/questions/42928765/convertnot-authorized-aaaa-error-constitute-c-readimage-453

Windows
-------
Install MiKTeX or TeX Live
Install ImageMagick
```.\compile_all.ps1```
