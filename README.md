Kargo-Code-Sample
=================

This project is a code sample for a shopping cart system that is running under apache web sever.

The application realizes the following features:
1. Login into the system. Username is "admin", and password is "1234".
2. Add product into the cart.
3. Show shopping cart. Do CRUD opeations for the cart.


Before running this application, there are some steps need to be done first.

1. Modify the apache httpd.conf file, allow using vhost
2. Modify the httpd-vhost.conf file, add the following:
	<VirtualHost *:80>
	  DocumentRoot "/usr/local/zend/apache2/htdocs/kargo/public"
	  ServerName kargo-local.com
	  SetEnv APPLICATION_ENV "development"
	
	  <Directory "/usr/local/zend/apache2/htdocs/kargo/public">
	  DirectoryIndex index.php
	  AllowOverride All
	  Order allow,deny
	  Allow from all
	  </Directory>
	
	  ErrorLog "/usr/local/zend/apache2/htdocs/kargo/logs/error-%Y-%m.log"
	  CustomLog "/usr/local/zend/apache2/htdocs/kargo/logs/access-%Y-%m.log" combined
	</VirtualHost>
	
3. Restart apache.
4. In current application folder, locate to application/configs/application.ini file, 
   change the following into the local databse info:

	[mysql]
	db.adapter=PDO_MYSQL
	db.params.host = kargo-local.com
	db.params.username = root
	db.params.password = root
	db.params.dbname = kargo
	
5. Locate to application/sql folder, there are three essentail sql files. In your local
   database, create a database named "kargo". Then simply copy and paste the sql queries 
   into local databases.
   
6. Run the application.
