## Assignment Questions and Solutions
This section provides the solutions to the assignment questions based on the analysis.

1. **Question 1: Is the table in 1st Normal Form (1NF)? Justify your answer.**  
   The table is not in 1st Normal Form because it contains empty cells and repeating fields. Empty cells violate the requirement for atomic values, as they indicate missing data that should be addressed. Repeating fields (e.g., multiple entries for the same VisitNo) suggest potential repeating groups, which are not allowed in 1NF.

2. **Question 2: Convert the Big Patient Table to 3rd Normal Form (3NF).**  
   **From Non-1NF to 1NF:**  
   - First, fill in the missing data in empty cells by repeating the appropriate values based on the functional dependencies.  
     For example, since PatNo → PatAge, PatCity, the empty fields in PatAge and PatCity can be filled using the corresponding records.  
     Additionally, since VisitNo → PatNo, VisitDate, PatAge, PatCity, we can infer that each VisitNo is unique and arbitrarily fill in the missing entries.  

![Non 1NF to 1NF-1](https://github.com/ventura658/Database-Normalization-Assignment/blob/221abf28080c3f5b2a8922a918c7c6e227edcc3b/Solution/Ex2-1.png)

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
     
![Non 1NF to 1NF-2](https://github.com/ventura658/Database-Normalization-Assignment/blob/221abf28080c3f5b2a8922a918c7c6e227edcc3b/Solution/Ex2-2.png)

![PatInfo](https://github.com/ventura658/Database-Normalization-Assignment/blob/072838b53a14488b11be33763daddde9a7650050/Solution/PatInfo.png)

![ProvInfo](https://github.com/ventura658/Database-Normalization-Assignment/blob/072838b53a14488b11be33763daddde9a7650050/Solution/ProvInfo.png)

     After this, the original table is converted to 1NF as follows:
     
![1NF](https://github.com/ventura658/Database-Normalization-Assignment/blob/072838b53a14488b11be33763daddde9a7650050/Solution/1NF.png)
  
   **From 1NF to 2NF:**  
   In the 1NF table, there is a partial dependency: VisitNo → VisitDate, PatNo. To resolve this, decompose the table as follows:  
  
![VisitDiagnosis](https://github.com/ventura658/Database-Normalization-Assignment/blob/95f6e1cbe1f9f15da77fe5babceab7acce305eb2/Solution/VisitDiagnosis.png)

![VisitInfo](https://github.com/ventura658/Database-Normalization-Assignment/blob/95f6e1cbe1f9f15da77fe5babceab7acce305eb2/Solution/VisitInfo.png)

   The resulting tables have no partial dependencies.  

   **From 2NF to 3NF:**  
   No transitive dependencies are present in the resulting tables, so they are already in 3NF.

3. **Question 3: Normalize the table using MySQL Workbench and save the new design.**  
   - First, determine the primary key: Based on the functional dependencies, use {VisitNo, ProvNo} as the primary key.  

![Primary Key](https://github.com/ventura658/Database-Normalization-Assignment/blob/072838b53a14488b11be33763daddde9a7650050/Solution/Ex3-1.png)

   - Handle partial dependencies:  
     VisitNo → PatNo, VisitDate, PatAge, PatCity and ProvNo → ProvSpecialty.  

![partial dependencies](https://github.com/ventura658/Database-Normalization-Assignment/blob/072838b53a14488b11be33763daddde9a7650050/Solution/Ex3-1.png)

   - Re-check for partial dependencies:  
     In the resulting VisitInfo table, there is a partial dependency PatNo → PatAge, PatCity.

![partial dependencies-2](https://github.com/ventura658/Database-Normalization-Assignment/blob/072838b53a14488b11be33763daddde9a7650050/Solution/Ex3-2.png)

   - Re-check for partial or transitive dependencies:  
     In the final tables, there are no partial or transitive dependencies, so the schema is in 3NF.  

![partial dependencies-3](https://github.com/ventura658/Database-Normalization-Assignment/blob/072838b53a14488b11be33763daddde9a7650050/Solution/Ex3-3.png)

   Use MySQL Workbench to create the normalized schema:  
[Ex2.mwb](https://github.com/ventura658/Database-Normalization-Assignment/blob/87b53f597ae26698f1c52beb64dadc0a4f99d18d/Solution/Ex2.mwb)
 and
[Ex2.sql](https://github.com/ventura658/Database-Normalization-Assignment/blob/87b53f597ae26698f1c52beb64dadc0a4f99d18d/Solution/Ex2.sql)

4. **Question 4: Create an Excel file for the normalized tables.**  
   Create an Excel file  with separate sheets for each normalized table. Distribute the original
 data across these sheets, ensuring all dependencies are respected.
[BigPatientDatabase](https://github.com/ventura658/Database-Normalization-Assignment/blob/87b53f597ae26698f1c52beb64dadc0a4f99d18d/Solution/BigPatientDatabase.xls)
