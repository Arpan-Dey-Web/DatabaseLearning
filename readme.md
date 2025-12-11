## ******************************************** Database Model Design Module ********************************************

### What is a Database?

A **database** is a structured collection of related data, organized for efficient storage, retrieval, and management.

### DBMS Full Meaning

**DBMS:** Database Management System

### What is a Key?

A **key** in a relational database is a field or a combination of fields that uniquely identifies a record in a table.

---

## Most Used Keys

1. **Super Key**
2. **Candidate Key**
3. **Primary Key**
4. **Alternative Key**
5. **Composite Key**
6. **Foreign Key**

---

## Super Key (সুপার কি)

ডেটাবেজ টেবিলের প্রতিটি রেকর্ডকে ইউনিকভাবে শনাক্ত করতে পারে এমন যেকোনো কলাম বা কলামের গ্রুপকে **Super Key** বলা হয়।

সহজভাবে:
**Super Key** মানে এমন একটি অ্যাট্রিবিউট সেট যা দিয়ে টেবিলের প্রতিটি রো কে আলাদা করে চেনা যায়।

| id | email | phone | name |
| -- | ----- | ----- | ---- |

এই টেবিলে নিচের সবগুলোই Super Key:

* id
* email
* phone
* id + email
* email + phone
* id + phone + name

### মনে রাখার বিষয়

✔ Super Key হলো সবচেয়ে বড় গ্রুপ: প্রয়োজনীয় অ্যাট্রিবিউটের সাথে অতিরিক্ত অ্যাট্রিবিউটও থাকতে পারে।
✔ Super Key এর ভেতর থেকেই পরে **Candidate Key** বের করা হয় (যেখানে অপ্রয়োজনীয় অ্যাট্রিবিউট থাকে না)।

---

## Set (সেট)

একটি **Set** হলো ভিন্ন ভিন্ন (unique) উপাদানের একটি সংগ্রহ। গাণিতিকভাবে Set সাধারণত কৌঁচি বন্ধনী `{ }` দিয়ে লেখা হয়।

### উদাহরণ

`A = {1, 2, 3, 4}`
এখানে A হলো একটি সেট, যেখানে 1, 2, 3, 4 তার উপাদান।

### বৈশিষ্ট্য

✔ উপাদানগুলো ইউনিক হয় (ডুপ্লিকেট থাকে না)
✔ উপাদানের ক্রম গুরুত্বপূর্ণ নয়
উদাহরণ: `{1,2,3}` এবং `{3,2,1}` একই Set

---

## Subset (সাবসেট)

একটি Set B কে Set A-এর **Subset** বলা হয়, যদি B-এর সব উপাদানই A-এর মধ্যে থাকে।

### উদাহরণ

`A = {1, 2, 3, 4}`

তাহলে:

* `B = {1, 2}` হলো Subset
* `C = {2, 3, 4}` হলো Subset
* `D = {1, 4}` হলো Subset
* `E = {1, 2, 3, 4}` (পূর্ণ সেট) সেটিও Subset

### গুরুত্বপূর্ণ

✔ খালি সেট `{ }` সব সেটের Subset
✔ একটি সেট নিজেও নিজের Subset

### সম্পূর্ণ Subset তালিকা

A = `{1, 2, 3}`

**SUBSET of A:**
`{}`, `{1}`, `{2}`, `{3}`, `{1,2}`, `{2,3}`, `{1,3}`, `{1,2,3}`

**PROPER SUBSET of A:**
`{}`, `{1}`, `{2}`, `{3}`, `{1,2}`, `{2,3}`, `{1,3}`

---

## Candidate Key (ক্যান্ডিডেট কি)

Candidate Key হলো এমন ন্যূনতম অ্যাট্রিবিউট সেট যা দিয়ে একটি টেবিলের প্রতিটি রোকে ইউনিকভাবে শনাক্ত করা যায়।
অর্থাৎ, এটি একটি Super Key, কিন্তু এর ভিতরে অপ্রয়োজনীয় কোনো অ্যাট্রিবিউট নেই।

এক কথায়:
**Candidate Key = Minimal Super Key**

### উদাহরণ

ধরো একটি students টেবিল:

| student_id | email | phone | name |
| ---------- | ----- | ----- | ---- |

নিম্নলিখিতগুলো রোকে ইউনিকভাবে শনাক্ত করতে পারে:

* student_id
* email
* phone
* student_id + email
* email + phone
* student_id + phone + name

Candidate Keys হবে শুধুমাত্র ন্যূনতমগুলো:

* student_id
* email
* phone

### বৈশিষ্ট্য

* এটি একটি মিনিমাল Super Key
* এক টেবিলে একাধিক Candidate Key থাকতে পারে
* এর মধ্য থেকে পরে Primary Key নির্বাচন করা হয়
* Candidate Key-এর কোনো অ্যাট্রিবিউট বাদ দিলে তা আর ইউনিক থাকে না

### ছোট উদাহরণ

Table: EMPLOYEE
Columns: emp_id, national_id, email

Candidate Keys:

1. emp_id
2. national_id
3. email

---

## Primary Key (প্রাইমারি কি)

Primary Key হলো একটি বিশেষ Candidate Key যা ডেটাবেজ টেবিলের প্রতিটি রোকে ইউনিকভাবে শনাক্ত করার জন্য নির্বাচিত হয়। এটি টেবিলের মেইন আইডেন্টিফায়ার।

### মূল বৈশিষ্ট্য

* প্রতিটি রোতে Primary Key এর মান ইউনিক হতে হবে
* Primary Key কখনো NULL হতে পারে না
* এক টেবিলে মাত্র একটি Primary Key থাকে
* Primary Key সাধারণত সবচেয়ে স্থিতিশীল এবং সর্বোত্তম শনাক্তকারী হিসেবে নির্বাচন করা হয়

উদাহরণ:

| id | email | phone | name |
| -- | ----- | ----- | ---- |

Candidate Keys:

* id
* email
* phone

এগুলোর মধ্যে থেকে টেবিলের প্রধান শনাক্তকারী হিসেবে সাধারণত **id** নির্বাচন করা হয়।

| টার্ম         | ব্যাখ্যা                                                     |
| ------------- | ------------------------------------------------------------ |
| Candidate Key | যেকোনো কলাম বা কলাম গ্রুপ যা রোকে ইউনিকভাবে শনাক্ত করতে পারে |
| Primary Key   | Candidate Key-গুলোর মধ্য থেকে নির্বাচিত মূল ইউনিক শনাক্তকারী |

---

## Alternative Key (অল্টারনেটিভ কি)

একটি টেবিলে যতগুলো Candidate Key থাকে, তার মধ্য থেকে Primary Key নির্বাচন করার পর বাকি Candidate Key-গুলোকে Alternative Key বলা হয়।

Primary Key ছাড়া অন্যান্য সব Candidate Key = Alternative Key

### উদাহরণ

| user_id | email | phone | name |
| ------- | ----- | ----- | ---- |

Candidate Keys:

* user_id
* email
* phone

Primary Key: user_id

Alternative Keys:

* email
* phone

### বৈশিষ্ট্য

* Alternative Key সর্বদাই একটি Candidate Key
* Alternative Key কখনোই Primary Key নয়
* প্রতিটি Alternative Key রোকে ইউনিকভাবে শনাক্ত করতে পারে
* এক টেবিলে Alternative Key একাধিক থাকতে পারে

---

## Composite Key (কম্পোজিট কি)

Composite Key হলো এমন একটি Key যা একটি কলাম দিয়ে ইউনিক হয় না, বরং একাধিক কলাম মিলিয়ে রোকে ইউনিকভাবে শনাক্ত করে।

Composite Key = একাধিক অ্যাট্রিবিউটের সমন্বয় যা ইউনিক শনাক্তকারী হিসেবে কাজ করে।

### কেন Composite Key ব্যবহার করা হয়

* যখন টেবিলের কোন একক কলামে ইউনিক ভ্যালু নেই
* যখন দুটির বেশি কলাম একসাথে মিললে রো ইউনিক হয়
* Many to Many সম্পর্ক match করতে (junction table)

### উদাহরণ

Table: ENROLLMENTS
Columns: student_id, course_id, enrolled_date

Composite Key:

* (student_id, course_id)

Reason:
A student can enroll in multiple courses, and each course has multiple students. But the combination of student_id and course_id সর্বদাই ইউনিক।

---

## Simple Key (সিম্পল কি)

Simple Key হলো এমন Candidate Key বা Primary Key যা একটি মাত্র কলাম দিয়ে গঠিত।
অর্থাৎ, single attribute দিয়েই রোকে ইউনিকভাবে শনাক্ত করা যায়।

### উদাহরণ

| emp_id | email | phone | name |
| ------ | ----- | ----- | ---- |

Simple Keys:

* emp_id
* email
* phone

প্রতিটি একাই একটি রো ইউনিক করতে পারে, তাই এগুলো Simple Key।

Primary Key: emp_id (Simple Key)
Alternative Keys: email, phone (এগুলিও Simple Key)

### বৈশিষ্ট্য

* Simple Key সর্বদাই single attribute
* এটি Candidate Key অথবা Primary Key হতে পারে
* এক টেবিলে একাধিক Simple Key থাকতে পারে


## Foreign key?
Foreign Key হলো এমন একটি কলাম বা কলামের সেট যা একটি টেবিলের রেকর্ডকে অন্য একটি টেবিলের Primary Key (বা Unique Key) এর সাথে যুক্ত করে।
Foreign Key ব্যবহার করা হয় দুই টেবিলের মধ্যে সম্পর্ক (relationship) তৈরি করতে এবং ডেটার রেফারেনশিয়াল ইন্টেগ্রিটি বজায় রাখতে।

সহজভাবে:
Foreign Key = অন্য টেবিলের Primary Key রেফার করে এমন কী

উদাহরণ
ধরো দুটি টেবিল আছে:
1. students টেবিল

| student_id (PK) | name  |
| --------------- | ----- |
| 1               | Arpan |
| 2               | Raj   |
| 3               | Mira  |


2. enrollments টেবিল

| enroll_id | student_id (FK) | course  |
| --------- | --------------- | ------- |
| 101       | 1               | Math    |
| 102       | 2               | Physics |
| 103       | 1               | English |

এখানে:

✔ tudents.student_id হলো Primary Key
✔ enrollments.student_id হলো Foreign Key, যা students.student_id কে রেফার করছে
অর্থাৎ, একজন student কোন কোন course এ ভর্তি হয়েছে তা Foreign Key দিয়ে জানা যায়।
## Foreign Key কী কাজ করে
✔ দুই টেবিলের মধ্যে সম্পর্ক তৈরি করে
✔ ভুল ডেটা ঢোকা বন্ধ করে
✔ এমন student_id insert হতে দেয় না যা students টেবিলে নেই
✔ delete/update করলে relationship বজায় থাকে (CASCADE rules)