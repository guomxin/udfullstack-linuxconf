# Server login
Domain: guomxin.imwork.net, port: 2200

# Hosted application
Please visit [website](http://guomxin.imwork.net:8880).<br>
Let me illustrate the reason why the port is not 80. The server in above section is a virtual machine on my desktop whose ip is 192.168.0.190 which can't be accessed on the internet. I have hosted the site on port 80 on the virtual machine. My router's domain is guomxin.imwork.net. I have mapped the router port 8880 -> server port 80 and router port 2200 -> server 2200. So we can access the virtual machine from internet.

# Software/package installed
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install python3-pip
- sudo apt-get install apache2
- sudo apt-get install libapache2-mod-wsgi-py3
- sudo apt-get install postgresql
- pip3 install flask packaging oauth2client passlib flask-httpauth
- pip3 install sqlalchemy flask-sqlalchemy psycopg2-binary requests

# Apache configuration
The code of flask application is located in directory `/var/www/udfullstack-itemcatalog`.
- Create the site's configuration file 'itemcatalog.conf' under `/etc/apache2/sites-enabled`
<pre>
  &lt;VirtualHost *:80&gt;
    WSGIDaemonProcess itemcatalog user=grader group=grader threads=1
    WSGIScriptAlias / /var/www/udfullstack-itemcatalog/itemcatalog.wsgi

    <Directory /var/www/udfullstack-itemcatalog>
        WSGIProcessGroup itemcatalog
        WSGIApplicationGroup %{GLOBAL}
        Order deny,allow
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
  &lt;/VirtualHost&gt;
</pre>
- sudo apachectl restart

# Postgresql configuration
sudo -u postgres psql
- create user catalog with password '111111';
- create database catalogdb;
- grant all privileges on database catalogdb to catalog;
