# INSTITUTIONAL EXAMINATION: WEB DEVELOPMENT

**Project Title:** Clinic Queueing Monitor
**Time Limit:** 2.5 Hours (Strict)
**Environment:** XAMPP, VS Code, Chrome

---
Building a system for a clinic waiting room. The screen is connected to a giant TV monitor in the waiting area. 

*   **On Load (Default View):** The screen must display the clinic's "Monitor View" (a 3-column board showing Waiting, Serving, and Done patients).
*   **Admin Actions:** There are two buttons at the top of the screen. 
    *   Button 1: "Add Patient" (Opens a modal to add a patient).
    *   Button 2: "Display Table" (Hides the Monitor View and shows the Admin Table with Edit/Delete actions).

---

##1: Database Setup
Create database **`clinic_db`**.

Create table **`patients`**:
*   `id` (INT, Primary Key, Auto Increment)
*   `patient_name` (VARCHAR 100)
*   `symptom` (VARCHAR 255)
*   `status` (VARCHAR 20, Default: **'Waiting'**)

---

##2: The Frontend UI

### 1. The Header & Buttons
*   Title: "Clinic Queue Monitor"
*   Two Buttons: `+ Add Patient` and `Toggle Admin Table`.

### 2. The Monitor View (Default)
*   Must use Flexbox or CSS Grid to create **3 equal columns** side-by-side: **WAITING**, **SERVING**, and **DONE**.
*   Each column should have a distinct background color (e.g., Yellow for waiting, Green for serving, Gray for done).
*   Display the patient names as giant cards/lists inside these columns.

### 3. The Admin Table View (Hidden by default)
*   A standard table: ID, Name, Symptom, Status, Actions.
*   Wrapped in an `overflow-x: auto` container.

### 4. The Modal
*   A form to add a patient (Name, Symptom).

---

## 3: JavaScript Logic
1.  **Toggle View:** Clicking "Toggle Admin Table" hides the Monitor View and shows the Table View (and vice versa). 
2.  **Validation:** If the name or symptom is empty, use `alert()` and stop the form submission.

---

## 4: Backend (PHP) - Read & Create
1.  **Read (Monitor):** You must run **three separate `SELECT` queries**:
    *   `SELECT * FROM patients WHERE status = 'Waiting'`
    *   `SELECT * FROM patients WHERE status = 'Serving'`
    *   `SELECT * FROM patients WHERE status = 'Done'`
    *   Loop through each query and display the names in their respective columns.
2.  **Create:** Form submits via POST to `process.php` and inserts the patient (default status 'Waiting').
3.  **Read (Admin Table):** Run a `SELECT * FROM patients` (show all) and loop through them into the HTML table.

---

## 5: The Admin Actions
Inside the Admin Table's Action column, add buttons to change the patient's status:
1.  **Serve:** `UPDATE patients SET status = 'Serving' WHERE id = ...`
2.  **Done:** `UPDATE patients SET status = 'Done' WHERE id = ...`
3.  **Delete:** `DELETE FROM patients WHERE id = ...`

---
