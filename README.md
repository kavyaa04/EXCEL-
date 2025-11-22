# EXCEL-
IN THE EXCEL PRACTICE
# 📊 Employee Dataset Simulation in Excel

This Excel file generates a realistic employee dataset for analytics practice.
Nothing was typed manually — every column was created using formulas, logic, and data-generation techniques.

## ✅ Columns Created

Serial No | Name | Phone | Email | Salary | Bonus% | Total Salary | DOB | Age | Department | Count

## ✅ Step-by-Step Logic & Formulas

1️⃣ Serial Number — Auto-generated IDs

Entered **1, 2, 3**, dragged down → Excel continues sequence automatically.
Purpose — every employee must have a unique identifier.

2️⃣ Names — Added Using Custom List

Created a custom list of names → dragged down.
Reason — avoids repetition & looks realistic.

3️⃣ Random Phone Numbers

FORMULA: =RANDBETWEEN(bottom, top)

=RANDBETWEEN(8889989898, 9963333221)
Purpose — generates valid 10-digit Indian-style numbers.

📧 Email Generation — Full Explanation

✅ Step 1 — Basic email using name


=B2 & "@gmail.com"

Problem — names were CAPITAL, but emails must be lowercase.

✅ Fix:
        FORMULA:  =LOWER(text)

=LOWER(B2 & "@gmail.com")

✅ Step 2 — Problem: duplicate names = duplicate emails

Example:

* Cora → [cora@gmail.com](mailto:cora@gmail.com)
* Another Cora → [cora@gmail.com](mailto:cora@gmail.com) ❌ NOT allowed

So we must detect duplicates first.


🔁 Counting Duplicate Names

Formula:    =COUNTIF(range, criteria)

=COUNTIF($B$2:B2, B2)


### Explanation:

* `$B$2` = fixed starting point → ALWAYS starts counting from row 2
* `B2` (last value) = keeps expanding as we drag down
* `B2` (criteria) = name we are counting

So results become:

Row 2 — Cora → count = 1
Row 3 — Robin → count = 1
Row 11 — Cora again → count = 2 ✅ duplicate detected

### But we don’t want the first email to end with 1

`cora1@gmail.com` cause in comapnies they use kav@gamil.com, kavs1@gmail.com etc..

So subtract 1:   =COUNTIF($B$2:B2, B2) - 1

* first Cora → 1-1 = 0
* second Cora → 2-1 = 1


✅ Final Email Formula — 

=IF(K2=0,
     LOWER(B2 & "@gmail.com"),
     LOWER(B2 & K2 & "@gmail.com")
)


Explanation:

* **IF K2 = 0** → name appears first time
  ✅ email = [cora@gmail.com](mailto:cora@gmail.com)

* **Else** (duplicate name)
  ✅ email = [cora1@gmail.com](mailto:cora1@gmail.com), [cora2@gmail.com](mailto:cora2@gmail.com)...

This guarantees:

✔ no duplicated emails
✔ no ugly zeros
✔ scalable — works for 50+ duplicates

💰 Salary Generation

FORMULA:    =RANDBETWEEN(bottom, top)

=RANDBETWEEN(55000, 450000)


🎯 Bonus %

##ROUND()

Purpose: Limit decimal places
Syntax:     =ROUND(number, num_digits)

##Used for random bonus %

=ROUND(RAND()/2, 2)

Why?

* `RAND()` gives random 0–1
* `/2` limits to 0–0.5 (0–50%)
* `ROUND(...,2)` gives 2 decimal places


## 💵 Total Salary

=D2 * (D2 + F2)


Logic — apply percentage bonus on salary.

---

## 🎂 Random Date of Birth

FORMULA:  =RANDBETWEEN(DATE(YYYY,MM,DD), DATE(YYYY,MM,DD))
=RANDBETWEEN(DATE(1982,1,1), DATE(2000,12,31))


## 🎉 Age Calculation — Correct Way

SYNTAX:     =DATEDIF(start_date, end_date, unit)

=DATEDIF(H2, TODAY(), "Y")

Unit meanings:

"Y" → full years
"M" → total months
"D" → total days
"YM" → months ignoring years
"MD" → days ignoring months
"YD" → days ignoring years

Why DATEDIF?

* ignores months & days
* gives clean whole age


## 🧹 Freezing Random Values

Because RAND, RANDBETWEEN & TODAY keep changing:

✅ Select entire sheet
✅ Copy → Paste Special → Values

Now dataset becomes stable.


## ✅ Key Excel Concepts Practiced

* AutoFill & Custom Lists
* Text concatenation (&)
* LOWER() formatting
* COUNTIF logic
* IF-based conditional automation
* Random data generation
* Date math using DATEDIF
* Reference handling ($ absolute & relative)
* Percentage calculations
* Data cleaning (Paste Values)


