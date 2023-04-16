---
layout: post
title:  "Compiling all the Putnam Exams into One PDF"
date:   2021-08-01
permalink: /:categories/:year/W:week/:short_day/:title:output_ext
categories: Task
---
## Downloading Every Putnam Exam
I wanted to print out all of the [Putnam Exam](https://en.wikipedia.org/wiki/William_Lowell_Putnam_Mathematical_Competition)s and bind it into a folder, but it would take a while to download every one individually.
So, I figured out how to use [cURL](https://en.wikipedia.org/wiki/CURL) to download all the pdfs from [Dr. Kedlaya's Putnam Archive](https://kskedlaya.org/putnam-archive/).

Let us look at the URL for one year of problems:
```
https://kskedlaya.org/putnam-archive/2022.pdf
```
The solution page for that year is at:
```
https://kskedlaya.org/putnam-archive/2022s.pdf
```
Luckily, Dr. Kedlaya was regular with his naming scheme, so the years can be enumerated.
I downloaded every year from 1985 to 2015's problems, solutions, in both pdf and tex format using [globbing](https://everything.curl.dev/cmdline/globbing).
```bash
curl -f "https://kskedlaya.org/putnam-archive/[1985-2022]{,s}.{pdf,tex}" -O --remote-name
```

## Making the pdf document
[](https://tex.stackexchange.com/questions/15989/toc-entries-and-labels-for-included-pdf-pages)
```tex
\documentclass{article}
\usepackage{pdfpages, graphicx, fancyvrb, hyperref}
\usepackage[lmargin=10mm, rmargin=10mm]{geometry}
\title{Putnam Exam Questions}
\author{MAA}
\date{1985-2021}

\hypersetup{}
\begin{document}
\maketitle
\thispagestyle{empty}
\begin{center}
\begin{BVerbatim}
#!/bin/bash
# Pull exams from Kiran Kedlaya's Putnam archive
curl -f "https://kskedlaya.org/putnam-archive/[1985-2021].pdf" -O --remote-name
\end{BVerbatim}
\end{center}

\newpage
% See 
% https://tex.stackexchange.com/questions/15989/toc-entries-and-labels-for-included-pdf-pages
% for how includepdf handles table of contents adding
\includepdf[pages=-, addtotoc={1, section, 1, 1985, t}]{../Putnam_Source_Files/1985.pdf}
% 1986- 2021 excluded for brevity
\includepdf[pages=-, addtotoc={1, section, 1, 2022, t}]{../Putnam_Source_Files/2022.pdf}
\end{document}
```

[Github Link](https://github.com/Neil-Penning/Putnam)
