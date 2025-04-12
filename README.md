# onkoplus
Application for creating a doctor's appointment created during Rakathon


Project consists of different parts:
1) Creating one database for all the medical clinics and hospitals that help to diagnose/cure/prevent/etc. cancer
2) Creating an algorithm that help to find the nearest clinic that solves the patient's problem
3) Creating a system to make an appointment to a doctor that person needs and for a doctor to see all the appointments
    with the whole information about the patient (previous appointments, examinations, diagnosis, etc.)

# Database

This database is created from the information provided by the website #1 in section "Materials"

All the hospitals are divided by the region that they are located in

Based on the type of help, clinics are divided into different categories (some clinics can have more than one):
- KOC - Komplexní onkologické centrum
- DOC - Dětské onkologické centrum
- HOC - Hematoonkologické centrum
- MS - Akreditované centrum mamografického screeningu
- CS - Akreditované centrum kolonoskopického screeningu
- LDN - Léčebna pro dlouhodobě nemocné a hospise
- PM - preventive medicine or pracoviště spolupracující s KOC

Besides that, there is an information about the address of the certain clinic, type of preventive medicine/examination that can be done in this clinic, website

The idea was to also add the capacity of a certain clinic, but, unfortunately, the only portal that was providing this information had a disclaimer that it wasn't renewed from the year 2007
BUT by using one unified appointment system this problem can be solved automatically (more about that in the part 3)

ROOM FOR IMPROVEMENT: Clinics do not provide what insurances do they cooperate with, this can be a very useful information for the foreigners that do not have VZP or any other govermental insurance


# Algorithm for looking for a clinic



Materials:
Mapa zdravotnických zařízení podílejících se na péči o onkologického pacienta:
1. https://www.onconet.cz/index.php?pg=kraj
