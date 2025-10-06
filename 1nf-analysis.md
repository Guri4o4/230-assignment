# 1NF Analysis

### Definition
A relation is in **First Normal Form (1NF)** if all attributes are atomic (no repeating groups, no multivalued attributes).

### Conversion for Each Table
- Department: (dept_id, dept_name, office) → all atomic 
- Instructor: (instructor_id, name, email, dept_id) → all atomic
- Student: (student_id, name, email, dob, major) → all atomic 
- Course: (course_id, course_name, credits, dept_id) → all atomic 
- Enrollment: (student_id, course_id, grade, semester) → all atomic 
- Prerequisite: (course_id, prereq_id) → all atomic 

### Result
All relations are already in **1NF**.