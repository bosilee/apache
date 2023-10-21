# Apache
A simple Apache server set up installation.

The Apache web server is an open-source HTTP server for modern operating systems including Linux and Windows. It is the most popular web server on the Internet. The configuration file of Apache and the installation method vary according to different distributions of Linux. But the default document root is /var/www/html in all distributions.

It is important to note that:
 Debian and Ubuntu distributions refer to Apache as “Apache2” and the configuration file of Apache2 is /etc/apache2/apache2.conf.
CentOS refer to Apache as httpd and configuration file of httpd is /etc/httpd/httpd.conf

# Ubuntu & Debian

Update Linux:

**sudo apt update**

install Apache:

**sudo apt-get install apache2**

Start the Apache process:

**sudo /etc/init.d/apache2 start**

Verify that the service is running:

**sudo /etc/init.d/apache2 status**

Restart Apache:

**/etc/init.d/apache2 restart**

check status:

**systemctl status apache2**

You should see the apache home page

# CentOS 6


Run the following command to install Apache.

**yum install httpd**

Start the Apache process.

**service httpd start**

Verify that the service is running:

**service httpd status**

Restart Apache:

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
