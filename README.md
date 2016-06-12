**This is an example of how to use SoapUI to test web services**

**Prerequisites**
* JDK 1.7+ is installed and %JAVA_HOME%\bin added to PATH
* ANT 1.8+ is installed (code.google.com/p/winant/)
* GIT CMD client is installed (like GIT BASH)
* SoapUI 5.2.1 (smartbearsoftware.com/distrib/soapui/5.2.1/SoapUI-5.2.1-windows-bin.zip) is installed
* MySQL 6.3 (dev.mysql.com/downloads/mysql) is installed
* Hotel Reservation database is created - run .\dbscripts\HotelReservationDBSchema.sql in MySQL
* MySQL database connection credentials are updated: .\conf\mysql.properties: username and password
* MySQL JDBC driver jar (dev.mysql.com/downloads/connector/j/5.1.html) is placed into %AXIS2_HOME%\lib
* Database instance is up: MySQL Workbench -> Instance -> Startup /Shutdown -> Start server
* Apache Axis2-1.6.1 web service container (http://axis.apache.org/axis2/java/core) is installed (AXIS2_HOME is pointing to its directory)
* rampart-1.6.1 web services security (archive.apache.org/dist/axis/axis2/java/rampart/1.6.1/) is installed:
  - RAMPART_HOME is pointing to its directory
  - rahas-1.6.1.mar and rampart-1.6.1.mar are placed into %AXIS2_HOME%\repository\modules
  
**How to build and deploy**
* clone this repository locally 
* cd to .\build>
* ant
* copy .\HotelReservation.aar into %AXIS2_HOME%\repository\services\ 

**How to run**
* Run %AXIS2_HOME%\bin\axis2server.bat
* goto localhost:8080/axis2/services: you should see three web services listed on a web page
* open .\SoapUI\HotelReservationProject-soapui-project.xml in SoapUI
* Navigate to GuestManagementServiceSoap11Binding -> addGuest -> Request 1: Submit request (Alt+Enter):
  - should receive "true" in response
  - MySQL Workbench - New SQL: SELECT * FROM hotel_reservation_db.guest_t; - should see the newly added guest
  



