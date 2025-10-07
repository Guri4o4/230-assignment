# Data Dictionary - Tables

## DEPARTMENT
**Description:** Stores information about academic departments that manage courses, instructors, and students.  
**Columns:**  
- dept_id: SERIAL PRIMARY KEY – unique identifier for each department  
- dept_name: VARCHAR(100) UNIQUE NOT NULL – department name (e.g., Computer Science)  
**Metadata:**  
- Source: University administration  
- Update Frequency: On creation or restructuring  
- Privacy: General  
- Valid Values: Names must be unique  

---

## INSTRUCTOR
**Description:** Stores information about instructors employed in departments.  
**Columns:**  
- instructor_id: SERIAL PRIMARY KEY – unique identifier  
- first_name: VARCHAR(50) NOT NULL  
- last_name: VARCHAR(50) NOT NULL  
- email: VARCHAR(100) UNIQUE NOT NULL  
- dept_id: INT NOT NULL – foreign key referencing DEPARTMENT(dept_id)  
**Metadata:**  
- Source: HR / Department  
- Update Frequency: On hire/exit  
- Privacy: PII  
- Valid Values: email must be in university domain  

---

## STUDENT
**Description:** Stores information about students registered at the university.  
**Columns:**  
- student_id: SERIAL PRIMARY KEY – unique identifier  
- first_name: VARCHAR(50) NOT NULL  
- last_name: VARCHAR(50) NOT NULL  
- email: VARCHAR(100) UNIQUE NOT NULL  
- dept_id: INT NOT NULL – foreign key referencing DEPARTMENT(dept_id)  
**Metadata:**  
- Source: Admissions / Registrar  
- Update Frequency: On admission or update  
- Privacy: PII (Sensitive)  
- Valid Values: valid email, dept_id must exist in DEPARTMENT  

---

## COURSE
**Description:** Stores details about courses offered by departments.  
**Columns:**  
- course_id: SERIAL PRIMARY KEY – unique identifier  
- course_name: VARCHAR(100) NOT NULL  
- credits: SMALLINT NOT NULL CHECK (credits > 0 AND credits <= 6)  
- dept_id: INT NOT NULL – foreign key referencing DEPARTMENT(dept_id)  
**Metadata:**  
- Source: Academic catalog  
- Update Frequency: At start of term  
- Privacy: General  
- Valid Values: credits between 1 and 6  

---

## ENROLLMENT
**Description:** Weak entity recording the enrollment of students in courses.  
**Columns:**  
- enrollment_id: SERIAL PRIMARY KEY – unique identifier  
- student_id: INT NOT NULL – foreign key referencing STUDENT(student_id)  
- course_id: INT NOT NULL – foreign key referencing COURSE(course_id)  
- grade: CHAR(2) CHECK (grade IN ('A','B','C','D','F','W'))  
**Metadata:**  
- Source: Registrar’s enrollment records  
- Update Frequency: Each semester  
- Privacy: PII (Sensitive)  
- Valid Values: one of A–F or W  

---

## PREREQUISITE
**Description:** Weak entity modeling prerequisite relationships between courses.  
**Columns:**  
- course_id: INT NOT NULL – foreign key referencing COURSE(course_id)  
- prereq_id: INT NOT NULL – foreign key referencing COURSE(course_id)  
- PRIMARY KEY(course_id, prereq_id)  
**Metadata:**  
- Source: Academic catalog  
- Update Frequency: At curriculum updates  
- Privacy: General  
- Valid Values: prereq_id must exist and be different from course_id  
