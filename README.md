# Blood-Bank-Management-System


#ABSTRACT 

The Project describes the Blood Bank management system. This report will help you to  know in deep the actual work that has been done as a team work. The main objective of this
application is to automate the complete operations of the blood bank. They need to maintain  hundreds of thousands of records. Also searching should be very faster, so they can
find  required details instantly. Main objective is to create a system which helps them to complete  their work faster in simple way by using computer not the oldest way which
is used paper.  Also our project contains updated information and many things else. A Blood Bank stores blood of various blood groups. Many donors donate blood, each of  
different blood group/type. A donor may donate blood more than once and he is identified  by a donor id(DID), name, address, email, phone number and dob.
The blood donated by the  donor is characterized by blood type. Before each donor donates his blood, he is required to  register himself as a donor with the medical personnel
who works at the Blood Bank. The  medical personnel is identified by employee id, name, address, email, phone number, and  dob. The Blood Banks receives orders for blood from 
many hospitals for emergency purposes  and other surgical requirements and each blood bank issues the same of required blood type.




INTRODUCTION 

Today you can easily connect with anything through internet services. So online platform is  the best choice for our project. Blood Bank aims serving for human welfare. 
We have all the  information, you will ever need. Many people are here for you, to help you, willing to donate  blood for you anytime. We have done all the job, rest is yours.
Search the blood group you  need. You can help us by registering on Blood Bank if you are willing to donate your blood  when needed. As a proud member of Blood Bank and a
responsible human being, you can  help someone in need. So, donate blood in online. Person who need to donate blood may  register on our website with the help of username
and password. The persons who need blood  donor, they can search and find blood donors by using our website. After searching, a list of  donors will be displayed and user 
can get brief details about their contact details, email  including their location, so they can communicate. This project is mainly towards persons who are willing to donate 
blood to the patients.  Through this system it will be easier to find a donor for exact blood type and easy to build  the connection between donor & the blood bank authorities. 
The main intend of building this  software is to formal the procedure of blood donation & motivate donors in order to donation  blood. We have tried to maintain all those 
information of donor which is easily  understandable to the doctors which makes them easy to find the donor.

SYSTEM SPECIFICATION 
Software Requirements: 
a. WINDOWS OS 
b. DB BROWSER 
c. SQL SERVER/SQL LITE 

Hardware Requirements: 
a. RAM 512 MB AND MORE 
b. 2.8 GHZ PROCESSOR
5 
OBJECTIVE 
1. We’ll start with an virtual representation of our database with the  help of an ER diagram 
2. We’ll set up our database 
a. Donar Table 
b. Recipient Table 
c. Medical Personnel Table 
d. Blood Donation Table 
e. Blood Transaction Table 
3. We’ll create our views 
a. PatientSeen 
b. BloodStock 
4. We’ll create our Trigger 
a. eligible

1.0 VIRTUAL REPRESENTATION - ER DIAGRAM 
An Entity–relationship model (ER model) describes the structure of a database with  the help of a diagram, which is known as Entity Relationship Diagram (ER  Diagram). An ER model is a design or blueprint of a database that can later be  implemented as a database. The main components of E-R model are: entity set and  relationship set. 

 
2.0 DATABASE - TABLES 
2.1 DONAR TABLE 

# CODE: 

CREATE TABLE Donor( 
DonorID INT AUTO_INCREMENT 
NOT NULL , firstName VARCHAR( 50 ) NOT  
NULL, lastname VARCHAR( 50 ) not null, address  
VARCHAR( 60 ) not null, email VARCHAR( 100 )  
not null, phone VARCHAR( 20 ) not null, dob  
DATE not null, bloodType varchar (3)NOT NULL ,  
PRIMARY KEY ( donorID ) ); 
2.2 RECIPIENT TABLE 
CODE: 

CREATE TABLE Recipient(  
recipientID INT AUTO_INCREMENT NOT  
NULL , firstName VARCHAR( 50 ) NOT NULL,  
lastname VARCHAR( 50 ) not null, address  
VARCHAR( 60 ) not null, email VARCHAR(  
100 ) not null, phone VARCHAR( 20 ) not null,  
dob DATE not null, bloodType varchar (3)NOT  
NULL , PRIMARY KEY ( recipientID ) );

2.3 MEDICAL PERSONNEL TABLE 
CODE: 

CREATE TABLE MedicalPersonnel( empID INT  
AUTO_INCREMENT NOT NULL , firstName  
VARCHAR( 50 ) NOT NULL , lastname VARCHAR(  
50 ) NOT NULL , address VARCHAR( 60 ) NOT  
NULL , email VARCHAR( 100 ) NOT NULL , phone  
VARCHAR( 20 ) NOT NULL , dob DATE NOT 
NULL , PRIMARY KEY ( empID )  

2.4 BLOOD DONATION TABLE 
CODE:

CREATE TABLE BloodDonation( bloodID INT AUTO_INCREMENT, donorID  
INT NOT NULL , dateDonated DATETIME NOT NULL , quantity INT NOT  
NULL , PRIMARY KEY ( bloodID ) , FOREIGN KEY ( donorID ) REFERENCES  
Donor( donorID ) );
9 
2.5 BLOOD TRANSACTION TABLE 
CODE:

CREATE TABLE BloodTransaction( transactID INT AUTO_INCREMENT , empID INT NOT NULL , dateOut DATETIME NOT NULL ,  quantity INT NOT NULL , recipientID INT NOT NULL ,
bloodID INT NOT NULL , PRIMARY KEY ( transactID ) , FOREIGN KEY (  empID ) REFERENCES MedicalPersonnel( empID ) , FOREIGN KEY ( recipientID ) 
REFERENCES Recipient( recipientID ) , FOREIGN  KEY ( bloodID ) REFERENCES BloodDonation( bloodID ) ); 

 

3.0 Views 
3.1 Patient Seen  
This view is made to see which patient is been seen by which medical  
personnel on which dates by joining the tables  
medicalpersonnel,bloodtransaction and recipient. 
CODE: 

create view PatientSeen as select m.firstName||' '|| m.lastName as 'Medical Personnel',  
r.firstname||' '||r.lastName as 'Patient Name', dateOut as 'Date Seen' From  
MedicalPersonnel m, BloodTransaction b, Recipient r where m.empID = b.empID AND  
r.recipientID = b.recipientID order by m.lastName ASC 

3.1 BloodStock  
This view give us an idea about the stocks of blood quantity that is present to us for each blood type by joinig the  tables bloodDonation and bloodTransaction. 
CODE: 

create view BloodStock as select Donor.bloodType as 'Blood Type', sum(BloodDonation.quantity) as 'In Stock'from
BloodDonation join Donor on BloodDonation.donorID = Donor.donorID where BloodDonation.bloodID not in (select bloodID  from BloodTransaction) group by bloodType;


 4.0 Trigger 
4.1 Eligible 
A trigger to check whether the person is eligible or not for donating the blood. 
CODE: 

CREATE TRIGGER eligible BEFORE INSERT ON Donor BEGIN SELECT CASE WHEN ( new.dob > "2001-12-31") THEN  RAISE(ABORT,"Donor Not Eligible to donate blood") END; END

 CONCLUSION 
▪ In conclusion we had successfully implemented the project. 
▪ The project is designed and developed keeping in view that it should be user friendly, searching should be easy, and it should have the good and easy display. ▪ All the experiment result showed that average response time is decreased. ▪ User is provided the option of monitoring the records he entered earlier. He can  see the desired records with the variety of options provided by him.



746711/Blood-Bank-Management-System- Project-Report
