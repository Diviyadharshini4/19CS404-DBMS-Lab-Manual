# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  

- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="964" height="732" alt="image" src="https://github.com/user-attachments/assets/cdd21789-81e7-42fc-ba0d-639b6de587a1" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Member	|Member_ID (PK), Name, Start_Date, Phone, Email, Membership_ID |	Stores the personal and membership details of each fitness club member.|
|Program	|Program_ID (PK), Program_Name, Category, Duration, Schedule |	Stores information about the fitness programs offered by the club.|
|Trainer|	Trainer_ID (PK), Trainer_Name, Specialization, Phone, Email	| Stores trainer details and their area of specialization.|
|Session |	Session_ID (PK), Session_Date, Session_Time|	Stores the date and time details of fitness sessions.|
|Attendance|	Attendance_ID (PK), Status, Remarks|	Records the attendance status of members for sessions.|
|Payment|	Payment_ID (PK), Amount, Payment_Date	|Stores payment details made by members.|

### Relationships and Constraints


| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member ↔ Program|	Many-to-many (M:N)	|Joins|	A member can join multiple programs, and a program can have multiple members.|
|Member ↔ Session|	One-to-many (1:N)|	Books	| A member can book multiple sessions, while each session is booked by one member.|
|Member ↔ Payment|	One-to-many (1:N)	|Makes	| A member can make multiple payments, while each payment belongs to one member.|
|Program ↔ Trainer|	Many-to-many (M:N)	|Assigned_to|	A program can be assigned to multiple trainers, and a trainer can be assigned to multiple programs.|
|Trainer ↔ Session|	One-to-many (1:N)|	Conducts|	One trainer can conduct multiple sessions, while each session is conducted by one trainer.|
|Session ↔ Attendance|	One-to-many (1:N) |	Has	| One session can have multiple attendance records, while each attendance record belongs to one session.|

### Assumptions
- Each member, trainer, program, session, attendance, and payment has a unique ID.
- A member can join more than one fitness program.
- A fitness program can have multiple members.
- A member can book multiple sessions.
- Each session is conducted by one trainer.
- A trainer can conduct multiple sessions.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  

- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:

<img width="1027" height="653" alt="image" src="https://github.com/user-attachments/assets/b9a743c4-f0c7-4b16-849a-489d429c3caa" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Staff	|Staff_ID (PK), Name	|Stores staff details.|
|Authentication System|	Login_ID (PK), Password	|Stores login credentials for staff authentication.|
|Reports|	Reg_No (PK/FK), Book_No (FK), Issue_Return|	Stores issue and return report details.|
|Readers|	User_ID (PK), FirstName, LastName, Name, Email, Phone_No, Address	|Stores details of library readers.|
|Books|	Book_No (PK), ISBN, Title, Author_No, Category, Edition|	Stores information about books.|
|Publisher|	Publisher_ID (PK), Name, Year_Of_Publication|	Stores publisher information.|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Staff ↔ Reports|	One-to-many (1:N)|	Manages	|One staff member can manage many reports.|
|Staff ↔ Authentication System|	One-to-one (1:1)	|Login|	Each staff member has one login account|
|Staff ↔ Readers|	Many-to-many (M:N) |	Keeps Track Of|	Staff can keep track of multiple readers.|
|Staff ↔ Books	|One-to-many (1:N)	|Maintain|	One staff member can maintain multiple books.|
|Readers ↔ Books|	One-to-many (1:N) |	Reserve/Return|	A reader can reserve multiple books overtime.|
|Publisher ↔ Books|	One-to-many (1:N)|	Published By|	One publisher can publish multiple books, while each book is published by one publisher.|

### Assumptions

- A book can be reserved by multiple readers at different times.
- A publisher can publish multiple books, while each book is published by one publisher.
- Each reservation records a Reserve_Date, Return_Date, and Due_Date.
- Reports record the issue and return details of books.
- The authentication system stores Login_ID and Password for authorized staff access.


### Scenario C: Restaurant Table Reservation & Ordering
**Business Context:**
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements :**

- Customers can reserve tables or walk in.
- Each reservation includes date, time, and number of guests.
- Customers place food orders linked to reservations.
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).
- Bills generated per reservation, including food and service charges.
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="999" height="644" alt="image" src="https://github.com/user-attachments/assets/0a15ef81-c9bc-409a-9434-b2e3e1eb0427" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Customer|	C-ID (PK), Name, Email, Phone, Address|	Stores customer details.|
|Reservation|	R-ID (PK), C-ID (FK), ID (FK), Date	|Stores customer reservation details.|
|Restaurant|	ID (PK), Name, Location	|Stores restaurant details.|
|Order|	O-ID (PK), C-ID (FK), ID (FK), Amount, Date|	Stores customer order details.|
|Delivery|	D-ID (PK), O-ID (FK), Date, Status|	Stores delivery information and status.|
|Menu Item|	M-ID (PK), R-ID (FK), Name, Price, Description	|Stores menu items offered by a restaurant.|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Customer ↔ Reservation|	One-to-many (1:N)	|Have|	One customer can have multiple reservations.|
|Reservation ↔ Restaurant|	Many-to-one (M:1) |	Have|	A restaurant can have multiple reservations.|
|Customer ↔ Order|	One-to-many (1:N) |	Place|	One customer can place multiple orders.|
|Order ↔ Restaurant|	Many-to-one (M:1) |	Receive	|A restaurant can receive multiple orders.|
|Restaurant ↔ Menu Item	|One-to-many (1:N)|	Offers|	One restaurant can offer multiple menu items.|
|Order ↔ Delivery|	One-to-one (1:1)	|Associated With|	Each order is associated with one delivery.|

##  Assumptions

- A restaurant can receive multiple orders.
- A restaurant can offer multiple menu items.
- Each reservation is associated with one customer and one restaurant.
- Each order is associated with one customer and one restaurant.
- Each order is associated with one delivery.
- Delivery records contain the delivery date and status.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
