# Nurse Scheduling Optimization Report 

### Course: Computational Operations Research (MATH 4320/8326)  
### Author: Md Tahidul Islam  
### Institution: University of Nebraska at Omaha  
### Semester: Spring 2025  

---

## 1. Problem Description

The objective of this project is to formulate and solve a realistic nurse scheduling optimization problem using Mixed Integer Programming (MIP). The model aims to assign a set of nurses to a weekly schedule of shifts across various hospital departments while minimizing total labor cost and satisfying complex scheduling, skill, and policy constraints.

---

## 2. Data Summary

The dataset includes:
- **Nurses**: Name, pay rate, qualification level, seniority.
- **Shifts**: Start/end times, department, day of the week, required number of nurses.
- **Skills**: Required skills for departments and nurse-specific skills.
- **Additional Constraints**: Nurse incompatibilities, preferred associations, vacation days.

---

## 3. Optimization Model

### Objective Function:
Minimize total salary cost = \( \sum (\text{Worktime}_n \times \text{PayRate}_n) \), with 1.5× multiplier for night shifts.

### Decision Variables:
- \( x_{n,s} \): Binary variable; 1 if nurse \( n \) is assigned to shift \( s \), 0 otherwise.
- \( w_n \): Continuous variable; total work hours for nurse \( n \).

### Constraints Implemented:
- **A.** No more than 2 consecutive shifts per nurse.
- **B.** Average qualification per shift \( \leq 3 \).
- **C.** Average seniority per shift \( \geq 4 \).
- **D.** Minimum skill requirement coverage per department.
- **E.** Each nurse must work \( \geq 30 \) hours.
- **F.** Night shifts (between 8PM and 8AM) are paid at 1.5× rate.
- **Additional:** No overlap in shift assignments, respect nurse vacations, and apply incompatibility and association constraints.

---

## 4. Results and Analysis

### 4.1 Worktime and Cost Comparison
- **Before constraints**: Some nurses worked < 30 hours; total cost: **$28,824**.
- **After constraints A–F**: All nurses worked ≥30 hours; cost increased to **$31,981**.
- Plots show improved fairness and compliance with policy.

### 4.2 Constraint Impact
- Constraint E (min 30h) reshaped work distribution.
- Constraints B, C, D introduced higher-skill nurses into more shifts.
- Constraint F increased cost due to night shift premiums.

---

## 5. Sensitivity Analysis

Three stress tests were conducted to assess model robustness:

| Scenario | Change Applied | Feasible? |
|----------|----------------|-----------|
| 1. Increased demand | Raised Min_Required for all shifts by +1 | ❌ No |
| 2. Increased skill needs | Added +1 to all skill requirements | ❌ No |
| 3. Nurse shortage | Removed 2 nurses from the pool | ❌ No |

The model failed to find a solution in all three cases, indicating it operates close to its feasibility limits and is sensitive to small disruptions.

---

## 6. Conclusion

The nurse scheduling model successfully assigns nurses while balancing costs, coverage, and institutional policies. However, the solution is highly sensitive to changes in demand and staffing. To increase robustness, future work could include soft constraints, overtime options, or flexibility in qualifications and skill coverage.

---

## 7. Tools Used
- Python, Jupyter Notebook
- IBM CPLEX (Docplex)
- Matplotlib, Pandas

---

## 8. Author Note
This report was submitted as part of Homework 3 in MATH 4320/8326. All analysis and modeling were conducted by Md Tahidul Islam under the guidance of the course instructor.

