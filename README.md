![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Power BI](https://img.shields.io/badge/PowerBI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-FF6F00?style=flat&logo=microsoft&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![Records](https://img.shields.io/badge/Records-1%2C500-blue)
![Fraud Rate](https://img.shields.io/badge/Fraud%20Rate-40.87%25-red)

# 🏥 Healthcare Revenue & Fraud Audit Analysis
**SQL • Power BI • DAX • Healthcare Analytics • Fraud Detection**

> **Headline finding:** 613 of 1,500 billing records (40.87%) were fraudulent, worth **₹248M — 52% of the ₹476M billed**. Phantom Billing was the largest fraud type (₹112M) and was billed **111% above** legitimate claims.

<img width="1920" height="1080" alt="Healthcare fraud dashboard overview" src="https://github.com/user-attachments/assets/a2a9d332-c1b4-4715-912e-6f25ab2495da" />
<img width="1920" height="1080" alt="Healthcare fraud dashboard, filtered view" src="https://github.com/user-attachments/assets/8d717613-620b-41a2-85c7-aad9b61f0bc9" />
<img width="1920" height="1080" alt="Healthcare fraud dashboard, drill-down view" src="https://github.com/user-attachments/assets/7f757664-6ba8-4fff-b8eb-d366c9021ab8" />

---

## 📌 Project Overview

An end-to-end audit framework that uses **SQL** for data interrogation and **Power BI** for executive-ready reporting. It classifies **1,500 patient billing records** into three fraud types — **Phantom Billing, Fake Treatment and Ghost Enrollee** — plus **No Fraud** (legitimate claims), and quantifies the financial impact to support audit, compliance and risk decisions.

---

## 🔢 Key Findings

| Metric | Value |
|---|---|
| Total patient records analyzed | 1,500 |
| Legitimate cases | 887 |
| Fraudulent cases | 613 |
| **Overall fraud rate** | **40.87%** |
| Total amount billed | ₹476,484,930 |
| Total fraudulent amount | ₹248,079,958 |
| Phantom Billing total | ₹112,168,420 |
| Fake Treatment total | ₹92,816,805 |
| Ghost Enrollee total | ₹43,094,731 |
| **Fraud share of total revenue** | **52.06%** |

> More than half of all billed revenue is linked to fraud, and Phantom Billing alone accounts for ₹112M (about 45% of fraud value).

---

## 💰 Average Billing by Fraud Type

| Fraud type | Cases | Avg amount billed | vs legitimate |
|---|---|---|---|
| No Fraud | 887 | ₹257,502 | baseline |
| Ghost Enrollee | 164 | ₹262,772 | +2% |
| Fake Treatment | 243 | ₹381,962 | **+48%** |
| Phantom Billing | 206 | ₹544,506 | **+111%** |

> Phantom Billing claims average **2.1× the legitimate claim** (₹544,506 vs ₹257,502), the strongest financial fraud signal in this dataset.

---

## 📖 Findings — The Data Story

### The scale of the problem
Of 1,500 records audited, **613 (40.87%)** were fraudulent, totalling ₹248 million, or **52.06%** of everything billed. For every ₹2 billed, more than ₹1 was fraudulent.

### Not all fraud is equal
Phantom Billing is the costliest fraud type: it bills at about twice the legitimate rate and concentrates in the most expensive procedures. Ghost Enrollee fraud is the hardest to spot, because its billing is almost identical to legitimate cases (+2%), so it can only be caught by cross-referencing admission and discharge dates (SQL Query 8).

### High-value procedures show a 100% fraud rate
Eight diagnoses had a **100% fraud rate** in this dataset, meaning every case filed under them was fraudulent:

| Diagnosis | Fraud cases | Avg billing (₹) | Total fraud (₹) |
|---|---|---|---|
| Epilepsy Surgery | 23 | 625,052 | 14,376,200 |
| Infertility Treatment (IVF) | 33 | 583,118 | 19,242,906 |
| Cosmetic Surgery | 27 | 581,172 | 15,691,632 |
| Organ Transplant | 23 | 579,659 | 13,332,161 |
| Cancer Treatment | 30 | 491,026 | 14,730,770 |
| Complex Heart Surgery | 26 | 506,539 | 13,170,025 |
| Neurosurgery | 21 | 503,447 | 10,572,384 |
| Advanced Spinal Surgery | 23 | 480,537 | 11,052,342 |

Fraud here is concentrated in **high-cost surgical procedures**, which are harder to verify and dispute. Epilepsy Surgery had the highest average billing (₹625,052, about 2.4× the legitimate baseline). **IVF alone accounts for ₹19.2M**, the largest fraudulent diagnosis category.

### Common conditions are also affected

| Diagnosis | Total cases | Fraud cases | Fraud rate |
|---|---|---|---|
| Hypertension | 90 | 35 | 38.89% |
| Tuberculosis | 103 | 40 | 38.83% |
| Gastroenteritis | 90 | 33 | 36.67% |
| Stroke | 84 | 28 | 33.33% |
| Pneumonia | 102 | 34 | 33.33% |
| Cesarean Section | 90 | 29 | 32.22% |

Tuberculosis had the highest case volume (103 records) with a 38.83% fraud rate, making it the highest-volume condition with significant fraud. Common, frequently billed conditions are harder to audit at scale.

### Fraud patterns differ by age group

| Age group | Dominant fraud type | Avg billing (₹) |
|---|---|---|
| 0–18 | Phantom Billing | 677,960 |
| 19–35 | Phantom Billing | 524,915 |
| 36–55 | Fake Treatment | 367,154 |
| 56–75 | Phantom Billing | 560,497 |
| 76+ | Phantom Billing | 548,259 |

- 🔴 **Children (0–18)** had the highest average Phantom Billing (₹677,960) of any age group.
- 🟠 **Patients 76+** had the most Ghost Enrollee cases (48). One possible explanation is that records for elderly patients are monitored less actively.
- 🟡 **Ages 36–55** are the only group where Fake Treatment is the dominant type.

### The worst individual cases
The largest single fraudulent claim was **₹988,887** for a Cosmetic Surgery Phantom Billing case, nearly 4× the legitimate average. All of the top 20 offending cases were Phantom Billing, across Cosmetic Surgery, Organ Transplant, Complex Heart Surgery, Epilepsy Surgery, IVF, Neurosurgery, Advanced Spinal Surgery and Cancer Treatment.

### The bottom line
₹248 million fraudulently billed. Eight surgical procedures at a 100% fraud rate. Children with the highest phantom billing. Patients 76+ with the most ghost enrollees. **In this dataset, fraud is concentrated in specific procedures and patient groups, which suggests it can be detected with the right data tools.**

---

## 🧮 SQL Analysis — 10 Queries

| # | Query | Technique |
|---|---|---|
| 1 | Total records and fraud rate overview | Aggregate functions, CASE WHEN |
| 2 | Fraud breakdown by type with average billing | GROUP BY, percentage calculation |
| 3 | Financial impact: total vs fraudulent billing | CASE WHEN, SUM, ROUND |
| 4 | Diagnosis vs treatment mismatch detection | WHERE inequality filter, GROUP BY |
| 5 | Fraud rate and average billing by diagnosis | CTE (WITH clause) |
| 6 | Diagnoses ranked by fraudulent billing amount | Window function: RANK() OVER (PARTITION BY) |
| 7 | Age-group segmentation of fraud | CASE WHEN age banding, GROUP BY |
| 8 | Ghost Enrollee: length-of-stay detection | DATEDIFF, STR_TO_DATE |
| 9 | Cases billed above the fraud-type average | Correlated subquery |
| 10 | Executive business summary in a single view | UNION ALL |

### SQL snippet — Query 5: fraud rate by diagnosis (CTE)

```sql
WITH diagnosis_summary AS (
    SELECT
        Diagnosis,
        COUNT(*) AS total_cases,
        SUM(CASE WHEN `Fraud Type` != 'No Fraud' THEN 1 ELSE 0 END) AS fraud_cases,
        ROUND(AVG(`Amount Billed`), 2) AS avg_billed
    FROM fraud
    GROUP BY Diagnosis
)
SELECT
    Diagnosis,
    total_cases,
    fraud_cases,
    ROUND(fraud_cases * 100.0 / total_cases, 2) AS fraud_rate_pct,
    avg_billed
FROM diagnosis_summary
ORDER BY fraud_rate_pct DESC;
```

---

## 📊 Power BI Dashboard — Visuals

| Visual | Insight delivered |
|---|---|
| KPI cards | Total billed, total fraud value, unique patients, average stay |
| Donut chart | Total billed split by gender |
| Line chart | Total fraud value by month of discharge |
| Scatter plot | Amount billed vs patient age, coloured by fraud type |
| Decomposition tree | Fraud value broken down by fraud type, then by treatment |
| Slicers | Filter by fraud type, diagnosis, treatment and discharge date |

---

## 🗃️ Dataset

| Column | Description |
|---|---|
| Patient_ID | Unique identifier for each patient record |
| Admission_Date | Date the patient was admitted |
| Discharge_Date | Date the patient was discharged |
| Diagnosis | Medical diagnosis |
| Treatment | Treatment provided |
| Amount_Billed | Total amount billed for the claim |
| Fraud_Type | Phantom Billing / Fake Treatment / Ghost Enrollee / No Fraud |
| Age | Patient age |
| Provider_ID | Healthcare provider identifier |

**Size:** 1,500 records | **Format:** CSV

**Source:** [ADD HERE: dataset name and link. If the data is synthetic or simulated, say so explicitly, because the 40.87% fraud rate and the eight 100%-fraud procedures are much higher than real-world rates.]

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| MySQL | Data extraction, validation and fraud pattern analysis (10 structured queries) |
| Power BI Desktop | Interactive KPI dashboard and executive reporting |
| DAX | Custom measures: fraud rate, average billing, total fraud value |
| Power Query | Data cleaning, date transformation and column standardization |

## 🚀 How to Run

### SQL analysis
1. Open a MySQL client (MySQL Workbench or DBeaver).
2. Import the dataset from the `Dataset/` folder.
3. Run the queries in the `SQL/` folder in order, Q1 through Q10.

### Power BI dashboard
1. Install Power BI Desktop (free).
2. Open `Power BI/Healthcare_Fraud_Dashboard.pbix`.
3. If prompted, update the data source path to your local `Dataset/` folder.
4. Refresh the data and explore the dashboard.

---

## 👤 Author

**Praises Kalintha**
📧 kalinthapraises777@gmail.com
🔗 [LinkedIn](https://www.linkedin.com/in/praises-kalintha-30a621354/)
💻 [GitHub](https://github.com/PraisesKalintha)

## 📄 License
This project is licensed under the MIT License.
