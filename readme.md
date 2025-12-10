
## ********************************************Database Model Design Module****************************************##
**What is Database
ans: Database is a structured collection of related data, organized for efficient storage, retrieval, and mangement

**DBMS Full meaning
ans: Database Management System

** What is key?
ans: A key in a relational database is a field or a combination of fields that uniqely identifies a record in a table


## Most Used Keys 
1. Super Key
2. Candidate key
3. Primary key
4. Alternative key
5. Composite key
6. foreign key


------------------------------------------------------------------------------------------------------------------------------
Super Key (সুপার কি)
ডেটাবেজ টেবিলের প্রতিটি রেকর্ডকে ইউনিকভাবে শনাক্ত করতে পারে এমন যেকোনো কলাম বা কলামের গ্রুপকে Super Key বলা হয়।

সহজভাবে:
Super Key মানে এমন একটি অ্যাট্রিবিউট সেট যা দিয়ে টেবিলের প্রতিটি রো কে আলাদা করে চেনা যায়।

| id | email | phone | name |
| -- | ----- | ----- | ---- |

এই টেবিলে:
id,
email,
phone,
id + email,
email + phone,
id + phone + name,
এসবই Super Key হতে পারে, কারণ সবগুলো কম্বিনেশন দিয়ে প্রতিটি রেকর্ডকে ইউনিকভাবে চেনা যায়।

**মনে রাখার বিষয়**
✔ Super Key হল সবচেয়ে বড় গ্রুপ: এতে প্রয়োজনীয় অ্যাট্রিবিউট ছাড়াও অতিরিক্ত অ্যাট্রিবিউট থাকতে পারে।
✔ Super Key এর ভেতর থেকেই পরে Candidate Key বের করা হয় (যেখানে অপ্রয়োজনীয় অ্যাট্রিবিউট থাকে না)।





➤ Set (সেট)
==> একটি Set হলো ভিন্ন ভিন্ন (unique) উপাদানের একটি সংগ্রহ| গাণিতিকভাবে Set সাধারণত কৌঁচি বন্ধনী { } দিয়ে লেখা হয়।

উদাহরণ:
A = {1, 2, 3, 4}
এখানে A হলো একটি সেট, যেখানে 1, 2, 3, 4 হলো তার উপাদান।

➤বৈশিষ্ট্য
✔ উপাদানগুলো ইউনিক হয় (ডুপ্লিকেট থাকে না)
✔ উপাদানের ক্রম গুরুত্বপূর্ণ নয় (যেমন {1,2,3} এবং {3,2,1} একই Set)

➤ Subset (সাবসেট)
একটি Set B কে Set A-এর Subset বলা হয়, যদি B-এর সব উপাদানই A-এর মধ্যে থাকে।

উদাহরণ:
A = {1, 2, 3, 4}
তাহলে
B = {1, 2} হলো A-এর Subset
C = {2, 3, 4} হলো Subset
D = {1, 4} হলো Subset
এমনকি E = {1, 2, 3, 4} (পুরো সেট) সেটিও Subset

➤গুরুত্বপূর্ণ
✔ খালি সেট { } সব সেটের Subset
✔ একটি সেট নিজেও নিজের Subset

•   →   ⇒   ➤   ➜   ⮞
✓   ✔
✦   ✧   ❖   ◆   ◈

