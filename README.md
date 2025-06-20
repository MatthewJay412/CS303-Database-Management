## 1. Identify Functional and Transitive Dependencies

We can identify some dependencies by reviewing how the fields relate to each other and the primary key. The primary key in this example is **Employee ID**.

### Functional Dependencies  
A functional dependency means that one attribute uniquely determines another. Here, **Employee ID** determines:
- First Name  
- Last Name  
- Street Address  
- City  
- State  
- Zip Code  
- Position  
- Salary  

These fields will remain together in the main table after normalization.

#### Fields with Functional Dependencies  
- **Employee ID**, **First Name**, **Last Name**  
- **Address**, **City**, **State**, **Zip Code**  
- **Position**, **Salary**, **Department**, **Manager**

### Transitive Dependencies  
A transitive dependency occurs when a non-key attribute depends on another non-key attribute instead of directly on the primary key.

#### Examples of Transitive Dependencies  
1. **Manager ⇄ Department ⇄ Position**  
   - Managers belong to departments, and departments define positions.  
2. **Position → Salary**  
   - People in the same position generally share the same salary.  
3. **City + State → Zip Code**  
   - A zip code is uniquely identified by its city and state.  
4. **Department → Manager ID**  
   - Each department has a designated Manager ID.

---

## 2. Identify the Primary Key

- **Primary Key:** `Employee ID`  

This column uniquely identifies each employee record.

---

## 3. Explain Why the Table Is Not in 3NF

To be in **Third Normal Form (3NF)**, a table must first satisfy 1NF and 2NF **and** have **no transitive dependencies** among non-key attributes.

### Third Normal Form (3NF)  
- All columns are atomic (single-valued).  
- Every non-key attribute depends **only** on the primary key (no transitive dependencies).

### Second Normal Form (2NF)  
- Table is in 1NF.  
- Every non-key attribute is fully functionally dependent on the entire primary key (no partial dependencies).

### First Normal Form (1NF)  
- No repeating groups or arrays.  
- All columns hold atomic values.  
- Each row is uniquely identified by a primary key.

#### Why It Fails 3NF  
Because attributes like **Manager**, **Department**, **Position**, **Salary**, **City/State/Zip** depend on each other (not just on **Employee ID**), the table exhibits transitive dependencies and therefore is **not** in 3NF.

---

## 4. Explain the Current Normalization Status

### 1NF  
- No repeating groups; each column is atomic.  
- A unique primary key (`Employee ID`) identifies every row.

### 2NF  
- Already in 1NF.  
- All non-key attributes fully depend on `Employee ID` (no partial dependencies).

> **Note:** The presence of transitive dependencies prevents 3NF compliance.

---

## 5. Create the Tables in MySQL

> _This section was left blank in the original assignment (0 points)._  
