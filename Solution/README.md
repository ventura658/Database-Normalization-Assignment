## Assignment Questions and Solutions
This section provides the solutions to the assignment questions based on the analysis.

1. **Question 1: Is the table in 1st Normal Form (1NF)? Justify your answer.**  
   The table is not in 1st Normal Form because it contains empty cells and repeating fields. Empty cells violate the requirement for atomic values, as they indicate missing data that should be addressed. Repeating fields (e.g., multiple entries for the same VisitNo) suggest potential repeating groups, which are not allowed in 1NF.

2. **Question 2: Convert the Big Patient Table to 3rd Normal Form (3NF).**  
   **From Non-1NF to 1NF:**  
   - First, fill in the missing data in empty cells by repeating the appropriate values based on the functional dependencies.  
     For example, since PatNo → PatAge, PatCity, the empty fields in PatAge and PatCity can be filled using the corresponding records.  
     Additionally, since VisitNo → PatNo, VisitDate, PatAge, PatCity, we can infer that each VisitNo is unique and arbitrarily fill in the missing entries.  

   - Next, identify one or more attributes to use as a key for the non-normalized table.  
     Given the functional dependencies:  
     - ProvNo → ProvSpecialty  
     - VisitNo → PatNo, VisitDate, PatAge, PatCity  
     - VisitNo, ProvNo → Diagnosis  

     Using the augmentation property of functional dependencies (A → B implies A ∪ C → B ∪ C):  
     - From VisitNo → PatNo, VisitDate, PatAge, PatCity, we get: VisitNo, ProvNo → PatNo, VisitDate, PatAge, PatCity, ProvNo.  
     - From ProvNo → ProvSpecialty, we get: VisitNo, ProvNo → VisitNo, ProvSpecialty.  
     - Combining with VisitNo, ProvNo → Diagnosis, we arrive at: VisitNo, ProvNo → VisitNo, VisitDate, PatNo, PatAge, PatCity, ProvNo, ProvSpecialty, Diagnosis.  

     Therefore, we define a composite key: {VisitNo, ProvNo}.  

   - Identify repeating fields and move them to a new table along with a copy of the relevant key.  
     After this, the original table is converted to 1NF as follows: [Describe or link to the updated table if available].  

   **From 1NF to 2NF:**  
   In the 1NF table, there is a partial dependency: VisitNo → VisitDate, PatNo. To resolve this, decompose the table as follows:  
   - New tables: [List the decomposed tables based on your analysis, e.g., one for VisitInfo and another for related attributes].  

   The resulting tables have no partial dependencies.  

   **From 2NF to 3NF:**  
   No transitive dependencies are present in the resulting tables, so they are already in 3NF.

3. **Question 3: Normalize the table using MySQL Workbench and save the new design.**  
   - First, determine the primary key: Based on the functional dependencies, use {VisitNo, ProvNo} as the primary key.  

   - Handle partial dependencies:  
     VisitNo → PatNo, VisitDate, PatAge, PatCity and ProvNo → ProvSpecialty.  

   - Re-check for partial dependencies:  
     In the resulting VisitInfo table, there is a partial dependency PatNo → PatAge, PatCity.  

   - Re-check for partial or transitive dependencies:  
     In the final tables, there are no partial or transitive dependencies, so the schema is in 3NF.  

   Use MySQL Workbench to create the normalized schema:  
   - Add entities for the new tables based on the 3NF design.  
   - Define relationships and export as [normalized_schema.mwb](normalized_schema.mwb) and [normalized_schema.sql](normalized_schema.sql).

4. **Question 4: Create an Excel file for the normalized tables.**  
   Create an Excel file ([normalized_tables.xlsx](normalized_tables.xlsx)) with separate sheets for each normalized table. Distribute the original data across these sheets, ensuring all dependencies are respected. For example:  
   - One sheet for "Patients" with PatNo, PatAge, PatCity.  
   - One sheet for "Visits" with VisitNo, VisitDate, etc.  
   Upload the file to the repository for reference.

## Files in This Repository
- **patient_table.csv**: The original table data.
- **normalized_schema.mwb**: MySQL Workbench file for the normalized design.
- **normalized_schema.sql**: SQL script for the normalized database.
- **normalized_tables.xlsx**: Excel file showing the normalized tables and distributed data.
- **(Optional)**: Add an image of your ERD diagram, e.g., ![ERD Diagram](images/erd_diagram.png). Upload it to an "images" folder.

## Supplementary Information
- **Author**: [Your name or team name, e.g., "Your Username"]
- **Date**: [Add the current date, e.g., "October 2023"]
- **Next Steps**: Update this README with any additional files or diagrams as you finalize your work. Commit changes regularly for version control.
- **Notes**: This assignment focuses on database normalization techniques. If you have questions or need to discuss the solutions, open an issue in this repository.

For collaboration or feedback, feel free to open an issue!
