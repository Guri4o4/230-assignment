# 2NF Analysis

### Definition
A relation is in **Second Normal Form (2NF)** if it is in 1NF and every non-key attribute 
is fully dependent on the whole primary key (no partial dependencies).

### Table by Table Analysis
- Department: PK = dept_id → no composite key → in 2NF.
- Instructor: PK = instructor_id → no composite key → in 2NF.
- Student: PK = student_id → no composite key → in 2NF.
- Course: PK = course_id → no composite key → in 2NF.
- Enrollment: PK = (student_id, course_id).  
  - grade, semester depend on both → in 2NF.
  - student details are stored in Student, course details in Course. 
- Prerequisite: PK = (course_id, prereq_id).  
  - fully dependent on both → in 2NF.

### Transitive Dependencies
- course_id → dept_id  
- dept_id → dept_name  
Resolved by keeping Department separate.

### Example Closure (Armstrong's Axioms)
FDs:  
- course_id → dept_id  
- dept_id → dept_name  

Closure of {course_id}:  
- Start: {course_id}  
- Apply FD1: {course_id, dept_id}  
- Apply FD2: {course_id, dept_id, dept_name}  

Thus {course_id}+ = {course_id, dept_id, dept_name}.

### Result
All tables are in **2NF** (and essentially also in 3NF).
