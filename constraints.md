# Data Dictionary - Constraints

## DEPARTMENT
- PK: dept_id  
- dept_name UNIQUE NOT NULL  

## INSTRUCTOR
- PK: instructor_id  
- FK: dept_id → DEPARTMENT(dept_id)  
- email UNIQUE NOT NULL  

## STUDENT
- PK: student_id  
- FK: dept_id → DEPARTMENT(dept_id)  
- email UNIQUE NOT NULL  

## COURSE
- PK: course_id  
- FK: dept_id → DEPARTMENT(dept_id)  
- credits CHECK (credits BETWEEN 1 AND 6)  

## ENROLLMENT
- PK: enrollment_id  
- FK1: student_id → STUDENT(student_id)  
- FK2: course_id → COURSE(course_id)  
- grade CHECK (grade IN ('A','B','C','D','F','W'))  

## PREREQUISITE
- PK: (course_id, prereq_id)  
- FK1: course_id → COURSE(course_id)  
- FK2: prereq_id → COURSE(course_id)  
- Constraint: prereq_id ≠ course_id  
