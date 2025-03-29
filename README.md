# Nurse Scheduling Optimization - GitHub Report

## Project Overview
This project addresses a real-world nurse scheduling problem using Mixed Integer Programming (MIP). The goal is to assign nurses to a weekly schedule across hospital departments in a way that minimizes labor costs while satisfying complex operational, skill, and policy-based constraints. The model was built and solved using Python and IBM CPLEX.

## Dataset Description
The input data includes the following:
- **Shifts**: Day, department, start/end time, and required staffing levels.
- **Nurses**: Names, seniority, qualification level, pay rate.
- **Skills**: Department-specific required skills and nurse skillsets.
- **Constraints**: Nurse vacation days, skill requirements, preferred associations, and incompatibilities.

## Model Formulation
### Objective:
Minimize the total salary cost by optimizing shift assignments, considering:
- Regular and night shift pay (1.5x multiplier for night hours).

### Decision Variables:
- Binary variable \( x_{n,s} \): whether nurse \( n \) is assigned to shift \( s \).
- Continuous variable \( w_n \): total work hours for nurse \( n \).

## Constraints Implemented
- **A:** No more than two consecutive shifts per nurse.
- **B:** Average qualification per shift must be \( \leq 3 \).
- **C:** Average seniority per shift must be \( \geq 4 \).
- **D:** Minimum skill requirements must be satisfied for each department.
- **E:** Every nurse must work at least 30 hours per week.
- **F:** Night shifts (8PM–8AM) are paid at 1.5× the regular rate.
- **Additional:** No overlapping shifts, vacation restrictions, incompatibility rules, and preferred nurse associations.

## Results Summary
### Baseline vs Constrained Model:
- **Without constraints A–F:** Total cost ≈ \$28,824; uneven worktime distribution.
- **With constraints A–F:** Total cost ≈ \$31,981; all nurses worked ≥30 hours.

### Workload Balance:
Plots show how constraints led to more equitable shift distributions and enforced policy compliance.

## Sensitivity Analysis
Three stress tests were conducted:
1. **Increased Minimum Requirements:** +1 to all `Min_Required` per shift → ❌ Infeasible.
2. **Increased Skill Requirements:** +1 to all department skill needs → ❌ Infeasible.
3. **Reduced Staff Availability:** Removed 2 nurses → ❌ Infeasible.

These results indicate the model is highly sensitive and operates near capacity, requiring careful constraint balancing.

## Tools Used
- Python (Pandas, Matplotlib, Docplex)
- IBM CPLEX Optimization Engine
- Jupyter Notebook

## Author
Md Tahidul Islam  
MATH 4320/8326 – Computational Operations Research  
University of Nebraska at Omaha, Spring 2025
