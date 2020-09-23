# DAMN VULNERABLE WEB APPLICATION

Damn Vulnerable Web Application (DVWA) is a PHP/MySQL web application that is damn vulnerable. Its main goal is to be an aid for security professionals to test their skills and tools in a legal environment, help web developers better understand the processes of securing web applications and to aid both students & teachers to learn about web application security in a controlled class room environment.

The aim of DVWA is to practice some of the most common web vulnerabilities, with various levels of difficulty, with a simple straightforward interface. Please note, there are both documented and undocumented vulnerabilities with this software. This is intentional. You are encouraged to try and discover as many issues as possible.
## Download

```sh
While there are various versions of DVWA around, the only supported version is the latest source from the official GitHub repository. You can either clone it from the repo:

git clone https://github.com/ethicalhack3r/DVWA.git

```
In Linux environment localhost files are stored in /var/www/html directory, so we open a terminal and change our directory to that directory using following command:
 
 ```sh
 cd /var/www/html
 ```
 Here we clone DVWA from it's Github repository. To clone it we run following command:
 ```sh
 git clone https://github.com/ethicalhack3r/DVWA
 ```
 Then we change the permission on dvwa directory by using following command:-
 ```sh
 sudo chmod -R 777 DVWA/
 ```
 Now we have to setup this web application to run properly for that we have to go into /dvwa/config directory.
 ```sh
 cd DVWA/config/ls
 ```
 This file contains default configuration. We need to make a copy of this file with .php extension name, we are coping this file because in future if anything goes wrong then we have the default values. So we copy this file with .php extension name using following command:-
 ```sh
 cp config.inc.php.dist config.inc.php
 ```

Then we use nano editor to make changes on our newly created PHP file.
```sh
 nano config.inc.php
 ```
We will make changes in this part the p@ssw0rd to pass and the user from user. Watch the following 
 ```sh
$_DVWA = array();
$_DVWA[ 'db_server' ]   = '127.0.0.1';
$_DVWA[ 'db_database' ] = 'dvwa';
$_DVWA[ 'db_user' ]     = 'user';
$_DVWA[ 'db_password' ] = 'pass';

 ```
 Then we save it using CTRL+X and press Y to save changes and Enter button to save and exit.

## configuring the database.

We start the mysql at first using following command:-
```sh
 service mysql start
 ```
 Now let's login to mysql using following command:-

```sh
 sudo mysql -u root 
 ```
 Now we create a database 
 ```sh
 create database dvwa;
 ```
 Then  we start with creating a new user by applying following command:-
 ```sh

 create user 'user'@'127.0.0.1' identified by 'pass';

 ```
 Then we grant this user all the privileges over the database.
 ```sh
 grant all privileges on dvwa.* to 'user'@'127.0.0.1' identified by 'pass';

 ```
 ## configure our apache2 server

 Here we are using version 7.3, if we use another version then the path might be change.
 ```sh
 cd /etc/php/7.3/apache2
 ``` 
 Here we configure the ' php.ini ' file using gedit.
 ```sh
 sudo gedit php.ini
 ```
 Using find function We need to change the allow_url_fopen and allow_url_include values to <mark>ON</mark>
 Then we start the apache2 server
 ```sh
 service apache2 start
 ```
 Let's open the browser and navigate to 127.0.0.1/dvwa/ first open will open the setup.php
 ![Final]()
  * Here we scroll down and click on "Create/Reset Database".

  * Then it will create and configure the database and we redirected to DVWA login page.
  ![Final1]()

  The default login is

    Username:- admin
    Password:- password

 After login we are in Damn Vulnerable Web Applications main page. Here is some general information and warnings. 
 ![final2]()  

 

