# 📊 Excel Math & Number Formula Practice

## 🎯 Objective

This practice file contains Excel Math & Number formulas, practice questions, and their solutions. The goal is to strengthen core Excel skills required for Data Analyst, MIS Executive, and Business Analyst roles.

---

# 🔢 Topics Covered

* SUM
* AVERAGE
* COUNT
* COUNTA
* COUNTBLANK
* MAX
* MIN
* LARGE
* SMALL
* ROUND
* ROUNDUP
* ROUNDDOWN
* ABS
* MOD
* INT
* TRUNC
* CEILING
* FLOOR
* CEILING.MATH
* FLOOR.MATH
* POWER
* SQRT
* PRODUCT
* RAND
* RANDBETWEEN
* SUMIF
* SUMIFS
* COUNTIF
* COUNTIFS
* AVERAGEIF
* AVERAGEIFS

---

# 📁 Dataset Information

Dataset contains 200 records with the following columns:

| Column Name     |
| --------------- |
| Order_ID        |
| Order_Date      |
| Region          |
| Sales_Rep       |
| Product         |
| Category        |
| Units_Sold      |
| Unit_Price      |
| Sales_Amount    |
| Cost            |
| Profit          |
| Customer_Rating |

---

# 📝 Practice Questions & Solutions

## Basic Math Functions

### Q1. Calculate Total Sales Amount

Formula:

```excel
=SUM(I2:I201)
```

---

### Q2. Calculate Total Profit

```excel
=SUM(K2:K201)
```

---

### Q3. Find Average Sales Amount

```excel
=AVERAGE(I2:I201)
```

---

### Q4. Find Average Customer Rating

```excel
=AVERAGE(L2:L201)
```

---

### Q5. Count Total Orders

```excel
=COUNTA(A2:A201)
```

---

## Maximum & Minimum

### Q6. Find Highest Sales Amount

```excel
=MAX(I2:I201)
```

---

### Q7. Find Lowest Profit

```excel
=MIN(K2:K201)
```

---

### Q8. Find 2nd Highest Sales Amount

```excel
=LARGE(I2:I201,2)
```

---

### Q9. Find 5th Smallest Profit

```excel
=SMALL(K2:K201,5)
```

---

### Q10. Count Available Ratings

```excel
=COUNT(L2:L201)
```

---

## Rounding Functions

### Q11. Round Average Sales to 2 Decimal Places

```excel
=ROUND(AVERAGE(I2:I201),2)
```

---

### Q12. Round Highest Sale to Nearest Thousand

```excel
=CEILING.MATH(MAX(I2:I201),1000)
```

---

### Q13. Round Down Average Rating

```excel
=ROUNDDOWN(AVERAGE(L2:L201),0)
```

---

### Q14. Round Up Average Profit to Nearest Hundred

```excel
=CEILING.MATH(AVERAGE(K2:K201),100)
```

---

## Advanced Math Functions

### Q15. Find Absolute Value of Minimum Profit

```excel
=ABS(MIN(K2:K201))
```

---

### Q16. Check Whether Total Orders Are Even or Odd

```excel
=MOD(COUNTA(A2:A201),2)
```

Result:

* 0 = Even
* 1 = Odd

---

### Q17. Find Square Root of Highest Sales Amount

```excel
=SQRT(MAX(I2:I201))
```

---

### Q18. Find Cube of Average Units Sold

```excel
=POWER(AVERAGE(G2:G201),3)
```

---

## Random Functions

### Q19. Generate Random Bonus Between ₹5000 and ₹20000

```excel
=RANDBETWEEN(5000,20000)
```

---

## Challenge Problem

### Q20. Create Performance Score

Formula:

```excel
=(I2/J2)*L2
```

Copy the formula down for all rows.

### Highest Performance Score

```excel
=MAX(N2:N201)
```

### Average Performance Score

```excel
=AVERAGE(N2:N201)
```

### Top 3 Performance Scores

```excel
=LARGE(N2:N201,1)
=LARGE(N2:N201,2)
=LARGE(N2:N201,3)
```

---

# 🔥 Conditional Formula Practice

## SUMIF

### Total Sales for North Region

```excel
=SUMIF(C2:C201,"North",I2:I201)
```

---

### Total Profit for Electronics Category

```excel
=SUMIF(F2:F201,"Electronics",K2:K201)
```

---

## SUMIFS

### Total Sales for North Region and Laptop Product

```excel
=SUMIFS(I2:I201,C2:C201,"North",E2:E201,"Laptop")
```

---

### Total Profit for South Region and Furniture Category

```excel
=SUMIFS(K2:K201,C2:C201,"South",F2:F201,"Furniture")
```

---

## COUNTIF

### Count Orders from West Region

```excel
=COUNTIF(C2:C201,"West")
```

---

### Count Ratings Greater Than 4

```excel
=COUNTIF(L2:L201,">4")
```

---

## COUNTIFS

### Count Mobile Orders from East Region

```excel
=COUNTIFS(C2:C201,"East",E2:E201,"Mobile")
```

---

### Count Electronics Orders with Rating Greater Than 4

```excel
=COUNTIFS(F2:F201,"Electronics",L2:L201,">4")
```

---

## AVERAGEIF

### Average Sales for North Region

```excel
=AVERAGEIF(C2:C201,"North",I2:I201)
```

---

### Average Profit for Furniture Category

```excel
=AVERAGEIF(F2:F201,"Furniture",K2:K201)
```

---

## AVERAGEIFS

### Average Sales for South Region and Mobile Product

```excel
=AVERAGEIFS(I2:I201,C2:C201,"South",E2:E201,"Mobile")
```

---

### Average Profit for Electronics Category with Rating Greater Than 4

```excel
=AVERAGEIFS(K2:K201,F2:F201,"Electronics",L2:L201,">4")
```

---

# 🎤 Interview Questions

1. Difference between ROUND, ROUNDUP, and ROUNDDOWN.
2. Difference between CEILING and FLOOR.
3. Difference between INT and TRUNC.
4. Difference between SUMIF and SUMIFS.
5. Difference between COUNTIF and COUNTIFS.
6. Difference between AVERAGEIF and AVERAGEIFS.
7. Why does SUMIFS start with sum_range?
8. Explain MOD function with examples.
9. What is the purpose of ABS function?
10. When should CEILING.MATH and FLOOR.MATH be used?
11. What is the difference between COUNT and COUNTA?
12. Explain LARGE and SMALL functions.
13. Difference between RAND and RANDBETWEEN.
14. What is the use of POWER and SQRT?
15. What is the difference between exact and approximate calculations in Excel?

---

## 🚀 Key Learning

Mastering these formulas builds a strong foundation for Excel-based Data Analytics, Reporting, MIS, and Dashboard development.

Happy Learning! 🎉