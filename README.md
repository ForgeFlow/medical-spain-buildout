# medical-spain-buildout
Odoo Buildout for Vertical Medical in Spain

# Tutorial for Odoo installation
[! [Build Status] (https://travis-ci.org/Eficent/medical-spain-buildout.svg?branch=10.0)] (https://travis-ci.org/Eficent/medical-spain-buildout )

Buildout for installation of Odoo with OCA Vertical Medical and OCA Spanish Localization. Tested on Ubuntu 16.04.

## Use

Install the PostgreSQL database
> sudo apt-get install postgresql
> sudo su - postgres

Create an Odoo user for postgres
> createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt odoo

Enter the password for the user Odoo. For testing purposes it is a good idea to use "odoo".
> Enter password for new role: ******* (Your password for the user postgres 'odoo')

> Enter it again: *******

Clone the repository:
> git clone https://github.com/Eficent/medical-spain-buildout.git odoo

Run the bootstrap. 
> python bootstrap.py

The following directory structure will be created

Bash

Odoo
> bin
> bootstrap.py
> buildout.cfg
> default.cfg
> develop-eggs
> downloads
> eggs
> nfe_xml└── 
> parts
> Scenario
> specific-parts
> src
> upgrade.py
> README.md
> var

Install the dependencies of some Python libs that Odoo uses. If they are not installed, the buildout will fail.

> sudo apt-get -y install build-essential checkinstall cdbs devscripts dh-make make fakeroot libxml-parser-perl check avahi-daemon curl vim g ++ python-setuptools python-pip python-dev xmlsec1 openssl python-lxml libxmlsec1 libxmlsec1-dev libjpeg -dev libfreetype6-dev zlib1g-dev libpng12-dev python-suds libpq-dev libsasl2-dev python-dev libldap2-dev libssl-dev pkg-config libpng-dev libjpeg8-dev libfreetype6-dev

Now run the Odoo installation with the command

> bin/buildout

The development version already comes with the * password * and postgres database port configured.

`Buildout` will run and download the modules and dependencies. With the execution being successful, we can now run Odoo. Do not forget to edit the `etc / odoo.cfg` file information.
 In this file you must add username and password that you have created for Odoo in Postgres
 
> bin/start_odoo

Now just open a browser (preferably google chrome) and access `Odoo` at:

> localhost: 8069

### To "freeze" the version of each module and dependency

After successfully executing the buildout, simply use the following command:

> bin/buildout -o odoo: freeze-to = odoo-freeze.cfg 

A file named `odoo-freeze.cfg` will be created with the dependencies and commits of each module. Thus
We have more control over the version of the modules and depedences that we use.

To use `freeze` just run

> bin/buildout -c odoo-freeze.cfg 
