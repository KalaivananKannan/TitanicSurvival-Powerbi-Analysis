# 🚢 Titanic Survival Analysis — Interactive Power BI Dashboard

## 📌 Project Overview
This project presents an interactive **5-page Power BI dashboard** analyzing the demographic, socio-economic, and geographical factors that influenced passenger survival rates aboard the RMS Titanic. 

The dashboard provides end-to-end insights using cleaned raw data, custom DAX measures, age binning, and intuitive page navigation.

---

## 📸 Key Dashboard Pages

| Page | Title | Description |
| :--- | :--- | :--- |
| **Page 1** | **Executive Overview** | Summary KPI cards (Total Passengers, Survivors, Survival Rate) and high-level distribution. |
| **Page 2** | **Demographics Analysis** | Breakdown of passenger survival by Gender (`Sex`) and Socio-economic Class (`Pclass`). |
| **Page 3** | **Passenger Class Analysis** | Deep-dive into class-based survival rates filtered by `Survival Status`. |
| **Page 4** | **Age Distribution vs Pclass** | Binned age trends (`Age (bins)`) cross-analyzed with passenger classes and gender filters. |
| **Page 5** | **Embarkation Port Insights** | Survival distribution across boarding locations (Cherbourg, Queenstown, Southampton). |

---

## 🛠️ Data Cleaning & Transformations (Power Query)
* **Missing Value Handling:** Imputed missing values in `Age` using median age (28) and filled blank `Embarked` values with the mode (`S` - Southampton).
* **Conditional Mapping:**
  * `Survival Status`: Mapped `1` $\rightarrow$ *"Survived"*, `0` $\rightarrow$ *"Did Not Survive"*.
  * `Passenger Class`: Mapped `1` $\rightarrow$ *"First Class"*, `2` $\rightarrow$ *"Second Class"*, `3` $\rightarrow$ *"Third Class"*.
* **Data Binning:** Created 10-year age groups (`Age (bins)`) for age distribution modeling.

---

## 📊 Key DAX Measures Used

```dax
Total Passengers = COUNT(train[PassengerId])
Total Survivors = CALCULATE(COUNT(train[PassengerId]), train[Survived] = 1)
Survival Rate = DIVIDE([Total Survivors], [Total Passengers], 0)
