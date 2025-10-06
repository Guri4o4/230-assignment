# 3NF Analysis

### Step 1: Reminder of 2NF
After 2NF, all partial dependencies were removed. Each non-key attribute is fully dependent on the primary key of its table.

---

### Step 2: Check for Transitive Dependencies
A transitive dependency happens when:
- A non-key attribute depends on another non-key attribute, instead of directly on the primary key.

**Example from our schema:**
- In `STUDENT`, attributes like `dept_name` should not be stored directly, because they depend on `dept_id`, not on `student_id`.
- In `COURSE`, the `dept_name` should not be repeated because it depends on `dept_id`.

---

### Step 3: Resolving Transitive Dependencies
To fix this, we ensure that:
- `DEPARTMENT` holds department-specific details (dept_id, dept_name).  
- `STUDENT` and `COURSE` only keep `dept_id` as a foreign key.  
- Instructor details stay only in the `INSTRUCTOR` table.  
- No table stores redundant values that can be derived via foreign keys.

---

### Step 4: Conclusion
After separating department info into its own table and linking with `dept_id`, our design satisfies **Third Normal Form (3NF)**:
- No partial dependencies.  
- No transitive dependencies.  
- Every non-key attribute depends only on the key, the whole key, and nothing but the key.
