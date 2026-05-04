# 🏥 Hospital Bed Availability Decision System

## Project Title
**Hospital Bed Availability Decision System**

## Group Members
| Name | Role |
|------|---------------------|
| Dilshod Fayzullayev | Logic Designer |
| Ibroximov Axmadjon | CircuitVerse Designer |
| Ibrohim Saidov | Python Developer |
| Timur Suyunov | Documentation Lead |
| Temur Yangibaev | Presentation |

## Course
**EEE120 – Digital Design Fundamentals**

## Instructor
Doctor Rajan

---

## Project Overview
This project automates hospital patient admission decisions using combinational digital logic. It evaluates four binary inputs and produces one of three outcomes: **ADMIT**, **WAITLIST**, or **REJECT/REFER**.

---

## Inputs (4 Binary Inputs)

| Symbol | Input Name | Description |
|--------|-----------|-------------|
| **B** | Bed Available | Is a hospital bed currently free? (1=Yes, 0=No) |
| **E** | Emergency Case | Is the patient classified as an emergency? (1=Yes, 0=No) |
| **D** | Doctor Approval | Has a doctor approved the admission? (1=Yes, 0=No) |
| **P** | Payment Cleared | Is insurance or payment confirmed? (1=Yes, 0=No) |

---

## Outputs (3 Outputs)

| Output | Meaning |
|--------|---------|
| **ADMIT** | Patient is assigned a bed immediately |
| **WAITLIST** | Patient is queued and monitored |
| **REJECT/REFER** | Patient is directed to another facility |

---

## Digital Logic Explanation

### Boolean Expressions

```
ADMIT    = B · D · (E + P)
WAITLIST = (B · D · E' · P') + (B · D' · E)
REJECT   = ADMIT' · WAITLIST'
```

### Rules in Plain English

1. **ADMIT** if: a bed is available **AND** doctor approved **AND** (emergency **OR** payment is cleared)
2. **WAITLIST** if: a bed is available AND doctor approved AND neither emergency nor payment, OR bed is available AND no doctor approval yet but it is an emergency
3. **REJECT/REFER** for all other cases

---

## CircuitVerse Link
> 🔗 [CircuitVerse project](https://circuitverse.org/users/426743/projects/hospital-f7023259-0d82-4910-a167-e43c10679932)

---

## Python Program Explanation

The Python program at `src/main.py` implements the same Boolean logic and supports three modes:

| Mode | Description |
|------|-------------|
| **Manual Check** | Enter inputs interactively |
| **Truth Table** | Print all 16 input combinations |
| **Test Cases** | Run predefined verification cases |

Logic implementation:

```python
admit    = bed and doctor and (emergency or payment)
waitlist = (bed and doctor and not emergency and not payment) \
         or (bed and not doctor and emergency)
reject   = not admit and not waitlist
```

---

## Repository Structure

```
EEE120_Final_Project_GroupName/
│
├── README.md
├── circuitverse_link.txt
├── demo_video_link.txt
├── screenshots/
│   ├── circuit_design.png
│   ├── circuit_design-admit.png
│   ├── circuit_design-reject.png
│   ├── circuit_design-whitelist.png
│   ├── python_output.png
│
├── src/
│   └── main.py
│
├── presentation
│   └── final_presentation.pdf
```

---

## How to Run

```bash
git clone https://github.com/adhamachilov/EEE120_Final_Project_5_HBADSP.git
cd EEE120_Final_Project_5_HBADSP
python src/main.py
```

No dependencies outside the Python standard library are required.

---

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/circuit_design.png` | Primary circuit design screenshot |
| `screenshots/python_output.png` | Python program output screenshot |
| `screenshots/circuit_design-admit.png` | ADMIT path screenshot |
| `screenshots/circuit_design-reject.png` | REJECT path screenshot |
| `screenshots/circuit_design-whitelist.png` | WAITLIST path screenshot |

---
