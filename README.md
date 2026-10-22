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

<img width="1422" height="847" alt="Screenshot 2026-10-22 230208" src="https://github.com/user-attachments/assets/d25b2f4f-e586-405d-b4d9-92f9e32b7d5f" />
<img width="1433" height="852" alt="Screenshot 2026-10-22 230124" src="https://github.com/user-attachments/assets/6d391b79-5692-449e-919b-c5c019eba71f" />
<img width="1441" height="855" alt="Screenshot 2026-10-22 230103" src="https://github.com/user-attachments/assets/42d0ccbe-1d50-4566-9c56-5058e360f52e" />
<img width="1423" height="849" alt="Screenshot 2026-10-22 230038" src="https://github.com/user-attachments/assets/b2c81b9e-8046-4e44-b4f2-77ab61af21f8" />
<img width="1420" height="851" alt="Screenshot 2026-10-22 225839" src="https://github.com/user-attachments/assets/620ca7a2-c977-4e5a-b4c0-526267156289" />
