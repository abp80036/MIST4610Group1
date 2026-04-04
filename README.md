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


![query](https://private-user-images.githubusercontent.com/272872318/573745786-c1542fbb-475f-44e0-8e4a-da17a9bd0eb8.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1Nzg2LWMxNTQyZmJiLTQ3NWYtNDRlMC04ZTRhLWRhMTdhOWJkMGViOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00NTA4MWE2MzczMGJhYjFlNDUzNGU3MTFiMjE2NGI5Y2U3MjRlMWM1MmExNWYxZGJiMWM5OTIxZDg0ZGU1MjZiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.1oGzf88HS4S2XbfQ8fx-dfqEKsFSkL7p2Ub1CbgGWsM)
#### Description: 
This query shows patients whose email addresses end in ".com". It uses a regular expression (REGEXP) to filter emails that match this pattern. The results return the patient’s information for anyone whose email ends with ".com".


#### 2. Find all medical encounters that are currently marked as “Scheduled.” Include the encounter ID, patient ID, provider ID, and appointment date.
![query](https://private-user-images.githubusercontent.com/272872318/573745789-ccce2e53-9313-4414-87b3-87fd660493ba.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1Nzg5LWNjY2UyZTUzLTkzMTMtNDQxNC04N2IzLTg3ZmQ2NjA0OTNiYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kYzQzMDhhZTBjYzU4NjFlNDc5YWIzODM3YzkxMmRjZGEzYjVmMzU4ZjEzZmFiNjhiZDhiNWI0M2MyYjg4M2JhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.E3GsEtB9ag7h_MkkDVXPsB38LPzzxJM85FU6iX2I6MM)
#### Description:
This query finds all medical encounters that currently have a status of "Scheduled." The subquery first identifies the encounter IDs that meet this condition, and then the main query pulls the encounter ID, patient ID, provider ID, and appointment date for those records.

#### 3. List the patient name and invoice amount for payments that are greater than $3000 that are associated with completed appointments that have been paid for. Additionally, order the results by invoice amount in ascending order. The finance team can use this to identify higher balances and prioritize follow-up actions.
- SQL: [WHERE and ORDER BY]
![query](https://private-user-images.githubusercontent.com/272872318/573745791-3545517d-d129-49e4-841f-9c1fc5487899.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1NzkxLTM1NDU1MTdkLWQxMjktNDllNC04NDFmLTljMWZjNTQ4Nzg5OS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jYzRhZjVhNzcyOTRhNGUxZWM5OGJkMzU0ZjJiMGExOWJmZjRiYWQ1MzVjYjI4YmE1Njc3MWIyZGY1NDgxOWYyJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.qk617wNoB5lUGukTW1mIfwVSDSbY2_7K3wGLDthNTyE)
#### Description:
This query finds patients who have invoice amounts greater than $3000 from appointments that have been marked as paid. It joins the Patients, MedicalEncounters, and Invoice tables to connect patient information with their billing records. The WHERE clause filters the results based on the invoice amount and appointment status, and the ORDER BY sorts the results from lowest to highest invoice amount.

#### 4. Lists all patients who haven't sent at least one message
![query](https://private-user-images.githubusercontent.com/272872318/573745794-6ea7bb89-abe8-45b0-9dc1-1b887739c33a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1Nzk0LTZlYTdiYjg5LWFiZTgtNDViMC05ZGMxLTFiODg3NzM5YzMzYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hZTRkYzE5YTYzMDI4ZmQwNjkxM2M0NDFkYjJjYmExZmJlNWUyOWUwOTIzZWE0MDBiOGQxNTExMTIyMDU2NjY4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.qIj4icrl7zWzvWi72zeCpv55q5AeBbjbpSQSwiydXVo)
#### Description:
This query finds patients who have not sent any messages. It checks the Communications table to see if there are any records linked to each patient, and if none exist, that patient is included in the results. The NOT EXISTS condition makes sure only patients with no messages are returned.
## Complex Queries
#### 5. For each patient, calculate the total amount billed (from invoices) and the total amount paid (from payments). Display the patient’s name along with both totals, even if a patient has no payments recorded.
![query](https://private-user-images.githubusercontent.com/272872318/573745796-bb18f18f-ad10-42f4-913b-55e93b08bbd1.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1Nzk2LWJiMThmMThmLWFkMTAtNDJmNC05MTNiLTU1ZTkzYjA4YmJkMS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01MjBjOTgzZjZkY2Y0NjM4OGZmZjk4NDI5MTUyMzUyYmIwZmE3ZjM0N2I4OGVhZDE4M2NjYjNmOTAwYjAwNjU5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.RRrMB1peVDpGd77vHar2aVEtuvWoQstNCRJMKyZ2_Kw)
#### Description:
This query calculates how much each patient has been billed and how much they have paid so far. It uses subqueries to add up the total invoice amounts and the total payments for each patient. The query still shows all patients even if they do not have any payments recorded, which means some totals may show as NULL. This helps compare what each patient owes versus what they have already paid.

#### 6. Identify the provider who has handled the highest number of medical encounters. Display the provider’s name and the total number of encounters they have managed.
![query](https://private-user-images.githubusercontent.com/272872318/573745798-176eb1b1-2ebd-46c4-93d0-4c480b08fab5.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1Nzk4LTE3NmViMWIxLTJlYmQtNDZjNC05M2QwLTRjNDgwYjA4ZmFiNS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0xZDM3ZGRhYWIwNGM3NWU4OGNlOGQ3MDRhMDMyODVmMWRiMDZjOGQwOTZmYTY4NDRjOGU2MDM2Mjg5ZjJmOWIzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.YbLW1DywBBkoWM7_Sf5LiVpGG83ija_XnjfW-Kjk-ik)
#### Description:
This query finds the provider who has handled the most medical encounters. The subquery counts how many encounters each provider has and orders them from highest to lowest, then selects the provider with the highest total. The main query then returns the name of that provider.

#### 7. List patients whose total payments exceed the average payment amount across all patients. This identifies patients with high payments that contribute to the overall revenue made, which can impact future business strategies. 
SQL: [SUBQUERY]
![query](https://private-user-images.githubusercontent.com/272872318/573745800-9f12b9cb-fd9f-422c-89db-73947776c507.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1ODAwLTlmMTJiOWNiLWZkOWYtNDIyYy04OWRiLTczOTQ3Nzc2YzUwNy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01N2U5NWY2MzZlNTRmZjYyOTYyMGQxMDE4MmQwMGM1NDA0NDE2YmQxNDE1ZTNjNmUwODVhYzZhNzkwYzFhYWMwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.xVI5Wg2Yx_pnrvEH-lvwWrao3R462HRB63aXLlqA8Vg)
#### Description:
This query finds patients whose total payments are higher than the average total payment across all patients. It first groups payments by patient to calculate how much each person has paid, then compares those totals to the overall average using a subquery. The HAVING clause filters the results to only show patients whose total payments are above that average.

#### 8. List all patients who have invoices with no payments at all. The finance team can use this to identify unpaid balances and focus on follow-up actions. 
SQL: [LEFT JOIN or NOT EXISTS]
![query](https://private-user-images.githubusercontent.com/272872318/573745802-56be12e0-a96f-4a1c-9d23-9a5204f2a5f2.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1ODAyLTU2YmUxMmUwLWE5NmYtNGExYy05ZDIzLTlhNTIwNGYyYTVmMi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01ZDNiZTI1NDgxNzUzNWY5M2I0OGJlYTlhZmNjNDkxYTkwOTE1ZTQ2MGRiYzE2NWI3MzQzMDkyMTMxZjFiMmUxJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.vwZmunNydb-KmHSqKV6I9oHjE5zMBTLEzyUYeXVzH2I)
#### Description:
This query finds patients who have invoices that do not have any payments recorded. It joins the Patients, MedicalEncounters, and Invoice tables to connect patients to their invoices, and then uses a NOT EXISTS subquery to check if any payments exist for those invoices. If no payment is found, the invoice is included in the results.

#### 9. Include the patient’s ID, first name, last name, prescription ID, and medication name. Make sure patients with no prescriptions still appear in the results.
- This lists every patient along with any prescription information, even if the patient has never received a prescription.
- (SQL Concepts used: LEFT JOIN)
![query](https://private-user-images.githubusercontent.com/272872318/573745804-8d15488d-ee67-4799-8761-a567e4ef492f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1ODA0LThkMTU0ODhkLWVlNjctNDc5OS04NzYxLWE1NjdlNGVmNDkyZi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT04YjdlNzUzNzE4YTliMzAwODc5MzNlM2YwNWFhNDQ3ZDU3ZmZiNDgzOWJkYWRkYjUwODgzMDcxYTQwMGRiZmIwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.ehF9CNTWVCdHrGCgV1l7p8QJASRBvCyOqWV8V9G-7sk)
#### Description:
This query lists all patients and any prescriptions they may have. A LEFT JOIN is used so that patients without prescriptions are still included in the results. If a patient does not have a prescription, the prescription fields will show as NULL. The results are ordered by patient name and prescription ID to keep the output organized.

#### 10. Calculates the total payments made by each patient and identifies those in the top 50% of total spending
![query](https://private-user-images.githubusercontent.com/272872318/573745806-aa98aaed-a28e-4716-a9a8-2a669d5732ab.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzUyNjc5NjksIm5iZiI6MTc3NTI2NzY2OSwicGF0aCI6Ii8yNzI4NzIzMTgvNTczNzQ1ODA2LWFhOThhYWVkLWEyOGUtNDcxNi1hOWE4LTJhNjY5ZDU3MzJhYi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQwNFQwMTU0MjlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMjM2MmUxZDYxZDFhM2E2YmZkYTE4MGE5ZjJmYzRiYWJlMWIyZjQ4YTVkZjcxOGUxODkwMzhjNjJmYjIxYjVhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.GQub_GCKC2lnxwlc--TRdlaMgXDZuH6oaoeR9TqrxTw)
#### Description:
This query highlights the highest-paying patients, enabling managers to focus resources on making sure these people are getting the health they need. This helps increase loyalty to the programs and also strengthens relationships with important patients.
## Database Information
Name of the database: ns_Sp26_61608_Group1
Additional Information: each marked query can be called using. _________

### Name of the database: 
ns_Sp26_61608_Group1 
### Additional Information: 
Each marked query can be called using CALL GP_Q1();
