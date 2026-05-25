# Problem 2 Solution (Step-by-Step)

## Part A — Prakash Electric Bulb Company

### Step 1: Define the decision quantities
Let:
- **x1** = number of days Plant 1 operates  
- **x2** = number of days Plant 2 operates  
- **x3** = number of days Plant 3 operates

These are the only quantities we can choose.

---

### Step 2: Build the cost expression (what we want to minimize)
Daily costs:
- Plant 1: Rs. 55,000  
- Plant 2: Rs. 60,000  
- Plant 3: Rs. 60,000  

Total operating cost:

**C = 55,000x1 + 60,000x2 + 60,000x3**

We want the **smallest** possible value of C.

---

### Step 3: Write the demand requirements
From the table, each plant produces a fixed number of units per day.

**Model 1 demand (300,000 units):**
```
8000x1 + 6000x2 + 12000x3 ≥ 300,000
```

**Model 2 demand (172,000 units):**
```
4000x1 + 6000x2 + 4000x3 ≥ 172,000
```

**Model 3 demand (249,500 units):**
```
8000x1 + 3000x2 + 8000x3 ≥ 249,500
```

Also:
```
x1, x2, x3 ≥ 0
```

---

### Step 4: Final LP model (Part A‑a)
**Minimize**

`C = 55,000x1 + 60,000x2 + 60,000x3`

**Subject to**
```
8000x1 + 6000x2 + 12000x3 ≥ 300,000
4000x1 + 6000x2 + 4000x3 ≥ 172,000
8000x1 + 3000x2 + 8000x3 ≥ 249,500
x1, x2, x3 ≥ 0
```

---

### Step 5: Simplex method summary (Part A‑b)
Because the constraints are “≥”, convert them to equalities by:
1. Subtracting surplus variables  
2. Adding artificial variables  
3. Using a two‑phase (or Big‑M) simplex procedure  

**Phase I:** find a feasible solution.  
**Phase II:** minimize the real cost.

**Optimal solution (from the simplex method):**
```
x1 = 22.5 days
x2 = 10.5 days
x3 = 4.75 days
```

**Minimum cost:**
```
C = Rs. 2,152,500
```

**Check (demands met exactly):**
- Model 1: 300,000 units  
- Model 2: 172,000 units  
- Model 3: 249,500 units

---

### Step 6: Excel Solver steps and results (Part A‑c)
1. Put x1, x2, x3 in three cells.  
2. Create total production formulas for each model.  
3. Create total cost formula.  
4. Open Solver:
   - Set Objective: Total Cost cell  
   - To: Min  
   - By Changing: x1, x2, x3  
   - Constraints: model productions ≥ demands  
   - Method: Simplex LP  

**Solver returns the same solution:**
```
x1 = 22.5 days
x2 = 10.5 days
x3 = 4.75 days
Minimum cost = Rs. 2,152,500
```

Interpretation: this schedule meets all demands at the lowest possible cost.

---

### Step 7: Memorandum (Part A‑d)
**To:** Prakash Electric Bulb Company  
**Subject:** Minimum‑Cost Production Schedule  

To meet all required bulb demands at the lowest cost, the plants should operate as follows:

| Plant | Days to Operate |
|------|-----------------|
| Plant 1 | 22.5 days |
| Plant 2 | 10.5 days |
| Plant 3 | 4.75 days |

This schedule exactly meets the required demand for all three bulb models and gives the minimum total operating cost of **Rs. 2,152,500**. Any other schedule would either cost more or fail to meet demand.

---

## Part B — Graphical Solution

### Step 1: Constraints
```
4x + 5y ≤ 1500
5x + 3y ≤ 1575
x + 2y ≤ 420
x, y ≥ 0
```

### Step 2: Find corner points
Intersect the lines and keep only points inside all constraints:

- (0, 0)
- (0, 210)
- (315, 0)
- (270, 75)

### Step 3: Evaluate Z = 13x + 11y

| Point | Z |
|------|----|
| (0, 0) | 0 |
| (0, 210) | 2310 |
| (315, 0) | 4095 |
| (270, 75) | 4335 |

### Step 4: Choose the largest value
**Maximum Z = 4335 at (x, y) = (270, 75).**
