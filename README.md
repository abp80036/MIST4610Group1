# MIST 4610 Project 1
## Team Name: Group 1
## Team Members:
Lauren Harville - [@]()

Andrew Heighton - [@]()

Asanti Kumera - [@]()

Aiden Pfeiffer - [@]()

Doc Rush - [@docrush](www.github.com/docrush)

Violet Sofish - [@]()
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
## Queries
## Database Information
Name of the database: ns_Sp26_61608_Group1
Additional Information: each marked query can be called using. _________
