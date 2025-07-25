# Ligature syllabique
Si vous devez relier deux syllabes pour que le chant se déroule bien, suivez les instructions ci-dessous.

## Code
Incluez le code ci-dessous dans le fichier latex de l'hymne dans ses sections Packages et Command respectives :

```tex
%------------------
% Packages
%------------------
\usepackage{tikz}
\usepackage{calc}

%------------------
% Ligature Command
%------------------
\newcommand{\ligature}[2]{%
  \begingroup
  \leavevmode
  \setbox0=\hbox{#1}%
  \setbox1=\hbox{#2}%
  \tikz[baseline=(base.base)]{
    \node[inner sep=0pt] (base) {\strut #1~#2};
    \coordinate (start) at ([xshift=\wd0-0.1em,yshift=0.5ex]base.south west);
    \coordinate (end) at ([xshift=\wd0+0.5em,yshift=0.5ex]base.south west);
    \draw[line width=0.25pt]
      (start) .. controls +(0.25em,-0.15em) and +(-0.25em,-0.15em) .. (end);
  }%
  \endgroup
}
```

## Comment l'utiliser ?

```tex
\ligature{mot1}{mot2}
```