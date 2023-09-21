
Q. Aws 2 tier project of student.var

     Step 1:-
                   Firest of all login to aws account.
 

Step 2:-
           Now firstly you have to create your VPC(virtual private cloud). So go VPC service and then click on your VPC. And then click on create VPC to create your VPC.
   







Step 3:-
            Next you will see the vpc create setting. So choose resources to create vpc only. And the gave a name to tat VPC. 
 

Step 4:-
            And then you have to select ipv4 CIDR block so in that select IPv4 CIDR manual input and then have IPv4 CIDR I have get class three ipv4 192.168.0.0/24 then leave as it is and click on create VPC.
 






Step 5:-
              After that you have to create subnets so I will make to subnet one public and  second private. So to create subnet click on create subnet.
 

Step 6:-
             Now u will see subnet creates options so first select your VPC and scroll down.
 





Step 7:-
            Now  create 1st subnets by giving name and then select availability zone then select ipv4 CIDR block means range of IP’s I was selected 192.168.0.0/25 










Step 8:-
            Now create 2nd one subnet my giving name and then select availability zone and them gave t ipv4 second range and then click on create subnet. And your subnet was created.
            
 






Step 9:-
             Now  you have  to create a route table to connect your VPC, subnet and IGW.  So click on create route table.
 

Step 10:-
               Now  you will see the  setting of creating route table. So gave a route table name my-public-RT then select your VPC. And then click on create route table. And next create one more  RT as private.
 
 

 
 






Step 11:-
               Next  you have to create internet gateway so click on internet gateway session and then click on create internet  gateway.
 


Step 12:-
                 You will see the setting of creating  IGW. So gave it name and simply click on create internet gateway. Then select your internet gateway 
 

 













Step 13:-
               Now your VPC was created completed.  
 

Step 14:-
                So after all set go to VPC setting and select VPC and then click on resource map now to see the connection on VPC subnet route table and internet gateway. See the following image my VPC has  added all thing but not connected.
 





Step 15:-
               So first connect your subnet to your route table. Public subnet to public RT and private subnet to private RT. So go to subnet session and then select your public subnet and then click on route table option and then edit route table association. And after that select public route table and save .  and do as it is to private subnet to connect private RT.
 

 
















Step 16:-
                Now you have to connect public route table to IGW and private to NTG(nate gateway).
So go to route tables session and  then select your public route table and then click on routes option and then edit routes. And then click on add route and  then in first column select 0.0.0.0/0 and then next column select internet gateway option and then select IGW and then save it and your  Public RT connect to IGW.
 

 









Step 17:-
               Now connect NAT gateway to private RT. So first of all create NAT gateway. Click on NAT gateways session and then click on create NAT gateway to your VPC.
 

Step 18:-
                 Now you will see NAT gateway create setting so gave it name. and then select the public subnet and then click oon public connective type after that allocate elastic IP to NAT gateway. And then create NAT gateway.
 


Step 19 :-
                Now  you have to go route table session and then select your private route table after that click on routes option in down side and then edit routes.
 

Step 20:-
                Now you have to click on add route and after that click on first column and select 0.0.0.0/0 after that select second column and in that select nat gateway option and ten select your newly added Nat and save changes and your private subnet also connected to Nat by RT.
Now your vpc was ready to launch public and private instances. 









Step  21:-
               Now you have to launch instances public and private instance. So I will show only where to changes to do at the launching instance time. Go to ec2 services and then launch instance. At the instance launch setting edit network setting and then click VPC an select your own VPC.
 

Step 22:-
                Next select public subnet to launch public instance.
 







Step 23:-
                Gave it public IP because it is public instance enable it.
 

Step 24:
             After that create new security group and add port 8080 in that SG. 
 












 















	
Step 25:-
                After that add in user following script to run with launching instance means configured with launched instance. 
#! /bin/bash  = to inter in environment
Sudo –I =to change local user to root user
wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.92/bin/apache-tomcat-8.5.92.tar.g = to download package tomcat
tar –xzvf  apache-tomcat-8.5.92.tar.gz –C /opt = and after that download package is in the archive and compression format downloaded so we have extract it by tar command.
And after that launch your public instance.
 














Step 26:-
                After that launch a private instance with following configuration and see downwards ss for how it configure. Edit network setting and  add your VPC.
 
 













Step 27:-
                Now  select your private subnet and then disable auto assign public IP because this instance is not our public instance. After that add security group in which added port 3306 of mariadb and 22 to ssh.
  

Step 28:-
                Now add following user data and then launch it. Following user data is for installing mariadb service to your private server.
 
Step 29:-
               After that get access of your public instance and by drag and drop process get student.war and jdbc connecter file as name mysql-connecter in your public instance. 
 

               

Step 30:-
              And then mv or cp  that filee to apache’s file which we have install in /opt.
student.war mv or cp to /opt/apache-tomcat-8.5.92/webapps and 
mysql-connector.jar file mv or cp to /opt/apache-tomcat-8.5.92/lib
 






Step 31:-
              Now you have to start a tomcat so you have to run the .sh file of catalina.sh file for .sh file run we have to install a java package. So run command #yum install java –y.
 
 

Step 32:-
               Now you have ready to run .sh file of catalina so run command # ./catalina.sh start and then ./startup.sh file.
 







Step 33:-
             Now hit your public IP of instance and your hosting page is ready only remaining mariadb connecting for data save.
Type in browser as it is. = http://54.194.157.234:8080/student/
  

Step 34:-
                Now you have to get access of private instance by ssh key so get that key on public instance  which has connected to your private instance.
 

Step 35:-
               First gave the name to you public and private instance a machine as public machine to public and private to private. By command hostnamectl.
 
As it is when you gave access of it by ssh.





Step 36:-
            Now you have get private instance access by ssh key.
 
 

Step 37:-
               Check user data script was run or not by rpm –q and package name.    
 
Step 38:-
               Now run command mysql_secure_installation to configure and secure your data tables. And configure it.
 


Step 39-
                 Now login to your mariadb table by entering command mysql –u root –p12345. 

Step 40:-
               Create data base as name studentapp.
 

Step 41:-
              Now you have to create table as name students with its table configuration.
create table students (student_id INT NOT NULL AUTO_INCREMENT,student_name VARCHAR(100) NOT NULL,student_addr VARCHAR(100) NOT NULL,student_age VARCHAR(3) NOT NULL,student_qual VARCHAR(20) NOT NULL,student_percent VARCHAR(10) NOT NULL,student_year_passed VARCHAR(10) NOT NULL,PRIMARY KEY (student_id));
 

Step 42:-
                After that create user of mariadb to use that table and gave it all privilages. 
 
 
 

Step 43:-
                Now go back to your  public instance to gave endpoint of mariadb. When you get back go /opt/ apache-tomcat-8.5.92/conf and vim cntext.xml
 















Step 44:-
              Go to line number 21 and write there following script with edition of  it username and its password of mariadb and then endpoint of db and then database name and then save it.
			<Resource name="jdbc/TestDB" auth="Container" type="javax.sql.DataSource"
               maxTotal="100" maxIdle="30" maxWaitMillis="10000"
               username="USERNAME" password="PASSWORD" driverClassName="com.mysql.jdbc.Driver"
               url="jdbc:mysql://DB-ENDPOINT:3306/DATABASE"/>
 








Step 45:-
               After that Now  you have  to restart catalina.sh file of bin an also startup.sh file. And your database was connect to tomcat.
 
 
 


                                                           ***THEN END***

