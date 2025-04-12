# onkoplus
Application for unifying data for oncological medical care, creating a filter for looking the clinic that solves person's problem and creating a doctor's appointment created during Rakathon

It is more of an idea of a large project that can help to unify different oncological centers, help patients to find any needed information about the medical care that they need and, in scaling perspective, can help to unify medical system over the whole Czech republic and digitalize making doctor's appointments.

Project consists of different parts:
1) Creating one database for all the medical clinics and hospitals that help to diagnose/cure/prevent/etc. oncological problem
2) Creating an algorithm that help to find the nearest clinic that solves the patient's problem (KOC, ROC, HOC, )
3) Creating a system to make an appointment to a doctor that person needs and for a doctor to see all the appointments
    with the whole information about the patient (previous appointments, examinations, diagnosis, etc.)

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

Besides that, there is such data as:
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
 
 information about the address of the certain clinic, type of preventive medicine/examination that can be done in this clinic, website

The idea was to also add the capacity of a certain clinic, but, unfortunately, the only portal that was providing this information had a disclaimer that it wasn't renewed from the year 2007
BUT by using one unified appointment system this problem can be solved automatically (more about that in the part 3)

ROOM FOR IMPROVEMENT: Clinics do not provide what insurances do they cooperate with (only on uzis), this can be a very useful information for the foreigners that do not have VZP or any other govermental insurance. As hackathon is a very time-limited event, there was little to no time to pay attention to all the needed details and add all of them to this database, so I was focusing only on the main ones


# Algorithm for looking for a clinic



Materials:
Information where exactly information was taken from:
1. https://www.onconet.cz/index.php?pg=kraj (!Information isn't actualized on the website!)
2. https://www.vzp.cz/pojistenci/zdravotnicka-zarizeni-a-specializovana-centra/specializovana-pracoviste/regionalni-onkologicka-centra
3. https://www.linkos.cz/pacient-a-rodina/lecba/kde-se-lecit/seznam-koc/
4. https://nrpzs.uzis.cz/index.php?pg=home--download
