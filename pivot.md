### **“Pivot Table এবং Unpivot: ডেটা অ্যানালাইসিসের লুকানো শক্তি”**

---

## Pivot Table নিয়ে A to Z ব্যাখ্যা

### Pivot Table কী?

Pivot Table হলো একটি ডেটা সামারি টুল যা বড় টেবিল বা ডেটাসেট থেকে দ্রুত এবং সহজে **সংক্ষেপিত তথ্য** বের করতে সাহায্য করে। আমরা যখন হাজার হাজার রো-এর ডেটা নিয়ে কাজ করি, তখন এক্সেলে বা SQL-এ Pivot Table ব্যবহার করে ডেটাকে বিভিন্ন দিক থেকে সাজানো, ফিল্টার করা, যোগফল বের করা, গড় বের করা বা ক্যাটেগরি অনুযায়ী ডেটা ভাগ করা সম্ভব হয়।

এক কথায়, Pivot Table হলো ডেটাকে **“Raw থেকে Insight”**-এ রূপান্তর করার একটি শর্টকাট।

---

### Pivot Table দেখতে কেমন?

Pivot Table মূলত একটি সারসংক্ষেপ টেবিল।

* কলামে থাকে কিছু ভ্যারিয়েবল
* রো-তে থাকে অন্য ভ্যারিয়েবল
* আর ভেতরে (Values এর ঘরে) থাকে সংখ্যাগত হিসাব যেমন **Sum, Count, Average, Min, Max** ইত্যাদি।

উদাহরণ:
ধরা যাক, আমাদের কাছে বিক্রয়ের ডেটা আছে যেখানে Product, Region, Sales Amount আছে।

**Raw Data:**

| Product | Region     | Sales |
| ------- | ---------- | ----- |
| Laptop  | Dhaka      | 50000 |
| Laptop  | Chattogram | 30000 |
| Mobile  | Dhaka      | 20000 |
| Mobile  | Chattogram | 15000 |

**Pivot Table (Sum of Sales by Product and Region):**

| Product   | Dhaka | Chattogram | Grand Total |
| --------- | ----- | ---------- | ----------- |
| Laptop    | 50000 | 30000      | 80000       |
| Mobile    | 20000 | 15000      | 35000       |
| **Total** | 70000 | 45000      | 115000      |

এখানে দেখা যাচ্ছে, Pivot Table কাঁচা ডেটাকে সুন্দরভাবে গুছিয়ে সহজবোধ্য করেছে।

---

### কেন Pivot Table ব্যবহার করি?

1. **বড় ডেটা থেকে ইনসাইট বের করার জন্য**
2. **অটোমেটিক সারাংশ বানাতে** (ম্যানুয়ালি ফিল্টার/গ্রুপ না করে)
3. **ডেটা বিশ্লেষণকে দ্রুত করার জন্য**
4. **নন-টেকনিক্যাল ইউজারদের জন্যও সহজবোধ্য**

---

### কোন ক্ষেত্রে Pivot Table ব্যবহার করা হয়?

* **বিক্রয় বিশ্লেষণ:** কোন প্রোডাক্ট কত অঞ্চলে কত বিক্রি হলো
* **ফাইন্যান্স:** মাসভিত্তিক খরচ বা আয়ের সারাংশ
* **অপারেশনস:** ডিপার্টমেন্টভিত্তিক খরচ বা কর্মচারী সংখ্যা
* **শিক্ষা:** ছাত্র-ছাত্রীদের রেজাল্টে কোন বিষয় থেকে গড় বা টপ পারফর্মেন্স
* **সার্ভে ডেটা:** লিঙ্গ, বয়স, এলাকা ইত্যাদির উপর ভিত্তি করে উত্তর গোষ্ঠীবদ্ধ করা

---

### কোন ডেটা সোর্স থেকে Pivot Table বানানো যায়?

Pivot Table মূলত **ট্যাবুলার ফর্ম্যাটে থাকা ডেটা** থেকে তৈরি হয়।
যেমন:

* **Excel** শীট
* **CSV** ফাইল
* **SQL ডেটাবেস** (Query এর আউটপুট)
* **Google Sheets**
* ERP বা CRM সফটওয়্যার থেকে এক্সপোর্ট করা ডেটা

---

### Pivot Table এর সুবিধা

1. **দ্রুত সারাংশ** তৈরি করা যায়
2. **ডাইনামিক** – মানে সহজে ফিল্টার, গ্রুপ, ড্রিল-ডাউন করা যায়
3. **ভিজ্যুয়ালাইজেশন ফ্রেন্ডলি** – Pivot Table থেকে চার্ট বানানো যায়
4. **নমনীয়তা** – একই ডেটা থেকে ভিন্ন দৃষ্টিকোণ তৈরি করা সম্ভব
5. **ডুপ্লিকেট কাজ কমানো** – একবার সেট করলে বারবার রিপোর্ট বানাতে ঝামেলা হয় না

---

## Unpivot (বা Reverse Pivot)

### Unpivot কী?

Unpivot হলো Pivot-এর উল্টো প্রক্রিয়া। Pivot Table যেখানে ডেটাকে সারাংশ বানায়, Unpivot সেখানে সারাংশ টেবিলকে আবার **কাঁচা ডেটা (Row format)**-এ ভেঙে ফেলে।

---

### Unpivot করলে কেমন দেখায়?

উপরের Pivot Table-টিকে যদি Unpivot করা হয়, তবে আবার কাঁচা ডেটা ফরম্যাটে ফিরে আসবে:

**Pivot Table (সংক্ষেপিত):**

| Product | Dhaka | Chattogram |
| ------- | ----- | ---------- |
| Laptop  | 50000 | 30000      |
| Mobile  | 20000 | 15000      |

**Unpivot করার পর:**

| Product | Region     | Sales |
| ------- | ---------- | ----- |
| Laptop  | Dhaka      | 50000 |
| Laptop  | Chattogram | 30000 |
| Mobile  | Dhaka      | 20000 |
| Mobile  | Chattogram | 15000 |

---

### কেন Unpivot দরকার হয়?

1. **Data Cleaning এর জন্য** – অনেক সময় বিশ্লেষণের আগে ডেটাকে Row format-এ আনা লাগে
2. **ETL Process (Extract, Transform, Load)-এ** – ডেটাবেস বা পাইথন/Pandas ব্যবহার করার জন্য টেবিলকে কাঁচা ফরম্যাটে রূপান্তর করা দরকার হয়
3. **Machine Learning/BI Tools (যেমন Power BI, Tableau)** – এগুলো সাধারণত ট্যাবুলার (row-based) ফরম্যাটে ডেটা বুঝে
4. **Flexibility** – Unpivot করলে আবার নতুন Pivot বানানো যায় অন্য ভ্যারিয়েবল দিয়ে

---

## সারমর্ম

* Pivot Table হলো ডেটা সামারি করার টুল, যা বড় ডেটাকে ছোট, পরিষ্কার এবং ইনসাইটফুল করে তোলে।
* Unpivot হলো ডেটাকে আবার কাঁচা রূপে ফিরিয়ে আনা।
* Pivot ডেটা বিশ্লেষণ ও রিপোর্টিংয়ের জন্য অপরিহার্য, আর Unpivot ডেটা প্রিপ্রসেসিং ও ইন্টিগ্রেশনের জন্য গুরুত্বপূর্ণ।

এভাবে Pivot এবং Unpivot দুটো একসাথে কাজ করে আমাদের ডেটাকে একদিকে **বুঝতে সহজ করে**, আরেকদিকে **প্রসেসিং-এর জন্য প্রস্তুত করে**।

---

# 1. **Excel এ Pivot এবং Unpivot**

### Pivot Table বানানোর প্রক্রিয়া

ধরা যাক, আমাদের ডেটা:

| Product | Region     | Sales |
| ------- | ---------- | ----- |
| Laptop  | Dhaka      | 50000 |
| Laptop  | Chattogram | 30000 |
| Mobile  | Dhaka      | 20000 |
| Mobile  | Chattogram | 15000 |

**Step:**

1. Excel-এ ডেটা সিলেক্ট করো
2. উপরে **Insert > PivotTable** এ যাও
3. New Worksheet/Existing Worksheet বেছে নাও
4. Fields থেকে:

   * `Product` → Rows এ দাও
   * `Region` → Columns এ দাও
   * `Sales` → Values এ দাও (Sum of Sales)

**Resulting Pivot Table:**

| Product   | Dhaka | Chattogram | Grand Total |
| --------- | ----- | ---------- | ----------- |
| Laptop    | 50000 | 30000      | 80000       |
| Mobile    | 20000 | 15000      | 35000       |
| **Total** | 70000 | 45000      | 115000      |

---

### Unpivot করার প্রক্রিয়া

Excel-এ Unpivot করার সরাসরি ফিচার নেই, তবে **Power Query Editor** ব্যবহার করতে হয়।

**Step:**

1. ডেটা টেবিলটা সিলেক্ট করে **Data > Get & Transform > From Table/Range** এ যাও
2. Power Query উইন্ডো ওপেন হবে
3. `Dhaka` আর `Chattogram` কলামগুলো সিলেক্ট করো
4. Right Click → **Unpivot Columns**
5. Close & Load করো

**Result:**

| Product | Region     | Sales |
| ------- | ---------- | ----- |
| Laptop  | Dhaka      | 50000 |
| Laptop  | Chattogram | 30000 |
| Mobile  | Dhaka      | 20000 |
| Mobile  | Chattogram | 15000 |

---

# 2. **SQL এ Pivot এবং Unpivot**

ধরা যাক, আমাদের টেবিলের নাম `SalesData`।

### Pivot (SQL Server এর উদাহরণ)

```sql
SELECT 
    Product,
    [Dhaka] AS Dhaka_Sales,
    [Chattogram] AS Chattogram_Sales
FROM
(
    SELECT Product, Region, Sales
    FROM SalesData
) AS SourceTable
PIVOT
(
    SUM(Sales)
    FOR Region IN ([Dhaka], [Chattogram])
) AS PivotTable;
```

**Output:**

| Product | Dhaka\_Sales | Chattogram\_Sales |
| ------- | ------------ | ----------------- |
| Laptop  | 50000        | 30000             |
| Mobile  | 20000        | 15000             |

---

### Unpivot (SQL Server এর উদাহরণ)

```sql
SELECT 
    Product,
    Region,
    Sales
FROM
(
    SELECT Product, [Dhaka], [Chattogram]
    FROM PivotTableExample
) AS SourceTable
UNPIVOT
(
    Sales FOR Region IN ([Dhaka], [Chattogram])
) AS UnpivotTable;
```

**Output:**

| Product | Region     | Sales |
| ------- | ---------- | ----- |
| Laptop  | Dhaka      | 50000 |
| Laptop  | Chattogram | 30000 |
| Mobile  | Dhaka      | 20000 |
| Mobile  | Chattogram | 15000 |

---

# 3. **Python (Pandas) এ Pivot এবং Unpivot**

```python
import pandas as pd

# Raw data
data = {
    'Product': ['Laptop', 'Laptop', 'Mobile', 'Mobile'],
    'Region': ['Dhaka', 'Chattogram', 'Dhaka', 'Chattogram'],
    'Sales': [50000, 30000, 20000, 15000]
}

df = pd.DataFrame(data)
print("Original Data:\n", df)
```

### Pivot Table (pandas `pivot_table`)

```python
pivot_df = df.pivot_table(values='Sales', index='Product', columns='Region', aggfunc='sum')
print("\nPivot Table:\n", pivot_df)
```

**Output:**

| Region | Chattogram | Dhaka |
| ------ | ---------- | ----- |
| Laptop | 30000      | 50000 |
| Mobile | 15000      | 20000 |

---

### Unpivot (pandas `melt`)

```python
unpivot_df = pivot_df.reset_index().melt(id_vars='Product', value_name='Sales', var_name='Region')
print("\nUnpivoted Data:\n", unpivot_df)
```

**Output:**

| Product | Region     | Sales |
| ------- | ---------- | ----- |
| Laptop  | Chattogram | 30000 |
| Laptop  | Dhaka      | 50000 |
| Mobile  | Chattogram | 15000 |
| Mobile  | Dhaka      | 20000 |

---

# 4. **Power BI তে Pivot এবং Unpivot**

### Pivot Table (Power BI তে আসলে Visual হিসেবে হয়)

1. ডেটা লোড করো Power BI Desktop এ
2. **Table Visual** বা **Matrix Visual** ব্যবহার করো
3. Rows এ `Product`, Columns এ `Region`, Values এ `Sales` রাখো
4. এটা Excel-এর মতো Pivot এর মতো আচরণ করবে

**Result Matrix (Pivot):**

| Product | Dhaka | Chattogram |
| ------- | ----- | ---------- |
| Laptop  | 50000 | 30000      |
| Mobile  | 20000 | 15000      |

---

### Unpivot (Power Query Editor)

1. Power BI-তে **Transform Data** এ যাও
2. `Dhaka`, `Chattogram` এর মতো কলামগুলো সিলেক্ট করো
3. Right Click → **Unpivot Columns**
4. Apply Changes

**Result:**

| Product | Region     | Sales |
| ------- | ---------- | ----- |
| Laptop  | Dhaka      | 50000 |
| Laptop  | Chattogram | 30000 |
| Mobile  | Dhaka      | 20000 |
| Mobile  | Chattogram | 15000 |

---

## সারমর্ম

* **Excel** → Insert > PivotTable / Power Query দিয়ে Unpivot
* **SQL** → PIVOT / UNPIVOT ক্লজ
* **Python (Pandas)** → `pivot_table()` এবং `melt()`
* **Power BI** → Matrix visual দিয়ে Pivot / Power Query Editor দিয়ে Unpivot

Pivot ব্যবহার হয় সারাংশ তৈরিতে, আর Unpivot ব্যবহার হয় ডেটা প্রিপ্রসেসিং বা অ্যানালাইসিসের জন্য সঠিক ফরম্যাটে আনতে।
