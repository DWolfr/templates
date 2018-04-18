# Acon templates

This class provides a template for lecture notes and studennotes, exercises, labs and student thesis.

A simple example for exercises and labs is given below:
```
\documentclass[
    paper=A4,
    twoside=true,
    openright,
    parskip=full,
    chapterprefix=true,
    11pt,
    headings=normal,
    bibliography=totoc,
    listof=totoc,
    titlepage=on,
    captions=tablebelow,
    draft=false,
]{scrreprt}

\usepackage[utf8]{inputenc}
\usepackage[ngerman]{babel}

\usepackage[
    figuresep=colon,
    sansserif=false,
    hangfigurecaption=false,
    hangsection=true,
    hangsubsection=true,
    hangsubsubsection=true,
    colorize=full,
    colortheme=bluemagenta,
    bibsys=biber,
    refsection=chapter,
    bibfile={bachelorpraktikumreferenzen},
    bibstyle=numeric,
    deutsch,
    showsolution=false,
    showfragen=false
]{acon_reports}

\usepackage{acon_math_formatting}
\usepackage{acon_math_abbreviations}
\newcommand{\mycaptionof}[2]{\captionof{#1}{#2\vspace{2ex}}}

\usepackage{hyperref}
\hypersetup{
    pdftitle={},
    pdfsubject={},
    pdfauthor={},
    pdfkeywords={},
    colorlinks=true,
    linkcolor=black,
    citecolor=black,
    urlcolor=black,
    plainpages=false,
    plainpages=false,
}

\begin{document}
\setcounter{page}{1}
\pagestyle{maincontentstyle_ueb}

\def\uebnum{99}
\def\thechapter{\uebnum}
\newcommand{\semester}{SS XX}

\chapter{Your Chapter name}
\section*{The related course name (\semester)}
\subsubsection*{Prof. Dr.--Ing. habil. Thomas Meurer, Lehrstuhl für
  Regelungstechnik}

\printbibliography[heading=subbibliography]

\end{document}
```
Annotations for the usage of the template:
* Bibliography:
	* Be sure to enter your ```.bib```-File as an option to the ```acon_reports``` package
	* In this example Biber is the bibliography-backend (option ```bibsys``` of the ```acon_reports``` package)
* Integrated environments:
	* theorem
	* example
	* exercise
	* lemma
	* remark
	* solution (normally hidden use ```showsolution=true``` as an option for the ```acon_reports``` package)
	* fragen (normally hidden use ```showfragen=true``` as an option for the ```acon_reports``` package)
* Implementation of figures and tables in the previously mentioned environments! **Do not use a figure or table environment there!** The related figures/tables are forced to stay in the related environment.
	* figures:
	 	```
		\begin{center}
		  \includegraphics[]{pictiure.pdf}
		  \mycaptionof{figure}{Caption of table.}
		  \label{label_for_figure}
		\end{center}
		```
	* tables:
	 	```
		\begin{center}
			\begin{tabular}{c|c}
				a & b
			\end{tabular}
			\mycaptionof{table}{Caption of the table.}
			\label{label_for_table}
		\end{center}
		```
