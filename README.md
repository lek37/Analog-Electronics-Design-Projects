# Welcome to my EE 2EI4 Project Repo!

## Disclaimer:
- Welcome to my 2EI4 Project page! Under this repositories you will find my project deliverables here. You are welcome to use this as a reference, but for your learning, please do not copy and paste everything into your report.
- For project 2 I didn't have time to do it properly since I was having 3 midterms squeezed in between with the due date. Consult other sources if possible. 
- **Project 3: Voltage Amplifiers** deliverable can be found in this video recording as my preferred submission: https://www.youtube.com/watch?v=q4y-tnzBNro. You can also write a report as an alternative way of submission as well.

## For LaTeX users (Overleaf)
If you use LaTeX to write your report, and you wish to use my formatting for your report, you can do the following: 
1. Copy and paste the following and put appropriate information (semester, date, your name, MacID, student number, project name,...). Do NOT click `Compile` yet, because you will have to set up the appropriate compiler for Times New Roman font. 
```
\documentclass[12pt]{article}
	
\usepackage[margin=1in]{geometry}		
\usepackage{amsmath}				
\usepackage{amssymb} 
\usepackage{fancyhdr}				
\usepackage{graphicx}	
\renewcommand{\contentsname}{Table of Contents}
\usepackage{enumitem}
\usepackage{cancel}					
\usepackage{hyperref}
\usepackage{float}
\usepackage{multirow}
\usepackage{indentfirst}
\usepackage[american, siunitx]{circuitikz}
\usepackage{circuitikz}
\usepackage{lipsum}
\usepackage{setspace}
\usepackage{tikz, tcolorbox} 
\usepackage[dvipsnames]{xcolor}
\usepackage{listings}
\usepackage{xcolor}
\usepackage{fontspec}
\setmainfont{Times New Roman}



\pagestyle{fancy}
\fancyhead[LO,L]{your name} % replace with your name!
\fancyhead[CO,C]{}
\fancyhead[RO,R]{\textbf{ELECENG 2EI4 Project 5 - Digital-to-Analog Converter}} % put the project title here 
\fancyfoot[LO,L]{}
\fancyfoot[CO,C]{\textbf{\thepage}}
\fancyfoot[RO,R]{}


%%%%%%%%%%%%%%%%%%%%%%

\spacing{1.25} % you can adjust the line spacing here if you wish to
\begin{document}
    
    \begin{titlepage}
    \begin{center}
    \vspace*{\fill}

    {\LARGE \textbf{ELECENG 2EI4 - Electronic Devices \& Circuits I}\par}
    \vspace{2.5cm}

    {\LARGE\bfseries Project 5 - Digital-to-Analog Converter\par} % appropriate project title
    \vspace{2.5cm}
    
    {\Large \textbf{your name - student number}\par}
    \vspace{2.5cm}
    
    {\large \textbf{Instructor:} Dr. Yaser M. Haddara\par} % don't change this unless Dr. Haddara is not teaching this course anymore
    \vspace{0.5cm}
    {\large \textbf{Term:} Winter 2026 \par} % winter 2027, 28,...?
    \vspace{0.5cm}
    
    {\large \textbf{Submission Deadline:} Sunday, April 12, 2026\par} % put the due date here. 
    \end{center}

    \vspace*{\fill}

    \textbf{Statement of Originality:} As a future member of the engineering profession, the student is responsible for performing the required work in an honest manner, without plagiarism and cheating. Submitting this work with my name and student number is a statement and understanding that this work is my own and adheres to the Academic Integrity Policy of McMaster University and the Code of Conduct of the Professional Engineers of Ontario. Submitted by \textbf{your name, MacID, student number}

\end{titlepage}

    \newpage
    \tableofcontents

    \listoffigures

    \listoftables

    \newpage

    % YOUR OWN WORK STARTS HERE!!!

\end{document}
```

2. On Overleaf, click `File`, then `Setting`, then `Compiler`, then `XeLaTeX` from the second dropdown box. This will allow you to render the code with Times New Roman font.
3. Click `Recompile`, and then you are all set. 

## Update Log:
- May 26, 2026: upload `.asc` file for Project 5. 
- Aug 4, 2026: fix some minor bugs of the LaTeX code template

