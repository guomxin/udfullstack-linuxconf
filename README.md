# configs
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install python3-pip
sudo apt-get install apache2
sudo apt-get install libapache2-mod-wsgi-py3
sudo apt-get install postgresql
pip3 install flask packaging oauth2client passlib flask-httpauth
pip3 install sqlalchemy flask-sqlalchemy psycopg2-binary requests

# postgresql configuration
sudo -u postgres psql
- create user catalog with password '111111';
- create database catalogdb;
- grant all privileges on database catalogdb to catalog;

