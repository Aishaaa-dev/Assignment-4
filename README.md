### Academic Advisor — README

#### Overview and files
**Purpose:** A small rule‑based academic advisor that maps student inputs to canonical facts, applies forward‑chaining rules, and returns conclusions with human‑readable explanations.

**Included files**
- **`advisor_gui.py`** — Tkinter GUI with an explanation panel showing why each conclusion was reached.  

---

### Requirements and installation
**Requirements**
- Python **3.8+**  
- For GUI: **Tkinter** (usually included with standard Python installs)

**Install**
```bash
# create a virtual environment (optional)
python -m venv venv
source venv/bin/activate   # macOS / Linux
venv\Scripts\activate      # Windows

# no external pip packages required
```

---

### Run instructions

#### GUI
```bash
python advisor_gui.py
```
- Enter **Student name** (optional), **GPA**, **Attendance %**, and checkboxes for the three boolean fields.  
- Click **Evaluate** to see **Normalized facts**, **Conclusions**, and **Explanations**.  
- Optionally enable **Show why other rules did not fire** to view missing antecedents.


<img width="377" height="304" alt="Screenshot 2026-06-05 160400" src="https://github.com/user-attachments/assets/631d91d8-920d-40a1-8d89-0ffb40fe6736" />
<img width="379" height="307" alt="Screenshot 2026-06-05 160252" src="https://github.com/user-attachments/assets/e10e514e-d7a5-45df-88d7-987be75f53a5" />


---
## Task 3

<img width="501" height="380" alt="Screenshot 2026-06-05 165946" src="https://github.com/user-attachments/assets/48853cf0-15a6-46cc-bfd9-5c7d76bb9d70" />
<img width="497" height="378" alt="Screenshot 2026-06-05 171905" src="https://github.com/user-attachments/assets/670a1185-e1bc-4ba8-bf5c-d4c14bedbb72" />
<img width="496" height="380" alt="Screenshot 2026-06-05 172008" src="https://github.com/user-attachments/assets/14a3e433-b711-4a78-af1e-780800f63c18" />




---
### Knowledge base, rules, and explanations
**Facts (normalized labels)**  
- GPA: `GPA Above 3.5`, `GPA Between 3.0 and 3.49`, `GPA Above 3.0`, `GPA Below 3.0`  
- Attendance: `Attendance Above 80%`, `Attendance Below 80%`  
- Discipline: `No Disciplinary Cases`, `Has Disciplinary Cases`  
- Fees: `No Outstanding Fees`, `Has Outstanding Fees`  
- Courses: `Completed Prerequisite Courses`, `Missing Prerequisite Courses`

**Rules (examples in code)**
- **Scholarship:** IF `GPA Above 3.5` AND `Attendance Above 80%` AND `No Disciplinary Cases` THEN `Eligible for Scholarship`  
- **Dean's List:** IF `GPA Above 3.5` AND `Attendance Above 80%` THEN `Dean's List Candidate`  
- **Graduation:** IF `GPA Above 3.0` AND `Completed Prerequisite Courses` AND `No Outstanding Fees` THEN `Eligible for Graduation`  
- **Probation:** IF `GPA Below 3.0` THEN `Academic Probation`  
- **Registration Block:** IF `Has Outstanding Fees` THEN `Registration Blocked`

**How explanations are produced**
- Each rule is checked against the normalized fact set.  
- If **all antecedents** are present the rule fires; the system records the rule name and builds a sentence listing the antecedents that were satisfied.  
- For non‑fired rules the system can optionally list which antecedents were missing.

---

**Inference Flow Diagram**
<img width="1536" height="1024" alt="Copilot_20260605_170906" src="https://github.com/user-attachments/assets/d892bb14-11db-4e5a-8d58-bc339b97bb8a" />
