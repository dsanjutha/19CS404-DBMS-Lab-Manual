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
<img width="852" height="561" alt="image" src="https://github.com/user-attachments/assets/89608ab0-90f6-4d49-9ecf-7e15cb89bd53" />


### Entities and Attributes

<img width="847" height="264" alt="Screenshot 2026-09-12 214603" src="https://github.com/user-attachments/assets/3f39817a-d404-4da3-8817-72563213ab6d" />


### Relationships and Constraints

<img width="851" height="232" alt="image" src="https://github.com/user-attachments/assets/463d8a23-e9e0-4a8c-b8bf-2e066af95129" />

### Assumptions
One membership type per member.

A program must have at least one trainer.

Personal training is optional and billed separately.

Attendance is recorded only when members participate.

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

<img width="850" height="593" alt="image" src="https://github.com/user-attachments/assets/6366e1e8-81f1-4421-b78e-b53ee90d954c" />

### Entities and Attributes
<img width="832" height="285" alt="image" src="https://github.com/user-attachments/assets/54440446-ba55-4bbe-9cbd-94bab51a8a83" />


### Relationships and Constraints

<img width="850" height="301" alt="image" src="https://github.com/user-attachments/assets/3a574903-ef05-489f-99f2-7efe1038a422" />


### Assumptions
Each book has only one copy in the database (copies could be modeled separately if needed).

Fines are tracked as part of loan record.

Members may or may not attend events.

Each event takes place in exactly one room.

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
<img width="853" height="497" alt="image" src="https://github.com/user-attachments/assets/49d07d5e-9607-4be7-aa7d-89853b5d94ff" />


### Entities and Attributes

<img width="850" height="311" alt="image" src="https://github.com/user-attachments/assets/1e6e9044-639f-43e6-8754-634de7cbf7ed" />


### Relationships and Constraints

<img width="846" height="298" alt="image" src="https://github.com/user-attachments/assets/990d815f-1bc0-4de8-9735-7827829d21bd" />


### Assumptions
Walk-in customers treated as reservations without advance booking.

One waiter handles a reservation at a time.

Service charge fixed per bill.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
