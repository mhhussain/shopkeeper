# shopkeeper
Shopkeeper php application (distribution)

## Notes

* Create directory for sessions and set the session file path in config.php
* Create directory at /opt/bitnami/apache2/configs
* Copy all config files from ~/application/config to /opt/bitnami/apache2/configs

To install this application, spin up a LAMP server via AWS Lightsails.

## remove default website

`cd /opt/bitnami/apache2/htdocs `

`rm -rf *`

## clone github repo

`git clone https://github.com/mhhussain/shopkeeper.git .`

## set write permissons on the settings file

`sudo chmod 777 /opt/bitnami/apache2/htdocs/writable`

`sudo chmod 777 /opt/bitnami/apache2/htdocs/writable/sessions`

## inject database password into configuration file

`cat /home/bitnami/bitnami_application_password`

## create database

`cat /opt/bitnami/apache2/htdocs/artifacts/shopkeeper.sql | /opt/bitnami/mysql/bin/mysql -u root -p$(cat /home/bitnami/bitnami_application_password)`

## restart apache

`sudo /opt/bitnami/ctlscript.sh restart apache`