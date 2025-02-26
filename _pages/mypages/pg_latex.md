---
layout: archive
permalink: /misc/latex/
title: How-to tex files
description: Last update on June 12, 2020
---


## Check spelling in a tex file (command line)

 ```bash
aspell -c file.tex -d en
```

## LaTeX sizes and 

| Command         | 10pt  | 11pt  | 12 pt |
|:----------------|:------|:------|:------|
| `\tiny`         | 5     | 6     | 6     |
| `\scriptsize`   | 7     | 8     | 8     |
| `\footnotesize` | 8     | 9     | 10    |
| `\small`        | 9     | 10    | 10.95 |
| `\normalsize`   | 10    | 10.95 | 12    |
| `\large`        | 12    | 12    | 14.4  |
| `\Large`        | 14.4  | 14.4  | 17.28 |
| `\LARGE`        | 17.28 | 17.28 | 20.74 |
| `\huge`         | 20.74 | 20.74 | 24.88 |
| `\Huge`         | 24.88 | 24.88 | 24.88 |

## Colors (Tableau 10)

```latex
\usepackage{xcolor}

\definecolor{Tab10fBlue}{RGB}{31,119,180}
\definecolor{Tab10fOrange}{RGB}{255,127,14}
\definecolor{Tab10fGreen}{RGB}{44,160,44}
\definecolor{Tab10fRed}{RGB}{214,39,40}
\definecolor{Tab10fPurple}{RGB}{148,103,189}
\definecolor{Tab10fBrown}{RGB}{140,86,75}
\definecolor{Tab10fPink}{RGB}{227,119,194}
\definecolor{Tab10fGray}{RGB}{127,127,127}
\definecolor{Tab10fYellow}{RGB}{188,189,34}
\definecolor{Tab10fCyan}{RGB}{23,190,207}

\definecolor{Tab10mBlue}{RGB}{114,158,206}
\definecolor{Tab10mOrange}{RGB}{255,158,74}
\definecolor{Tab10mGreen}{RGB}{103,191,92}
\definecolor{Tab10mRed}{RGB}{237,102,93}
\definecolor{Tab10mPurple}{RGB}{173,139,201}
\definecolor{Tab10mBrown}{RGB}{168,120,110}
\definecolor{Tab10mPink}{RGB}{237,151,202}
\definecolor{Tab10mGray}{RGB}{162,162,162}
\definecolor{Tab10mYellow}{RGB}{205,204,93}
\definecolor{Tab10mCyan}{RGB}{109,204,218}

\definecolor{Tab10lBlue}{RGB}{174, 199, 232}
\definecolor{Tab10lOrange}{RGB}{255, 187, 120}
\definecolor{Tab10lGreen}{RGB}{152, 223, 138}
\definecolor{Tab10lRed}{RGB}{255, 152, 150}
\definecolor{Tab10lPurple}{RGB}{197, 176, 213}
\definecolor{Tab10lBrown}{RGB}{196, 156, 148}
\definecolor{Tab10lPink}{RGB}{247, 182, 210}
\definecolor{Tab10lGray}{RGB}{199, 199, 199}
\definecolor{Tab10lYellow}{RGB}{219, 219, 141}
\definecolor{Tab10lCyan}{RGB}{158, 218, 229}
```

## BibTex entry

Assuming one uses the bibliography style:

```latex
\bibliographystyle{apsrev4-1}
```

### For standard bibliography display

```latex
@article{name48_1,
author = {A. Name and B. Name and C. {Al Name}},
title = {Title of the paper},
journal = {Journal of blabla},
volume = {8},
pages = {9},
year = {2048},
keywords = {theory,blabla},
url = {[insert doi link here]}
}
```


### For arXiv entries

```latex
@misc{arxivName20,
author = {A. Name and B. Name},
title = {Title of the paper},
year = {2020},
HowPublished = {\url{[insert arXiv url here]}}
}
```


### For cases where the volume number is not in bold (hack)

```latex
@article{name07_1,
author = {A. Name and B. Name and C. {Al Name}},
title = {Title of the paper},
journal = {Journal of blabla, \textbf{8}, 9 (2048)},
keywords = {theory,blabla},
url = {[insert doi link here]}
}
```

This works fine for notes using the bibliography style:
```latex
\bibliographystyle{unsrt}
```


### For books

```latex
@book{gelfand61_b1,
author = {I. M. Gel'fand and G. E. Shilov and N. Ya. Vilenkin and M. I. Graev},
title = {Generalized {F}unctions. {V}ol. 1: {P}roperties and {O}perations},
publisher = {Academic Press, New York},
edition = {1st ed.},
year = {1964}
}
```

Note that first letters in the title must be surrounded by braces to stay in capital after processing. The url field can be added if a doi link is available.



