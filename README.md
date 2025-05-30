# warp-solver-validation

A lightweight validation harness for the RK4-based warp solver.  
Runs baseline Minkowski and Schwarzschild profiles and produces a single LaTeX file (`validation_results.tex`) that downstream repos can consume.

## Dependencies

- Python 3.7+  
- NumPy  
- SymPy  
- The solver module (`solver.py`) and stencil definitions (`solver_update.tex`) from your `warp-solver-equations` repo

## Installation

```bash
git clone https://github.com/<your-org>/warp-solver-validation.git
cd warp-solver-validation
pip install numpy sympy
```

Place or symlink `solver.py` and `solver_update.tex` into this directory.

## Usage

```bash
python run_validation.py
```

This will generate `validation_results.tex` in the project root.

## Output

-   **validation\_results.tex**  
    A standalone LaTeX document containing an error‐norm table with Pass/Fail status for each test case.
    

Downstream pipelines can include or import this `.tex` file directly—no PDF step required here.
