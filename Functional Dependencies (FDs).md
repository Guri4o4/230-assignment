# Functional Dependencies (FDs)

## Department
- dept_id → dept_name, office

## Instructor
- instructor_id → name, email, dept_id

## Student
- student_id → name, email, dob, major

## Course
- course_id → course_name, credits, dept_id

## Enrollment (weak entity)
- (student_id, course_id) → grade, semester

## Prerequisite (recursive relationship)
- (course_id, prereq_id) → relationship exists

---

# Candidate Keys
- Department: dept_id
- Instructor: instructor_id
- Student: student_id
- Course: course_id
- Enrollment: (student_id, course_id)
- Prerequisite: (course_id, prereq_id)
