# JBosss

## few basic terminologies
- Jar - Java Archive, Groupe of _.class_ files
- War - Web Archive, contains other web components like:
    - Servlets
    - JSP
    - HTML
    - CSS
    - JS
    - XML
- EAR - Enterprise archive
- EAR contains web related components and non-web J2EE components as well
- Web server - userd for web related projects
- Application servers - used for web related and non-web related J2EE projects

## Questions
__What is JTA?__
- Java Transaction API - Standard Java interfaces between a transaction manager and the parties involved in a distributed transaction system.

__What is the purpose of JMX agent?__
- Java Management Extensions (JMX) is a Java technology that supplies tools for managing and monitoring applications.

__What is jboss cache?__
- Frequently accessed Java objects are cached by initialyzing JBoss cache to improve the performance of e-business applications

__What is JNDI?__
- Java Naming and Directory Interface (JNDI) is an application programming interface (API) that provides naming and directory functionality to applications written using the Java programming language

__How to view the contents of a jar?__
- jar –tf <filename.jar>
  
  (The jdk bin path should be set properly to run the above, you can directly run it as in the below example as well 
"C:\Program Files\Java\jdk1.8.0_241\bin\jar" –tf filename.jar)

__What is the name of the web server in JBOSS EAP?  What is the default port of the web server?__
- Undertow is the name of the web server.
- 8080 is the default port of the web server in JBOSS eap

__What is Wildfly in JBOSS EAP?__
- Wildfly is the application server in JBOSS EAP. Previously the application server in JBoss EAP was called as JBoss AS.

__What is clustering? Which component of JBOSS EAP does this clustering?__
- Clustering is the concept of grouping of multiple resources but still they appear as a single entity to the end user.
- Clustering is achieved through the component called as _Infinispan_ in JBoss EAP

__Which specification is followed in JBoss EAP to store data onto the database?__
- Persistence stands for storing the data onto a database. The Java Persistence API (JPA) is a Java specification for accessing, persisting, and managing data between Java objects and a relational database.

__How to choose the right JDK for Wildfly and JBoss EAP 7?__
- [Link to overview](http://www.mastertheboss.com/jbossas/wildfly-8/choosing-the-jdk-for-wildfly-and-jboss-eap-7/)

__JBoss Installation__
- Straight installation of _jboss-eap-installer.jar_
- After installation go to _installpath_ __...\bin\__ and try to start server with _standalone.bat_. Pay attention on Java JDK version and to port for the application must be free. If the standard port ist busy, it is posable to change it in the _standalone.xml_ under _..\standalone\configuration_
- JBoss install service
  ```cmd
  service.bat install /name [name_of_service]
  ```
  It can take a while. After the installation is over, you can open _Services_ and a new service will appear there (look for [name_of_service] that was given by installation).

- Delete a service in Windows:
    - SC STOP [shortservicename]
  	- SC DELETE [shortservicename]

-  Service starten:
    - net start [service name] <br>
    oder
    - sc start [service name]

-  kill service.msc:
    - sc queryex [service name] # JBoss-eap-7.1_Int
    - taskkill /pid [pid number] /f

- For managing multiple site on the system, apache-Server is needed. It is necessary to configure a files for every application. _//apache/Apache24/conf/vhosts_
  