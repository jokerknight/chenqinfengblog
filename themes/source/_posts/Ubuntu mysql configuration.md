title: "Ubuntu mysql configuration"
date: 2016-02-19 13:38:00 
categories: [服务器]
tags: [mysql,Ubuntu,3306端口,外网访问]
---


# Ubuntu mysql configuration


----------


## Install





    apt-get install mysql-server 
    
During the setup it will prompts you set root password, be sure to keep in mind importantly! 


----------


----------


## Check 



### Login

    
    mysql -u root -p 
   

then enter the password which set during the setup.

### DDL/DML/DDL 

 - DDL

| COMMOND       | DESCRIPTION   |  
| ------------- |:-------------:| 
| CREATE        | create tables/view/object |  
| ALTER         | alter object      | 
| DROP          | drop databases/tables/view      |


 - DML

| COMMOND       | DESCRIPTION   |  
| ------------- |:-------------:| 
| SELECT        | query record from one or multiple tables |  
| INSERT         | create record      | 
| UPDATE          | update record      | 
| DELETE          | delete record       |
 

 - DDL

| COMMOND       | DESCRIPTION   |  
| ------------- |:-------------:| 
| GRANT        | granted permission |  
| REVOKE         | recycle permission      | 

and others.


----------


----------


## Configuration 


### Allow NetWork Access

 - Check 3306 port

		netstat -an|grep 3306
		tcp6    0      0     127.0.0.1:3306    LISTEN
	look at that  it's just allow local to access 3306 port 

 - Allow access everywhere 
	
		vi /etc/mysql/mysql.conf.d/mysqld.cnf
	
	comments bind-address = 127.0.0.1 

 * Restart Ubuntu 
	 	
		shutdown -r now

 * Check 3306 port again

		netstat -an|grep 3306
		tcp6    0      0     :::3306    LISTEN
This means that you can use port 3306 to access mysql success! 

### Update root access permission 

		sudo mysql -u root -p  
		mysql>grant all privileges on *.* to 'root'@'%' identified by 'xxxxxx';


xxxxx is password.
then let settings available.

    mysql>flush privileges;​

### Restart mysql service

 if you have some other custom configuration, such as buffer_pool_size/log_file_size or others, you should restart you mysql service.

    service mysql restart 


----------


----------


## Finally
Congratulations! you have success resolved Ubuntu Mysql Configuration!
now, you can access mysql via mysql client or program success!


----------
