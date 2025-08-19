## **১. Unnormalized Data (Normalization করা হয়নি)**

| StudentID | StudentName | CourseName | InstructorName |
| --------- | ----------- | ---------- | -------------- |
| 1         | Rahim       | Math       | Mr. Karim      |
| 2         | Karim       | Math       | Mr. Karim      |
| 3         | Salma       | Math       | Mr. Karim      |
| 4         | Jamil       | Physics    | Mrs. Afsana    |
| 5         | Sumon       | Physics    | Mrs. Afsana    |
| 6         | Tania       | Chemistry  | Mr. Hasan      |
| 7         | Rakib       | Chemistry  | Mr. Hasan      |
| 8         | Shila       | Math       | Mr. Karim      |
| 9         | Rafi        | Physics    | Mrs. Afsana    |
| 10        | Sumi        | Math       | Mr. Karim      |

---

### **এখানে সমস্যা**

1. **Redundancy (অতিরিক্ত ডেটা)**

   * *Math* কোর্সের জন্য *Mr. Karim* এর নাম অনেকবার রিপিট হচ্ছে (৫ বার)।
   * Physics এর জন্য *Mrs. Afsana* এর নাম ৩ বার এসেছে।
   * Chemistry এর জন্য *Mr. Hasan* এর নাম ২ বার এসেছে।
   * একই তথ্য অনেকবার রাখলে স্টোরেজ অপচয় হয় এবং ডেটা ম্যানেজ করা কঠিন হয়।

2. **Update Anomaly (আপডেট সমস্যা)**

   * যদি *Mr. Karim* এর নাম ভুল লিখা থাকে এবং ঠিক করতে হয়, তাহলে অনেক রোতে একসাথে ঠিক করতে হবে।
   * যদি এক জায়গায় ভুলে না ঠিক করা হয়, তাহলে ডেটা অসঙ্গত হয়ে যাবে।

3. **Insertion Anomaly (নতুন ডেটা ঢোকাতে সমস্যা)**

   * যদি নতুন একটি কোর্স তৈরি হয় কিন্তু এখনো কোনো ছাত্র ভর্তি হয়নি, তাহলে এই টেবিলে কোর্সের তথ্য রাখা যাবে না, কারণ StudentID ছাড়া নতুন রো ঢোকানো যাবে না।

4. **Deletion Anomaly (ডেটা মুছতে গিয়ে সমস্যা)**

   * যদি Math কোর্সের শেষ ছাত্র Rahim কে মুছে ফেলা হয়, তাহলে *Math কোর্স* আর *Mr. Karim* এর তথ্যও হারিয়ে যাবে।

---

## **২. Normalized Data (Normalization করা হয়েছে)**

**Students Table**

| StudentID | StudentName | CourseID |
| --------- | ----------- | -------- |
| 1         | Rahim       | C1       |
| 2         | Karim       | C1       |
| 3         | Salma       | C1       |
| 4         | Jamil       | C2       |
| 5         | Sumon       | C2       |
| 6         | Tania       | C3       |
| 7         | Rakib       | C3       |
| 8         | Shila       | C1       |
| 9         | Rafi        | C2       |
| 10        | Sumi        | C1       |

**Courses Table**

| CourseID | CourseName | InstructorID |
| -------- | ---------- | ------------ |
| C1       | Math       | I1           |
| C2       | Physics    | I2           |
| C3       | Chemistry  | I3           |

**Instructors Table**

| InstructorID | InstructorName |
| ------------ | -------------- |
| I1           | Mr. Karim      |
| I2           | Mrs. Afsana    |
| I3           | Mr. Hasan      |

---

### **এখানে সমাধান**

1. **Redundancy কমেছে**

   * *Mr. Karim* এর নাম শুধু একবার Instructor টেবিলে আছে।
   * Course ও Instructor এর তথ্য আর রিপিট হচ্ছে না।

2. **Update সহজ**

   * *Mr. Karim* এর নাম আপডেট করতে হলে Instructor টেবিলের এক রো পরিবর্তন করলেই সব জায়গায় আপডেট হয়ে যাবে।

3. **Insertion সহজ**

   * নতুন কোর্স যুক্ত করা যাবে Students টেবিলে কিছু না দিয়েই, শুধু Courses টেবিলে এন্ট্রি করলেই হবে।

4. **Deletion সমস্যা নেই**

   * কোনো ছাত্র ডিলিট করলেও Courses ও Instructors টেবিলে তথ্য থাকবে।

---

### **তুলনা:**

| বিষয়                    | Unnormalized Data        | Normalized Data         |
| ----------------------- | ------------------------ | ----------------------- |
| ডেটা রিপিট              | অনেক বেশি                | প্রায় নেই               |
| আপডেট সমস্যা            | অনেক রোতে একসাথে করতে হয় | শুধু এক জায়গায় করতে হয়  |
| নতুন ডেটা ঢোকানো সমস্যা | আছে                      | নেই                     |
| ডিলিট সমস্যা            | আছে                      | নেই                     |
| স্টোরেজ                 | বেশি লাগে                | কম লাগে                 |
| সম্পর্ক (Relationship)  | স্পষ্ট নয়                | স্পষ্টভাবে টেবিল লিঙ্কড |
