# MIST 4610 Project 1
## Team Name: Group 1
## Team Members:
Lauren Harville - [@4610LaurenGit](https://github.com/4610LaurenGit/Sp26_61608_Group-1.git)

Andrew Heighton - [@AndrewHeighton](https://github.com/AndrewHeighton/MIST4610GroupProject1.git)

Asanti Kumera - [@asanti00](https://github.com/asanti00/MIST4610GroupProject1.git)

Aiden Pfeiffer - [@abp80036](https://github.com/abp80036/MIST4610Group1.git)

Doc Rush - [@docrush](https://github.com/docrush/MIST-4610-Group-1-Telehealth )

Violet Sofish - [@VioletSofish](https://github.com/VioletSofish/4610-Group-1-project#4610-group-1-project )

## Problem Description:
We are a telehealth patient & provider portal focused on managing virtual clinic throughput and insurance reimbursement. We are responsible for making and facilitating appointments, patient-physician communications, and prescriptions. Physicians can have multiple specialties, appointments have a status, and encounter status and insurance claim payments are linked.
## Data Model
Our model is a fictional telehealth platform that maps out the relationships between patients, providers, insurance, payments, and medical records. At the center, patients are the driving force of our database. Patients have unique IDs, names, identification information and contanct information.

Each appointment between a patient and a provider is recorded as a medical encounter. These are stored with the meeting date and status, whether the appointment is currently scheduled, completed but unpaid for, or paid for. The providers can have many different titles, each having their own names and identification/contact information. Outside of appointments, any emails, on-platform messages, or calls between patient and provider are stored with a timestamp and transcript as communications.

Providers can write prescriptions, which are recorded as a many-to-many relationship with the prescribed patient. Each patient also has a one-to-one relationship displaying their medical history and current information, which is reviewed by the provider prior to meetings.

After each encounter, a single invoice is generated. This invoice can be payed off in multiple installments and by either the patient, insurance, or a combination of the two - depending on the policy. After the invoice is fully covered, the status of the MedicalEncounter is changed to 'paid'.

There are a few different InsuranceProvider companies, each offering a handful of unique plans. Each unique pairing of one of these InsurancePlans and a patient is recorded as CustomerInsurance, a many-to-many relationship.
![Data Model](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/data%20model%20screenshot.png?raw=true)
## Data Dictionary
Communications:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/communications.png?raw=true)
CustomerInsurance:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/Customerinsurance.png?raw=true)
InsurancePlan:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/insuranceplan.png?raw=true)
InsuranceProvider:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/insuranceprovider.png?raw=true)
Invoice:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/invoice.png?raw=true)
MedicalEncounters:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/medicalencounters.png?raw=true)
MedicalRecords:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/medicalrecords.png?raw=true)
Patients:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/patients.png?raw=true)
Payments:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/payments.png?raw=true)
Prescriptions:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/prescriptions.png?raw=true)
Provider:
![communications](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/provider.png?raw=true)
## Query Matrix


![matrix](https://github.com/docrush/MIST-4610-Group-1-Telehealth/blob/main/matrix.png?raw=true)
## Simple Queries
#### 1. Retrieve a list of all patients whose email ends in “.com”. Include their first name, last name, phone number, and email.


<img width="1774" height="1143" alt="Screenshot 2026-04-03 222029" src="https://github.com/user-attachments/assets/a8c0961b-e0dc-4a2c-8e2d-01148167971f" />

#### Description: 
This query shows patients whose email addresses end in ".com". It uses a regular expression (REGEXP) to filter emails that match this pattern. The results return the patient’s information for anyone whose email ends with ".com".


#### 2. Find all medical encounters that are currently marked as “Scheduled.” Include the encounter ID, patient ID, provider ID, and appointment date.
<img width="1762" height="1151" alt="Screenshot 2026-04-03 222039" src="https://github.com/user-attachments/assets/abc1ee6d-eea0-408d-8f72-fdbc903c5ac2" />

#### Description:
This query finds all medical encounters that currently have a status of "Scheduled." The subquery first identifies the encounter IDs that meet this condition, and then the main query pulls the encounter ID, patient ID, provider ID, and appointment date for those records.

#### 3. List the patient name and invoice amount for payments that are greater than $3000 that are associated with completed appointments that have been paid for. Additionally, order the results by invoice amount in ascending order. The finance team can use this to identify higher balances and prioritize follow-up actions.
- SQL: [WHERE and ORDER BY]
<img width="1765" height="1148" alt="Screenshot 2026-04-03 222047" src="https://github.com/user-attachments/assets/c4c3e9b8-b6a2-41d3-bdc2-9a35cca6721d" />

#### Description:
This query finds patients who have invoice amounts greater than $3000 from appointments that have been marked as paid. It joins the Patients, MedicalEncounters, and Invoice tables to connect patient information with their billing records. The WHERE clause filters the results based on the invoice amount and appointment status, and the ORDER BY sorts the results from lowest to highest invoice amount.

#### 4. Lists all patients who haven't sent at least one message
<img width="1766" height="1155" alt="Screenshot 2026-04-03 222056" src="https://github.com/user-attachments/assets/71b5f65f-ffa3-4cb1-89c4-8199751f14d2" />

#### Description:
This query finds patients who have not sent any messages. It checks the Communications table to see if there are any records linked to each patient, and if none exist, that patient is included in the results. The NOT EXISTS condition makes sure only patients with no messages are returned.
## Complex Queries
#### 5. For each patient, calculate the total amount billed (from invoices) and the total amount paid (from payments). Display the patient’s name along with both totals, even if a patient has no payments recorded.
<img width="1769" height="1146" alt="Screenshot 2026-04-03 222105" src="https://github.com/user-attachments/assets/91c41e28-fe19-4852-bfc3-fe74b6725ab5" />

#### Description:
This query calculates how much each patient has been billed and how much they have paid so far. It uses subqueries to add up the total invoice amounts and the total payments for each patient. The query still shows all patients even if they do not have any payments recorded, which means some totals may show as NULL. This helps compare what each patient owes versus what they have already paid.

#### 6. Identify the provider who has handled the highest number of medical encounters. Display the provider’s name and the total number of encounters they have managed.
<img width="1768" height="1167" alt="Screenshot 2026-04-03 222114" src="https://github.com/user-attachments/assets/66c11b5a-6716-4bcb-8e22-7ce18dc66074" />

#### Description:
This query finds the provider who has handled the most medical encounters. The subquery counts how many encounters each provider has and orders them from highest to lowest, then selects the provider with the highest total. The main query then returns the name of that provider.

#### 7. List patients whose total payments exceed the average payment amount across all patients. This identifies patients with high payments that contribute to the overall revenue made, which can impact future business strategies. 
SQL: [SUBQUERY]
<img width="1769" height="1148" alt="Screenshot 2026-04-03 222121" src="https://github.com/user-attachments/assets/2d9c4bc9-9cda-466e-b03e-97726390c11b" />

#### Description:
This query finds patients whose total payments are higher than the average total payment across all patients. It first groups payments by patient to calculate how much each person has paid, then compares those totals to the overall average using a subquery. The HAVING clause filters the results to only show patients whose total payments are above that average.

#### 8. List all patients who have invoices with no payments at all. The finance team can use this to identify unpaid balances and focus on follow-up actions. 
SQL: [LEFT JOIN or NOT EXISTS]
<img width="1768" height="1155" alt="Screenshot 2026-04-03 222127" src="https://github.com/user-attachments/assets/cbd0c963-7b5a-4b49-a514-1c0d323ed67f" />

#### Description:
This query finds patients who have invoices that do not have any payments recorded. It joins the Patients, MedicalEncounters, and Invoice tables to connect patients to their invoices, and then uses a NOT EXISTS subquery to check if any payments exist for those invoices. If no payment is found, the invoice is included in the results.

#### 9. Include the patient’s ID, first name, last name, prescription ID, and medication name. Make sure patients with no prescriptions still appear in the results.
- This lists every patient along with any prescription information, even if the patient has never received a prescription.
- (SQL Concepts used: LEFT JOIN)
<img width="1760" height="1153" alt="Screenshot 2026-04-03 222134" src="https://github.com/user-attachments/assets/6484a96c-e203-45ce-adcc-73f247f2b215" />

#### Description:
This query lists all patients and any prescriptions they may have. A LEFT JOIN is used so that patients without prescriptions are still included in the results. If a patient does not have a prescription, the prescription fields will show as NULL. The results are ordered by patient name and prescription ID to keep the output organized.

#### 10. Calculates the total payments made by each patient and identifies those in the top 50% of total spending
<img width="1769" height="1137" alt="Screenshot 2026-04-03 222141" src="https://github.com/user-attachments/assets/0bcac149-6c73-4194-b123-884ea14e8147" />

#### Description:
This query highlights the highest-paying patients, enabling managers to focus resources on making sure these people are getting the health they need. This helps increase loyalty to the programs and also strengthens relationships with important patients.
## Database Information
Name of the database: ns_Sp26_61608_Group1
Additional Information: each marked query can be called using. _________

### Name of the database: 
ns_Sp26_61608_Group1 
### Additional Information: 
Each marked query can be called using CALL GP_Q1();
