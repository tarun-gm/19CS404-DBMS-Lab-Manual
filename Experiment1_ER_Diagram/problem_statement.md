<img width="1536" height="1024" alt="ChatGPT Image Aug 20, 2026, 08_24_08 PM" src="https://github.com/user-attachments/assets/ce82591c-943b-4fd8-9b3a-490f75cf94c3" />
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


## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| Member | **member_id (PK)**, name, membership_type, start_date | Stores registered gym members |
| Program | **program_id (PK)**, name, description, program_type | Stores fitness programs such as Yoga, Zumba, and Weight Training |
| Trainer | **trainer_id (PK)**, name, specialization, phone, email | Stores trainer details |
| Session | **session_id (PK)**, session_date, start_time, end_time, **member_id (FK)**, **trainer_id (FK)** | Stores personal training sessions booked by members |
| Attendance | **attendance_id (PK)**, status, check_in_time, check_out_time, **session_id (FK)** | Records attendance for each session |
| Payment | **payment_id (PK)**, payment_type, amount, payment_date, payment_for, **member_id (FK)**, **session_id (FK)** | Tracks membership and session payments |

## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Joins | M:N | Member – Program | A member can join multiple programs and a program can have multiple members |
| Assigned To | M:N | Program – Trainer | A program can have multiple trainers and a trainer can be assigned to multiple programs |
| Books | 1:N | Member – Session | A member can book multiple personal training sessions |
| Conducted By | 1:N | Trainer – Session | A trainer can conduct multiple sessions and each session is conducted by one trainer |
| Has Attendance | 1:1 | Session – Attendance | Each session has one attendance record |
| Makes | 1:N | Member – Payment | A member can make multiple payments |
| For | 1:N | Payment – Session | A payment can be associated with a personal training session |

## Assumptions

- Each member is uniquely identified by a **member_id**.
- Each member registers with a **name, membership type, and start date**.
- A member can join multiple fitness programs such as **Yoga, Zumba, and Weight Training**.
- A program can have multiple members and multiple trainers.
- A trainer can be assigned to multiple fitness programs.
- Members can book personal training sessions with trainers.
- Each personal training session is conducted by one trainer.
- Attendance is recorded for each personal training session.
- Payments are tracked for both **memberships and personal training sessions**.
- `member_id`, `trainer_id`, `program_id`, and `session_id` are used as foreign keys where applicable.
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
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
