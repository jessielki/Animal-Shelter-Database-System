# Animal-Shelter-Database-System

## 📌 Project Overview

This project implements a fully normalized relational database schema to streamline daily operations for an animal shelter or sanctuary. It includes automated table creation with constraint validation (check constraints, foreign key cascades, regex pattern matching), comprehensive sample data population, and complex analytical SQL queries.

### ⭐ Highlights
* **Relational Schema Design:** Features 13 interconnected tables linking animals, categories, staff, volunteers, duties, adopters, medical treatments, and donors.
* **Integrity Constraints:** Enforces strict data integrity using regex validation for Malaysian IC numbers (`YYMMDD-PB-###G`) and email formats, along with custom check constraints on age ranges and health ratings.
* **Advanced SQL Queries:** Demonstrates Outer Joins, multi-table aggregations (4+ tables), subqueries, date functions, pattern matching, and complex boolean logic.

---

## 🗄️ Database Architecture & Entity Relationships

The database tracks the full lifecycle of shelter animals from intake to adoption or ongoing medical/sanctuary care:

* **Core Entities:**
  * `animal` & `category` (Junction: `animal_category` for multi-tagging age/breed classes)
  * `staff`, `task`, `staff_duty`
  * `volunteer`, `volunteer_duty` (Supervised by `staff`)
  * `adopter` & `adoption`
  * `veterinary` (Medical treatment tracking by staff)
  * `donor` & `donation`

---

## ⚙️ Schema Features & Constraints

* **Staff IC Regex Validation:** `CHECK (REGEXP_LIKE(staffIC, '^\d{6}-\d{2}-\d{4}$'))`
* **Email Formatting Validation:** Validates `adopterEmail` structure.
* **Health Scale:** `healthRating NUMERIC(1)` constrained between `1` and `5`.
* **Gender & Age Checks:** Constrained inputs (`'M'`, `'F'`) and age boundaries (`0` to `40`).

---

## 💡 Key Analytical Queries Included

The script provides pre-built queries for key operational reporting:

1. **Adoption Status (Left Outer Join):** Lists all shelter animals alongside their adoption status and adopter details if adopted.
2. **Staff Supervision Workload (4-Table Join + Aggregation):** Counts volunteer duties supervised by each staff member grouped by task.
3. **Volunteer Duty Logs (Pattern Matching & Date Functions):** Filters volunteers matching specific name patterns during specific date windows.
4. **Health & Record Tracking Duties (Complex Logic):** Identifies staff handling health monitoring and record tracking between specific timeframes.
5. **Unadopted Adult Cats (Nested Subqueries):** Uses subqueries to find unadopted animals matching specific categorical classifications (`C2` - Adult Cat).
6. **Long-Term Sanctuary Health Assessment:** Identifies animals residing in the sanctuary over a year with top health ratings (`5`).

---

## 🚀 How to Run

**Execution:**
   * Open `6_3_script.sql` (or paste the contents into your SQL tool).
   * Run the script in sequence. The script will automatically drop pre-existing tables, build the schema, populate data, and output query execution results.
  
