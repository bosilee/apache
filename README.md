# Apache
A simple Apache server set up installation.

The Apache web server is an open-source HTTP server for modern operating systems including Linux and Windows. It is the most popular web server on the Internet. The configuration file of Apache and the installation method vary according to different distributions of Linux. But the default document root is /var/www/html in all distributions.

It is important to note that:
 Debian and Ubuntu distributions refer to Apache as “Apache2” and the configuration file of Apache2 is /etc/apache2/apache2.conf.
CentOS refer to Apache as httpd and configuration file of httpd is /etc/httpd/httpd.conf

# Ubuntu & Debian

Run the following command to install Apache.

**apt-get install apache2**

Run the following command to start the Apache process.

**/etc/init.d/apache2 start**

Verify that the service is running by executing the following command.

**/etc/init.d/apache2 status**

Run the following command to restart Apache.

**/etc/init.d/apache2 restart**


Configure Apache server

The next step is to set up the web server configuration for the domain. The Apache configuration directory is /etc/apache2 and apache2.conf is main Apache configuration file. Each domain needs its own Virtual Host configuration file.

The configuration files use the .conf extension, and need to be saved in the /etc/apache2/sites-available/ directory.

Create a file at /etc/apache2/sites-available/yourdomain.com.conf and add the following lines to it.

**nano /etc/apache2/sites-available/yourdomain.com.conf**

<virtualhost *:80="">  
ServerAdmin webmaster@localhost  
ServerName yourdomain.com  
ServerAlias www.yourdomain.com  
DocumentRoot /var/www/yourdomain.com  
ErrorLog ${APACHE_LOG_DIR}/error.log  
CustomLog ${APACHE_LOG_DIR}/access.log combined  
</virtualhost>
Create a directory for the website and then create index.html file for the website.

**mkdir /var/www/yourdomain.com**

Add some content to index.html.

**vi /var/www/yourdomain.com/index.html**

Restart Apache service for the above changes to take effect.

**/etc/init.d/apache2 restart**

or

**sudo systemctl restart apache2**

Open any browser and enter the website URL.

http://yourdomain.com


# CentOS 6


Run the following command to install Apache.

**yum install httpd**

Run the following command to start the Apache process.

**service httpd start**

Verify that the service is running by executing the following command.

**service httpd status**

Run the following command to restart Apache.

**service httpd restart**


Configure Apache server

The next step is to set up the web server configuration for the domain. The configuration files name is httpd.conf, and the Apache configuration directory location is /etc/httpd/.

Open the apache configuration file which is /etc/httpd/conf/httpd.conf and add the following lines to the bottom of the file.

**vi /etc/httpd/conf/httpd.conf**

<virtualhost *:80="">
ServerAdmin root@yourdomain.com
ServerName yourdomain.com
DocumentRoot /var/www/html/yourdomain.com/
ErrorLog /var/log/httpd/yourdomain.com/error.log
CustomLog /var/log/httpd/yourdomain.com/access.log combined
</virtualhost>
Create a directory for the website and then create index.html file for the website.

**mkdir /var/www/html/yourdomain.com**

Now add some content to index.html.

**vi /var/www/html/yourdomain.com/index.html**

Restart Apache service for the above changes to take effect.

**service httpd restart**

Open any browser and enter the website URL.

http://yourdomain.com
