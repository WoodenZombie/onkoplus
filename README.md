# Onko+: Unified oncology appointment system

Application for unifying data for oncological medical care, creating a filter for looking the clinic that solves person's problem and creating a doctor's appointment created during Rakathon

It is an idea of a large project that can help to unify different oncological centers, help patients to find any needed information about the medical care that they need and digitalize making doctor's appointments.

Project consists of 3 different parts:
1) Creating one database for all the medical clinics and hospitals that help to diagnose/cure/prevent/etc. onkological problem
2) Creating an algorithm that help to find the nearest clinic that solves the patient's problem based on their needs, location of the clinic and its capacity
3) Make an application that helps to make an appointment to a doctor (for the patient) and to provide the time for the appointments, see who and when made an appointment and plan the schedule (for the doctor)

# Database

This example of a database is created from the publicly provided information

All the hospitals are divided by the region that they are located in

Based on the type of help, clinics are divided into different categories (some clinics can have more than one):
- KOC - Komplexní onkologické centrum
- ROC - Regionální onkologická centra
- DOC - Dětské onkologické centrum
- HOC - Hematoonkologické centrum
- MS - Akreditované centrum mamografického screeningu
- CS - Akreditované centrum kolonoskopického screeningu
- LDN - Léčebna pro dlouhodobě nemocné a hospise
- PSKOC - pracoviště spolupracující s KOC

Besides that, there is such data as (but not limited to):
- Is it a govermental or a private clinic
- Address
- (If ROC) Type of tumours that clinic specializes on, that are also divided into different categories:
- - NKO - Nádorů kolorekta  
- - NHC - Hepatocelulárního karcinomu 
- - NPL - Nádorů plic
- - GIS - Gastrointestinálního stromálního tumoru
- - NPR - Nádorů prsu 
- - ZNP - Zhoubných nádorů prostaty 
- - NLE - Nádorů ledvin 
- - NOV - Nádorů ovárií a dělohy
- Type of available examinations
- Category of diagnostical fiels of medicine
- Medical equipment
- Is there a possibility of hospitalisation
- Website
- Email
- Ordination contact phone number
- What insurances does this clinic cooperates with
- Nearest appointment time (more about that in the part three)

Example of a collected and classified data you can find in clinics.json
Due to time limitations of the hakathon it is limited to three clinics only, but the final database will have much more parameters and all the medical care providers that specialize in oncology or cooperate with KOC
Data was automatically crawled using artificial intelligence from clinics' official websites and wasn't verified in National registr of medical care providers so it can contain mistakes, data is provided only for the purpose of displaying future data structure

# Algorithm for looking for a clinic

# Unified oncology appointment application

## System Overview
The Onko+ is a centralized platform designed to:

- Provide patients with access to a unified database of all accredited oncology clinics in the Czech Republic.
- Optimize clinic capacity by prioritizing ROC when possible, reducing the burden on KOC
- Enable online reservations with available specialists based on patient needs.

## Expected Outcomes
For Patients:

- Faster access to correct clinic type
- Reduced wait times by optimizing capacity.

For Healthcare System:
- Lower KOC overload by redirecting patients to ROCs (if possible).
- Better resource utilization (equipment, specialists).

## Workflow

1. Patient->API: Request consultation
2. API->Database: Query clinics
3. Database->API: List of matching clinics
4. API->Facility: Check doctor availability
5. Facility->API: Confirm slot
6. API->Patient: Show booking options
7. Patient->API: Confirm reservation
8. API->Facility: Finalize booking
9. Facility->API: Reservation confirmed
10. API->Patient: Send confirmation

# GDPR Compliance Documentation for Onko+

Onco+ processes sensitive personal and health data, making GDPR compliance critical. This part of documentation outlines the measures to ensure full compliance with Regulation (EU)

## Types of Data Processed
Category - Examples - GDPR Classification
Personal Data - Name, email, phone number, address - Article 4(1) GDPR
Health Data	Diagnosis - (ICD-10 codes), prescribed medications, medical history - Special Category (Art. 9)
Appointment Data - Clinic location, doctor’s name, date/time of visit - Personal Data
Technical Data - IP address, device ID, cookies - Personal Data

## Explicit Consent for Health Data
Workflow:

- Separate consent checkbox for processing health data.
- Granular options (e.g., "Share diagnosis with clinic only").

UI:
☑ I consent to the processing of my health data (ICD-10 codes, medications) for the purpose of booking this oncology appointment.

## Third-Party Data Sharing
A. Clinics & Doctors
Data Shared: Appointment details, diagnosis (if consented).
GDPR Compliance: Signed Data Processing Agreements with all facilities.

B. Cloud Providers
Measures:

- Data stored in EU-based servers
- DPA in place with provider.

# Security & GDPR Measures
## A. Authentication

Architecture integrates BankID (Nordic e-identification standard) for secure patient authentication while maintaining GDPR compliance for health data processing.

BankID Benefits:

- No password storage (relying on bank security)
- eIDAS-compliant (EU standard)

Session Handling:

- Short-lived JWT tokens (1h expiry)
- Refresh tokens with re-authentication

## B. Data Protection
Health Data Isolation:

- Stored separately from BankID identifiers
- Linked via pseudonymous IDs:

appointments:
  booking_id: "a1b2c3"
  patient_ref: "bankid:123456" -> Not directly identifiable 
  clinic_id: "roc_pardubice"

## C. Audit Trail
Logs: 

- Who accessed health data (BankID sub + timestamp)
- Purpose (e.g., "appointment booking")

Tools:

- Azure Monitor

References:
1. Czech National Cancer Control Program: https://www.onconet.cz/index.php?pg=kraj 
2. List of regional oncological centers and what kind of tumours they specialize on: https://www.vzp.cz/pojistenci/zdravotnicka-zarizeni-a-specializovana-centra/specializovana-pracoviste/regionalni-onkologicka-centra
3. List of komplex oncological centers: https://www.linkos.cz/pacient-a-rodina/lecba/kde-se-lecit/seznam-koc/
4. Database of medical care providers available for downloading: https://nrpzs.uzis.cz/index.php?pg=home--download
5. Definition of ROC and what kind of help they can provide: https://www.linkos.cz/files/pro_odborniky/napl_onko_prog/sled_predikce_onko/Forum/04_2024/9-Spoluprace-KOC-ROS-delegovani-lecby-aktulnI-vyvoj-z-pohledu-VZP.pdf
6. Inspiration (Estonian unified healthcare govermental system): https://www.tehik.ee/en
