# Palmoria-HR-Analysis
# 🏢 Palmoria HR Analysis Dashboard – Power BI Project

This Power BI project focuses on analyzing the gender equality and compensation structure of **Palmoria Group**, a manufacturing company operating in Nigeria. The analysis was carried out to uncover gender disparities, performance trends, salary gaps, and compliance with new wage regulations.

---

## 📁 Project Files
- Power BI Report: `Palmoria-HR-Analysis.pbix`
- Dashboard Images:
  - `palmoria-hr-analysis-dashboard.png`
  - `male-dashboard.png`
  - `rating-picture.png`
  - `female-dasboard.png`

---

## 🎯 Objective
To provide Palmoria management with data-driven insights around:
- Gender representation across departments and locations
- Salary and bonus allocation by gender
- Performance ratings and their impact on compensation
- Compliance with the regulatory minimum salary requirement of $90,000

---

## 📊 Dashboard Overview

The dashboard includes:
- **Gender Distribution** by Region & Department
- **Salary Band Analysis**
- **Performance Rating by Gender**
- **Bonus Distribution**
- **Key Metrics Cards**:
  - Total Staff
  - Total Salary
  - Total Compensation
  - Staff earning above $90,000
  - Total Bonus Paid

![Dashboard](palmoria-hr-analysis-dashboard.png)

---

## 📌 Key Findings

- **Gender Imbalance**: Male employees dominate in most departments, especially in technical roles.
- **Pay Gap**: Male employees earn more on average than females across most departments.
- **Regulatory Compliance**: Only **152 out of 465** employees earn above $90,000 in some branches.
- **Performance & Gender**: Most females are rated “Average” or “Good,” but receive lower average bonuses compared to males with the same ratings.

---

## 🧮 Key DAX Measures

### 🎯 Gender Pay Gap

```DAX
GenderPayGap = 
VAR AvgMale = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]), 'Palmoria Group emp-data'[Gender Category] = "Male")
VAR AvgFemale = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]), 'Palmoria Group emp-data'[Gender Category] = "Female")
RETURN
DIVIDE(AvgMale - AvgFemale, AvgMale)
```

---

### 💰 Bonus Calculation (in Power Query logic)

```M
if [Performance Rating] = "Very Poor" then [#"Bonus Rules.Very Poor"] 
else if [Performance Rating] = "Poor" then [#"Bonus Rules.Poor"] 
else if [Performance Rating] = "Average" then [#"Bonus Rules.Average"] 
else if [Performance Rating] = "Good" then [#"Bonus Rules.Good"] 
else if [Performance Rating] = "Very Good" then [#"Bonus Rules.Very Good"] 
else null
```

---

### 📈 Total Bonus Paid

```DAX
TotalBonusPaid = SUM('Palmoria Group emp-data'[BonusAmount])
```

### 💼 Total Compensation

```DAX
TotalCompensation = SUM('Palmoria Group emp-data'[TotalCompensation])
```

### 👥 Staff with Salary >= 90,000

```DAX
HighEarners = 
CALCULATE(COUNTROWS('Palmoria Group emp-data'), 'Palmoria Group emp-data'[Salary] >= 90000)
```

---

## 📦 Tools Used
- Power BI (Power Query, DAX, Visualizations)
- Excel (Data Preparation)
- JSON (Custom Theme Styling)

---

## 🧠 Insights Delivered
Palmoria can now:
- Target gender disparities in performance reviews and promotions
- Monitor bonus allocations for fairness
- Ensure compliance with wage laws
- Improve diversity reporting

---

## 📸 Additional Visuals

### Rating by Gender
![Rating by Gender](rating-picture.png)

### Male Dashboard Filter
![Male Dashboard](male-dashboard.png)

### Female Dashboard Filter
![Female Dashboard](Female-dashboard.png)

---

## 📌 Author

**[Oreoluwa Bonojo ]** – Data Analyst  
🌍 Location: Nigeria  
📧 Contact: [orebonojo@gmail.com]  

