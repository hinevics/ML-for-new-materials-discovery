# ML for new materials discovery

% last updated in April 2002 by Antje Endemann
% Based on CVPR 07 and LNCS, with modifications by DAF, AZ and elle, 2008 and AA, 2010, and CC, 2011; TT, 2014; AAS, 2016

\documentclass[runningheads]{llncs}
\usepackage{graphicx}
\usepackage{amsmath,amssymb} % define this before the line numbering.
\usepackage{ruler}
\usepackage{color}
\usepackage[width=122mm,left=12mm,paperwidth=146mm,height=193mm,top=12mm,paperheight=217mm]{geometry}
\begin{document}
% \renewcommand\thelinenumber{\color[rgb]{0.2,0.5,0.8}\normalfont\sffamily\scriptsize\arabic{linenumber}\color[rgb]{0,0,0}}
% \renewcommand\makeLineNumber {\hss\thelinenumber\ \hspace{6mm} \rlap{\hskip\textwidth\ \hspace{6.5mm}\thelinenumber}}
% \linenumbers
\pagestyle{headings}
\mainmatter
\def\MySubNumber{***}  % Insert your submission number here

\title{Band Gap ML part} % Replace with your title

\titlerunning{the best conference ever submission ID \MySubNumber}

\authorrunning{the best conference ever submission ID \MySubNumber}

\author{Anonymous}
\institute{Paper ID \MySubNumber}


\maketitle

\begin{abstract}


\keywords{}
\end{abstract}

\section{Introduction}
\section{Methods}
% work in progress

\subsection{Machine Learning}

In this section we will describe our take on implementing a Machine learning algorithm for Band Gap prediction.

\subsubsection{Previous work}
 There were several notable attempts at utilizing Machine Learning to predict physical properties of various materials.  Huang et al. reported prediction of band gap properties for ternary metal nitride compounds using ML approach based on calculated hybrid functionals of HSE and DFT PBE and  [30]. In their study electronegativity, valence and covalent radius were selected as features for the training of the ML algorithm and prediction. In another study, high accuracy of the prediction was achieved with the ML algorithm trained on a dataset with 3 features of each elements in the compound: ionic radius, electronegativity and number of row associated with position of the element in the periodic table [31].


\subsubsection{Data source}
Firstly, we screened open-access Materials Project and High Performance Computing Center Materials databases to identify stable ternary metal nitride compounds with optical properties that may be suitable for solar energy harvesting. The compounds with predicted band gap values of over 0.5 eV were considered. This is because the DFT method used in the databases for the calculation of the compounds was based on generalized gradient approximation (GGA+U). The latter is known to underestimate the band gap values of the materials relative to the experimentally measured ones [29].


\subsubsection{Dataset preparation}
The algorithm was trained using a dataset of experimentally reported band gap values of about 360 ternary metal nitrides, oxides, sulfides and phosphides compounds.

A lack of data is a common problem in machine learning. This usually imposes limitations on various parts of machine learning pipeline that we will discuss below.

\subsubsection{Feature extraction and processing}
Having low amounts of data also imposes certain limits on the amount of features that can be used without causing the curse of dimensionality [-1]. This suggests us to pick a number of features $d<<N$, where $N=360$ is the total number of data samples available in the training split.

The list of characteristic element-specific features used for the machine learning prediction includes detailed electronic configuration, maximum valence, atomic mas, electronegativity, atomic and covalent radius, ionization potential, electron affinity, period, group and block of the constituent elements.


\subsubsection{Model}
 Limited dataset size also affects the choice of the model and limits our choices depending on the model's complexity, since a very sophisticated model, e.g. deep neural network with many parameters, will tend to overfit when the number of training samples is too low.
 
We used support vector regression (SVR) with the nonlinear radial basis function  (RBF) kernel as a machine learning model in our experiments. The model of choice was implemented with the use of the Scikit-learn framework and Python 3.x.


\subsubsection{Results}
The ML prediction of the band gap values was used in combination with the data available in the open access databases to reduce the number of potential candidates for the subsequent theoretical simulations with hybrid functionals of HSE. In addition, the remaining compounds were sorted based on the value of effective electron and hole masses available in the following database [26][27][28].



-1) Trunk, G. V. (July 1979). "A Problem of Dimensionality: A Simple Example". IEEE Transactions on Pattern Analysis and Machine Intelligence. PAMI-1 (3): 306–307.
 


\clearpage

\bibliographystyle{splncs}
\bibliography{egbib}
\end{document}

