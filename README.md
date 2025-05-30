# warp-solver-validation

A small validation suite for the RK4-based warp solver.  
It runs two baseline tests—Minkowski and Schwarzschild profiles—and generates a standalone LaTeX report of the $L_2$ and $L_\infty$ error norms, marking each test as Pass/Fail.

## Repository Structure
```
.  
├── run\_validation.py # Script that performs RK4 validation tests  
├── validation\_results.tex # LaTeX template (output) for the results  
├── solver.py # Your RK4 solver module (must provide integrate\_step)  
└── solver\_update.tex # Stencil definitions for the RK4 RHS
```
## Prerequisites

- Python 3.7 or higher  
- NumPy  
- SymPy  
- A working LaTeX installation (e.g. TeX Live, MiKTeX) for compiling `validation_results.tex`

## Installation

```bash
git clone https://github.com/<your-org>/warp-solver-validation.git
cd warp-solver-validation
pip install numpy sympy
```

Ensure that `solver.py` and `solver_update.tex` from your `warp-solver-equations` repo are placed in this directory (or adjust the import/path accordingly).

## Usage

1.  **Run the validation script**
    
```bash
python run_validation.py
```
    
    This will produce `validation_results.tex` in the project root.
    
2.  **Compile the LaTeX report**
    
```bash
pdflatex validation_results.tex
```
    
    You should see a PDF summarizing the $L\_2$ and $L\_\\infty$ errors and Pass/Fail status for each test.
    

## Example Output

```latex
\documentclass{article}
\usepackage{booktabs}
\begin{document}

\section*{Baseline Validation Results}

\begin{tabular}{lrrl}
\toprule
Test           & $L_2$ Error & $L_\infty$ Error & Status \\
\midrule
Minkowski      & 1.23e-05    & 4.56e-05         & Pass   \\
Schwarzschild  & 7.89e-04    & 1.23e-03         & Pass   \\
\bottomrule
\end{tabular}

\end{document}
```

## Customization

-   Tolerance thresholds (`tol`) can be adjusted at the top of `run_validation.py`.
    
-   Additional analytic profiles can be added by defining new functions and appending to the test table.
