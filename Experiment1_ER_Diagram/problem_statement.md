# ER Diagram Workshop – Submission Template
NAME : TARUN G M
REG NO : 212223060284
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
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/9b9590d4-401e-4449-9986-b8a863a371a9" />


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
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/53d039ef-592f-4daf-8f27-e7d92abdb893" />


### Entities and Attributes

| **Entity** | **Attributes (PK, FK)** | **Notes** |
|---|---|---|
| **Member** | **member_id (PK)**, name, email, phone, address, join_date | Stores library member details |
| **Book** | **book_id (PK)**, title, author, category, isbn | Stores book information |
| **Loan** | **loan_id (PK)**, loan_date, due_date, return_date | Records book borrowing and return details |
| **Fine** | **fine_id (PK)**, amount, fine_date, status | Stores overdue fine details |
| **Event** | **event_id (PK)**, event_name, event_date, description | Stores library event details |
| **Speaker** | **speaker_id (PK)**, name, role, organization | Stores event speakers or authors |
| **Room** | **room_id (PK)**, room_name, capacity, location, room_type | Stores rooms used for events and study |
| **Registration** | **registration_id (PK)**, registration_date, status | Records member event registrations |

### Relationships and Constraints


| **Relationship** | **Cardinality** | **Participation** | **Notes** |
|---|---|---|---|
| **Borrows** | 1:M | Member – Book – Loan | A member can borrow multiple books; each loan records a borrowing transaction |
| **Generates** | 1:0..1 | Loan – Fine | A loan may generate zero or one fine for an overdue return |
| **Has Speaker** | M:M | Event – Speaker | An event can have multiple speakers/authors and a speaker can participate in multiple events |
| **Registers** | M:M | Event – Member | Members can register for multiple events and an event can have multiple registered members |
| **Occurs In** | M:1 | Event – Room | Each event takes place in one room; a room can host multiple events at different times |

### Assumptions

- Each member, book, loan, fine, event, speaker, room, and registration has a unique primary key.
- A member can borrow multiple books, and each borrowing transaction is recorded as a loan.
- A book can be borrowed by different members over time.
- A loan may or may not generate a fine depending on whether the book is returned late.
- Each event can have one or more speakers or authors.
- Members can register for multiple library events.
- Each event is assigned to one room, while a room can be used for multiple events at different times.
- Rooms can be used for both events and study purposes.
- Overdue fines are calculated and recorded for books returned after the due date.

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
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/9ab2d0de-d46f-427c-968e-38c99cb530eb" />


### Entities and Attributes


| **Entity** | **Attributes (PK, FK)** | **Notes** |
|---|---|---|
| **Customer** | **customer_id (PK)**, name, phone, email, address | Stores customer details |
| **Reservation** | **reservation_id (PK)**, reservation_date, reservation_time, no_of_guests, type | Stores table reservation details; type can be Reserved or Walk-in |
| **Table** | **table_id (PK)**, table_no, capacity, location, status | Stores restaurant table details; status can be Available or Occupied |
| **Order** | **order_id (PK)**, order_time, order_type | Stores food order details; order type can be Dine-in or Walk-in |
| **Order_Item** | **order_item_id (PK)**, quantity, unit_price, total_price | Stores individual dishes included in an order |
| **Dish** | **dish_id (PK)**, dish_name, description, price | Stores menu dish details |
| **Category** | **category_id (PK)**, category_name, description | Stores dish categories such as Starter, Main, and Dessert |
| **Waiter** | **waiter_id (PK)**, name, phone | Stores waiter details |
| **Bill** | **bill_id (PK)**, bill_date, food_total, service_charge, tax, grand_total | Stores billing details for a reservation |

### Relationships and Constraints


| **Relationship** | **Cardinality** | **Participation** | **Notes** |
|---|---|---|---|
| **Makes** | 1:M | Customer – Reservation | A customer can make multiple reservations; each reservation belongs to one customer |
| **Reserved For** | M:1 | Reservation – Table | Each reservation is made for one table; a table can have multiple reservations at different times |
| **Has** | 1:1 | Reservation – Order | Each reservation has one food order |
| **Taken By** | M:1 | Order – Waiter | Each order is handled by one waiter; a waiter can handle multiple orders |
| **Contains** | 1:M | Order – Order_Item | An order can contain multiple order items |
| **For** | M:1 | Order_Item – Dish | Each order item refers to one dish; a dish can appear in multiple order items |
| **Belongs To** | M:1 | Dish – Category | Each dish belongs to one category; a category can contain multiple dishes |
| **Generates** | 1:1 | Reservation – Bill | Each reservation generates one bill containing food and service charges |

### Assumptions


- Each customer, reservation, table, order, order item, dish, category, waiter, and bill has a unique primary key.
- A customer can make multiple reservations, while each reservation is associated with one customer.
- A reservation can be either a **Reserved** booking or a **Walk-in**.
- Each reservation is assigned to one restaurant table.
- A reservation can have one food order containing multiple dishes.
- Each order is handled by one waiter, while a waiter can handle multiple orders.
- Each order item represents a dish and stores its quantity, unit price, and total price.
- Each dish belongs to one category: **Starter, Main, or Dessert**.
- A bill is generated for each reservation and includes food total, service charge, tax, and grand total.
- A table can be reserved multiple times at different dates and times.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
