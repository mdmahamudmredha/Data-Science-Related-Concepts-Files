#  Demo Table: `Students`

| id | name  | class | marks | gender |
| -- | ----- | ----- | ----- | ------ |
| 1  | Rahim | 6     | 75    | Male   |
| 2  | Karim | 6     | 85    | Male   |
| 3  | Salma | 7     | 60    | Female |
| 4  | Tania | 7     | 90    | Female |
| 5  | Rakib | 8     | 40    | Male   |
| 6  | Shila | 8     | 70    | Female |
| 7  | Sumon | 6     | 55    | Male   |
| 8  | Rafi  | 7     | 95    | Male   |
| 9  | Jamil | 8     | 80    | Male   |
| 10 | Sumi  | 6     | 65    | Female |

 এখানে ১০ জন ছাত্র/ছাত্রী আছে। এখন এই ডেটা ব্যবহার করে আমরা প্রতিটি বিষয় ব্যাখ্যা করব।

---

# 1️⃣ **Basic Column Selection**

### (a) সব কলাম আনা

```sql
SELECT * FROM Students;
```

 আউটপুট → পুরো টেবিল (১০ রো)।

### (b) নির্দিষ্ট কলাম আনা

```sql
SELECT name, marks FROM Students;
```

 আউটপুট → শুধু `name` আর `marks` কলাম দেখাবে।

| name  | marks |
| ----- | ----- |
| Rahim | 75    |
| Karim | 85    |
| Salma | 60    |
| ...   | ...   |

### (c) Alias (নতুন নাম দেওয়া)

```sql
SELECT name AS StudentName, marks AS Score FROM Students;
```

 আউটপুট → কলামের নতুন নাম `StudentName` আর `Score`।

---

# 2️⃣ **DISTINCT**

### (a) ইউনিক ক্লাস লিস্ট

```sql
SELECT DISTINCT class FROM Students;
```

 আউটপুট → {6, 7, 8}
 ডুপ্লিকেট বাদ দিয়ে শুধু ইউনিক ক্লাস।

### (b) ইউনিক জেন্ডার লিস্ট

```sql
SELECT DISTINCT gender FROM Students;
```

 আউটপুট → {Male, Female}

---

# 3️⃣ **Aggregate Functions**

 Aggregate মানে হলো **সারসংক্ষেপ / summary বের করা**।

### (a) COUNT → মোট ছাত্র সংখ্যা

```sql
SELECT COUNT(*) AS TotalStudents FROM Students;
```

 আউটপুট → 10

### (b) SUM → মোট মার্কস

```sql
SELECT SUM(marks) AS TotalMarks FROM Students;
```

 আউটপুট → 715

### (c) AVG → গড় মার্কস

```sql
SELECT AVG(marks) AS AverageMarks FROM Students;
```

 আউটপুট → 71.5

### (d) MIN → সবচেয়ে কম মার্কস

```sql
SELECT MIN(marks) AS LowestMark FROM Students;
```

 আউটপুট → 40

### (e) MAX → সবচেয়ে বেশি মার্কস

```sql
SELECT MAX(marks) AS HighestMark FROM Students;
```

 আউটপুট → 95

---

# 4️⃣ **DISTINCT + Aggregate একসাথে**

### (a) কত ইউনিক ক্লাস আছে?

```sql
SELECT COUNT(DISTINCT class) AS UniqueClasses FROM Students;
```

 আউটপুট → 3

### (b) কত ইউনিক জেন্ডার আছে?

```sql
SELECT COUNT(DISTINCT gender) AS UniqueGenders FROM Students;
```

 আউটপুট → 2

---

#  সারাংশ

* **Basic Column Selection** → ডেটা থেকে কোন কোন কলাম দেখতে চাই তা বেছে নেওয়া যায়।
* **DISTINCT** → ডুপ্লিকেট বাদ দিয়ে ইউনিক ভ্যালু দেখা যায়।
* **Aggregate Functions** → ডেটার সারাংশ বের করা যায় (মোট সংখ্যা, যোগফল, গড়, সবচেয়ে ছোট-বড়)।
