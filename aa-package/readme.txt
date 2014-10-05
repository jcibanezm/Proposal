%                                                             readme.txt
% AA vers. 8.1, LaTeX class for Astronomy & Astrophysics
% read-me file
%                                                 (c) EDP Sciences, 2012
%                                            tex-support@edpsciences.org
%-----------------------------------------------------------------------
%
%-----------------------------------------------------------------------
% What's New in AA v8.1 (November 2012)
%-----------------------------------------------------------------------

Main change is this version 

A&A now accepts TeX files designed for LaTeX  as well as PDFLaTeX.
Depending on your preferred LaTeX engine (LaTeX or pdfLaTeX), figures 
should be sent as encapsulated PostScript files or in any other format 
as PDF, JPG, TIF, BMP, and GIF (compatible with pdfLaTeX).

The following files are part of the macro package AA 

  readme.txt      This file
  aa.cls          The document class file
  aadoc.pdf       User's Guide 
  aa.dem          Example of an article (LaTeX source)


  bibtex/       Directory for BIBTeX style
   aa.bst       Bibliography style file 
   natbib.sty   This package reimplements the LaTeX \cite command 
   natnotes.pdf Brief reference sheet for Natbib        

Remember to transfer dvi and pdf files as binaries!

%-----------------------------------------------------------------------
% Tips 
%-----------------------------------------------------------------------
% How to add in-text citation clickers that link to the corresponding
% ADS abstract pages.
% contributed by Robert J. Rutten of Utrecht University.
%-----------------------------------------------------------------------

This is a latex recipe to turn the year in an in-text citation into a
clicker in the pdf or html output file that links into ADS, opening
the corresponding abstract page in your browser.  In this manner, an
on-screen reader of your paper may open the cited abstract or download
the cited paper in parallel to reading your paper, without jumping to
the reference list of the latter.  

Clicking on the author part of the citation will cause a jump to the
reference as usual.

Insert the following commands into the preamble of your latex file:
----------------------------------------
\usepackage{natbib,twoopt}
 \usepackage[breaklinks=true]{hyperref} %% to avoid \citeads line fills
 \bibpunct{(}{)}{;}{a}{}{,}    %% natbib format like A&A and ApJ
 \newcommandtwoopt{\citeads}[3][][]{\href{http://adsabs.harvard.edu/abs/#3}%
                                        {\citealp[#1][#2]{#3}}}
 \newcommandtwoopt{\citepads}[3][][]{\href{http://adsabs.harvard.edu/abs/#3}%
                                        {\citep[#1][#2]{#3}}}
 \newcommandtwoopt{\citetads}[3][][]{\href{http://adsabs.harvard.edu/abs/#3}%
                                        {\citet[#1][#2]{#3}}}
 \newcommandtwoopt{\citeyearads}[3][][]%
   {\href{http://adsabs.harvard.edu/abs/#3}{\citeyear[#1][#2]{#3}}}
-------------------------------------------

Usage: use ADS biblabels and enter one per \citeads command, as in:

---------------------------
The existence of two emission features in the solar spectrum near
12~$\mu$m was announced by
\citetads{1981ApJ...247L..97M}. %% Murcray+others, MgI features
We explained them already during the previous millennium
\citepads[see][]{1992A&A...253..567C}, %% Carlsson+Rutten+Shchukina MgI
using the standard model of the solar atmosphere formulated in the
monumental papers by \citeauthor{1973ApJ...184..605V}
(\citeyearads{1973ApJ...184..605V}, % VALI
\citeyearads{1976ApJS...30....1V}, % VALII
\citeyearads{1981ApJS...45..635V}). % VALIII
---------------------------

This trick was contributed by Robert J. Rutten of Utrecht University.
The above example of its usage is taken from his latex manual and template
for students at http://www.staff.science.uu.nl/~rutte101/Report_recipe.html 
%-----------------------------------------------------------------------
