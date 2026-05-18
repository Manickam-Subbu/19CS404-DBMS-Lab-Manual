# ER Diagram Workshop – Submission Template

## Objective

To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose

Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Name:** Manickam Subbu
**Reg. No.:** 212223060147

**Business Context:**
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**

- Members register with full name, phone, email, membership type, and start date.
- Each member can join multiple programs (Yoga, Zumba, Weight Training, etc.).
- Trainers are assigned to programs; a program may have multiple trainers.
- Members may book personal training sessions with trainers.
- Attendance is recorded for each session.
- Payments are tracked for memberships and sessions.

---

### ER Diagram:

<img width="1142" height="634" alt="image" src="https://github.com/user-attachments/assets/f9a40f96-9dd0-4b3b-8f62-f581add14412" />
---

### Entities and Attributes

| Entity | Attributes (PK underlined) | Notes |
|---|---|---|
| MEMBER | <u>MemberID</u>, FullName, Phone, Email, MemberType, StartDate | Stores registered gym member details |
| PROGRAM | <u>ProgramID</u>, ProgramName, Schedule, Duration | Fitness classes like Yoga, Zumba, Weight Training |
| TRAINER | <u>TrainerID</u>, TrainerName, Specialization, Phone, HireDate | Certified trainers assigned to programs |
| SESSION | <u>SessionID</u>, SessionDate, StartTime, Duration, Fee | One-on-one personal training session booked by a member |
| ATTENDANCE | <u>AttendID</u>, Status, Notes | Tracks attendance for each session |
| PAYMENT | <u>PaymentID</u>, Amount, PaymentDate, Method, PaymentType | Covers membership and session-related payments |

---

### Relationships and Constraints

| Relationship | Entities Involved | Cardinality | Notes |
|---|---|---|---|
| JOINS | MEMBER — PROGRAM | M : N | A member can join multiple programs; a program can have multiple members |
| ASSIGNED TO | PROGRAM — TRAINER | M : N | A program can have multiple trainers; a trainer can be assigned to multiple programs |
| BOOKS | MEMBER — SESSION | 1 : N | One member can book many sessions; each session belongs to one member |
| CONDUCTS | TRAINER — SESSION | 1 : N | One trainer can conduct many sessions; each session is conducted by one trainer |
| PAYS FOR | MEMBER — PAYMENT | 1 : N | One member can make multiple payments; each payment belongs to one member |
| (Attendance link) | SESSION — ATTENDANCE | 1 : N | One session can have multiple attendance records |

---

### Assumptions

- The SESSION entity refers only to personal one-on-one training bookings, not group fitness classes.
- Group fitness classes are managed through the PROGRAM enrolment (JOINS relationship).
- The PAYMENT entity covers both membership fees and session charges, differentiated by the PaymentType attribute.
- Each session is conducted by exactly one trainer; co-training is not modelled.
- Attendance records are maintained per session.
- M:N relationships (JOINS, ASSIGNED TO) are resolved using bridge/junction tables in the relational schema.
- TrainerName, Phone, HireDate, and Specialization are the key attributes maintained for each trainer.
- SessionDate, StartTime, Duration, and Fee uniquely describe each personal training session.
