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

  $ sudo apt install texlive-latex-extra

Alternativamente, existen plataformas online en donde uno puede crear, incorporar y/o editar archivos `.tex`, `.bib`, `.sty`, etc., 
así como incluir archivos gráficos.
