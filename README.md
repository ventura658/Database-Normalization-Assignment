# Database Normalization Assignment

   ## Introduction
   This repository is dedicated to an assignment on database normalization. It involves analyzing a given table of patient visits (provided in CSV format), determining its normal form, normalizing it to 3rd Normal Form (3NF), implementing the design in MySQL Workbench, and visualizing the results in an Excel file.

   The original table represents patient visit data and includes the following columns: VisitNo, VisitDate, PatNo, PatAge, PatCity, ProvNo, ProvSpecialty, and Diagnosis. The functional dependencies are provided for normalization.

   ## Original Table
   Below is the provided table in a readable format. The full data is also available in the CSV file: [BigPatientTable.csv](patient_table.csv).

  [BigPatientTable.png](patient_table.csv).

   ## Assignment Questions
   This assignment consists of four questions based on the table above:

   1. **Question 1**: Is the table in 1st Normal Form (1NF)? Justify your answer.
      - Analyze whether the table has atomic values, no repeating groups, and a primary key.

   2. **Question 2**: Convert the Big Patient Table to 3rd Normal Form (3NF). The functional dependencies are:
      - PatNo → PatAge, PatCity
      - ProvNo → ProvSpecialty
      - VisitNo → PatNo, VisitDate, PatAge, PatCity
      - VisitNo, ProvNo → Diagnosis
      
      Show the result of each step in the normalization process (from 1NF to 2NF to 3NF).

   3. **Question 3**: Normalize the table using MySQL Workbench and save the new design as a .mwb file and an SQL script.
      - Use MySQL Workbench to create the normalized schema.
      - Export the model as a .mwb file and generate an SQL script (e.g., `normalized_schema.sql`).
      - Upload these files to the repository and link them here.

   4. **Question 4**: Create an Excel file that displays the new normalized tables and distributes the original table's data across them.
      - For example, create separate sheets for each new table (e.g., one for patients, one for visits, etc.).
      - Upload the Excel file (e.g., `normalized_tables.xlsx`) to the repository and link it here.

   ## Solution Guidelines
   Below are high-level steps to approach this assignment:

   - **For Question 1**: Check if the table is in 1NF by ensuring:
     - All attributes are atomic (e.g., no arrays or multi-values).
     - There are no repeating groups.
     - A primary key exists (e.g., VisitNo could be a candidate).

   - **For Question 2**: Follow the normalization process:
     - **1NF**: Ensure the table meets the criteria above.
     - **2NF**: Remove partial dependencies (dependencies on part of the primary key).
     - **3NF**: Remove transitive dependencies.
     - Document each step with new table designs.

   - **For Question 3**: 
     - Open MySQL Workbench, create a new EER diagram.
     - Add entities based on your 3NF design and define relationships.
     - Save as .mwb and export to SQL.

   - **For Question 4**:
     - Use Excel to create worksheets for each normalized table.
     - Populate them with data from the original CSV.
     - Example: One sheet for "Patients" with PatNo, PatAge, PatCity, another for "Visits" with VisitNo, VisitDate, etc.
