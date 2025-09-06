## 🗂 Dataset: `ExamResults`

| StudentID | Name  | Gender | Subject   | CorrectAns | IncorrectAns | EachQMark | NegMark | Price | Quantity | ExamDate   |
| --------- | ----- | ------ | --------- | ---------- | ------------ | --------- | ------- | ----- | -------- | ---------- |
| 1         | Rahim | Male   | Math      | 18         | 2            | 5         | 1       | 100   | 2        | 2025-02-10 |
| 2         | Karim | Male   | Physics   | 15         | 5            | 4         | 1       | 80    | 3        | 2025-02-12 |
| 3         | Salma | Female | Chemistry | 20         | 0            | 5         | 1       | 120   | 1        | 2025-02-15 |
| 4         | Jamil | Male   | Math      | 10         | 10           | 5         | 1       | 90    | 4        | 2025-02-18 |
| 5         | Tania | Female | Physics   | 17         | 3            | 4         | 1       | 150   | 2        | 2025-02-20 |
| 6         | Rakib | Male   | Chemistry | 12         | 8            | 5         | 2       | 200   | 1        | 2025-02-22 |
| 7         | Shila | Female | Biology   | 19         | 1            | 5         | 1       | 50    | 5        | 2025-02-23 |
| 8         | Rafi  | Male   | Math      | 8          | 12           | 5         | 1       | 40    | 10       | 2025-02-24 |

---
## 📋 **Questions Based on Dataset**

### 🔢 **Expressions & Calculations**

1. Calculate the **Actual Mark** for each student using the formula:
   `(CorrectAns * EachQMark) - (IncorrectAns * NegMark)`
2. Calculate the **Total Price** for each student using:
   `(Price * Quantity)`
3. Display student name, actual mark, and a column showing **PASS** if actual mark ≥ 50, otherwise **FAIL**.

---

### 🔍 **Subqueries**

4. Find the student(s) who achieved the **highest actual mark**.
5. Find all students whose **actual mark is above the class average**.
6. Find the student(s) who scored the **lowest actual mark**.

---

### 🔤 **String Functions**

7. Display each student's name in **UPPERCASE** and subject in **lowercase**.
8. Show only the **first 3 characters** of each student's name.
9. Find the **length of each student's name**.
10. Concatenate the **Name and Subject** columns in a single column as `FullInfo`.

---

### 📅 **Date/Time Functions**

11. Display the **current date and time**.
12. For each student, extract the **Year, Month, and Day** from `ExamDate`.
13. Add **7 days** to each student's `ExamDate` and display as `NextExamDate`.

---

### 🧮 **Math Functions**

14. Round each student's **Actual Mark** to 0 decimal places.
15. Show the **Ceil** and **Floor** values of `(CorrectAns * EachQMark) / 3`.
16. Display the **absolute value** of `NegMark` for each student.



## ✅ কোন কোন কলামে কোন কাজ করবে

| Topic                          | Column(s) to Use                                                          |
| ------------------------------ | ------------------------------------------------------------------------- |
| **Expressions & Calculations** | `CorrectAns`, `IncorrectAns`, `EachQMark`, `NegMark`, `Price`, `Quantity` |
| **Subquery**                   | `CorrectAns`, `IncorrectAns`, `Name`, `Subject`                           |
| **String Functions**           | `Name`, `Subject`                                                         |
| **Date/Time Functions**        | `ExamDate`                                                                |
| **Math Functions**             | Calculated Mark বা Total Price                                            |

---

## 🧮 **Expressions & Calculations Examples**

### Q1️⃣: Actual Mark হিসাব করো

**Formula:** `(CorrectAns * EachQMark) - (IncorrectAns * NegMark)`

```sql
SELECT 
  Name,
  Subject,
  (CorrectAns * EachQMark) - (IncorrectAns * NegMark) AS ActualMark
FROM ExamResults;
```

**Expected Output (কিছু দেখানো):**

| Name  | Subject   | ActualMark |
| ----- | --------- | ---------- |
| Rahim | Math      | 86         |
| Karim | Physics   | 55         |
| Salma | Chemistry | 100        |

---

### Q2️⃣: Price × Quantity দিয়ে Total বের করো

```sql
SELECT 
  Name,
  Price,
  Quantity,
  (Price * Quantity) AS Total
FROM ExamResults;
```

**Expected Output:**

| Name  | Price | Quantity | Total |
| ----- | ----- | -------- | ----- |
| Rahim | 100   | 2        | 200   |
| Karim | 80    | 3        | 240   |
| Rafi  | 40    | 10       | 400   |

---

### Q3️⃣: Pass/Fail দেখাও (৫০ এর বেশি হলে Pass, নইলে Fail)

```sql
SELECT 
  Name,
  (CorrectAns * EachQMark) - (IncorrectAns * NegMark) AS ActualMark,
  CASE 
    WHEN (CorrectAns * EachQMark) - (IncorrectAns * NegMark) >= 50 THEN 'PASS'
    ELSE 'FAIL'
  END AS Result
FROM ExamResults;
```

---

## 🔍 **Subquery Examples**

### Q1️⃣: Highest Mark কে পেয়েছে?

```sql
SELECT Name, Subject, (CorrectAns * EachQMark) - (IncorrectAns * NegMark) AS ActualMark
FROM ExamResults
WHERE (CorrectAns * EachQMark) - (IncorrectAns * NegMark) = (
  SELECT MAX((CorrectAns * EachQMark) - (IncorrectAns * NegMark)) 
  FROM ExamResults
);
```

**Output:** Salma | Chemistry | 100

---

### Q2️⃣: যারা গড় Actual Mark-এর উপরে আছে তাদের নাম

```sql
SELECT Name, (CorrectAns * EachQMark) - (IncorrectAns * NegMark) AS ActualMark
FROM ExamResults
WHERE (CorrectAns * EachQMark) - (IncorrectAns * NegMark) > (
  SELECT AVG((CorrectAns * EachQMark) - (IncorrectAns * NegMark))
  FROM ExamResults
);
```

---

### Q3️⃣: সর্বনিম্ন স্কোর কার?

```sql
SELECT Name, (CorrectAns * EachQMark) - (IncorrectAns * NegMark) AS ActualMark
FROM ExamResults
WHERE (CorrectAns * EachQMark) - (IncorrectAns * NegMark) = (
  SELECT MIN((CorrectAns * EachQMark) - (IncorrectAns * NegMark)) FROM ExamResults
);
```

---

## 🔤 **String Functions Examples**

```sql
-- UPPER() & LOWER()
SELECT Name, UPPER(Name) AS UpperName, LOWER(Subject) AS LowerSubject FROM ExamResults;

-- SUBSTRING() -> নামের প্রথম ৩ অক্ষর
SELECT Name, SUBSTRING(Name, 1, 3) AS ShortName FROM ExamResults;

-- LENGTH()
SELECT Name, LENGTH(Name) AS NameLength FROM ExamResults;

-- CONCAT()
SELECT CONCAT(Name, ' - ', Subject) AS FullInfo FROM ExamResults;
```

---

## 📅 **Date/Time Functions Examples**

```sql
-- NOW()
SELECT NOW() AS CurrentDateTime;

-- YEAR(), MONTH(), DAY()
SELECT Name, YEAR(ExamDate) AS ExamYear, MONTH(ExamDate) AS ExamMonth, DAY(ExamDate) AS ExamDay
FROM ExamResults;

-- DATEADD() -> ExamDate এর সাথে ৭ দিন যোগ করো
SELECT Name, DATE_ADD(ExamDate, INTERVAL 7 DAY) AS NextExamDate
FROM ExamResults;
```

---

## 🔢 **Math Functions Examples**

```sql
-- ROUND Actual Mark
SELECT Name, ROUND((CorrectAns * EachQMark) - (IncorrectAns * NegMark), 0) AS RoundedMark
FROM ExamResults;

-- CEIL & FLOOR
SELECT Name,
  CEIL((CorrectAns * EachQMark) / 3) AS CeilValue,
  FLOOR((CorrectAns * EachQMark) / 3) AS FloorValue
FROM ExamResults;

-- ABS() -> Negative Mark কে Positive করে দেখানো
SELECT Name, ABS(NegMark) AS PositiveNegMark FROM ExamResults;
```

---

✅ **এই Dataset & Queries দিয়ে তুমি সবকিছু দেখাতে পারবে:**

* Expressions & Calculations
* Subquery
* String Functions
* Date/Time Functions
* Math Functions
