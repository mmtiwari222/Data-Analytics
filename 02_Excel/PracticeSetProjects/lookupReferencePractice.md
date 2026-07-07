# 📝 Practice Questions & Solutions

---

# 🟢 VLOOKUP Practice

### Q1. Find Employee Name using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:B,2,FALSE),"Employee Not Found"))
```

---

### Q2. Find Department using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:C,3,FALSE),"Employee Not Found"))
```

---

### Q3. Find Designation using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:D,4,FALSE),"Employee Not Found"))
```

---

### Q4. Find Manager using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:E,5,FALSE),"Employee Not Found"))
```

---

### Q5. Find Branch using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:F,6,FALSE),"Employee Not Found"))
```

---

### Q6. Find Region using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:G,7,FALSE),"Employee Not Found"))
```

---

### Q7. Find Salary using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:M,13,FALSE),"Employee Not Found"))
```

---

### Q8. Find Bonus using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:N,14,FALSE),"Employee Not Found"))
```

---

### Q9. Find Rating using Employee ID

```excel
=IF(A2="","",IFERROR(VLOOKUP(A2,Employee_Master!A:O,15,FALSE),"Employee Not Found"))
```

---

### Q10. Create a Dynamic Employee Report using VLOOKUP

Retrieve:

- Employee Name
- Department
- Designation
- Manager
- Branch
- Region
- Salary
- Bonus
- Rating

---

# 🟡 XLOOKUP Practice

### Q11. Find Employee Name using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!B:B,"Employee Not Found"))
```

---

### Q12. Find Department using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!C:C,"Employee Not Found"))
```

---

### Q13. Find Salary using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!M:M,"Employee Not Found"))
```

---

### Q14. Find Bonus using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!N:N,"Employee Not Found"))
```

---

### Q15. Find Rating using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!O:O,"Employee Not Found"))
```

---

### Q16. Find Manager using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!E:E,"Employee Not Found"))
```

---

### Q17. Find Branch using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!F:F,"Employee Not Found"))
```

---

### Q18. Find Email using Employee ID

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!S:S,"Employee Not Found"))
```

---

### Q19. Return "Employee Not Found" if Employee ID doesn't exist.

```excel
=IF(A2="","",XLOOKUP(A2,Employee_Master!A:A,Employee_Master!B:B,"Employee Not Found"))
```

---

### Q20. Perform Left Lookup

Find Employee ID using Employee Name.

```excel
=IF(B2="","",XLOOKUP(B2,Employee_Master!B:B,Employee_Master!A:A,"Employee Not Found"))
```

---

# 🟠 INDEX + MATCH Practice

### Q21. Find Salary using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!M:M,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q22. Find Department using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!C:C,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q23. Find Manager using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!E:E,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q24. Find Branch using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!F:F,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q25. Find Region using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!G:G,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q26. Find Salary using Employee ID (INDEX + MATCH)

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!M:M,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q27. Find Bonus using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!N:N,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q28. Find Rating using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!O:O,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q29. Find Email using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!S:S,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

### Q30. Find Phone Number using Employee ID

```excel
=IF(A2="","",IFERROR(INDEX(Employee_Master!T:T,MATCH(A2,Employee_Master!A:A,0)),"Employee Not Found"))
```

---

# 🔵 Other Lookup & Reference Functions

### Q31. Return Employee Name using LOOKUP

```excel
=LOOKUP(A2,Employee_Master!A:A,Employee_Master!B:B)
```

---

### Q32. Return Salary using LOOKUP

```excel
=LOOKUP(A2,Employee_Master!A:A,Employee_Master!M:M)
```

---

### Q33. Retrieve January Sales using HLOOKUP

```excel
=HLOOKUP("Jan",A1:M2,2,FALSE)
```

---

### Q34. Retrieve March Sales using HLOOKUP

```excel
=HLOOKUP("Mar",A1:M2,2,FALSE)
```

---

### Q35. Convert Vertical Employee List into Horizontal List

```excel
=TRANSPOSE(A2:A11)
```

---

### Q36. Convert Horizontal Product List into Vertical List

```excel
=TRANSPOSE(A1:J1)
```

---

### Q37. Find Current Row Number

```excel
=ROW(A2)
```

---

### Q38. Count Total Rows

```excel
=ROWS(A2:A251)
```

---

### Q39. Find Current Column Number

```excel
=COLUMN(M1)
```

---

### Q40. Count Total Columns

```excel
=COLUMNS(A:T)
```

---

# 🔴 Challenge Questions

### Q41.
Create an Employee Search System using VLOOKUP.

---

### Q42.
Create an Employee Search System using XLOOKUP.

---

### Q43.
Create an Employee Search System using INDEX + MATCH.

---

### Q44.
Compare VLOOKUP and XLOOKUP outputs.

---

### Q45.
Compare VLOOKUP and INDEX + MATCH outputs.

---

### Q46.
Retrieve all employee details using Employee ID.

---

### Q47.
Display "Employee Not Found" when ID doesn't exist.

---

### Q48.
Perform a Left Lookup using XLOOKUP.

---

### Q49.
Retrieve Salary, Bonus and Rating together.

---

### Q50.
Build a Dynamic Employee Dashboard where entering an Employee ID automatically displays all employee information.
