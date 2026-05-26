# Viva Preparation Notes — Q2 Linear Programming Problem (MA4001NP Logic and Problem Solving)

These notes are for **reading, revision, and viva preparation**. They explain concepts step-by-step in simple, correct language.

---

## 1. Problem Overview
- **What is a Linear Programming Problem (LPP)?**
  - An LPP is a mathematical model that **optimizes (maximizes or minimizes)** a linear objective function subject to linear constraints.
  - “Linear” means variables appear only to the first power and are not multiplied together.
- **Purpose of optimization**
  - To **use limited resources efficiently** (cost, time, materials) while meeting goals (profit, demand, service level).
- **Minimization vs Maximization**
  - **Minimization:** reduce cost/time/effort while meeting requirements.
  - **Maximization:** increase profit/output/utility within limits.
- **Real-world applications**
  - Production planning, transportation, diet planning, staffing, scheduling, mixing/blending.
- **Why businesses use LPP**
  - It provides **best-possible decisions** backed by numbers, not guesswork.

**Quick memory tip:**  
“**M**inimize **M**oney spent; **M**aximize **M**oney made.”

---

## 2. Important Definitions (with simple examples)
- **Decision Variables:** unknowns you control.
  - Example: `x1 = days Plant 1 runs`.
- **Objective Function:** formula you optimize.
  - Example: `Min Z = 55,000x1 + 60,000x2 + 60,000x3`.
- **Constraints:** limits that must be satisfied.
  - Example: total production of Model 1 ≥ 300,000 units.
- **Feasible Region:** all solutions that satisfy every constraint.
- **Optimal Solution:** best feasible solution (min or max).
- **Slack Variables:** extra amount when a “≤” constraint is not tight.
  - Example: if capacity is 100 and you use 90, slack = 10.
- **Artificial Variables:** temporary variables used in simplex for “≥” or “=” constraints.
- **Non-negativity Constraints:** variables cannot be negative (x ≥ 0).
- **Maximization:** make objective as large as possible.
- **Minimization:** make objective as small as possible.

---

## 3. Part A – Minimization Problem (Step-by-Step)
**Problem context:** Three plants produce three models of bulbs. Each plant has daily capacity and daily cost. Find how many days to run each plant to **meet demand at minimum cost**.

### 3.1 Decision Variables
Let:
- `x1` (or **x**) = days Plant 1 operates  
- `x2` (or **y**) = days Plant 2 operates  
- `x3` (or **z**) = days Plant 3 operates  

These are decision variables because **we control the number of operating days**.

### 3.2 Objective Function (Minimization)
Daily operating costs:
- Plant 1: Rs. 55,000/day
- Plant 2: Rs. 60,000/day
- Plant 3: Rs. 60,000/day

So the total cost is:
- `Z = 55,000x1 + 60,000x2 + 60,000x3`

We **minimize Z** because the company wants **minimum operating cost** while meeting demand.

**Math step explanation**
- Cost from Plant 1 = (cost per day) × (days) = `55,000 × x1`
- Cost from Plant 2 = `60,000 × x2`
- Cost from Plant 3 = `60,000 × x3`
- Total cost is the sum of all three terms.

### 3.3 Constraints (Demand for Each Model)
Daily production capacities (units/day):
- Plant 1: Model 1 = 8,000; Model 2 = 4,000; Model 3 = 8,000
- Plant 2: Model 1 = 6,000; Model 2 = 6,000; Model 3 = 3,000
- Plant 3: Model 1 = 12,000; Model 2 = 4,000; Model 3 = 8,000

**Model 1 demand (300,000 units)**
- Total production = `8000x1 + 6000x2 + 12000x3`
- Constraint: `8000x1 + 6000x2 + 12000x3 ≥ 300,000`
  - Meaning: combined Model 1 output from all plants must meet demand.

**Model 2 demand (172,000 units)**
- Total production = `4000x1 + 6000x2 + 4000x3`
- Constraint: `4000x1 + 6000x2 + 4000x3 ≥ 172,000`
  - Meaning: combined Model 2 output must be at least 172,000 units.

**Model 3 demand (249,500 units)**
- Total production = `8000x1 + 3000x2 + 8000x3`
- Constraint: `8000x1 + 3000x2 + 8000x3 ≥ 249,500`
  - Meaning: combined Model 3 output must be at least 249,500 units.

**Non-negativity**
- `x1, x2, x3 ≥ 0` (days cannot be negative)

---

## 4. Understanding Constraints
- **Why constraints are necessary**
  - They represent **real-world limits** (demand, capacity, policy).
- **Meaning of “≥”**
  - The company must **meet or exceed demand** for each model.
- **Why production demand must be satisfied**
  - Under-producing fails customer orders and hurts business reputation.
- **What happens if constraints are violated**
  - Solution becomes **infeasible** (not allowed in real life).
- **Why non-negativity constraints are important**
  - Negative days or negative production **have no real meaning**.

---

## 5. Simplex Method Concepts (Conceptual)
- **What is the simplex method?**
  - An algorithm to find the **best (optimal) solution** of an LPP by moving along corners of the feasible region in higher dimensions.
- **Why simplex is used**
  - Graphical method works only for 2 variables; simplex handles **many variables**.
- **Basic feasible solution (BFS)**
  - A solution at a corner point (intersection of constraints) that satisfies all constraints.
- **Pivot element**
  - The element used to update the tableau when moving to a better BFS.
- **Key column**
  - The column that shows which variable will **enter** the basis.
- **Key row**
  - The row that shows which variable will **leave** the basis (minimum ratio test).
- **Iteration process**
  - Repeat pivoting to improve the objective value until no improvement is possible.
- **Optimality condition**
  - For minimization: no negative reduced costs (in standard form).

---

## 6. Excel Solver Implementation (Step-by-Step)
- **Create the Excel template**
  - Make cells for `x1, x2, x3`.
  - Add formulas for each constraint’s left-hand side.
  - Add a cell for total cost `Z`.
- **Enter decision variables**
  - Put starting guesses (e.g., 0) in `x1, x2, x3`.
- **Set the objective function**
  - `Z = 55,000x1 + 60,000x2 + 60,000x3`.
- **Enter constraints**
  - Model 1: `8000x1 + 6000x2 + 12000x3 ≥ 300,000`.
  - Model 2: `4000x1 + 6000x2 + 4000x3 ≥ 172,000`.
  - Model 3: `8000x1 + 3000x2 + 8000x3 ≥ 249,500`.
  - Non-negativity: `x1, x2, x3 ≥ 0`.
- **Choose “Changing Variable Cells”**
  - Select the cells containing `x1, x2, x3`.
- **Add constraints in Solver**
  - Use “Add” and input each constraint exactly.
- **Select method**
  - Choose **Simplex LP** (since the model is linear).
- **Generate reports**
  - Ask Solver for Answer, Sensitivity, and Limits reports.

**Why Solver is useful**
- Fast, reliable, and avoids hand calculation errors.

**Common Solver setup mistakes**
- Wrong sign (≥ vs ≤)
- Forgetting non-negativity
- Selecting wrong objective (Max instead of Min)

---

## 7. Excel Reports (What They Mean)
- **Answer Report**
  - Shows the final values of variables and constraints.
  - Confirms which constraints are binding.
- **Sensitivity Report**
  - Shows how sensitive the solution is to changes in costs or RHS values.
  - Helps decide if small changes will change the optimal plan.
- **Limits Report**
  - Shows how much each variable can change while still meeting constraints.

**Business interpretation**
- Sensitivity helps managers test “what-if” situations without solving again.

---

## 8. Final Minimization Solution (Interpretation)
Optimal days:
- **Plant 1:** 22.5 days  
- **Plant 2:** 10.5 days  
- **Plant 3:** 4.75 days  

**Why this minimizes cost**
- Plant 1 has the **lowest daily cost**, so it is used most.
- Plants 2 and 3 are used just enough to meet remaining demand.

**Minimum cost calculation**
- `Z = 55,000(22.5) + 60,000(10.5) + 60,000(4.75)`
- `Z = 1,237,500 + 630,000 + 285,000`
- **Z = Rs. 2,152,500**

**Business meaning**
- This schedule meets **all demand** with **minimum expense**.

---

## 9. Memorandum Explanation
- **Purpose of memorandum**
  - To communicate results clearly to management.
- **Why recommendations are formal**
  - Decisions affect costs and operations; professionalism builds trust.
- **How technical results become business language**
  - Convert “x1 = 22.5” into “Operate Plant 1 for 22.5 days.”
- **Importance**
  - Management needs **clear actions**, not just equations.

---

## 10. Part B – Graphical Maximization Problem
**Objective Function**
- Maximize: `Z = 13x + 11y`

**Constraints**
- `4x + 5y ≤ 1500`
- `5x + 3y ≤ 1575`
- `x + 2y ≤ 420`
- `x, y ≥ 0`

**Why convert inequalities into equations?**
- To draw each line and find intercepts.
  - Example: `4x + 5y = 1500` is the boundary line.

**Intercept calculations**
- For `4x + 5y = 1500`:
  - If `y = 0`, `x = 1500/4 = 375`
  - If `x = 0`, `y = 1500/5 = 300`
- For `5x + 3y = 1575`:
  - If `y = 0`, `x = 1575/5 = 315`
  - If `x = 0`, `y = 1575/3 = 525`
- For `x + 2y = 420`:
  - If `y = 0`, `x = 420`
  - If `x = 0`, `y = 210`

**Origin test**
- Plug (0,0) into each constraint:
  - If true, shade the side containing the origin.

**Feasible region**
- The overlap of all shaded areas is feasible.

**Corner point method**
- Evaluate Z at each vertex because optimum occurs at vertices in a linear model.

---

## 11. Graphical Solution (Step-by-Step)
**Vertices (corner points)**
- (0,0)
- (0,210)
- (315,0)
- (270,75) — intersection of `5x+3y=1575` and `x+2y=420`

**Intersection calculation**
- From `x + 2y = 420` ⇒ `x = 420 − 2y`
- Substitute into `5x + 3y = 1575`:
  - `5(420 − 2y) + 3y = 1575`
  - `2100 − 10y + 3y = 1575`
  - `−7y = −525` ⇒ `y = 75`
  - `x = 420 − 2(75) = 270`

**Evaluate objective function**
- `Z(0,0) = 0`
- `Z(0,210) = 13(0) + 11(210) = 2310`
- `Z(315,0) = 13(315) + 11(0) = 4095`
- `Z(270,75) = 13(270) + 11(75) = 3510 + 825 = 4335`

**Conclusion**
- Maximum profit **Z = 4335** at **B(270,75)**.

---

## 12. Practical Understanding (Real-World Meaning)
- **Minimization**
  - Used to **reduce cost**, e.g., cheapest production plan that still meets demand.
- **Maximization**
  - Used to **increase profit/output**, e.g., best product mix within resource limits.
- **Applications**
  - Factories: production schedules, machine hours
  - Transport: minimize fuel or time
  - Manufacturing: raw material mix
  - Scheduling: staff shifts, timetable optimization
  - Resource allocation: budget distribution

---

## 13. Common Viva Questions with Answers (50)
1. **What is an LPP?**  
   - Short: A model to optimize a linear objective with linear constraints.  
   - Technical: Optimize `Z = cᵀx` subject to `Ax ≤/≥ b`, `x ≥ 0`.  
   - Follow-up: Why must it be linear?
2. **Why do we use decision variables?**  
   - Short: They represent choices we control.  
   - Technical: They form the vector `x` in the model.  
   - Follow-up: What happens if you choose wrong variables?
3. **What is the objective function here?**  
   - Short: Minimize operating cost.  
   - Technical: `Min Z = 55,000x1 + 60,000x2 + 60,000x3`.  
   - Follow-up: What if costs change?
4. **Why is it a minimization problem?**  
   - Short: We want the lowest cost.  
   - Technical: Costs are positive and constraints ensure demand.  
   - Follow-up: Could it ever be maximization?
5. **What is a constraint?**  
   - Short: A condition that must hold.  
   - Technical: A linear inequality/equality in `x`.  
   - Follow-up: What if a constraint is removed?
6. **Explain non-negativity.**  
   - Short: Negative production is impossible.  
   - Technical: `x ≥ 0` ensures real-world feasibility.  
   - Follow-up: What if negative values were allowed?
7. **What is a feasible region?**  
   - Short: Set of all valid solutions.  
   - Technical: Intersection of all constraint half-planes.  
   - Follow-up: Can it be empty?
8. **What is a basic feasible solution?**  
   - Short: A corner point solution.  
   - Technical: A feasible solution with `m` basic variables.  
   - Follow-up: Why are BFS important?
9. **Why does optimum occur at a vertex?**  
   - Short: Linear objective over a polygon peaks at corners.  
   - Technical: Follows from convexity and linearity.  
   - Follow-up: Does this hold for nonlinear problems?
10. **What is slack?**  
    - Short: Unused capacity in “≤” constraints.  
    - Technical: `s = b − Ax` with `s ≥ 0`.  
    - Follow-up: When is slack zero?
11. **What is surplus?**  
    - Short: Excess over a “≥” constraint.  
    - Technical: `Ax − s = b` with surplus `s ≥ 0`.  
    - Follow-up: Why do we subtract surplus?
12. **Why add artificial variables?**  
    - Short: To start simplex with a feasible basis.  
    - Technical: Used in Big-M or two-phase methods.  
    - Follow-up: How do we remove them?
13. **What is the simplex method?**  
    - Short: An algorithm to reach the best corner point.  
    - Technical: Iterative pivoting on a tableau.  
    - Follow-up: Why not use graphing for 3 variables?
14. **What is a pivot element?**  
    - Short: The element used to update the tableau.  
    - Technical: Intersection of key row and key column.  
    - Follow-up: What makes a correct pivot?
15. **Explain key column selection.**  
    - Short: Column with greatest improvement potential.  
    - Technical: Most negative reduced cost for minimization.  
    - Follow-up: What if there is a tie?
16. **Explain key row selection.**  
    - Short: The smallest ratio test row.  
    - Technical: `b_i / a_ij` minimum positive value.  
    - Follow-up: What if no positive ratio exists?
17. **What is degeneracy?**  
    - Short: When a BFS has a zero basic variable.  
    - Technical: Can cause cycling in simplex.  
    - Follow-up: How is cycling avoided?
18. **How do you check feasibility?**  
    - Short: Substitute values into all constraints.  
    - Technical: Verify `Ax ≤/≥ b` and `x ≥ 0`.  
    - Follow-up: What if one fails?
19. **Explain sensitivity analysis.**  
    - Short: Check how changes affect the optimal solution.  
    - Technical: Uses shadow prices and allowable ranges.  
    - Follow-up: Why is it useful for managers?
20. **What is a shadow price?**  
    - Short: Value of one extra unit of a resource.  
    - Technical: Dual variable value for a constraint.  
    - Follow-up: Can it be negative?
21. **Why use Excel Solver?**  
    - Short: Fast and accurate for linear models.  
    - Technical: Uses Simplex LP automatically.  
    - Follow-up: What happens if you choose GRG?
22. **What does “binding constraint” mean?**  
    - Short: Constraint exactly met at optimum.  
    - Technical: Slack/surplus = 0.  
    - Follow-up: Why are binding constraints important?
23. **How do you find intercepts?**  
    - Short: Set x=0 then y=0.  
    - Technical: Solve boundary equations for axis points.  
    - Follow-up: Why are intercepts useful?
24. **What is the corner point method?**  
    - Short: Evaluate Z at each vertex.  
    - Technical: Check all extreme points of feasible region.  
    - Follow-up: How many vertices can exist?
25. **Why does Plant 1 run the most days?**  
    - Short: It has the lowest daily cost.  
    - Technical: Cost coefficient is minimum in objective.  
    - Follow-up: What if its capacity were lower?
26. **Why do we have ≥ in demand constraints?**  
    - Short: Demand must be met or exceeded.  
    - Technical: Production totals must be at least required.  
    - Follow-up: When would we use equality?
27. **Explain the meaning of x1, x2, x3.**  
    - Short: Plant operating days.  
    - Technical: Continuous decision variables in days.  
    - Follow-up: Are they integers?
28. **What is the feasible region shape?**  
    - Short: A polygon in 2D.  
    - Technical: A convex polyhedron in higher dimensions.  
    - Follow-up: Why convex?
29. **How is the optimum verified in Part B?**  
    - Short: Compare Z at all vertices.  
    - Technical: Max Z among feasible corners.  
    - Follow-up: Could an edge also be optimal?
30. **Why is (270,75) optimal?**  
    - Short: It gives highest Z = 4335.  
    - Technical: It satisfies all constraints with max objective.  
    - Follow-up: Which constraints are binding there?
31. **What is a dual problem?**  
    - Short: A related LPP that flips roles of constraints.  
    - Technical: Dual of min is max and vice-versa.  
    - Follow-up: Why is duality important?
32. **What is unboundedness?**  
    - Short: Objective can increase without limit.  
    - Technical: Feasible region open in improving direction.  
    - Follow-up: How do you detect it?
33. **What is infeasibility?**  
    - Short: No solution satisfies all constraints.  
    - Technical: Constraint system has no intersection.  
    - Follow-up: How do you fix infeasibility?
34. **Explain the role of artificial variables in Part A.**  
    - Short: Help start simplex for ≥ constraints.  
    - Technical: Added then penalized in Big-M.  
    - Follow-up: What if they remain in final solution?
35. **What is the meaning of Z?**  
    - Short: Total cost or total profit.  
    - Technical: Objective function value.  
    - Follow-up: Is Z always monetary?
36. **Why are constraints linear?**  
    - Short: LPP requires linear relationships.  
    - Technical: Coefficients constant; variables not multiplied.  
    - Follow-up: What if cost per day changes with time?
37. **Can LPP handle integer decisions?**  
    - Short: Not directly; needs integer programming.  
    - Technical: Add integrality constraints.  
    - Follow-up: Why is that harder?
38. **What is the Big-M method?**  
    - Short: Penalty method for artificial variables.  
    - Technical: Add ±M in objective to force removal.  
    - Follow-up: What is two-phase method?
39. **Why do we check all vertices in graphing?**  
    - Short: Max/min occurs at a vertex.  
    - Technical: Linear objective on a convex polytope.  
    - Follow-up: What about ties?
40. **What is a tie in simplex?**  
    - Short: Two candidates for entering/leaving.  
    - Technical: Multiple optimal or degenerate solutions.  
    - Follow-up: How do you choose?
41. **What if demand increases?**  
    - Short: Re-solve with new RHS values.  
    - Technical: Use sensitivity ranges if within limits.  
    - Follow-up: What if outside limits?
42. **What does “binding” mean in Part B?**  
    - Short: Constraint exactly equals the limit.  
    - Technical: For (270,75), constraints 2 and 3 are binding.  
    - Follow-up: Which one is non-binding?
43. **How do you explain results to managers?**  
    - Short: Convert numbers to actions.  
    - Technical: State days, costs, and benefits clearly.  
    - Follow-up: Why is it important?
44. **Why is simplex better than trial-and-error?**  
    - Short: Systematic and guaranteed.  
    - Technical: Moves along BFS with objective improvement.  
    - Follow-up: What is its worst-case complexity?
45. **What is the role of the feasible region?**  
    - Short: It limits possible solutions.  
    - Technical: Defines all valid x vectors.  
    - Follow-up: What if region is unbounded?
46. **What is the interpretation of (0,210)?**  
    - Short: Produce using only y.  
    - Technical: x = 0, y = 210 satisfies constraints.  
    - Follow-up: Is it optimal?
47. **Why is non-negativity assumed?**  
    - Short: Negative production has no meaning.  
    - Technical: Keeps solution in realistic domain.  
    - Follow-up: What if returns are allowed?
48. **What is a continuous variable?**  
    - Short: Can take fractional values.  
    - Technical: Real-valued decision variable.  
    - Follow-up: Is 22.5 days acceptable?
49. **How do you verify the cost calculation?**  
    - Short: Multiply cost per day by days and sum.  
    - Technical: Evaluate objective at optimal x.  
    - Follow-up: What if rounding is required?
50. **What is the main conclusion for Q2?**  
    - Short: A cost-minimizing schedule and a profit-maximizing point.  
    - Technical: `x1=22.5, x2=10.5, x3=4.75` and `(270,75)`.  
    - Follow-up: How would changes affect these?

---

## 14. Common Mistakes and Viva Traps
- Wrong feasible region due to shading the wrong side.
- Incorrect intercepts (division errors).
- Using **≤** instead of **≥** (or vice-versa).
- Forgetting non-negativity constraints.
- Misinterpreting decision variables.
- Mixing models (Model 1/2/3) in constraints.
- Objective function sign mistakes.
- Solver set to **Max** instead of **Min**.
- Not checking if all constraints are satisfied.
- Reporting a point that is outside the feasible region.

---

## 15. Limitations and Improvements
- **Limitations**
  - Assumes linearity and constant rates.
  - Assumes divisibility (fractional days allowed).
  - Ignores uncertainty and real-world variability.
- **Why real problems are more complex**
  - Costs may change, demand may fluctuate, resources may be discrete.
- **Possible improvements**
  - Use integer programming for whole days.
  - Use stochastic models for uncertain demand.
  - Add more realistic constraints (labor, maintenance).

---

## 16. Final Revision Sheet (Quick Notes)
### Important formulas
- Objective: `Z = Σ (cost × decision variable)`
- Constraints: `Σ (capacity × decision variable) ≥ demand`
- Graphing: set `x=0` and `y=0` to get intercepts

### Key concepts
- Feasible region = all valid solutions
- Optimal = best feasible solution
- Slack/surplus = unused/excess
- Simplex moves between corner points

### Key viva points
- Explain **why** objective is min or max
- Interpret variables in business language
- State which constraints are binding

### Quick revision summary
- Minimize cost with demand constraints (Part A)
- Use simplex/solver for 3 variables
- Maximize profit graphically (Part B)
- Optimum at vertices

### Last-minute tips
- Draw a quick constraint graph and check shading.
- Always compute Z at every vertex.
- Double-check signs and units.
