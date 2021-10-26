# Minitutorial sobre como usar LaTeX.

## Que es LaTeX? ##

LaTeX es un *lenguaje* para escribir papers, libros, reportes, etc. que requieran el uso de notación matemática, referencias bibliográficas, inclusión de gráficos y tablas, etc.

## Como se trabaja en LaTeX? ##

Típicamente, se trabaja sobre un archivo principal `main.tex` (puede tener otro nombre, ej. `mi-paper.tex`).
Este archivo es de formato texto, por lo que puede ser creado y editado con  cualquier editor de texto común y silvestre. 
Algunas veces `main.tex` hace referencia a otros archivos. 
Por ejemplo:

* archivos `.tex` que contienen capítulos de libros,
* archivos `.bib` un archivo para incluir referencias bibliográficas,
* archvos `.sty` que especifican *estilos*,
* etc.

También suelen referenciarse archivos gráficos en formato `.pdf`, `.ps`, `.png`, `.jpg`, etc., que constituyen las figuras a incluir en el documento.
Estos archivos de figura se crean con otro software, ej. `Python+matplotlib`, etc.

Luego se utiliza un software para compilar `main.tex` a formato `.pdf` o `.ps` entre otros.
En **Ubuntu** por ejemplo, se recomienda instalar

    $ sudo apt-get update
    $ sudo apt-get install texlive-latex-extra texlive-lang-spanish texlive-publishers
    
Luego, asumiendo que existe un archivo `fig1.pdf`, y un archivo `references.bib` con el contenido

    @book{verhulst1985nonlinear,
       title =     {Nonlinear Differential Equations and Dynamical Systems},
       author =    {Ferdinand Verhulst},
       publisher = {Springer},
       isbn =      {0387506284; 9780387506289},
       year =      {1985},
       series =    {Universitext},
       edition =   {First Edition}
    }

    @book{wiggins2003introduction,
       title =     {Introduction to applied nonlinear dynamical systems and chaos},
       author =    {Wiggins S.},
       publisher = {Springer},
       isbn =      {0387001778},
       year =      {2003},
       series =    {},
       edition =   {2ed.},
       volume =    {}
    }

podemos compilar el siguiente mini ejemplo (contenido de `main.tex`)

    \documentclass[aps,prl,twocolumn,groupedaddress]{revtex4-2}

    \usepackage{graphicx}
    \usepackage{amssymb}
    \usepackage{amsmath}
    \usepackage{color}
    \usepackage{hyperref}
    \usepackage{babel}[spanish] % To write in spanish
    \usepackage[utf8]{inputenc}
    \setcounter{secnumdepth}{3}

    \DeclareMathOperator*{\argmax}{arg\,max}
    \DeclareMathOperator*{\argmin}{arg\,min}
    \newcommand{\avrg}[1]{\left\langle #1 \right\rangle}
    \newcommand{\nelta}{\bar{\delta}}

    \begin{document}

    \title{Ejemplo de artículo LaTex}

    \author{Juan I. Perotti}
    \email[]{juan.perotti@unc.edu.ar}
    \affiliation{Instituto de Física Enrique Gaviola (IFEG-CONICET), Ciudad Universitaria, 5000 Córdoba, Argentina}
    \affiliation{Facultad de Matemática, Astronomía, Física y Computación, Universidad Nacional de Córdoba, Ciudad Universitaria, 5000 Có|rdoba, Argentina}

    \date{\today}

    \begin{abstract}
    Este es el resúmen al inicio del artículo.
    \end{abstract}

    \maketitle

    \section{
    \label{intro}
    Introducción
    }

    En los libros~\cite{verhulst1985nonlinear,wiggins2003introduction} podemos aprender sobre formas normales.

    \section{
    \label{resultados}
    Resultados
    }

    El atractor de Lorenz viene dado por la ecuación
    \begin{eqnarray}
    \label{eq1}
    \dot{x}_1 &=& \sigma(x_2-x_1) \\
    \dot{x}_2 &=& x_1(\rho-x_3)-x_2 \nonumber \\
    \dot{x}_3 &=& x_1x_2-\beta x_3 \nonumber
    \end{eqnarray}

    \begin{figure}
    \includegraphics*[scale=.9]{fig1.pdf}
    \caption{
    \label{fig1}
    Aquí va la descripción de la figura.
    }
    \end{figure}

    En la figura~\ref{fig1}, podemos apreciar el atractor de Lorenz generado a partir de la ODE en la ecuación~\ref{eq1}.
    Esta figura fué extraída del primer libro mencionados en la sección~\ref{intro}.

    \subsection{
    \label{ejemplos}
    Ejemplos
    }

    Así incluimos direcciones web~\url{https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes}.

    \bibliography{references}

    \onecolumngrid
    \appendix

    \section{este es un apéndice}
    \label{appA}

    Los apéndices los incluimos en formato de una columna.

    \end{document}
    
con la secuencia de comandos

    $ pdflatex main.tex
    $ bibtex main.aux
    $ pdflatex main.tex
    $ pdflatex main.tex
    
lo cual generará el archivo `main.pdf`, además de unos cuantos archivos auxiliares que podemos ignorar y/o borrar.

En Windows existen programas como [MiKTeX](https://miktex.org/download).

Alternativamente, existen plataformas online tales como [Overleaf](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes) en donde uno puede crear, incorporar y/o editar archivos `.tex`, `.bib`, `.sty`, etc., así como incluir archivos gráficos.
