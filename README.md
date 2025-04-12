# Onko+: Unified oncology appointment system
Application for unifying data for oncological medical care, creating a filter for looking the clinic that solves person's problem and creating a doctor's appointment created during Rakathon

It is an idea of a large project that can help to unify different oncological centers, help patients to find any needed information about the medical care that they need and digitalize making doctor's appointments.

Project consists of 3 different parts:
1) Creating one database for all the medical clinics and hospitals that help to diagnose/cure/prevent/etc. onkological problem
2) Creating an algorithm that help to find the nearest clinic that solves the patient's problem based on their needs, location of the clinic and its capacity
3) Make an application that helps to make an appointment to a doctor (for the patient) and to provide the time for the appointments, see who and when made an appointment and plan the schedule (for the doctor)

# Database

This example of a database is created from the information provided by the website #1 in section "Materials"

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

Example of a collected and classified data you can find in onko_hospitals.json
Due to time limitations of the hakathon it is limited to three clinics only, but the final database will have much more parameters and all the medical care providers that specialize in oncology or cooperate with KOC
Data was automatically crawled using artificial intelligence from clinics' official websites and wasn't verified in National registr of medical care providers so it can contain mistakes, data is provided only for the purpose of displaying possible data structure

# Algorithm for looking for a clinic

# Unified oncology appointment application

Materials:
1. Czech National Cancer Control Program: https://www.onconet.cz/index.php?pg=kraj 
2. List of regional oncological centers and what kind of tumours they specialize on: https://www.vzp.cz/pojistenci/zdravotnicka-zarizeni-a-specializovana-centra/specializovana-pracoviste/regionalni-onkologicka-centra
3. List of komplex oncological centers: https://www.linkos.cz/pacient-a-rodina/lecba/kde-se-lecit/seznam-koc/
4. Database of medical care providers available for downloading: https://nrpzs.uzis.cz/index.php?pg=home--download
5. Definition of ROC and what kind of help they can provide: https://www.linkos.cz/files/pro_odborniky/napl_onko_prog/sled_predikce_onko/Forum/04_2024/9-Spoluprace-KOC-ROS-delegovani-lecby-aktulnI-vyvoj-z-pohledu-VZP.pdf
