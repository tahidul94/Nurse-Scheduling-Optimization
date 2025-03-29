# Nurse-Scheduling-Optimization
# Nurse Scheduling Optimization - Homework 3

This repository contains code and analysis for Homework 3 of the Computational Operations Research course. The goal was to build, solve, and analyze a Mixed Integer Programming model that assigns nurses to hospital shifts under real-world constraints.

---

## 📁 Files Included
- `nurses_assignment_problem.ipynb`: Jupyter notebook implementing the optimization model and visualization.
- `Data_Nurses_Assignment_Problem.xlsx`: Dataset including shift details, skills, vacations, and nurse info.
- `hw3.pdf`: Final report PDF with analysis, graphs, and conclusions.

---

## 📌 Objectives
1. **Formulate the nurse assignment problem** using constraints A–F based on real data.
2. **Analyze the impact of each constraint** on worktime distribution and cost.
3. **Perform sensitivity analysis** to identify what changes break feasibility.

---

## 🔧 Constraints Implemented
- **A:** No more than two consecutive shifts per nurse.
- **B:** Average qualification of assigned nurses per shift ≤ 3.
- **C:** Average seniority per shift ≥ 4.
- **D:** Each department must meet its skill coverage requirements.
- **E:** Every nurse must work at least 30 hours per week.
- **F:** Night shifts (8pm–8am) incur 1.5x pay rate.

---

## 📈 Results Summary
- **Before vs After Constraints:**
  - Cost increased from ~$28,824 to ~$31,981.
  - Worktime became more evenly distributed (all ≥30h).
- **Sensitivity Testing:**
  - Increasing demand, skill needs, or reducing staff → infeasible.

---

## 📊 Visual Outputs
- Nurse worktime before vs after constraints.
- Shift assignments per nurse.
- Sensitivity test summary.

---

## ✍️ Authors
- Md Tahidul Islam  
- University of Nebraska at Omaha  
- Spring 2025, MATH 4320/8326

---

## 📬 Contact
Feel free to reach out with questions or feedback: [mdtahidulislam@unomaha.edu]

---

## 🛠 Tools Used
- Python (with Docplex, Pandas, Matplotlib)
- IBM CPLEX Optimization Studio
- Jupyter Notebooks

